# Socket-based-drone-control-system

Group assignment done in collaboration with Lorenzo Benedetti, Matteo Carlone, Fabio Conti, Claudio Del Gaizo, Marco Macchia, Andrea Manera, Francesco Pagano, Samuele Pedrazzi, Luca Predieri, Ettore Sani.

## How to run

Compiles all scripts
```bash
cd ./project/
./install.sh <pathname> #pathname is the folder that will contain the executables

```

The <pathname> directory will contain the src folder, the help.sh and run.sh bash scripts and a README.txt
All executables will be in their own respective directories in the src folder.
In <pathname> folder, run:
```bash
./run.sh

```

## Description

This project is the result of our first real cooperative assignment. It is a concurrent program composed by 5 processes, 4 drones and 1 master,
communicating through sockets.

Initially the master process is executed in his own console. The console will be used to print the position of all the 4 drones in real-time.
After the console initialization (using the ncurses library), it creates a socket used by drones to send their positions, or better, their
movement request. The master in fact is capable of checking if the drone that wants to move can do it safely, without colliding with the walls
or the other drones. Everytime the master receives a request, it handles it and sends to the appropriate drone the confirm or the negation of the
movement. 

The master console shows every drone with his own label and his own state (active, marked in green, and idle, marked in blue), and it also shows every position
that has been already visited using dots.

During the execution each drone continousely compute a new position that has to be sent to the master, and waits for the answer. The drones also have
a internal battery that discharged during flight. When the battery is empty, every drone can land and refuel the battery, momentarily goind in idle state
(this action is communicated to the master in order to update the GUI). The console of each drone can show many things, f.e. the battery charge status
and the actual position and the drone's already explored positions.   
