---
title: "Orthtree"
date: 2022-08-07T10:28:35+02:00
draft: False
---

{{< figure src="/img/employment/cgal-logo.png" >}}

<!-- About the position -->

Over the summer of 2020 I participated in Google's [Summer of Code](https://summerofcode.withgoogle.com/) program,
which pairs students with open source projects.
Because of my [N-Body]({{< ref "/n-body" >}}) project I was familiar with tree-based algorithms, 
so I was drawn to CGAL's proposed Octree project.
I was paired with [Simon Giraudot](https://www.linkedin.com/in/simongiraudot/?originalSubdomain=fr)
and worked remotely, corresponding by daily email and regular calls.

<!-- About the project -->

{{< figure src="/img/employment/cgal-orthtree-structure.png" 
caption="*The boxes of an orthtree (black) produced by a point cloud (blue)*" >}}

The goal of the project was to create a new CGAL package which provides an Octree data structure.
An Octree subdivides 3d space into a hierarchy which can be used to speed up certain types of searches. 
CGAL already had one Octree implementation which was used internally by its Shape Detection package,
but it couldn't easily be generalized to other applications.
The Shape Detection package was the primary use-case which guided my API design,
and I also spoke with stakeholders at CGAL and Inria to determine which features would be most useful.

<!-- About the cgal & c++ -->

Working on a new package for CGAL was interesting, 
because the organization makes use of C++ in ways I had never encountered before.
CGAL code is the most generic I have encountered, making heavy use of templates and template metaprogramming.
By the end of the project, I had a much stronger understanding of the language,
and of type theory in general.

<!-- About the results -->

{{< figure src="/img/employment/cgal-orthtree-benchmark.png"
caption="*Benchmark comparing the Octree to a similar data structure*" >}}

The new Octree package was complete partway through the summer, 
and I spent the remainder of the time transitioning the Shape Detection package to the new API,
optimizing and benchmarking, and writing documentation for the API.
After I returned to school, my mentor expanded the library to work in 2-dimensional space (Quadtree)
and in N-Dimensional space (Orthtree).
The Orthtree is now available to users of CGAL since version 5.3. 

To learn more about the Octree project, 
read my short [blog post](https://www.cgal.org/2021/04/27/Orthtree/) announcing its release,
or see the [documentation](https://cgal.geometryfactory.com/CGAL/doc/master/Orthtree/index.html).


<!-- learn more -->
