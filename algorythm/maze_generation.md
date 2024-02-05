# Maze Generation

## Wilson's algorithm

> Wilson’s algorithm was developed by David Bruce Wilson, a principle
> researcher at Microsoft and an affiliate associate professor of
> mathematics at the University of Washington.

This algorithm performs  a [loop-erased random walk](https://en.wikipedia.org/wiki/Loop-erased_random_walk) , which means that as it goes, if the path it is forming happens to intersect with itself and form a loop, it erases that loop before continuing on.

Wilson's algorithm generates an unbiased sample from the [uniform distribution](https://en.wikipedia.org/wiki/Discrete_uniform_distribution) over all mazes.

### Flowchart

```mermaid
graph TD;
	Start
	---> A(Choose the first maze cell at random)
	---> D1{All cells have been visited ?}
		D1 --no--> 
			B1(Choose another cell to create a path) --->
			C(Choose a random nearby cell C) --->
			D{C belongs to the maze ?}
				D--yes--> Dn(Add current path to the maze and delete walls)
				D--no--> Dy{C is part of the current path}
				Dy --yes--> Dyy(Erase loop)
					---> Dyy1(Current cell = C)
					---> E
				Dy --no--> E
				Dn--->D1
			E(Choose a random nearby cell C) --->D
			D1 --yes-------------> Exit

```

> Written with [StackEdit](https://stackedit.io/).
