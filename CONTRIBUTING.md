# Unity Development Guidelines
To ensure application stability and easier collaboration, we have guidelines, these guidelines are focused on establishing a standard approach for different areas of coding, so that all commited code has a known effective pattern.

**Programming Guidelines:**
1. Programming will be done using Unity's native language: C#. [why]() | [how]()
2. Programming should follow the declarative paradigm, in the case that it isn't applicable, programming would be done using the procedural paradigm. [why]() | [how]()
3. Only use the GameAssets object in Unity to reference and use GameObjects and scripts. [why]() | [how]()
4. Scripts must be made for one purpose. [why]() | [how]()
5. Name files and variables to their exact functionality. [why]() | [how]()
6. Classes, functions, events, and similar should be in PascalCase, everything else should be in camalCase. [why]() | [how]()
7. Variables that may be used by other scripts should be public, other variables should be private. [why]() | [how]()
8. Variables should be declared after imports, where variables that are similar will not be spaced. [why]() | [how]()
9. Variables should be stored near the top of a file, where public variables are defined first then (after line spacing) private variables are defined. [why]() | [how]()
10. Use FixedUpdate() classes for any physics calculation. [why]() | [how]()

Note: These guidelines are incomplete, please find and report anything you disagree with in this list in Discord with other developers. Espicially since this list is recent.
