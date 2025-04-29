# VR/AR/XR Interaction Guidelines

This document outlines a community-molded list of details that make good VR/AR/XR interactions. It is a collection of structures to make good interactions within the virtual, augmented & mixed reality worlds. Periodically updated based on community and standards. Some of these may be subjective, but most apply to all interactions.

Contributions are welcome. Edit [this file](README.md) and submit a pull request.

## Imersion

- Mimic as most real life physics as possible
- Sound physics can help in accessibility and immersion

## Interactivity

- Generally, your body and objects should **not** break any laws of physics unless it's on purpose
- - it's ok to be able to pass through a slime, it isn't to pass your hand through solid bricks
- Adjust values fluidly by using CSS [`clamp()`](https://developer.mozilla.org/en-US/docs/Web/CSS/clamp), e.g. `clamp(48px, 5vw, 72px)` for the `font-size` of a heading
- Fonts should have some sort of smoothing applied for better legibility
- Fonts should be subset based on the content, alphabet or relevant language(s)
- Font weights below 200 should not be used
- Prevent text resizing unexpectedly

## Design

- Optimistically update data locally and roll back on server error with feedback
- Authentication redirects should happen on the server before the client loads to avoid janky URL changes
- Style the document selection state with `::selection`
- Display feedback relative to its trigger:
  - Show a temporary inline checkmark on a successful copy, not a notification
  - Highlight the relevant input(s) on form error(s)
- Empty states should prompt to create a new item, with optional templates

## Sound

- Aplying sound physics and reverbs to your audio

## Motion

- Switching themes should not trigger transitions and animations on elements [^1]
- Animation duration should not be more than 200ms for interactions to feel immediate
- Animation values should be proportional to the trigger size:
  - Don't animate dialog scale in from 0 → 1, fade opacity and scale from ~0.8
  - Don't scale buttons on press from 1 → 0.8, but ~0.96, ~0.9, or so
- Actions that are frequent and low in novelty should avoid extraneous animations: [^2]
  - Opening a right click menu
  - Deleting or adding items from a list
  - Hovering trivial buttons
- Looping animations should pause when not visible on the screen to offload CPU and GPU usage
- Use `scroll-behavior: smooth` for navigating to in-page anchors, with an appropriate offset

## Touch

- Hover states should not be visible on touch press, use `@media (hover: hover)` [^3]
- Font size for inputs should not be smaller than 16px to prevent iOS zooming on focus
- Inputs should not auto focus on touch devices as it will open the keyboard and cover the screen
- Apply `muted` and `playsinline` to `<video />` tags to auto play on iOS
- Disable `touch-action` for custom components that implement pan and zoom gestures to prevent interference from native behavior like zooming and scrolling
- Disable the default iOS tap highlight with `-webkit-tap-highlight-color: rgba(0,0,0,0)`, but always replace it with an appropriate alternative

## Optimizations

- Large `blur()` values for `filter` and `backdrop-filter` may be slow
- Scaling and blurring filled rectangles will cause banding, use radial gradients instead
- Sparingly enable GPU rendering with `transform: translateZ(0)` for unperformant animations
- Toggle `will-change` on unperformant scroll animations for the duration of the animation [^4]
- Auto-playing too many videos on iOS will choke the device, pause or even unmount off-screen videos
- Bypass React's render lifecycle with refs for real-time values that can commit to the DOM directly [^5]
- [Detect and adapt](https://github.com/GoogleChromeLabs/react-adaptive-hooks) to the hardware and network capabilities of the user's device

## Accessibility

- Disabled buttons should not have tooltips, they are not accessible [^6]
- Box shadow should be used for focus rings, not outline which won’t respect radius [^7]
- Focusable elements in a sequential list should be navigable with <kbd>↑</kbd> <kbd>↓</kbd>
- Focusable elements in a sequential list should be deletable with <kbd>⌘</kbd> <kbd>Backspace</kbd>
- To open immediately on press, dropdown menus should trigger on `mousedown`, not `click`
- Use a svg favicon with a style tag that adheres to the system theme based on `prefers-color-scheme`
- Icon only interactive elements should define an explicit `aria-label`
- Tooltips triggered by hover should not contain interactive content
- Images should always be rendered with `<img>` for screen readers and ease of copying from the right click menu
- Illustrations built with HTML should have an explicit `aria-label` instead of announcing the raw DOM tree to people using screen readers
- Gradient text should unset the gradient on `::selection` state
- When using nested menus, use a "prediction cone" to prevent the pointer from accidentally closing the menu when moving across other elements.

[^1]: Switching between dark mode or light mode will trigger transitions on elements that are meant for explicit interactions like hover. We can [disable transitions temporarily](https://paco.me/writing/disable-theme-transitions) to prevent this. For Next.js, use [next-themes](https://github.com/pacocoursey/next-themes) which prevents transitions out of the box.
[^2]: This is a matter of taste but some interactions just feel better with no motion. For example, the native macOS right click menu only animates out, not in, due to the frequent usage of it.
[^3]: Most touch devices on press will temporarily flash the hover state, unless explicitly only defined for pointer devices with [`@media (hover: hover)`](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/hover).
[^4]: Use [`will-change`](https://developer.mozilla.org/en-US/docs/Web/CSS/will-change) as a last resort to improve performance. Pre-emptively throwing it on elements for better performance may have the opposite effect.
[^5]: This might be controversial but sometimes it can be beneficial to manipulate the DOM directly. For example, instead of relying on React re-rendering on every wheel event, we can track the delta in a ref and update relevant elements directly in the callback.
[^6]: Disabled buttons do not appear in tab order in the DOM so the tooltip will never be announced for keyboard users and they won't know why the button is disabled.
[^7]: As of 2023, Safari will not take the border radius of an element into account when defining custom outline styles. [Safari 16.4](https://developer.apple.com/documentation/safari-release-notes/safari-16_4-release-notes) has added support for `outline` following the curve of border radius. However, keep in mind that not everyone updates their OS immediately.
