---
title: "Spectrogram"
date: 2022-08-06T12:43:34+02:00
draft: false
---

{{< figure src="/img/projects/spectrogram-output.jpg" >}}

Spectrogram was a 4 month (one-semester) project completed as part of my coursework at Virginia Tech.
The assignment allowed for a lot of leeway when selecting a task;
because of my interest in music, I wanted to build a spectrogram (a type of audio visualizer).
I formed a group with two like-minded students,
and we set out with the goal of making a cross-platform C++ program which would visualize the system's audio streams.

Because the program doesn't play the music itself, it receives no information about upcoming audio.
This required us to apply real-time programming techniques to ensure the latency was acceptably low.

Because of Covid, this project needed to be completed remotely. 
This forced us to pay special attention to our development processes, to ensure our team was always on the same page.
I took on a software-architect role and designed interfaces 
so that we could independently build the different parts of the program.
I also configured a continuous integration pipeline, 
so that we could use unit tests to ensure intended behavior at the boundaries between modules.

{{< figure src="/img/projects/spectrogram-diagram.png"
caption="*The UML Diagram which dictated the structure of our program.*" >}}

I took responsibility for the low level plumbing of the program.
This included the interface with the cross-platform audio stream library [SoundIO](http://libsound.io/),
and the lock-free queues needed to communicate the captured data to the program's other processes.
My teammates developed other parts of the program, 
including most of the UI (using [QT](https://www.qt.io/design)), 
plot rendering (using [QCustomPlot](https://www.qcustomplot.com/)), 
and the fourier transform (using [FFTW](https://www.fftw.org/)).

{{< figure src="/img/projects/spectrogram-ui.jpg" caption="*Screenshot of the completed QT program.*" width="80%">}}

I was especially enthusiastic about this project, 
because it's something which I could make use of after development was complete.
On my own time (during and after the course), 
I developed a [GTK](https://www.gtk.org/)-based frontend on top the same audio pipeline foundation.
I have a personal preference for GTK over QT, and this was a way to learn more about building GTK applications.

To learn more about this project, see the open source (GPLv3) repo on Github:

{{< github-card "spectrogram" >}}
