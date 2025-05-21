<h1>Basic Approach</h1>

Maze Setup:
The maze is read from a text file, where some cells are walls and others are open paths. The Triwizard Cup, Harry, and the Death Eater are each placed at random open spots in the maze.

Game Rules:
Harry and the Death Eater can move up, down, left, or right, but not through walls. The Death Eater always chases Harry using the shortest possible path. Harry’s goal is to reach the Cup without getting caught.

Learning for Harry:
At first, Harry moves randomly. Over time, Harry learns how to move by using a technique called Q-learning. Harry gets a reward when he reaches the Cup, a penalty if caught, and a small penalty for each step taken.

Training:
The program runs many games (episodes) where Harry tries to reach the Cup. After each move, Harry’s strategy (Q-table) is updated based on what happened. Training continues until Harry can consistently reach the Cup without being caught.

Visualization:
The whole process is shown visually using Pygame, so to watch Harry and the Death Eater move in the maze.

<h2>Assumptions:</h2>

Walls are represented by #. The Cup is marked with C. Maze is surrounded by walls (no out-of-bounds spawns). Harry, Death Eater, and Cup never spawn in walls. 
Step penalty (-1) encourages the model to give faster solutions. No intermediate rewards are given for getting closer to the Cup. Training stops after 10 consecutive wins or 1000 episodes.<br>

<h3>Colour Codes:</h3>
| Element   | Color      | RGB Value   | Description        |<br>
|-----------|------------|-------------|--------------------|<br>
| Hydrogen  | White      | 255,255,255 | Maze barriers        |<br>
| Carbon    | Black      | 0,0,0       | Empty maze area           |<br>
| Nitrogen  | Blue       | 0,0,255     | Harry’s current position (circle)         |<br>
| Oxygen    | Red        | 255,0,0     | Death Eater’s position (circle)         |<br>
| Fluorine  | Green      | 0,255,0     | Triwizard Cup (square/rect)    |




<h2>How to run:</h2>
Open the terminal or command prompt and run:<br>
<b>pip install pygame numpy matplotlib</b>
<br>
Add the python code and the sample maze file in the same folder. In the terminal go to the same folder in which the files are stored and run:
python >code filename<.py
