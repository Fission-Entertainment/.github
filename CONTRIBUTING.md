# Coding Guidelines
To ensure application stability and easier collaboration, we have guidelines, these guidelines are focused on establishing a standard approach for different areas of coding, so that all commited code has an effective known pattern.

**General Guidelines:**
1. Only use the GameAssets object in Unity to reference and use GameObjects. [reason]()
2. Name files and variables to their exact functionality, if a script renders an axe, it should be called AxeRenderer. [reason]()
3. Classes, functions, events, and similar should be in PascalCase, everything else should be in camalCase. [reason]()
4. Variables that may be used by other scripts should be public, other variables should be private. [reason]()
5. Add setter functions for variables that could be changed by other scripts, such as a SetMoveSpeed() function for player speed. [reason]()

**Case-Specific Guidelines:**
1. Use FixedUpdate() classes for any physics calculation. [reason]()
2. Use a stringbuilder for string concatenation. [reason]()
3. Variables should be stored near the top of a file, where public variables are defined first then (after line spacing) private variables are defined. [reason]()
4. Do not use awake(). [reason]()

Note: These guidelines are incomplete, please find and report anything you disagree with in this list in Discord with other developers. Espicially since this list is recent.