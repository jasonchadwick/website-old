[← back to home](../main.md)

# Cosmic string research

In the summer of 2019, I worked with Ken Olum at the Tufts Institute of Cosmology to study the properties of smooth cosmic string loops. I began the summer running computational simulations of cosmic strings and later transitioned to working on a mathematical proof with Prof. Olum. Below is an explanation of cosmic strings and a brief summary of my research.

### The Higgs field in the early universe

---

*([paraphrased from this excellent description](https://arxiv.org/html/astro-ph/0005186))*

The Higgs field permeates all space and has a “value” everywhere. If the Higgs field is in its ground state, the point where it is stable, its value is zero everywhere. This is the current state of the field. However, right after the Big Bang, the Higgs field was in a state of unstable equilibrium. As the universe cooled down, the field began to transition from this equilibrium point to a new value with lower energy. If this happens at one point in the field, then the field close to this point will also take on this value, and thus the new state would expand outwards in a bubble, with the field inside the bubble having transitioned to a new phase.

In a cooling universe, such a phase transition would not necessarily proceed in an orderly fashion. Instead, there would be separate regions in which the Higgs field transitions to different new states, because the bubbles take some time to expand and the phase change could happen in many places at around the same time. As these regions began to merge, they will not necessarily all just become one big space. For example, we can visualize the possible values of the Higgs field as a hill with a valley on each side. At the Big Bang, the Higgs field is positioned unstably at the top of the hill. Then, when it transitions, it either rolls down one side or the other. If an expanding bubble with a left-falling field meets a bubble with a right-falling field, they could not smoothly transition to one another, leaving a barrier of energy between them where the energy of the field goes up and over the hill. Right along this barrier, the Higgs field still has the characteristics of the initial post - Big Bang field. This type of topological defect is known as a domain wall. (We do not think that these exist because they would be very obvious in the sky, as far as we know).

### Cosmic strings

---

However, many models predict a Higgs field with circular symmetry, such that the field begins on a hill in the middle and is surrounded on all sides by a ring-shaped valley. The field can fall in any direction and its “position” can be denoted by an arrow that points outward from the center and can be between 0 and 360 degrees. (This is not a direction in physical space, just a way of visualizing the possible states of the field.) So, different points in space can have different arrow directions. As separate regions of broken symmetry merge, it is not always possible for the field orientations to match. A cosmic string forms when the orientation of the arrows cannot be adjusted so as to keep the Higgs field in the minimum energy state at all places. With our arrow example, this would be if the arrows of multiple different bubbles point away from some place in the middle. For most of space, the field is in its new state, but at the point where the arrows cannot “smooth out”, the Higgs field must pass over the central hill, creating a narrow, extremely massive structure with unbroken symmetry (the original Higgs value) along its length. 

Grand Unified Theories, which aim to unite the strong interaction with the already unified electroweak force, tend to contain Higgs fields that produce these cosmic strings.

As cosmic strings move through the universe, they are predicted to emit gravitational waves due to their extremely high energy density. This is the main way that cosmologists expect to someday observe cosmic strings. The purpose of my research was to get closer to this goal by simulating the evolution of cosmic strings and finding the expected gravitational wave emissions to guide future observations.

### Proving that smooth loops will decay

---

So that was the theoretical physics background for cosmic strings. I mainly worked with the mathematical interpretation, which deals with the strings as objects with zero thickness (in reality, the strings are thinner than the width of an atom, so zero is a fair approximation for many cases).

Cosmic strings can have features called "cusps" and "kinks". A cusp is where the string doubles back on itself, and the point at the top temporarily moves at the speed of light. A "kink" is a sharp bend in the string.

When a long string intersects itself, it will break off a small loop (leaving a kink behind in the original string). It is predicted that remaining cosmic strings in the universe are mostly loops. I studied a subclass of these loops, those which have no cusps or kinks. The shape of the loop can be described by two 3D line functions, known as a' and b', which are time and space derivatives of the string. These functions, projected onto the unit sphere, must both average to 0 over their length. When the a' and b' functions intersect one another, there is a cusp in the string. When there is a discontinuous jump in one or the other, there is a kink.

Initially, we wanted to examine a specific loop of my research advisor's design that had no kinks or cusps. While I was running simulations of it, I saw that the loop intersected itself. Cosmic string loops oscillate with a certain period, and if they self-intersect during this period, they will break into smaller loops and eventually disintegrate. We were not able to find a similar loop that did not self-intersect, and visual inspection of a' and b' hinted that this problem may be unavoidable. My research advisor reached out to others and eventually found a different loop that is stable, but it had a fundamentally different formation. After discussing with my advisor, we decided to try to prove that all loops of our type of configuration would intersect themselves before they could complete a full oscillation.

We were unable to complete a rigorous proof by the end of the summer, although we did verify several special cases. Looking at the bigger picture, the work we did was not necessarily the most groundbreaking or influential, but I really enjoyed working on a problem that nobody had attempted before and actually getting some results out of it. The problem-solving process was fun and thought provoking, and I learned a lot about the process of academic research, as well as computational physics and proof-writing specifically.

[← back to home](../main.md)
