**List Syntax:**
- Each list's videos mostly last between 3-30 seconds to explain the concept.
- Each list is organized from top to bottom based on effectivity.
- Tags like [CPU] say what the main focus of the enhancement is.

# 3D Performance Enhancements:
- Indirect Instancing (II): https://youtu.be/6mNj3M1il_c?t=507 [CPU]
- Occlusion culling: https://youtu.be/Teo0_enKUCM?t=171 [GPU]
- Analyzing the profiler: GTA V had 4 minute loading times on high-end consoles due to one piece of code, fixing it was quick, and had a 70% boost in loading performance, that's how most big bottlenecks are. [Any]
- Object pooling: https://youtu.be/7EZ2F-TzHYw?t=157 [CPU]
- Baking lights: https://youtu.be/VnG2gOKV9dw?t=134 [CPU]
- Imposters LOD: https://youtu.be/WIOI6C3t88E?t=149 (there is a slight impact on graphics quality, so it may be replaced with Indirect Instancing, or we can use a mix of the two, or it can be turned on at very low graphics settings) [GPU]
- Baking animations: https://youtu.be/Hh5zcT2IkaQ?t=65 (Costs a good bit of memory) [CPU]
- Binary search: https://youtu.be/BBpAmxU_NQo?t=733 [CPU]
- HLOD: https://youtu.be/f6KaJHUfE2M?t=54 [GPU]
- ECS: https://youtu.be/_U9wRgQyy6s?t=83 [CPU, RAM]
- Burst: https://www.youtube.com/watch?v=Z9-WkwdDoNY&t=292s [CPU]
- Jobs: https://youtu.be/C56bbgtPr_w?t=55 [CPU]
- URP: Universal RP (Render Pipeline) just gives a big performance boost by default compared to the built-in RP [CPU]
- Tailored Performance: Getting the machine's performance specifications and tailoring the game to it automatically, if the RAM is too high and the CPU can handle it, we can remove baked animations and use skinned animations. [Any]
- Subscenes: https://www.youtube.com/watch?v=91kJtsDLTyE&t=129s [RAM]
- Combining meshes: https://youtu.be/IrYPkSIvpIw?t=32 [CPU]
- Removing unused packages: Unity has a lot of packages added by default, and each one has an impact on performance, removing some unused packages and some of Unity's built-in packages, nearly doubled the performance. [Any]
- Use WebGPU for websites: https//youtu.be/PPmkMe4dDl0?t=37 (it's released and supported by major browsers, but Unity does not yet support it, however, there is confirmation that they are officially working on it, so we'd need to wait) [CPU]
- Very low-level language Functions: For example: we can create super optimized data types (string, float, etc.) in Rust, then use a certain tool to export it as a .dll file, to integrate it with the Unity project. [CPU, RAM]
- Caching: Cache (add variable values once) everything possible in update functions. [CPU]

**Lesser performance enhancements:**
- Addressable assets: https://youtu.be/XIHINtB2e1U?t=49 [Disk]
- Cloud Content Delivery: https://youtu.be/5IvPPI7YnwU?t=1154 (for content only accessible to specific users, like admin tools) [Disk]
- Reduce different materials: https://youtu.be/IrYPkSIvpIw?t=32 [CPU]
- Remove unnecessary settings: for example: disable accelerometer if you don't use mobile (accelerometer is the input from device movement, so if you tilt your phone, the accelerometer is the one detecting that as input) [Any]
- Coroutines delayed Update(): Using coroutines we can make them wait an amount of time before re-executing, so rather than updating every frame, we update every second as an example. [CPU]
- Custom-made mesh colliders: https://www.youtube.com/watch?v=zLEhpVj9Jb8&t=167s (We can make a script that automatically gets the mesh, uses a function similar to Blender's decimate, and applies that mesh as the collider) [CPU]
- Shader variant stripping: https://youtu.be/Ml6Ko06-9yM?t=196 [GPU]
- Optimizing UI: having 2 Canvases, 1 for dynamic (animated) elements and 1 for static elements + Always setting UI's Z position to 0. [CPU]
- Optimizing Audio: Reduce compression bitrate (<200kb = decompress, >=200kb = compress, large = stream) [CPU]
- Only having 2 LOD modes: https://youtu.be/pm5636_jiP0?t=743 (Doesn't sound big, but it's just to have a scalable LOD system, that we use for all games, and never worry about it again) [CPU]
- Project settings: Disable static batching (Replaced with II), enable prebake mesh colliders, enable texture mipmap stripping, enable optimize mesh data (may cause shading/pos processing issues), and enable new input system (mainly for the event-based calls). [Any]
- Render distance: Use fog and reduce render distance to render less objects. [GPU]
- Use case-specific variable types: Like use GameObject[] for an array of gameobjects, rather than Array[]. [CPU, RAM]
- Scene Optimization: Unity has to search through all objects when using any searching method like GameObject.Find() (bottom to top), so organize the scene so that atleast it's fast to reach the player object. [CPU]

*Note: Finding the default options on Unity or creating a script to automatically set the settings for certain performance enhancements should be implemented instead of manually setting them for each project.*

# 2D Performance Enhancements:
- Textures: Texture compression + atlas [Disk]
- Grayscale assets and color them by the renderer [GPU]
- For constant colors, use 1px assets and change the size by the renderer component [RAM]

This list is highly incomplete, and would be filled after a 2D game is made.

# Other Performance Enhancements
**Code focused performance optimization:**
- Do addition, not multiplication: For example, if the current game has 30k gameobjects, and I want to get a specific gameobject to check a certain variable it has, and lets say I only need to iterate through that variable 200 times it would be a foreach loop for gameobjects and a foreach loop for that list: 30,000 x 200, which is 6 million cycles, rather than 30k x 200, keep it 30k + 200, have a for loop which increments i, and just access the lists with an index of i, from 6 million iterations, to 30,200 iterations.
- Reducing function calls: For example: Instead of having an if statement for each input device that executes every frame, have an event that, when the button is pressed, the function gets called, this can be very good for expensive scripts.
- Removing arguments: Passing in function arguments can slow execution, because for each use of any funtion argument variable, it creates a new variable for it, so when you use it 3 times, its creating the same variable 3 times, declaring it inside of the function keeps it as 1 variable instance. [CPU]
- Stringbuilders for strings that are modified often: normal strings are not modifiable (immutable), so every single change creates a new string variable in memory with the modified value, stringbuilders don't have that (mutable), you can re-use the same variable. [CPU, RAM]

*Note: Implementation of any code focused performance optimization would depend on the usability as well, for example, stringbuilders help memory a lot if strings are often modified, but may not be fun to write compared to strings.*

**Editor performance enhancements:**
- Automatic assembly references: Automatically generating assembly definitions per folder that has scripts.
- Disabling reload domain: Domain reload takes a massive amount of time compared to not having it on, rather than disabling it entirely, we can disable it for entering playmode, to enter and exit playmode fast, the main effect it has is, any static scripts won't be called by Unity on playmode, which we can avoid. To disable it, go to Edit>Project Settings>Editor>Uncheck Reload Domain.