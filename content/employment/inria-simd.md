---
title: "SIMD"
date: 2022-08-07T20:12:52+02:00
draft: false
---

{{< figure src="/img/employment/inria-logo.png" >}}

I enjoyed my time [building an Octree for CGAL]({{< ref "/cgal-orthtree" >}}), 
and I was interested in continuing the same type of work.
After the end of the summer I kept in touch with my mentor, 
and he put me in contact with his colleagues at [Inria](https://www.inria.fr/en).
Once I knew I would be attending graduate school in Europe we made arrangements for in-person work at 
[Inria's research campus](https://www.inria.fr/en/inria-centre-universite-cote-azur) in Sophia Antipolis, France.

At Inria, I reported to [Pierre Alliez](https://team.inria.fr/titane/team/pierre-alliez/).
My goal for the summer was to look at ways SIMD instructions could be incorporated into the CGAL library.
Specifically, I examined Intel's [Embree](https://github.com/embree/embree) library,
and how it used SIMD in its Bounding Volume Hierarchy to accelerate intersection searches.
The intention was to find some optimizations which could be carried over to CGAL's 
AABB (Axis-Aligned Bounding-Box) Tree package.
Embree was a useful project to study because it was the product of hardware-software-compiler codesign:
the software engineers writing Embree worked directly with those developing the Intel Compiler,
ensuring that their code would produce optimal SIMD assembly.

This was more exploratory than previous projects, with the main work product being a regular report on my findings.
For more information, you can find a copy those notes [here]({{< ref "/inria-simd-blog" >}}).
During my time at Inria, I identified and tested the following avenues for optimization:

- *N-Way Tree*:
  Produces a shallower hierarchy than a (conventional) 2-way tree, 
  but this would normally be cancelled out by more expensive comparisons at each node.
  With SIMD instructions, those comparisons can be done in parallel.
- *Vectorized Bounds Checking*: 
  With SIMD, we can compare the X, Y, and Z bounds of a pair of boxes in parallel,
  making box-box intersections faster.
  This is useful even for 2-way trees.
- *Parallel Tree Construction*: 
  Subtrees can be constructed simultaneously after higher level nodes are finished,
  using conventional parallelism concepts.
- *Implicit Tree Structure*: 
  Child nodes can be placed at specific memory addresses, 
  so that parents don't need to maintain references to their children.
  The splitting algorithm can distribute children so that a _complete_ tree is produced,
  resulting in a data structure which requires much less memory.
- *Rapid Tree Constructor*: 
  Sorting the points along a space-filling curve can be done efficiently using radix sort,
  This is a way to build a low-quality tree very rapidly,
  especially because it allows bounding boxes to be created from the bottom-up.
- *Modified AABB-Tree Implementations with Different Topologies*: 
  The objects sorted by CGAL's AABB-Tree can pre-compute their own bounding boxes.
  By changing how we place child nodes in the tree structure,
  we can avoid giving leaf nodes bounding boxes, reducing overall memory requirements.

Over the course of the project, I also produced useful tools and tests:

- A script which analyzes the prevalence of SIMD instructions in a specific function of a given binary.
- A script for visualizing the branches within a specific function using objdump.
- Test implementations and benchmarks of simple algorithms with a variety of C++ SIMD libraries.
- A number of standardized benchmark datasets for evaluating tree construction performance in different scenarios.