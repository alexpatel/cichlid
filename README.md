# cichlid

Alex's 263 project on automated porting.

[Asana Project](https://app.asana.com/0/430530769407377/430530769407377).

From [Wikipedia, "Adaptive
Radiation"](https://en.wikipedia.org/wiki/Adaptive_radiation#Cichlid_fish):

> Another famous example is the cichlid fishes in lakes of the East African
Rift. The lakes in this area are believed to support and sustain about 2,000
different species of these fish, each with different ecological and
morphological characteristics such as body size.[9] Like the Galápagos Islands,
these lakes form a fragmented landscape that isolates the cichlid fish from one
another, allowing them, and many of the organisms they live with, to evolve
separately. The diversity of the lakes is in fact quite extraordinary because
the adaptive radiations here are sometimes so young.

# Notes from James 9/15

- ironclad - why aren't u using this in princess
- trying to figure out mutation function that takes current port and tweak it
until you maximize some utility function
    - maybe genetic programming, AI techniques
- start with something very small
- start with SORTING
    - you have two sorting functions `f(ints)` and `g(ints)` where `f` is incorrect and `g` is correct
    - how do you transform (mutate) `f` into `g` so that f is correct
    - if you can do that then you can do porting it's just computer code
- come up with your own ideas, don't read any other papers and pollute your head
- then google about genetic algorithms
- write a paragraph in english about high level goal
    - functional notions of correctness that don't require formal steps 
    - the concrete application is if u have existing piece of software  

# References

- LWN.net - Porting Linux to a new processor architecture
    - [part 1: The basics](https://lwn.net/Articles/654783/)
    - [part 2: The early code](https://lwn.net/Articles/656286/)
    - [part 3: To the finish line](https://lwn.net/Articles/657939/)
- [LWN.net - Porting Linux to a new architecture](https://lwn.net/Articles/597351/)
- [Youtube - How to Port Linux to a New Processor Architecture by Joel
Porquet](https://www.youtube.com/watch?v=2UVX0YPmvOA)
- [U-Boot - the Universal Boot Loader](https://www.denx.de/wiki/U-Boot/WebHome)
- [What is Linux Kernel
Porting?](http://opensourceforu.com/2014/09/what-is-linux-kernel-porting/)
- [Linux Porting Guide -
embedded](http://www.embedded.com/design/connectivity/4023297/Linux-Porting-Guide)
- [Porting Linux - eLinux.org](elinux.org/images/e/e3/Masters-PortingLinux.pdf)
- [Porting Linux on an ARM
board](elinux.org/images/e/e3/Masters-PortingLinux.pdf)
- [Porting Linux to a Homemade
CPU](https://www.bigmessowires.com/2014/10/23/porting-linux-to-a-homemade-cpu/)
- [Embedded Linux Conference 2016 - Porting Linux to a new processor
architecture](elinux.org/images/6/64/Porquet.pdf)
- [How to Port Linux to a New Processor Architecture by Joel
Porquet](https://www.youtube.com/watch?v=2UVX0YPmvOA)
- [Microsoft Research - Ironclad](https://www.microsoft.com/en-us/research/project/ironclad/)
- [Dafny programming language](https://github.com/Microsoft/dafny/)
- [Microsft Research - SymDiff: Differential Program Verifier](https://www.microsoft.com/en-us/research/project/symdiff-differential-program-verifier/)
