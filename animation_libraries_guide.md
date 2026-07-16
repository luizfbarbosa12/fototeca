# Deep Dive: Free Animation Libraries for Web (2025-2026)

A comprehensive overview of what's possible to animate for free using modern JavaScript libraries.

---

## TL;DR: The Landscape

| Library | Size | Best For | Learning Curve | Free? |
|---------|------|----------|-----------------|-------|
| **Motion** (React) | 12KB | React-based UI animations | Easy | ✅ MIT Licensed |
| **GSAP** | 22KB (core) | Complex timelines, scroll, SVG | Medium | ✅ 100% Free (Apr 2025) |
| **Anime.js** | 17KB | Lightweight, elegant animations | Easy | ✅ Open Source |
| **Three.js** | 150KB+ | 3D graphics, WebGL | Hard | ✅ Open Source |
| **Popmotion** | 11.7KB | Functional, physics-based motion | Medium | ✅ Open Source |
| **Lottie** | 40KB | After Effects → JSON animations | Easy | ✅ Open Source (Airbnb) |
| **Theatre.js** | 50KB | Visual timeline editor | Hard | ✅ Open Source |
| **Mo.js** | 20KB | Motion graphics, bursts | Medium | ✅ Open Source |

---

## 1. MOTION (Formerly Framer Motion) — The React King

**Status:** Rebranded in 2025 to "Motion," became independent project  
**License:** MIT (100% free)  
**Package:** `motion/react` (was `framer-motion`)

### What You Can Animate
- DOM elements (divs, spans, etc.)
- SVG paths, strokes, fills
- CSS properties (transform, opacity, colors)
- Layout shifts with layout animations
- Gesture-based animations (drag, hover, whileInView)
- Automatic scrolling triggers

### Key Capabilities

**1. Declarative Animation API**
```javascript
<motion.div
  initial={{ opacity: 0, scale: 0.8 }}
  animate={{ opacity: 1, scale: 1 }}
  transition={{ duration: 0.5, ease: "easeOut" }}
>
  Animated content
</motion.div>
```

**2. SVG Path Animation**
- Draw SVG paths with `pathLength`, `pathSpacing`, `pathOffset`
- Perfect for logo reveals, signatures, line drawings
- Morph between shapes using `motion.path`

**3. Layout Animations**
- Animate when elements change position/size
- Single `layout` prop handles the complexity
- Smooth transitions between grid/flex layout changes

**4. Scroll-Triggered Animations**
- `whileInView` trigger when element enters viewport
- Combine with scroll position for parallax
- `useScroll()` hook for scroll progress

**5. Drag & Drop**
- One-line drag implementation
- Physics-based momentum with `momentum`
- Constrain to boundaries with `whileDrag`

### Best Use Cases
- React component animations
- Interactive UI micro-interactions
- SVG logo animations & reveals
- Scroll-triggered entrance animations
- Drag-and-drop interfaces
- Layout transitions in dashboards

### Free Features (Everything)
Motion is 100% free with no paid tier. Premium Motion Kit (paid) offers pre-built components, not core animation features.

---

## 2. GSAP — The Professional Powerhouse

**Status:** 100% FREE as of April 2025 (Webflow acquisition)  
**License:** MIT Licensed  
**Community:** 11+ million production sites

### What You Can Animate
- **DOM**: Any CSS property, transforms, dimensions
- **SVG**: Paths, attributes, morphing, drawing
- **Canvas**: Coordinates driving animations
- **WebGL/Three.js**: Model properties
- **Text**: Character-by-character, words, lines
- **Objects**: Any JavaScript object properties
- **Colors**: Full color space support

### Key Plugins (All Free Now)

**ScrollTrigger** — The Most Powerful
```javascript
gsap.registerPlugin(ScrollTrigger);

gsap.to(".element", {
  scrollTrigger: {
    trigger: ".element",
    start: "top center",
    end: "bottom center",
    scrub: 1, // smooth scrub to scroll
    pin: true, // pin element while scrolling
    markers: true
  },
  y: 500,
  duration: 3
});
```
- Pin sections to viewport
- Scrub animations to scroll position
- Snap points and velocity tracking
- Horizontal scrolling sequences
- Parallax effects

**MorphSVG** — Shape Transformations
- Morph one SVG shape to another (any point count)
- Create liquid-like distortions
- Complex shape transitions with ease

**DrawSVG** — Stroke Animation
- Animate stroke from 0% to 100% drawn
- Perfect for: logos, signatures, circuit traces
- Drawing along paths
- Custom stroke animations

**SplitText** — Text Effects (Rewritten 2025)
- Split text into: characters, words, lines
- Stagger animations per unit
- Reveal effects: fade, scale, blur, rotate, clip
- 50% smaller in 2025 version
- Native accessibility for screen readers

**Draggable** — Gesture Control
- Drag elements smoothly
- Inertia/momentum physics
- ThrowProps for realistic deceleration
- Multi-touch support
- Snap to grid/points

**Physics2D** — Physics Engine
- Gravity simulations
- Velocity/acceleration
- Collision detection
- Perfect for particle systems, confetti, bouncing

**MotionPathPlugin** — Path Animation
- Animate objects along SVG paths
- Rotation follows path automatically
- Custom easing along path
- Rollercoaster effects, orbital paths

### Timeline Orchestration (Core Feature)
```javascript
const tl = gsap.timeline();

tl.to(".box", { duration: 1, x: 100 })
  .to(".box", { duration: 1, rotation: 360 }, 0) // parallel
  .to(".circle", { duration: 0.5, y: -50 }, 0.5) // offset
  .addLabel("midpoint")
  .to(".text", { opacity: 1 }, "midpoint");

// Control timeline
tl.play();
tl.reverse();
tl.seek("midpoint");
```

### Performance Excellence
- 20x faster than jQuery animations
- Hardware-accelerated transforms
- Consistent 60 FPS on mid-range devices
- Optimized for mobile performance

### Best Use Cases
- Award-winning portfolio sites
- Complex scroll sequences (pinning, parallax)
- SVG morphing and logo reveals
- Text animations (split reveals, scramble)
- Interactive galleries with momentum
- Animated dashboards & data visualizations
- Page transitions & fullscreen reveals

### What Makes GSAP Free Now?
- Core library: Always free
- All plugins (ScrollTrigger, MorphSVG, DrawSVG, SplitText, Physics2D, Draggable, etc.): Free since April 2025
- Commercial use: 100% allowed
- No attribution required

---

## 3. Anime.js — Lightweight Elegance

**Size:** 17KB (smaller than Motion)  
**License:** MIT Open Source  
**Best For:** Simple, elegant animations with minimal overhead

### What You Can Animate
- CSS properties (transforms, colors, opacity)
- DOM attributes
- SVG elements and paths
- JavaScript objects
- Canvas properties
- Layered, cascading animations

### Key Features

**1. Simple API**
```javascript
anime({
  targets: '.element',
  translateX: 250,
  rotate: '360deg',
  backgroundColor: '#FFF',
  duration: 800,
  easing: 'easeInOutQuad'
});
```

**2. Built-in Stagger System**
```javascript
anime.timeline()
  .add({
    targets: '.item',
    translateY: -20,
    opacity: 1,
    delay: anime.stagger(100), // 100ms between each
    duration: 800
  });
```

**3. Timeline Management**
- Synchronize multiple animations
- Control playback (play, pause, reverse)
- Callback functions on completion

**4. SVG Support**
- Animate SVG attributes
- Morph between paths
- Line drawing effects

### Best Use Cases
- Loading animations
- Button hover effects
- Modal enter/exit animations
- Smooth scrolling libraries
- Lightweight UI frameworks
- Mobile-first projects (small bundle size)

---

## 4. Three.js — 3D & WebGL

**GitHub Stars:** 102K+  
**License:** MIT Open Source  
**The Standard:** De facto standard for web 3D

### What You Can Animate
- 3D mesh positions, rotations, scales
- Camera movements and zoom
- Lighting (position, intensity, color)
- Material properties (color, opacity, metalness)
- Texture animations
- Particle systems
- WebGL post-processing effects

### Capabilities

**Scenes & Models**
```javascript
const scene = new THREE.Scene();
const mesh = new THREE.Mesh(geometry, material);
scene.add(mesh);

// Animate in render loop
function animate() {
  mesh.rotation.x += 0.01;
  mesh.rotation.y += 0.01;
  renderer.render(scene, camera);
  requestAnimationFrame(animate);
}
```

**What's Possible**
- Interactive 3D product configurators
- Data visualizations (3D charts, graphs)
- Immersive gaming experiences
- Virtual showrooms
- Augmented reality (AR) with WebXR
- Procedurally generated worlds
- Physics-based cloth simulations
- Particle effects (rain, snow, fire)
- Custom shader animations

### Why It's Powerful
- Abstracts WebGL complexity
- Massive ecosystem of loaders (GLTF, OBJ, FBX, Collada)
- Support for: textures, shadows, lighting, cameras, post-processing
- Real-time ray tracing capabilities
- VR/AR ready with WebXR support

### Learning Curve
Steeper than other libraries, but worth it for 3D work. Excellent documentation and 10,000+ examples.

### Best Use Cases
- 3D product visualization
- Interactive data visualizations
- Game development
- Virtual reality experiences
- Architectural visualizations
- Physics simulations

---

## 5. Lottie — After Effects to Web

**Creator:** Airbnb (open-sourced)  
**Format:** JSON-based (vector animations)  
**Size:** Tiny (often <50KB for complex animations)

### The Workflow
1. **Design:** Create animation in Adobe After Effects
2. **Export:** Use Bodymovin/LottieFiles plugin to export as JSON
3. **Deploy:** Drop JSON file into web/app with Lottie player
4. **Scale:** Vector format scales perfectly to any size

### What You Can Animate
- Vector graphics (shapes, paths, fills, strokes)
- Text (typographic animations)
- Transforms (position, rotation, scale)
- Opacity and complex layering
- Mask animations
- Adjustable timing and easing
- Interactive playback (play, pause, speed, direction)

### Key Advantages
```javascript
// Super simple to use
lottie.loadAnimation({
  container: document.getElementById('lottie'),
  renderer: 'svg',
  loop: true,
  autoplay: true,
  path: 'animation.json'
});

// Control it
lottie.setSpeed(0.5); // half speed
lottie.play();
lottie.setDirection(-1); // reverse
```

**Dynamically Update at Runtime**
```javascript
// Change colors, swap assets without re-exporting
animation.renderer.elements[0].style.fill = '#FF0000';
```

### File Sizes (Compare to Alternatives)
- Lottie JSON: 20-50KB (typical)
- GIF of same animation: 500KB-2MB
- PNG sequence: 5-50MB
- Video: 100KB-10MB (but rasterized)

### Limitations
- Designed for "playback" animations, not interactive
- Some After Effects features not supported
- Performance on low-end devices needs optimization

### Best Use Cases
- Loading screens and spinners
- Success/error states
- Onboarding animations
- Empty states and illustrations
- Marketing animations
- Illustrations that need to be animated
- Mobile app animations (works iOS/Android too)

---

## 6. Popmotion — Functional Animation

**Size:** 11.7KB (tiny)  
**Philosophy:** Functional, composable, framework-agnostic  
**Powers:** Built the foundation for Motion (Framer Motion)

### What You Can Animate
- Numbers and colors
- Complex strings (SVG paths, CSS box-shadows)
- Spring physics animations
- Decay/inertia animations
- Keyframe sequences
- Staggered animations

### Key Features

**Spring Physics**
```javascript
import { spring, value } from 'popmotion';

spring({
  from: 0,
  to: 100,
  stiffness: 300,
  damping: 10,
  onUpdate: (latest) => console.log(latest)
}).start();
```

**Multi-type Animation**
```javascript
import { animate } from 'popmotion';

animate({
  from: { x: 0, background: 'red' },
  to: { x: 100, background: 'blue' },
  duration: 1000,
  onUpdate: (v) => element.style.transform = `translateX(${v.x}px)`
});
```

**Modular & Composable**
- Only import what you need
- 4.5KB for core animate function
- Compose complex animations from primitives

### Best Use Cases
- React component motion (before Motion library)
- Gesture-driven animations
- Physics-based interactions
- Custom animation engines
- WebGL/Three.js property animation
- Lightweight motion for performance-critical apps

---

## 7. Theatre.js — Visual Timeline Editor

**Concept:** Timeline-based animation with visual editor  
**Best For:** Cinematic sequences, choreographed animations

### What Makes It Unique
```javascript
import { getProject } from '@theatre/core';

const sheet = getProject("MySheet").sheet("Sheet");

// Track values over time with keyframes
const obj = sheet.object("obj", {
  position: { x: 0, y: 0 },
  rotation: 0
});

obj.position.x.onValuesChange(v => {
  element.style.transform = `translateX(${v}px)`;
});

// Edit keyframes visually in the editor
sheet.sequence.play();
```

### Capabilities
- Synchronized multi-object animation
- Visual timeline editor in browser
- Keyframe management GUI
- Works with Three.js for 3D scenes
- State snapshots for reproducibility

### Best Use Cases
- Long, choreographed animations
- Cinematic sequences
- Collaborative design → dev workflows
- Complex multi-element choreography

---

## 8. CSS Animations & View Timeline API (Native)

**Zero Dependencies:** Built into browsers  
**2025+ Advantage:** View Timeline API closes the "GSAP gap"

### CSS Animations (Always Available)
```css
@keyframes slide {
  from { transform: translateX(0); }
  to { transform: translateX(100px); }
}

.element {
  animation: slide 1s ease-in-out forwards;
}
```

**Strengths:**
- No JavaScript needed
- Hardware accelerated
- Great performance
- Respects `prefers-reduced-motion`

**Limitations:**
- Limited control
- No complex sequencing
- Can't respond to runtime input easily

### View Timeline API (Chrome 115+, Safari 17.4+)

**Scroll-Driven Animations (No Plugin Needed)**
```css
.element {
  animation: slide linear;
  animation-timeline: view();
}

@keyframes slide {
  from { transform: translateX(0); }
  to { transform: translateX(100px); }
}
```

**What It Enables**
- Animations tied to scroll progress
- Element-specific view ranges
- Reduce bundle size for simple scroll animations
- 22KB less (no ScrollTrigger needed)

### CSS + JavaScript Hybrid
```javascript
element.addEventListener('scroll', () => {
  const progress = scrollPosition / maxScroll;
  element.style.transform = `rotate(${progress * 360}deg)`;
});
```

### When to Use CSS vs JavaScript
- **Pure CSS:** Simple fades, slides, basic hover states
- **CSS View Timeline:** Simple scroll-triggered entrance effects
- **JavaScript (GSAP/Motion):** Complex sequences, multiple triggers, runtime control

---

## 9. Practical Capability Matrix

### Backgrounds
| Feature | CSS | Motion | GSAP | Anime.js | Three.js |
|---------|-----|--------|------|----------|----------|
| Gradient shift | ✅ | ✅ | ✅ | ✅ | ✅ |
| Parallax layers | ⚠️ | ✅ | ✅ | ✅ | ✅ |
| Animated particles | ❌ | ✅ | ✅ | ⚠️ | ✅✅ |
| Fluid/gooey effects | ❌ | ⚠️ | ✅ | ⚠️ | ✅ |
| WebGL effects | ❌ | ❌ | ❌ | ❌ | ✅✅ |
| SVG morphing | ❌ | ✅ | ✅✅ | ✅ | ❌ |

### SVG & Vectors
| Feature | CSS | Motion | GSAP | Lottie | Three.js |
|---------|-----|--------|------|--------|----------|
| SVG path draw | ⚠️ | ✅ | ✅✅ | ✅ | ⚠️ |
| Shape morph | ❌ | ✅ | ✅✅ | ✅ | ✅ |
| Stroke animation | ⚠️ | ✅ | ✅✅ | ✅ | ⚠️ |
| Text animation | ❌ | ⚠️ | ✅✅ | ✅ | ⚠️ |
| After Effects export | ❌ | ❌ | ❌ | ✅✅ | ❌ |

### Scroll & Interactive
| Feature | CSS | Motion | GSAP | View Timeline |
|---------|-----|--------|------|----------------|
| Entrance animation | ✅ | ✅✅ | ✅✅ | ✅ |
| Pin section | ❌ | ⚠️ | ✅✅ | ❌ |
| Scroll scrub | ❌ | ⚠️ | ✅✅ | ✅ |
| Parallax | ⚠️ | ✅ | ✅✅ | ❌ |
| Drag/gesture | ❌ | ✅✅ | ✅ | ❌ |

---

## 10. Real-World Examples (What's Actually Possible)

### 1. Animated Hero Background
**Stack:** GSAP + Canvas
- Particle system following mouse
- Gradient animation
- SVG elements morphing in background
- Scroll-triggered reveal of content
**File size:** 22KB (GSAP core)

### 2. Product Showcase
**Stack:** Three.js + GSAP
- 3D rotating model
- Interactive camera control
- Timeline-synchronized UI animations
- Add to cart with physics bounce
**File size:** ~150KB (Three.js)

### 3. After Effects Animation on Website
**Stack:** Lottie
- Design beautiful animation in AE
- Export as JSON (<40KB)
- Embed with single line of code
- Works on web, iOS, Android
**File size:** <50KB typical

### 4. Scroll Storytelling
**Stack:** GSAP ScrollTrigger + SVG
- Multiple sections pinning
- SVG illustrations drawing themselves
- Text reveals character-by-character
- Parallax backgrounds
- Velocity-based animations
**File size:** 22KB (GSAP core + ScrollTrigger plugin)

### 5. Interactive UI with Gestures
**Stack:** Motion (React) + Framer
- Drag-and-drop cards
- Magnetic buttons (attract to cursor)
- Layout animations on state change
- Scroll-triggered list reveals
**File size:** 12KB (Motion)

### 6. Data Visualization
**Stack:** Three.js or D3 + Motion
- Animated 3D charts
- Real-time data updates
- Interactive drill-down
- Multiple synchronized animations

### 7. Micro-interactions
**Stack:** Anime.js or Motion
- Button ripple effects
- Input focus animations
- Toast notifications
- Loading spinners
- Icon animations
**File size:** 12-17KB

---

## 11. Bundle Size Comparison

```
CSS (native)        0KB    ✅ Best for simple animations
View Timeline API   0KB    ✅ Best for scroll (modern browsers)
Popmotion          11.7KB  ✅ Tiny, functional
Motion             12KB    ✅ React-focused, compact
Anime.js           17KB    ✅ Lightweight, versatile
Mo.js              20KB    ✅ Motion graphics
GSAP (core)        22KB    ✅ + plugins: ScrollTrigger(35KB), SplitText(15KB)
Theatre.js         50KB    ⚠️  Overkill for simple animations
Lottie             40KB    ✅ Worth it for complex AF animations
Three.js           150KB+  ⚠️  Only for 3D/WebGL work
```

### Production Reality
- Most sites combine: CSS (80%) + GSAP/Motion (for 15%) + Lottie (for 5%)
- Modern bundlers tree-shake unused code
- Gzip compression reduces actual network size by 50-70%

---

## 12. Choosing Your Stack

### Quick Decision Tree

**Just React Components?**
→ Motion (12KB, easiest API, MIT)

**Need Scroll Magic & Advanced Timeline?**
→ GSAP (22KB core, all plugins free now)

**After Effects Animations?**
→ Lottie (piggyback on designer's work, <50KB)

**3D/WebGL Product Visualization?**
→ Three.js (150KB+ but necessary)

**Tiny Bundle, Lightweight Site?**
→ CSS + View Timeline API + Anime.js (17KB)

**Complex Choreography with Visual Editor?**
→ Theatre.js (50KB but incredible workflows)

**Performance-Critical Mobile?**
→ CSS + Anime.js + selective GSAP plugins

---

## 13. 2026 Trends & What's Free

### The Big Shift: Everything's Free Now
- GSAP: 100% free as of April 2025 (was paid)
- Motion: MIT licensed
- Three.js: MIT licensed
- Lottie: Open source (Airbnb)
- All plugins: Free, no paywall

### Emerging Standards
- **View Timeline API:** Native scroll animations without plugin (Chrome 115+)
- **dotLottie:** Compressed Lottie format, even smaller files
- **Motion Kit:** Premium components (optional), not required
- **Webflow Integration:** GSAP native in Webflow Interactions

### What's NOT Free
- Design tools (Figma animations → free exports)
- 3D modeling (Spline free tier exists)
- Video editing for After Effects (Creative Cloud subscription)

---

## 14. Project Context: Fototeca Artistic Portfolio

This guide is being consulted in the context of building an artistic photography portfolio for **Fototeca**, a nightlife photographer. That context introduces specific requirements that should inform animation library choices:

### Fluid Transitions Are a Hard Requirement

This is not a product landing page or a corporate portfolio. It is a work of art built around a day-to-night atmospheric transition. **Abrupt, mechanical, or "web-like" transitions are unacceptable.** Every animation must feel organic, continuous, and immersive.

- **Scroll-scrubbed animations** (GSAP ScrollTrigger or CSS View Timeline) are strongly preferred over snap-triggered state changes
- **Easing must be soft** — ease-in-out curves, custom beziers, or spring physics; never linear or snap
- **No hard section cuts.** Sections bleed into one another. The transition zone between daytime and nighttime is the product, not a loading screen

### Image-Driven Transition

Fototeca's own photographs (sourced from a local images folder) are active participants in the transition, not passive content at the end of it. This means:
- Images should fade or dissolve into view during the scroll transition, not appear all at once in a grid
- Photo opacity, blur, and color overlay can be tied to scroll position
- Libraries that handle `opacity`, `filter`, and CSS property scrubbing well are valuable here — GSAP ScrollTrigger and CSS custom properties are ideal

### Desktop & Mobile Are Both Primary Targets

The site must deliver the full atmospheric experience on both desktop and mobile. Animation choices must account for this:
- Scroll-scrubbed transitions must feel natural with touch scrolling on mobile, not just mouse wheels on desktop
- Parallax effects should be reduced or disabled on mobile to avoid performance issues and motion sickness
- Hover states (used heavily on photo cards) need touch-equivalent interactions (`:active`, tap events) on mobile
- Test animation frame rates on mid-range mobile hardware, not just desktop Chrome

Libraries like GSAP ScrollTrigger and Motion handle touch scroll events natively. CSS View Timeline also works with touch scroll. Any custom scroll listener must be tested on iOS Safari specifically, which has historically quirky scroll behavior.

### Decorative Asset Question (Open)

The site needs ornamental elements (stars, textures, geometric shapes) beyond photography. The sourcing of these assets is **not yet decided**:
- **Free SVG libraries** (SVG Repo, The Noun Project, Heroicons) — broad selection, needs curation
- **Hand-picked assets** from various free sources — more control, more time
- **Custom minimal SVGs** — perfect fit, requires design work

Once assets are decided, the animation approach for them (CSS keyframe twinkle, GSAP entrance, Lottie loop) can be finalized. SVG-heavy decorative elements pair particularly well with **GSAP DrawSVG** or **Motion** for entrance animations.

---

## 15. Getting Started

### Installation

**Motion/React**
```bash
npm install motion
```

**GSAP**
```bash
npm install gsap
```

**Anime.js**
```bash
npm install animejs
```

**Three.js**
```bash
npm install three
```

**CDN (No Build Tools)**
```html
<script src="https://cdn.jsdelivr.net/npm/gsap@3.15/dist/gsap.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/gsap@3.15/dist/ScrollTrigger.min.js"></script>
```

---

## 15. Resources & Documentation

| Library | Docs | Examples | Community |
|---------|------|----------|-----------|
| Motion | motion.dev | 400+ copy-paste examples | Very active (Framer team) |
| GSAP | gsap.com/learn | GSAPify (100+ effects) | Largest community |
| Anime.js | animejs.com | CodePen collection | Active but smaller |
| Three.js | threejs.org | 10,000+ examples | Massive, game dev focused |
| Lottie | lottie.airbnb.tech | LottieFiles library | Growing motion designer community |
| Theatre.js | theatrejs.com | Visual editor included | Design tools integrating |

---

## Summary: What's Possible for FREE in 2026

✅ **Complex SVG morphing & drawing animations** (GSAP MorphSVG, DrawSVG)  
✅ **Scroll-triggered parallax & pinning** (GSAP ScrollTrigger)  
✅ **Interactive 3D graphics** (Three.js)  
✅ **After Effects animations on web** (Lottie)  
✅ **Drag-and-drop with physics** (Motion, GSAP Draggable)  
✅ **Text character-by-character reveals** (GSAP SplitText)  
✅ **Particle systems & physics** (GSAP Physics2D, Three.js)  
✅ **Timeline choreography** (Theatre.js, GSAP timeline)  
✅ **Native scroll animations** (CSS View Timeline API)  
✅ **Gesture-based UI animation** (Motion gestures)  

**Nothing is paywall-locked anymore.** The entire professional web animation ecosystem is free.
