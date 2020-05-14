Pandemic Simulation in Australia

---------------------------------

This read me provides a basic overview of the approach that the software takes to simulating a pandemic.
Australia (or any other region if the data and map files are changed) is modelled as a graph. Major population
centres are captured as instances of the City class. Connections between cities (roads, railways, etc.) are captured
as neighbours on the City class, in other words, if two cities are connected, they will store each other as neighbours.
If you wish to see the connections on the map during the simulation, you can uncomment the marked section of the
animate map function to display them.

Once the data is read in and the graph is created, the simulation sets some parameters based on the chosen value
of SIMULATION NUMBER. It controls things like the mortality rate (i.e. the proportion of people who get the disease
who will die), the duration of the illness (i.e. how long it takes after contracting the disease for someone to die or
recover), etc. The simulation number also controls things like where the infection starts from and whether there are
any treatment centres present. For example, simulation 0 (the default) starts the pandemic in Alice Springs while
simulations 1 and 2 start the pandemic in Rockhampton, Brisbane and the Gold Coast. You can change the simulation
number as you wish to look at how the pandemic might proceed with different starting locations and parameters.
Once the simulation is setup, it proceeds in a sequence of turns, or steps. Each turn the following happens:

• The start of turn method is called for each city, which moves any infected cases on route to the city, into the
city proper.

• The run turn method is called on each city. This sends some proportion of the infected cases in the city to the
neighbouring cities (though they won’t arrive until the following turn). Then some proportion of the infected
cases in the city either die or recover. Finally, any remaining infected cases spread the disease to healthy
inhabitants.

• The run turn method is called on each treatment centre. The treatment centre cures any infected cases in the
city they are in (as long as their supply of cure is sufficient).

The main work of the simulation is done in the run turn method on the City class, which is responsible for moving
the infected cases around the map and generally controlling the spread of the pandemic. Once a turn is complete, it is
displayed visually on the map along with some statistics. Then, the next turn begins and the whole process repeats,
until either there are no infected cases left, or a pre-defined stopping condition is reached.
