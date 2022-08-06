---
title: "N-Body"
date: 2022-08-06T15:06:06+02:00
draft: false
---

{{< figure src="/img/projects/n-body-galaxy.jpg" >}}

N-Body is a personal project I started in the summer before my first year of university, 
in order to build familiarity with C++ in preparation for one of my year-1 courses.
That preparation was ultimately redundant (it was an introductory course),
but I enjoyed the work, and I've continued to add to the project during off periods, since.

The [n-body problem](https://en.wikipedia.org/wiki/N-body_problem) is the algorithmic challenge of modeling
the interactions between very large number of point masses -- 
for example, when simulating the formation of galactic clusters.

My first version of the n-body project focused on the algorithmic aspects. 
I explored multithreading using OpenMP and implemented a 
[Barnes-Hut](https://en.wikipedia.org/wiki/Barnes%E2%80%93Hut_simulation) solver to improve performance,
inspired by articles like [this one](https://jheer.github.io/barnes-hut/)
and guided by [this course curriculum](https://jheer.github.io/barnes-hut/).

In addition to further optimization, 
later versions added improved rendering with [Magnum](https://magnum.graphics/)
and a user interface built with [Gtk 4](https://www.gtk.org/).

{{< figure src="/img/projects/n-body-ui-run.png" >}}

The latest version fully decouples the simulation and UI threads, 
for smooth interaction even with very large simulations.
Some other features include:

- Simulation data saved & loaded from JSON files
- UI for viewing and modifying parameters of individual particles
- Runtime-selectable algorithm, with adjustable algorithm parameters
- Movable camera, with arcball controls or numeric inputs
- Runtime selectable shader for different rendering styles
- Live statistics about the particles and simulation performance


{{< figure src="/img/projects/n-body-ui-table.png" width="80%" >}}
{{< figure src="/img/projects/n-body-ui-particle.png" width="40%" >}}

To take a closer look at the techniques used in this project, see the open source (GPLv3) repo on Github:

{{< github-card "n_body" >}}
