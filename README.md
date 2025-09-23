# Unity Design - Week 03

## Agenda
1. [UI Canvas and UI Components](#UI-Canvas-and-UI-Components)
2. [Video Player](#Unity-Video-Player)  
3. [Audio Basics](#Unity-Audio-Basics)  
4. [Particle System](#Unity-Particle-System)  
5. [Lighting System](#Unity-Lighting)  
6. [Tweening with DOTween](#DO-Tween)  
7. [Class Assignment - Week #03](#Create-with-Code)  

---

# UI Canvas and UI Components
## 🖼️ The Canvas
- The **foundation** of every Unity UI.
- All UI elements **must** be children of a Canvas.
- Handles:
  - Rendering order of UI elements.
  - Scaling for different screen resolutions.
  - Event system interaction.

**Canvas Render Modes**:
1. **Screen Space - Overlay** → UI is drawn directly on screen (most common for HUDs).
2. **Screen Space - Camera** → UI is rendered relative to a camera.
3. **World Space** → UI behaves like a 3D object in the scene.

---

## 🚀 Getting Started
1. Create a new Canvas (`GameObject > UI > Canvas`).
2. Add a **Panel** to serve as background.
3. Add UI elements: Text, Buttons, Sliders, etc.
4. Attach scripts to UI elements to handle interaction.

---

## 🎥 UI Components Video Tutorials
- https://learn.unity.com/tutorial/ui-components

---

## 🧩 UI Components

### 1. **Text / TextMeshPro**
- Displays text on screen.
- **TextMeshPro** is the modern, flexible alternative with better styling and performance.

### 2. **Image**
- Displays 2D sprites or textures.
- Used for icons, backgrounds, and decorative UI.

### 3. **Raw Image**
- Displays unscaled textures (e.g., video, render textures).

### 4. **Button**
- Clickable element that triggers actions via the `OnClick()` event.

### 5. **Toggle**
- Checkbox-like UI that switches between **on/off** states.

### 6. **Slider**
- Draggable bar to represent a numeric value within a range (e.g., volume).

### 7. **Scrollbar**
- Scrollable control for lists or large panels.

### 8. **Dropdown**
- Expanding list to select one option from many.

### 9. **Input Field**
- Allows user text entry.
- Often paired with scripts for chat boxes, usernames, or form input.

### 10. **Panel**
- A rectangular container (usually semi-transparent).
- Used to group UI elements visually.

### 11. **Mask / Rect Mask 2D**
- Restricts visibility of child elements to a defined shape.
- Useful for scroll views and minimaps.

### 12. **Scroll View**
- A ready-made component combining:
  - **Viewport** (mask)
  - **Content** (elements)
  - **Scrollbars**
- Enables scrolling through long lists or panels.

### 13. **Event System**
- Automatically created with a Canvas.
- Handles user input (mouse, touch, keyboard, gamepad).

---

## 🎨 Layout Components
Unity provides special components to help organize UI:

- **RectTransform** → replaces Transform for UI elements (anchors, pivot, stretch).
- **CanvasScaler** → scales UI for different screen resolutions.
- **Layout Group Components**:
  - Horizontal Layout Group
  - Vertical Layout Group
  - Grid Layout Group
- **Content Size Fitter** → adjusts element size automatically based on content.

---

## 💡 Best Practices
- Use **TextMeshPro** instead of legacy Text.
- Organize UI using **Panels** and **Layout Groups** for flexibility.
- Minimize number of **Canvases**—too many can hurt performance.
- Use **Anchors** to make UI responsive to different screen sizes.

---

## 📚 Resources
- 📖 [Unity Manual – UI Overview](https://docs.unity3d.com/Manual/UISystem.html)  
- 📖 [Unity Manual – Canvas](https://docs.unity3d.com/Manual/UICanvas.html)  
- 📖 [Unity Manual – UI Components](https://docs.unity3d.com/Manual/script-UI.html) 

---

## 📌 Assignment Week #3 - Unit 1 Player Control - Apply UI Elements
- Add on to the Unit 1 sample driving game prototype with UI Screen elements. Create a Start Screen and Settings Screen with UI elements for the game. 
- https://learn.unity.com/project/unit-1-driving-simulation?uv=6&courseId=5cf96c41edbc2a2ca6e8810f

- Reference Videos on Styling UI Elements:
- https://www.youtube.com/watch?v=674k6lHqpPc
- https://www.youtube.com/watch?v=IuuKUaZQiS

- Tutorial for Setting Menu:
- https://learn.unity.com/pathway/creative-core/unit/creative-core-ui/tutorial/add-toggles-and-sliders-3?version=6.0

- Excellent review video:
- https://www.youtube.com/watch?v=Unnd0cOSiLU&list=PL1aAeF6bPTB5dCFmbg9Mo9wSSdxeL2o49



