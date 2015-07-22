# Avis Anguis
PuzzleScript port of Snakebird.

[Play here](http://terzalo.com/avis-anguis/ "Play Avis Anguis")

There's just one demo level for the time being.

Differences with Snakebird mechanics:

- Limited number of movable boxes (up to 3, increasable)
- No teleporter yet.
- You have to manually undo last move if a snake died.
- Useless "jumps" straight upward are not discarded from history.

## How to make levels

### The tools

[Official documentation for Levels](http://www.puzzlescript.net/Documentation/levels.html)  
[Official documentation for Level Editor](http://www.puzzlescript.net/Documentation/leveleditor.html)

Levels are listed in the end of the source file. They are in plain text, so one of the ways to make your level is just to type everything you need. You can see what character represents what in LEGEND section of the source code.

The other way is to use PuzzleScript level editor. To access it, build and run source code in [PuzzleScript game editor](http://www.puzzlescript.net/editor.html) and either click "Level Editor" link on top of the page or press E key.

I recommend you to put `run_rules_on_level_start` command in the beggining of source code in parentheses, like this: `(run_rules_on_level_start)`. This will stop the game from processing the level for play mode on level start and you will see the level as it was built in the editor. Just don't forget to remove parentheses after you finish.

Make sure to save the level before you do any player actions, as the level will be processed on the first move. To save the level, click "S" icon on the top left of game area, copy level text from the console and paste it into source code. Playtest, then rebuild the game to reset saved level.

### The rules

There are not much restrictions on how you build the level.

The most important part is creation of snake(bird)s. Start by placing the head of necessary color. There can only be one snake of each color, so three snakes max. Then add the tail by placing arrows, each poiting towards the tile they are connected to. If you start from the tail and follow the arrows, you should end up on the head.

Examples:

              ....    .......
    ......    .↓..    .→→↓...
    .→→→2.    .↓..    .↑.→→↓.
    ######    .→1.    .↑3←←←.
              ####    #######
              
![Snake examples](http://i.imgur.com/C3xPOAR.png)

(You can think of arrows as snake skeletons, since they kinda look like it)

All arrows should point at head or other arrow, and no head or arrow should have more than one arrow pointed at it.

Other things to consider while building a level:

- At least one tile of ground is necessary. The game will place invisible maintenance objects on it.
- You probably don't want snakes to be able to reach level borders. See how long snakes can get on the given level and add enough space or place obstacles. Fill the entire bottom row with water, it kills both snakes and boxes, unlike spikes.
- Don't use one box type to create multiple boxes, this will break gravity.
- Sometimes you'll want to place something on top of "background" box tile, but the editor allows only one object per tile. The game will try to fill holes in "background" box tiles, but it will need at least one such tile to be visible. Sometimes this may result in unwanted background tiles.
- While more than one exit per level should probably work, I did not test it. Proceed with caution.

Thank you!
