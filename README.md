# VR/AR/XR Interaction Guidelines

This document outlines a community-molded list of details that make good VR/AR/XR interactions. It is a collection of structures to make good interactions within the virtual, augmented & mixed reality worlds. Periodically updated based on community and standards. Some of these may be subjective, but most apply to all interactions.

Contributions are welcome. Edit [this file](README.md) and submit a pull request.

## Immersion

- Mimic as most real-life physics as possible
- Use realistic scale and 1:1 proportion if possible, unless a stylized scale is a deliberate design choice.
- Avoid floating, detached, or screen-fixed UI elements
- Always design with 3D space in mind—depth, occlusion, and spatial relationships matters.
- Match environment lighting, shadows, and atmospheric effects to user expectations and the context of the experience.
- Reactions from the world should feel grounded (e.g., footsteps on different surfaces, hand collisions).

## Interactivity

- Your body and objects should **not** break any laws of physics or ui/game mechanics unless intentional [^1]
- Grabs, throws, touches and other interactions should react instantly and make sense within ui/game mechanics and physics
- Actions require visual, auditory, and/or haptic feedback.
- - The type and intensity of feedback should match the action's importance and context.
- Avoid complex gestures that are hard to repeat
- Avoid complex or overly precise gestures that are difficult to learn or perform.
- Interactions should be forgiving of minor inaccuracies but not feel floaty, imprecise, or unresponsive.
- - Implement smart snapping or assistance where it enhances usability without feeling restrictive.
- Consider context of use if the user is standing, seated, or moving.
- - Design interactions that are appropriate for the expected user posture and activity level.

## Design

- Fonts should have some sort of smoothing (e.g., anti-aliasing) and contrast for clear legibility.
- Fonts should be subset based on the content, alphabet or relevant language(s)
- Maintain a visual hierarchy using size, distance, contrast, color, and placement to guide user's attention. [^2]
- Avoid extremely thin font weights (e.g., below 200) as they can be difficult to read in VR/AR/XR displays.
- Prevent text from resizing, jittering, or moving unexpectedly.
- UI elements should stay at a comfortable and readable distance and scale.
- - typically within a 1 to 3-meter range for near-field UI. Avoid placing UI too close (causing eye strain) or too far (reducing legibility).
- Don’t rely on tiny details or flat icons with no depth, use space to give UI elements presence and make them easier to interact.
- For gaze-activated elements, ensure clear indication of focus (hover state) and a deliberate confirmation step (e.g., dwell time, button press) to prevent accidental activation.

## Sound

- Apply sound physics (e.g., spatialization, Doppler effect, reverbs, environment occlusion) to enhance both accessibility, immersion, and situational awareness.
- Use directional (3D) audio to guide attention, indicate off-screen events, and provide spatial cues.
- Confirm actions with subtle, satisfying audio cues. Overly loud or jarring sounds can be unpleasant.
- Avoid repetitive, annoying, or easily fatiguing [sound loops/fatigue](https://www.youtube.com/watch?v=GNzUFyuZtWM)
- Match volume levels and audio effects to the virtual environment, event significance, and distance from the sound source.
- Give users volume control for everything [^3]

## Motion

- Avoid unexpected, uncontrolled, or forced camera movements [^4]
- Provide multiple locomotion options such as teleportation, smooth locomotion (with adjustable speed), and arm-swing based movement.
- Allow users to rotate in increments (snap turn)
- Allow users to rotate their view in increments (snap turn) as well as smooth rotation, with adjustable speeds for both.
- Reduce or carefully manage motion acceleration and deceleration to minimize nausea.
- Maintain 1:1 tracking for hand and objects movement relative to the real-world motion.
- Avoid forced character movement unless it is essential to the core gameplay or narrative and the user has opted in or been warned.
- Don’t animate the player's virtual body (avatar) in ways that do not precisely match user input.
- Consider implementing dynamic FOV reduction (vignetting) during artificial locomotion or fast rotations as a comfort measure to reduce peripheral motion cues.

## Optimizations

- Prioritize a consistently high and stable frame rate (e.g., 72Hz, 90Hz, 120Hz, depending on the target hardware) above all else.
- - even if it means reducing visual fidelity.
- Avoid overdraw (rendering the same pixel multiple times) and use efficient shaders, especially in large or complex scenes.
- - Utilize techniques like single-pass stereo rendering.
- Use occlusion culling (not rendering objects hidden by other objects) and frustum culling (not rendering objects outside the camera's view).
- Use LOD systems for complex models, displaying simpler versions of objects when they are further away.
- Load only necessary assets for the current view or upcoming interactions. Stream assets dynamically where possible.
- Compress textures, audio, and other assets to reduce memory footprint and loading times. Use appropriate compression formats for XR.
- monitor memory usage, especially on mobile and standalone headsets with limited resources. Implement strategies to manage and release memory effectively.
- Bake lighting (pre-calculate and store lighting information in textures) for static environments whenever possible.
- Regularly profile the application on target hardware to identify performance bottlenecks and address them proactively.

## Accessibility

- Provide options for left-handed and right-handed use. Design experiences that are comfortable for both seated and standing play, or clearly indicate the intended posture.
- Use a combination of haptics, sound, and visual cues to convey information, ensuring that users who may have limitations in one sensory modality can still understand critical feedback.
- Offer colorblind-friendly palettes or ensure that information is not conveyed by color alone.
- Include comprehensive subtitle and caption options for all spoken dialogue and important sound events.
- - Bonus point if you allow users to customize subtitle appearance (size, background).
- Allow users to remap controls to suit their preferences and physical needs.
- Avoid relying solely on sound or solely on visuals to communicate critical information.
- Provide comfort settings (e.g., snap turn, smooth turn speed, locomotion vignettes, reduced motion options, forward-facing) [^5]
- Ensure text is readable from common viewing distances and angles within the virtual environment.
- Design interactions that do not require excessive or uncomfortable physical movements.
- Provide clear and concise tutorials to introduce users to controls, mechanics, and features. Allow users to revisit tutorials.

## Emerging Considerations

- Explore how AI can be used to predict user intent, personalize experiences, create more natural NPC interactions, or adapt environments dynamically.
- As haptic technology evolves, consider how more nuanced and realistic tactile feedback can enhance immersion and interaction.
- Be mindful of the ethical implications of XR experiences, including data privacy, user safety, potential for addiction, and the creation of misleading or harmful content.

[^1]: These guidelines aim for consistency and comfort, but not every rule fits every experience. Breaking them with purpose—whether for style, accessibility, or storytelling—is valid. Just test with users and make it intentional.
[^2]: A strong visual hierarchy ensures readability and focus. Use size, distance, and contrast to lead the eye and prevent confusion.
[^3]: Independent control of music, voice, environment, and UI sounds improves usability for users with different sensitivity needs or environments.
[^4]: Forced movement (like rollercoaster sequences) can be disorienting for many users. Use sparingly, and always provide an opt-out or comfort mode.
[^5]: Comfort settings should be easy to find and adjustable mid-experience. Don't hide them behind deep menus or initial setup only.
