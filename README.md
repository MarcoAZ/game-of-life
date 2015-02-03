# CONWAY'S GAME OF LIFE
	The program creates a window into a seemingly infinite world where cells live or die depending on the status of its neighbors. The cell dies if there are only 1 or fewer live neighbors or more than 3. If there are exactly 3 live neighbors, the cell is born or stays alive. There are a few options for starting configurations. After the number of requested generations, the user can stop the program there or continue with more generations.
	
## DESIGN
	The window into this simulation will be a 2D array of size 80 X 22. To give the effect of this being a window into an infinite world, the actual simulation will be at least 12 spaces beyond this window, giving an actual size of 160 X 102. Each spot of the 2D array is given a value of 0, which indicates that it is dead. This sets the stage for everything else.
	Before drawing out the beginning of the simulation, there are several user inputs that need to be considered. First, I will list a few pre-set configurations that the user will pick from. This will include the glider as well as others of my own design. After they choose the pre-set, they must choose a row and column within the borders of the window. This ensures the simulation is different every time. These pre-sets must have their own functions that will later draw the pre-set onto the board at the given row/column. 
	Finally, it’s time to draw the starting board. Each cell in the 2D array is represented with a space since this indicates they are dead to begin with. Then, the chosen pre-set is drawn on with X’s to represent that they are live. Just as important, the cell itself in the 2D array is set equal to 1. This is important when it comes to counting the number of live neighbors. After asking for an input on the number of generations to draw, the board is drawn onto the terminal and pauses on it for ~1 second.
	Step one is to copy the board onto a temporary board so that births and deaths occur at the same time. Then, cell by cell, the number of live neighbors are counted. Depending on how many are alive, the value of the cell in the copied board is changed to 1 if it is now (or still is) alive and 0 if it is dead. The board is again copied, this time from the copy to the original. The 80X22 board is drawn to the terminal and the system pauses for a brief second. The simulation loops back to the beginning of this paragraph for the number of generations that was input by the user. After that number of generations, the program will ask if the user would like to continue for a new number of generations. A response of no exits the program and a response of yes asks for an input of a number and runs the simulation for the length of this new number.

## TESTING
	The first errors were made for the edges of the “infinite” board causing segmentation faults. I was testing different locations on the window and any coordinates close enough to the edges caused the segmentation fault. I had not considered that the program would check for neighbors that didn't actually exist, so the program was trying to access areas that were not available.
	The next issue was that when choosing where to put the pre-set, if the edges of the visible board are chosen, there doesn't appear to be anything drawn to the board. This occurred while I was still testing putting pre-sets on the board at different locations. At the very least, one cell should be visible when an edge or corner is chosen. I added a square to test the entire perimeter and locate what the issue is. Although the square doesn't seem to be an interesting configuration for the game, it did help me discover that I had not been drawing all the cells that I intended. I had accounted for ghost cells on the left edge but neglect those on the right. Everything seemed to be working as intended at this point.
	Another issue was creating a glider gun. I had, truthfully, misinterpreted that requirement, and thought making a glider configuration had filled this requirement. In order to put in an actual small gun oscillator, I will have to enlarge the ghost edges. After painstakingly entering in the live cells for the configuration, the pre-set was done. I changed the ghost edges to fit this pre-set easily and the glider now worked as an oscillator.
	Besides these issues, I made the usual mistakes that I always seem to make. These include forgetting semicolons at the end of lines, using a plus sign instead of a minus sign, and forgetting syntax (i.e ”board = [rows][cols]” when I meant “board[rows][columns]”).
	
## Reflection
	The assignment seemed very daunting at first but after reading each requirement and breaking it down into simpler steps, it become much more manageable. This time to design it before jumping in gave me a clearer view into what needed to be done. However, it seems I would have profited from spending just a little more on the design. I had not designed the configurations thoroughly beforehand. I wrote out ideas for what configurations I wanted but did not take the time to consider how I would enter them in. The way I had to do it was by brute-force. I set every cell I needed alive, one at a time. This was long and tedious. If I had spent some more time designing this, I could have saved myself some a lot of boring work. Whenever there is repetition in coding, it means there is usually a better way to go about it. If I had spent that extra time designing, I could have found an elegant solution.