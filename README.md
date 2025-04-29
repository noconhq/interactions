# VR/AR/XR Interaction Guidelines

This document outlines a community-molded list of details that make good VR/AR/XR interactions. It is a collection of structures to make good interactions within the virtual, augmented & mixed reality worlds. Periodically updated based on community and standards. Some of these may be subjective, but most apply to all interactions.

Contributions are welcome. Edit [this file](README.md) and submit a pull request.

## Immersion

- Mimic as most real-life physics as possible
- Use realistic scale and 1:1 proportion if possible
- Avoid floating, detached or screen-fixed UI
- Always design with 3D space in mind—depth matters
- Match environment lighting and shadows to user expectations
- Reactions from the world should feel grounded (e.g. footsteps, hand collisions)

## Interactivity

- Your body and objects should **not** break any laws of physics or ui/game mechanics unless it's on purpose [^1]
- Grabs, throws, and touches should react instantly and make sense within ui/game mechanics and physics
- Actions need visual and/or haptic feedback
- Avoid complex gestures that are hard to repeat
- Interactions should be forgiving but not floaty or imprecise

## Design

- Fonts should have some sort of smoothing applied for better legibility
- Fonts should be subset based on the content, alphabet or relevant language(s)
- Maintain a visual hierarchy using size, distance, and contrast [^2]
- Font weights below 200 should not be used
- Prevent text resizing unexpectedly
- UI elements should stay at a readable distance and scale
- Don’t rely on tiny details or flat icons with no depth

## Sound

- Apply sound physics (e.g., reverbs, occlusion) to enhance both accessibility and immersion
- Use directional audio to guide attention
- Confirm actions with subtle audio cues
- Avoid repetitive or annoying [sound loops/fatigue](https://www.youtube.com/watch?v=GNzUFyuZtWM)
- Match volume and effects to environment and distance
- Give users volume control for everything [^3]

## Motion

- Avoid unexpected camera movement [^4]
- Provide teleport or smooth locomotion options
- Allow users to rotate in increments (snap turn)
- Reduce motion acceleration to avoid nausea
- Keep hand and object movement 1:1 with the user’s real motion
- Avoid forced character movement unless essential to gameplay
- Don’t animate the player body unless it matches user input exactly

## Optimizations

- Keep frame rate stable, even if it means reducing visual fidelity
- Avoid overdraw and complex shaders in large scenes
- Use occlusion and frustum culling
- Load only what’s needed in the current view
- Compress assets to reduce load times
- Monitor memory usage—especially on mobile and standalone headsets
- Bake lighting when possible for better performance

## Accessibility

- Provide options for left-handed and seated use
- Use haptics, sound, and visual cues together
- Offer colorblind-friendly palettes
- Include subtitle and caption options
- Allow input remapping
- Avoid relying only on sound or only on visuals to communicate critical info
- Provide comfort settings (snap turn, vignette, reduced motion, etc.) [^5]
- Text should be readable from common distances and angles

[^1]: These guidelines aim for consistency and comfort, but not every rule fits every experience. Breaking them with purpose—whether for style, accessibility, or storytelling—is valid. Just test with users and make it intentional.
[^2]: A strong visual hierarchy ensures readability and focus. Use size, distance, and contrast to lead the eye and prevent confusion.
[^3]: Independent control of music, voice, environment, and UI sounds improves usability for users with different sensitivity needs or environments.
[^4]: Forced movement (like rollercoaster sequences) can be disorienting for many users. Use sparingly, and always provide an opt-out or comfort mode.
[^5]: Comfort settings should be easy to find and adjustable mid-experience. Don't hide them behind deep menus or initial setup only.
