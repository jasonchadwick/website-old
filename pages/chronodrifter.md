[← back to home](../index.md)

# Chronodrifter: a 2D time-manipulation puzzle platformer

[Github repository](https://github.com/placeholder-studios-dev/chronodrifter)

[Live web game](https://placeholder-studios-dev.github.io/chronodrifter)

---

Chronodrifter is a 2D puzzle platformer based around the idea of time reversal. The player can slow down and reverse the time of their environment without affecting their own timeline, which allows for cool tricks like below:

| ![towerjump-gif](/files/tower.gif) |
|:--:|
|Climbing a tower of blocks by reversing time.|

I began the project in the summer of 2021 and resumed working on it that winter after the semester ended, along with a few friends. We plan to release the game once we develop it further, and potentially create a 3D version in the future.

### Storing time history of objects

---

Each time-reversible object maintains a stack of previous states (structs that implement the StateInterface interface)

[← back to home](../index.md)