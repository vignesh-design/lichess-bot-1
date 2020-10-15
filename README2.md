# This is another text file.

This is another text file.

# Experiments with lichess-bot

# Move Overhead and Network Lag 

There are 2 different latency settings in config.yml, "Move Overhead" and "move_overhead". Both are likely measured in Milliseconds.

"Move Overhead" refers to the chess engine's move overhead settings, for example Stockfish has a default Move Overhead of 30.
"move_overhead" refers to the actual lag between lichess and your device. In lichess-bot.py it can be seen that "move_overhead" is
subtracted from wtime and btime, yielding in a less-than-true time being sent to the engine. 

From "rigorous" testing using @BlazikenBot2000, I have made a few observations regarding Move Overhead and move_overhead:

Move Overhead, by definition, impact ALL of the engine's moves, from the beginning of the game, to the end of the game. The maximum search
time of each move is "shortened" by the Move Overhead value. This may result is some low-depth search if Move Overhead is too high (ie.
5000). 
move_overhead, on the other hand, largely impacts only the last few moves, especially when the time left equals or is less than
move_overhead. 

Thus in order to avoid clock flags I only set move_overhead value, as the bot will not go below that time limit. I have Move Overhead at the default value. 

# This does not solve the following errors:
