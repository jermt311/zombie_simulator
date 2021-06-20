# Zombie Simulation
Considering how fast the COVID-19 pandemic has spread across the world, I was interested in simulating how long a Zombie Apocalypse would take to infect the world and how long humanity would survive this apocalypse. <br />

The simulated apocalypse will work as follows: <br />
The world will be represented by a 2-dimensional grid of squares with a random number of healthy people and zombies distributed around the world. Each day, a person can either stay in the same square or move 1 square in any direction (i.e. up, downn, left or right). If a zombie spends a day in the same square as the healthy human, the human will become infected (effectively becoming a zombie). <br />

I will explain the simulation parameters and classes first before getting to the simluation implementation itself.

### The simulation implementation will have four (4) parts: 
- Specify the parameters of the simulation
- Initialise the number of people for the simulation
- Run the simulation (at each timestep, the location of each person and zombie will be updated as well as if the human has become a zombie)
- The simulation will be plotted

### Parameters
The simulation will be initialised with four (4) paramters: 
- The size of the 2-dimensional world `side_length` with a default of 40 squares per side
- The maximum timeframe the simulation will run for `maxtime` with a default of 1000 days
- The number of people in the simulation `npeople` with a default of 100
- The rate that a zombie can spontaneously enter remission and return to being a healthy human `remission` with a default of 0

### People
Each person will be associated with a number of pieces of information
- Their x coordinate (an integer between 1 and the size of the world)
- Their y coordinate (an integer between 1 and the size of the world)
- Whether or not they are a zombie

### The Simulation
The Simulation will consist of calculations that occur inside the loop over a period of time. 
- We have to identify where the person will move to (north, south, east, west, north west, north east, south east, south west or stay put)
- If the person where to move outside the defined world (i.e. x, y < 0 or x, y > side_length - 1), they will come through the other side of the world (thus assuming they have periodic boundary conditions). 
- For example: `A person who moves to x = -1 will instead move to x = side_length - 1`.
- Identify which people are zombies and which people aren't
- To handle identification of infections, for each zombie/ non-zombie pair, we need to check if a zombie is infecting the same square as a non-zombie (if their x and y coordinates are equal) and if so, turn the human into a zombie
- Finally, for each zombie, we need to check if they spontaneously return to being a human (due to `remission`)

### Plotting of Results
- A scatter plot will be used where a dot shows the position of the zombie or human on the xy plane.
- Healthy people will be plotted in blue
- Zombies will be plotted in green.
