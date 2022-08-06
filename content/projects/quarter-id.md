---
title: "Quarter Id"
date: 2022-08-06T11:25:08+02:00
draft: false
---

{{< figure src="/img/projects/quarter-id-quarter.jpg" >}}

Quarter ID was an 8-month (two-semester) project completed in my last year at Virginia Tech
as part of the university's "capstone" program.
The goal of the project was to design and build a system
which coin collectors could use to identify and evaluate the condition of washington quarters.

I was paired with three other students, two studying electrical engineering, and one studying computer vision.
The first half of the project was focused around designing the hardware;
because of Covid-19 I was the only student on campus, so I did most of the construction.
This involved a high-resolution greyscale camera and lens from Basler,
and a pair of high CRI computer vision lights.
We tuned the arrangement of camera and lights to maximize the clarity of the coin face,
and then constructed a rudimentary frame to hold the equipment in the right position.

{{< figure src="/img/projects/quarter-id-apparatus.jpg"
caption="*The somewhat ramshackle apparatus, built in my closet because of Covid.*">}}

We began some software work immediately,
but unfortunately our computer vision student needed to leave the project shortly after the hardware was finished.
This made me the only student with programming experience;
combined with my possession of the hardware, this meant that I needed to take on a leadership role.
I delegated the simpler computer vision tasks to my teammates as they were learning Python and OpenCV,
and integrated the subsystems they created into the unified program.

Despite the loss of a teammate, our system was able to achieve the following goals:

- Control the camera to collect pictures of a batch of coins
- Locate and isolate the coins within the camera's field of vision
- Rotate the coins so that each image was upright
- Identify the date on each coin

To take a closer look at the techniques used in this project, see the open source (GPLv3) repo on Github:

{{< github-card "washington-quarter-id" >}}
