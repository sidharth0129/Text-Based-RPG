1. 


TODO 1

The Scene constructor stores the scene data and creates exactly enough choice slots for the number of choices in the scene. It also sets every choice slot to nullptr. Since there can only be up to 3 choices, this is O(1).

TODO 2

The destructor deletes every child scene, choices array, and scene data. This is O(n) since there can be n number of deletes.

TODO 3

isEnding checks if the scene has 0 choices and if it does the scene is an ending. This is O(1).

TODO 4

getChoice checks if the index is valid and returns the scene stored at that choice. This is O(1).

TODO 5

setChoice checks if the index is valid and stores the next scene in that choice slot. This is O(1).

TODO 6

countScenes recursively goes through the tree and counts every scene. This is O(n) since every scene is visited once.

TODO 7

countEndings recursively goes through the tree and counts every scene that has 0 choices. This is O(n) since every scene might need to be checked.

TODO 8

height recursively goes through the tree and finds the longest path from the current scene to an ending. This is O(n) since every scene is visited.

TODO 9

clear deletes the root, which also deletes all of the scenes below it, and then sets the root to nullptr. This is O(n) since the entire tree might need to be deleted.

TODO 10

load opens the story file, reads the starting HP, and calls readScene to build the story tree. This is O(n) since every scene in the story needs to be loaded.

TODO 11

readScene reads a scene and recursively reads all of the scenes below it. This is O(n) since every scene is read and created once.

TODO 12

askChoice asks the player for a choice until they enter a valid number. This is O(1) in terms of n because the number of scenes does not affect it.

TODO 13

play moves through the story while keeping track of HP, loot, and inventory. It also searches the inventory when an item is found. This is O(n squared) in the worst case because there can be up to n scenes visited and each inventory search can take up to O(n).

TODO 14

printStats prints the number of scenes, endings, and the height of the tree by calling the three tree functions. This is O(n) because each function might go through the whole tree.

TODO 15

printSpoilers starts the process of printing every ending by calling printEndings from the root. This is O(n) because all scenes may be visited.

TODO 16

printEndings recursively goes through the tree and prints the path for every ending it reaches. This is O(n) since every scene is visited.

TODO 17

greedyRun travels through one path and always chooses the next scene with the most immediate loot. This is O(n) because in the worst case it can travel through n scenes.

TODO 18

bestLoot recursively checks every choice to find the surviving path with the most total loot. This is O(n) because each scene in the tree is visited once.

TODO 19

optimalRun calls bestLoot from the root and prints the best path and total loot that it finds.

2. 

Each scene allocates exactly numChoices slots because there doesn't need to be extra space for slots that might be unused. An ending holds 0 choices because it can be considered a literal ending of that path, a 'leaf'.

3. 

Every child scene stored in choices_, then the choices_ array, then  data_. If choices_ was deleted first, I would lose the pointers to the child scenes which could cause memory leakage.

4. 

In my story, greedy takes path 1-1 and gets 9 loot. It chooses the first path because the first scene gives 8 loot immediately, but the next scene kills Yuji with an HP change of -20.

Optimal takes path 2-1-1-1-1 and gets 16 loot. It starts with 2 loot, but the full path gives more loot and Yuji survives. Greedy loses because it only looks at the next scene instead of looking at the entire path.

5. 

bestLoot checks every possible path, but doesn't repeatedly visit the same scenes, so the function visits n scenes total, and therefore is O(n) and not exponential.

6. 

My game uses search, addFront, size, and print from List. search checks whether the player already has an item so duplicates are not added. addFront adds a new item to the inventory. size tells how many items are in the inventory, and print displays them at the end of the game.
A single search takes O(n) time, where n is the number of items currently in the bag


