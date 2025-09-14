# Unity Design - Week 03

## Agenda

1. [Video Player](#Video-Player)  
2. [Unity C# Basics](#Unity-C#-Basics)  
3. [Arithmetic Operators & Order of Operations](#Arithmetic-Operators-Order-of-Operations)  
4. [C# - Beginner Unity Scripting](#Beginner-Unity-Scripting)  
5. [UI Canvas and UI Components](#UI-Canvas-and-UI-Components)  
6. [Class Assignment - Week #02](#Create-with-Code)  

---
# Video Player 🎬

A hands-on guide for using Unity’s **Video Player** component will help you import videos, configure the Video Player, and render clips as full-screen cutscenes or in-world displays.

---

## 📌 What You’ll Learn
- How to **import video clips** into Unity.  
- The **Video Player** component and its key settings.  
- Different **render modes**: overlay, camera plane, mesh, render textures.  
- **Step-by-step walkthrough** with screenshots.  
- Tips for **aspect ratio, performance, and compatibility**.  

---

## 🧰 Step 1: Importing a Video
1. Drag your video file into the Unity **Assets** folder.  
2. Select the video asset and review import settings in the **Inspector**:  
   - ✅ **Transcode**: Ensures platform compatibility (recommended).  
   - ✅ **Loop**: Enable if the video should repeat.  

📸 *Example: Video asset import settings*  
![Video Import Settings](images/video-import-settings.png)

---

## 🎮 Step 2: Add a Video Player Component
1. Create an empty GameObject (`GameObject > Create Empty`).  
2. Rename it `VideoPlayer`.  
3. In the **Inspector**, click **Add Component > Video Player**.  
4. Drag your video clip into the **Video Clip** slot.  

📸 *Example: Video Player component attached to GameObject*  
![Video Player Component](images/video-player-component.png)

---

## 📺 Step 3: Choose a Render Mode

### 1. **Camera Far/Near Plane**
- Plays video **full-screen** in front of or behind a camera.  
- Perfect for cutscenes or splash screens.  
- Set `Render Mode = Camera Near Plane` or `Far Plane`.  

📸 *Full-screen video render via camera*  
![Camera Render Example](images/video-camera-mode.png)

---

### 2. **Material Override (In-World Screen)**
- Apply video as a **texture** on a 3D object (like a TV screen or billboard).  
- Steps:
  1. Create a **3D Object > Quad**.  
  2. Create a **Material** and assign it to the Quad.  
  3. In Video Player → `Render Mode = Material Override`.  
  4. Assign your Quad’s Mesh Renderer and set the property (e.g. `_MainTex`).  

📸 *In-world TV screen example*  
![Material Override Example](images/video-material-override.png)

---

### 3. **Render Texture**
- Flexible method: sends video to a **RenderTexture** asset.  
- Useful for post-processing, UI backgrounds, or custom shaders.  

Steps:  
1. Create **Assets > Create > Render Texture**.  
2. Assign it in Video Player → `Target Texture`.  
3. Use the RenderTexture in any **UI Image** or **Material**.  

📸 *Render Texture setup in Inspector*  
![Render Texture Example](images/video-render-texture.png)

---

## 🔧 Step 4: Fixing Aspect Ratio
- If the video looks **stretched**:
  - Adjust Quad’s scale when using Material Override.  
  - Match RenderTexture width/height to the video’s resolution.  

📸 *Correct aspect ratio vs stretched*  
![Aspect Ratio Fix](images/video-aspect-ratio.png)

---

## 💡 Tips & Best Practices
- ✅ Always enable **Transcode** for cross-platform support.  
- ✅ Use **Render Texture** for advanced effects (shaders, UI backgrounds).  
- ✅ Keep videos **compressed** for performance (especially mobile).  
- ✅ Use **Material Override** for immersive, in-world playback.  
- ✅ Use **Camera Render** for simple, full-screen cutscenes.  

---

## 🎯 Example Use Cases
- 🎬 **Cutscenes** → Render mode: Camera Near Plane.  
- 📺 **TV/Monitor in scene** → Render mode: Material Override.  
- 🌌 **Background animation** → Render mode: Render Texture + UI Image.  

---

## 📚 References
- 📖 [Unity Manual – Video Player](https://docs.unity3d.com/Manual/VideoPlayer.html)  
- 📖 [Unity Manual – Render Texture](https://docs.unity3d.com/Manual/class-RenderTexture.html)  

---

