# Unity Design - Week 03

## Agenda
1. [Lifecycle of Unity Frame](#Life-Cycle-Frame-Methods)
2. [UI Canvas and UI Components](#UI-Canvas-and-UI-Components)
3. [Scene Management](#Scene-Management)
4. [Key Input / MouseInput](#Key-Mouse-Input)
5. [Instantiate Prefab](#Instantiate-Prefab)
6. [Random Range](#Random-Range)
7. [Class Assignment - Week #03](#Apply-UI-Elements)  

# 🧱 Lifecycle of Unity Frame Events

- **Unity Event Functions Diagram**:  

![Unity Lifecycle](images/LifecycleUnity.png)

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

# Unity Scene Management

Scene Management in Unity is the system that controls loading, unloading, and transitioning between different game levels or environments. Scenes are containers for your game’s objects, lighting, UI, and gameplay logic. By mastering scene management, you can build structured projects, create menus, and implement smooth level transitions.

---

## 📖 What is a Scene in Unity?

A **Scene** in Unity is like a stage or level of your game. It holds:

* GameObjects (characters, environments, UI, etc.)
* Components (scripts, physics, colliders, etc.)
* Lighting & rendering data
* Navigation and baked data

Every Unity project starts with a default scene, but you can create as many scenes as needed to organize your game.

---

## ⚙️ Scene Management API

Unity provides the **`UnityEngine.SceneManagement`** namespace to handle scene operations.

### Importing

```csharp
using UnityEngine.SceneManagement;
```

### Common Functions

* **Load a Scene by Name**

  ```csharp
  SceneManager.LoadScene("Level1");
  ```
* **Load a Scene by Build Index**

  ```csharp
  SceneManager.LoadScene(1);
  ```
* **Load Additively (keep current scene active)**

  ```csharp
  SceneManager.LoadScene("UIOverlay", LoadSceneMode.Additive);
  ```
* **Unload a Scene**

  ```csharp
  SceneManager.UnloadSceneAsync("UIOverlay");
  ```
* **Get the Active Scene**

  ```csharp
  Scene activeScene = SceneManager.GetActiveScene();
  Debug.Log("Current Scene: " + activeScene.name);
  ```
  
---

## 🎮 Example: Level Transition Script

```csharp
using UnityEngine;
using UnityEngine.SceneManagement;

public class SceneController : MonoBehaviour
{
    public void LoadLevel(string sceneName)
    {
        SceneManager.LoadScene(sceneName);
    }

}
```

Attach this script to a UI button to handle menu navigation.

---

# Unity Key & Mouse Input in `Update()`

Handling **player input** is a core part of gameplay in Unity. Using the `Update()` frame event, you can check for **keyboard keys** and **mouse clicks** each frame. This allows you to implement movement, shooting, menu navigation, and other interactions.

---

## 🔄 Why Use `Update()` for Input?

The `Update()` method runs **once per frame**, making it ideal for checking input events in real time. Unity’s Input system captures key presses and mouse activity, which you can query inside `Update()`.

---

## ⌨️ Keyboard Input

Unity provides several ways to detect keyboard keys using the `Input` class.

### Common Methods

* **`Input.GetKey`** – returns `true` while the key is held down.
* **`Input.GetKeyDown`** – returns `true` only in the frame the key is pressed.
* **`Input.GetKeyUp`** – returns `true` only in the frame the key is released.

### Example

```csharp
using UnityEngine;

public class PlayerController : MonoBehaviour
{
    void Update()
    {
        // Move left and right
        if (Input.GetKey(KeyCode.A))
            transform.Translate(Vector3.left * Time.deltaTime);

        if (Input.GetKey(KeyCode.D))
            transform.Translate(Vector3.right * Time.deltaTime);

        // Jump (triggered once on key press)
        if (Input.GetKeyDown(KeyCode.Space))
            Debug.Log("Jump!");

        // Quit (triggered once on release)
        if (Input.GetKeyUp(KeyCode.Escape))
            Application.Quit();
    }
}
```

---

## 🖱️ Mouse Input

Mouse input works the same way, with additional support for button clicks and cursor position.

### Mouse Buttons

* `0` → Left button
* `1` → Right button
* `2` → Middle button

### Example

```csharp
void Update()
{
    // Left click (pressed down this frame)
    if (Input.GetMouseButtonDown(0))
        Debug.Log("Left Mouse Button Clicked");

    // Hold right button
    if (Input.GetMouseButton(1))
        Debug.Log("Right Mouse Button Held");

    // Release middle button
    if (Input.GetMouseButtonUp(2))
        Debug.Log("Middle Mouse Button Released");

    // Mouse position in screen space
    Vector3 mousePos = Input.mousePosition;
    Debug.Log("Mouse Position: " + mousePos);
}
```

---

## 🎮 Example: Simple Character Controller

```csharp
using UnityEngine;

public class SimpleController : MonoBehaviour
{
    public float moveSpeed = 5f;

    void Update()
    {
        float moveX = 0f;

        if (Input.GetKey(KeyCode.A))
            moveX = -1f;
        else if (Input.GetKey(KeyCode.D))
            moveX = 1f;

        transform.Translate(new Vector3(moveX, 0, 0) * moveSpeed * Time.deltaTime);

        if (Input.GetMouseButtonDown(0))
            Debug.Log("Player attacked!");
    }
}
```
---


# Instantiate Prefabs

In Unity, **prefabs** are reusable GameObject templates. The **`Instantiate()`** method allows you to create clones of prefabs at runtime, enabling dynamic spawning of enemies, bullets, items, UI elements, and more.

---

## 🧩 What is a Prefab?

A **Prefab** is a saved GameObject asset in your Unity project that stores:

* Meshes, sprites, or UI elements
* Components (scripts, colliders, physics, etc.)
* Property values and child objects

They serve as **blueprints** that can be reused and instantiated multiple times in a scene.

---

## ⚙️ Instantiating a Prefab

### Syntax

```csharp
Object Instantiate(Object original);
Object Instantiate(Object original, Vector3 position, Quaternion rotation);
Object Instantiate(Object original, Transform parent);
```

---

## 🎮 Example: Basic Instantiation

```csharp
using UnityEngine;

public class Spawner : MonoBehaviour
{
    public GameObject prefab; // Assign in Inspector

    void Start()
    {
        // Spawn prefab at origin
        Instantiate(prefab);
    }
}
```

---

## 📍 Instantiating with Position & Rotation

```csharp
public class Spawner : MonoBehaviour
{
    public GameObject prefab;

    void SpawnAtPoint()
    {
        Vector3 spawnPos = new Vector3(0, 1, 0);
        Quaternion spawnRot = Quaternion.identity;

        Instantiate(prefab, spawnPos, spawnRot);
    }
}
```

* `Quaternion.identity` → default rotation (no rotation).

---

## 🌳 Parenting Instantiated Objects

```csharp
public Transform parentObject;

void SpawnAsChild()
{
    Instantiate(prefab, parentObject);
}
```

Useful for organizing objects under a hierarchy (e.g., bullets under a "BulletContainer").

---

## 🔁 Runtime Examples

### 1. Enemy Spawner

```csharp
public GameObject enemyPrefab;

void Update()
{
    if (Input.GetKeyDown(KeyCode.Space))
    {
        Vector3 randomPos = new Vector3(Random.Range(-5f, 5f), 0, Random.Range(-5f, 5f));
        Instantiate(enemyPrefab, randomPos, Quaternion.identity);
    }
}
```

---

### 2. Shooting Projectiles

```csharp
public GameObject bulletPrefab;
public Transform firePoint;

void Shoot()
{
    Instantiate(bulletPrefab, firePoint.position, firePoint.rotation);
}
```

---

# Unity `Random.Range`

Randomness is essential in game development for creating variety, unpredictability, and replayability. Unity provides the **`Random.Range`** method to generate random numbers for positions, rotations, loot drops, AI behavior, and more.

---

## 🎲 What is `Random.Range`?

`Random.Range` is part of the **`UnityEngine`** namespace. It returns a random number between two specified values.

### Syntax

```csharp
float value = Random.Range(min, max);   // Random float between min [inclusive] and max [inclusive]
int value = Random.Range(min, max);     // Random int between min [inclusive] and max [exclusive]
```

---

## 🔢 Using Random with Floats

When using **floats**, the range is **inclusive** on both ends.

```csharp
void Update()
{
    // Random speed between 1.0 and 5.0
    float randomSpeed = Random.Range(1f, 5f);
    Debug.Log("Random Speed: " + randomSpeed);
}
```

* Returns values like `1.0`, `2.73`, `4.99`, or even `5.0`.

---

## 🔢 Using Random with Integers

When using **integers**, the **minimum is inclusive** but the **maximum is exclusive**.

```csharp
void Start()
{
    // Picks a number from 1, 2, or 3 (never 4)
    int randomChoice = Random.Range(1, 4);
    Debug.Log("Random Choice: " + randomChoice);
}
```

* Useful for dice rolls, selecting random array indices, or choosing random options.

---

## 🎮 Example Use Cases

### 1. Random Position

```csharp
Vector3 randomPos = new Vector3(
    Random.Range(-10f, 10f),
    0f,
    Random.Range(-10f, 10f)
);
transform.position = randomPos;
```

Places the object at a random position within a square area.

---

### 2. Random Enemy Spawn

```csharp
public GameObject[] enemies;

void SpawnEnemy()
{
    int index = Random.Range(0, enemies.Length);
    Instantiate(enemies[index], transform.position, Quaternion.identity);
}
```

Chooses a random enemy prefab to spawn.

---

### 3. Randomized Loot Drop Chance

```csharp
void DropLoot()
{
    float chance = Random.Range(0f, 1f);
    if (chance < 0.25f)
        Debug.Log("Rare Item Dropped!");
    else
        Debug.Log("Common Item Dropped!");
}
```

Gives a **25% chance** to drop a rare item.

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



