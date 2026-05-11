# HTML Template

Use this architecture for generated interview decks. Keep the file self-contained unless local image assets are needed.

## Required Structure

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Case Study Deck</title>
    <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Manrope:wght@500;700;800&family=Source+Sans+3:wght@400;600&display=swap" />
    <style>
      :root {
        --bg: #f7f7f4;
        --surface: #ffffff;
        --ink: #151515;
        --muted: #686b70;
        --line: #d9d8d2;
        --accent: #1f6feb;
        --accent-soft: #dbeafe;
        --font-display: "Manrope", sans-serif;
        --font-body: "Source Sans 3", sans-serif;
        --slide-padding: clamp(1rem, 4vw, 4rem);
      }

      /* Paste viewport-base.css here. */

      body {
        margin: 0;
        background: var(--bg);
        color: var(--ink);
        font-family: var(--font-body);
      }

      .slide {
        background: var(--bg);
      }

      .slide-content {
        gap: clamp(0.75rem, 2vw, 2rem);
      }

      h1,
      h2,
      h3 {
        font-family: var(--font-display);
        letter-spacing: 0;
      }

      .eyebrow {
        color: var(--accent);
        font-size: var(--small-size);
        font-weight: 700;
        text-transform: uppercase;
      }

      .screenshot {
        max-height: min(58vh, 560px);
        border: 1px solid var(--line);
        border-radius: 10px;
        object-fit: contain;
      }

      .reveal {
        opacity: 0;
        transform: translateY(18px);
        transition:
          opacity 420ms ease,
          transform 420ms ease;
      }

      .slide.visible .reveal {
        opacity: 1;
        transform: translateY(0);
      }
    </style>
  </head>
  <body>
    <main>
      <section class="slide title-slide">
        <div class="slide-content">
          <p class="eyebrow reveal">Interview Case Study</p>
          <h1 class="reveal">Project / Case Title</h1>
          <p class="lede reveal">One-sentence positioning statement.</p>
        </div>
      </section>

      <section class="slide">
        <div class="slide-content">
          <p class="eyebrow reveal">Decision</p>
          <h2 class="reveal">Slide title states the point</h2>
          <p class="reveal">Short evidence-backed message.</p>
        </div>
      </section>
    </main>

    <nav class="nav-dots" aria-label="Slide navigation"></nav>

    <script>
      class SlideDeck {
        constructor() {
          this.slides = Array.from(document.querySelectorAll(".slide"));
          this.index = 0;
          this.nav = document.querySelector(".nav-dots");
          this.buildNav();
          this.observe();
          this.bindKeys();
          this.bindTouch();
          this.goTo(0);
        }

        buildNav() {
          if (!this.nav) return;
          this.nav.innerHTML = "";
          this.slides.forEach((_, i) => {
            const button = document.createElement("button");
            button.type = "button";
            button.setAttribute("aria-label", `Go to slide ${i + 1}`);
            button.addEventListener("click", () => this.goTo(i));
            this.nav.appendChild(button);
          });
        }

        observe() {
          const observer = new IntersectionObserver(
            (entries) => {
              entries.forEach((entry) => {
                if (entry.isIntersecting) {
                  this.index = this.slides.indexOf(entry.target);
                  entry.target.classList.add("visible");
                  this.updateNav();
                }
              });
            },
            { threshold: 0.6 }
          );
          this.slides.forEach((slide) => observer.observe(slide));
        }

        bindKeys() {
          document.addEventListener("keydown", (event) => {
            if (["ArrowDown", "ArrowRight", " ", "PageDown"].includes(event.key)) {
              event.preventDefault();
              this.goTo(this.index + 1);
            }
            if (["ArrowUp", "ArrowLeft", "PageUp"].includes(event.key)) {
              event.preventDefault();
              this.goTo(this.index - 1);
            }
          });
        }

        bindTouch() {
          let startY = 0;
          window.addEventListener("touchstart", (event) => {
            startY = event.touches[0].clientY;
          });
          window.addEventListener("touchend", (event) => {
            const delta = startY - event.changedTouches[0].clientY;
            if (Math.abs(delta) > 40) this.goTo(this.index + (delta > 0 ? 1 : -1));
          });
        }

        goTo(index) {
          const next = Math.max(0, Math.min(index, this.slides.length - 1));
          this.slides[next].scrollIntoView({ behavior: "smooth" });
          this.index = next;
          this.updateNav();
        }

        updateNav() {
          if (!this.nav) return;
          Array.from(this.nav.children).forEach((button, i) => {
            button.toggleAttribute("aria-current", i === this.index);
          });
        }
      }

      new SlideDeck();
    </script>
  </body>
</html>
```

## Slide Content Rules

- Title slide: project name, role, and one positioning sentence.
- Case setup: problem, audience, constraints, and stakes.
- Decision slides: show a specific choice, the alternatives, and why the chosen path won.
- Visual walkthrough: use large screenshots with annotations, not tiny galleries.
- Outcome slide: separate confirmed outcomes from inferred learnings.

## Asset Rules

- Put images in `assets/` beside the HTML file.
- Use relative paths like `assets/final-flow.png`.
- Add meaningful `alt` text.
- Do not base64-embed large screenshots.
