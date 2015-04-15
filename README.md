# ChunkPosition
This code sample is from a part of a game I was working on that dealt with the positioning of the game world as the player traversed across it (in a 2D environment). This piece of code is taken from a script written in C# from a game that was developed in Unity. As such, some objects and member variables accessed are specific to the Unity Engine or to other scripts in the project.

The example shown is of two helper methods that are used to position the 'chunk' of the level being moved into place. This code illustrates overcoming a specific obstacle that I intentionally forced the game to encounter. Within Unity anything marked with just a static 'collider' is considered to be fixed and the engine intends for it never to be moved. Because of this, the engine can make some physics optimizations in order to gain performance. The downside is that if the object ends up moving a heavy performance penalty is incurred. I want to gain the performance optimization of using the static colliders, but without encountering the penalty for moving them. All of this has to happen at runtime so it is all automated. 

The first method specifically finds the exact position the new chunk needs to be moved to based on the location of the previous chunk. Since the coordinates the engine uses within the game world originate from the center of all objects, we need to calculate an offset to determine how far in front of the last chunk to place the new one. The objects need to line up correctly in the game world so it is critical to get this calculation correct.

The second method is called by the first before anything is actually moved. The method recursively calls itself to remove all colliders within a given objects hierarchy. The method is not limited in anyway based on how the object's hieracrhy might be structured nor is it by how big/small the hieracrhy may be. Once all the movement and setup for the new chunk is done, these colliders are added back on (not shown in this code).

I like this coding example because I have found it to be a robust solution to the problem. The position method allows for a new chunk to be moved up or down and operates based on the characteristics of whatever is passed into it. Likewise, the recursive method is an elegant solution to the problem of removing colliders from a vast array of differing objects and their hierarchies.

Thank you for reading.
Zach Earnest
