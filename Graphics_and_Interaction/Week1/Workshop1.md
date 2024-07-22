# Workshop 1
## Installation of Unity
* Ensure correct version of __unity (2022.3.x LTS)__
  * Ensure __WebGL Build Support__

## Unity
* Unity is a __cross-platform game engine__
* Scripting primarily in __C#__

### Pros of Unity
* Rapid development and maximal code reuse
* Component based architecture
* Wide spread support for VR and AR
* Vast online resources available

### Unity 101
* __Scenes__ contain a heirarchy of game objects
* All game objects have a __transform__ component that describes position, rotation and scale (relative to the parent)
* __project__ is essentially a file explorer
* __console__ tab is console duhhh
* __Inspector__ tab allows you to inspect a object's __composition__
* Game objects can have additional components attached to it
* Components can be __built in__ or __custom written classes (C#)__
* Examples of game object __compositions__
  * \<Transform>
  * \<Transform, Camera>
  * \<Transform, Mesh Renderer>

## C#, OOP and Unity
Components in unity are just C# __classes__ that inherit from a special engine class called __MonoBehaviour__

Once classes inherit from __MonoBehaviour__ methods can be implemented to react to in-game events, unity __automatically calls these methods__ for you when the events occur

For example, _Update()_ is called once per 'frame'