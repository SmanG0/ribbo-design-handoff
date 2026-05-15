# Ribbo UI Design Handoff

Two standalone HTML previews for the dev team to implement. Open each file in your browser — no build step, no dependencies.

---

## Files

### `typing-animation.html`
New liquid glass typing indicator to replace the current gray bubble.

- Side-by-side before/after comparison (animated + static)
- In-context preview inside a chat widget
- Full CSS implementation reference with exact property values
- Specifies which lines to change in `HeroDemo.tsx` and `Playground.tsx`

### `hero-variations.html`
Redesigned hero section right column + 6 brand variation showcases.

- Hero section mockup: 3 differently branded chatbots (fan arrangement) instead of one
- Full gallery of 6 complete brand variants: coffee shop, e-commerce, healthcare, finance, beauty, tech
- Each variant shows a different color, icon, and brand identity
- All 6 use the new liquid glass typing indicator

---

## What to implement

### 1. Typing indicator (both files reference this)

Replace the current gray bubble in:
- `components/HeroDemo.tsx` lines 143–154
- `components/Playground.tsx` lines 304–308

Add to `app/globals.css`:
```css
.typing-glass {
  background: rgba(255, 255, 255, 0.72);
  backdrop-filter: blur(24px) saturate(200%);
  -webkit-backdrop-filter: blur(24px) saturate(200%);
  border: 1px solid rgba(255, 255, 255, 0.82);
  box-shadow:
    0 8px 32px rgba(66, 73, 255, 0.20),
    0 2px 8px rgba(0, 0, 0, 0.06),
    inset 0 1px 0 rgba(255, 255, 255, 0.96);
  border-radius: 18px 18px 18px 4px;
  padding: 13px 17px;
  display: flex;
  gap: 6px;
  align-items: center;
}

.typing-dot {
  width: 7px;
  height: 7px;
  border-radius: 50%;
  background: linear-gradient(135deg, #4249ff, #8b5cf6);
  animation: liquid-pulse 1.05s cubic-bezier(0.45, 0, 0.55, 1) infinite;
}
.typing-dot:nth-child(2) { animation-delay: 0.21s; }
.typing-dot:nth-child(3) { animation-delay: 0.42s; }

@keyframes liquid-pulse {
  0%, 100% {
    transform: scale(0.62) translateY(2px);
    opacity: 0.32;
    box-shadow: 0 0 4px rgba(66, 73, 255, 0.12);
  }
  50% {
    transform: scale(1.18) translateY(-2px);
    opacity: 1;
    box-shadow: 0 0 16px rgba(66, 73, 255, 0.58), 0 0 5px rgba(139, 92, 246, 0.38);
  }
}
```

JSX usage:
```jsx
<div className="typing-glass">
  <span className="typing-dot" />
  <span className="typing-dot" />
  <span className="typing-dot" />
</div>
```

### 2. Hero section right column (`components/Hero.tsx`)

Replace the single `<HeroDemo />` on the right with 3 mini branded chatbot windows in a fan arrangement. See `hero-variations.html` Section 1 for the exact layout, positioning, and brand configurations.

The concept: instead of cycling through conversations in one widget, show 3 simultaneously branded widgets that communicate "looks like your brand" at a glance.

---

## Design system

The liquid glass spec lives at `~/Desktop/Ribbo/liquid-glass.md` — all glass utilities are already in `app/globals.css` (`.glass`, `.glass-card`, etc.). The typing indicator uses the same four-ingredient formula (translucent bg + backdrop blur + border + inset highlight).

---

## Questions

Contact Saahil — saahil@ribbo.ai
