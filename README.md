# game

## Write your own agent

write student_agent. To do so: 

1. Modify the [`student_agent.py`](agents/student_agent.py) file in [`agents/`](agents/) directory, which extends the [`agents.Agent`](agents/agent.py) class. 
2. Implement the `step` function with your game logic
3. Register your agent using the decorator [`register_agent`](agents/random_agent.py#L7). The `StudentAgent` class is already decorated with `student_agent` name, feel free to change it or keep it the same.
4. [This step is already done for `StudentAgent`] Import your agent in the [`__init__.py`](agents/__init__.py) file in [`agents/`](agents/) directory
5. Run and test your agent using the information above

    ```
    python simulator.py --player_1 random_agent --player_2 student_agent --display 
    ```

6. Check autoplay with your agent and `random_agent` is working

    ```
    python simulator.py --player_1 random_agent --player_2 student_agent --autoplay
    ```

## Game Rules

### Game Setting
On an *M* x *M* chess board, 2 players are randomly distributed on the board with one player occupying one block.

### Game Moving
In each iteration, one player moves at most `K` steps (between `0` and `K`) in either horizontal or vertical direction, and must put a barrier around him or her in one of the 4 directions except the boarders of the chess board. The players move in a round-robin way.

#### Note: 
 - Each player cannot go into other player's place or put barriers in areas that already have barriers.
 - Currently the maximal number of steps is set to `K = (M + 1) // 2`.

### Game Ending
The game ends when each player is separated in a closed zone by the barriers and boundaries. The final score for each player will be the number of blocks in that zone.
```math
S_i = \#\text{Blocks of Zone}_i
```

### Goal
Each player should maximize the final score of itself, i.e., the number of blocks in its zone in the endgame.

### Example Gameplay
Here we show a gameplay describing a $`2`$-player game on a $`5\times 5`$ chessboard. Each player can move at most $`3`$ steps in each round.

<p align="center">
  <img src="https://github.com/wenjunRose/game/blob/main/Gameplay.gif" width="600" height="600">
</p>

The final score is $`A:B = 15:10`$. So A wins the game.
