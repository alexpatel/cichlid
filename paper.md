# Notes from James 9/15

- ironclad - why aren't u using this in princess
- trying to figure out mutation function that takes current port and tweak it
until you maximize some utility function
    - maybe genetic programming, AI techniques
- start with something very small
- start with SORTING
    - you have two sorting functions `f(ints)` and `g(ints)` where `f` is
    incorrect and `g` is correct
    - how do you transform (mutate) `f` into `g` so that f is correct
    - if you can do that then you can do porting it's just computer code
- come up with your own ideas, don't read any other papers and pollute your head
- then google about genetic algorithms in like 4-5 days from now
- write the introduction before you do any research 
- write a paragraph in english about high level goal
    - functional notions of correctness that don't require formal steps 
    - the concrete application is if u have existing piece of software  

# Paper/argument scratchpad

- From ASPLOS discussion, first what is the problem to solve:
    - "Margo: we want to work with legacy systems (and
    barrelfish is a legacy system), and build generalizable techniques that can be
    applied to any traditional or well-designed non-traditional kernel"
    - "Margo: verifiable kernels are great but A DIFFERENT PROBLEM. we want
    to mitigate the labor required to PORT AN OPERATING SYSTEM."

- Things from philosophy about how to argue:
    - Argumentation is dialectical, first choose the dialectic and then argue
    - In order to make positive arguments you have to sometimes make negative
    arguments. Negative arguments look like takedowns, but this is okay because
    people can be wrong.
    - Structure outline as one negative argument and one positive argument

- Negative argument: formalizing CPU is hard, I believe it will not work
    - Intel spec is written in English, we may be trying to write semantics
    about something (CPU) that may not actually well defined semantically (implementation
    dependent) at the architecture level rather than the board level - [is that true?]
        - If you want to formalize CPU specs that may not capture exactly how
        CPU behaves, eventually you'll get into probabilistic reasoning and
        things that deal with variance in board and CPU
        - How many CPUs on the market that implement MIPS? ([MIPS arch
        wikipedia](https://en.wikipedia.org/wiki/MIPS_architecture)) 
        - How do you deal with the fact that the chip makers are just
        engineering chips agains the English spec, why would you expect their chips to
        behave exactly the same
            - Is there differing behavior across different MIPS chips that is
            relevant for porting to MIPS?
    - Observation from philosophy: logic is the science of thought, lambda
    calculus is an applied logic
        - Goldfarb: "Lambda calculus = turing machines = HGK systems, so I'm going
        to teach you HGK because I like that one"
        - Does using lambda calculus/type theory logic assume a *perfect* model of
        your computer, that process is just the same as a physical Turing machine.
            - If yes, then why is Intel making new processor (performance, CPU features, etc.)
            - Porting is about working with the hardware, is it true that one
            can just equate CPUs and turing machines

- Positive argument: formalize the porting process instead
    - Porting isn't just about the MD parts of the kernel, you have to port
    tons of things all the way from compiler to application level.
        - techniques used to solve MD kernel component porting don't just need
        to work across arbitrary boards and architectures
    - Do you have to model how the CPU works in order to port your kernel?
        - No, people who port kernels do not know the full spec of the CPU before they do it.
            - There is a difference between "I read the spec" and "I know the
            spec"
                - For the latter to be true it must be the case that you have a mental
                model of the CPU that has feature parity with a board that
                implements that CPU. 
        - They just sit down and screw around with the codes until it works
        - How is formalizing CPU taking advantage of the legacy systems
            - Legacy systems aren't just existing kernels that work
            - It's the fact that we have an implementation of a processor that works
        - In CS161, students just build and compile kernel then run threadtest
            - that's all they need to do so start hacking. Don't need to know how sys161
            works, or have to read all of OS161 code. They just have to run it.
            - So just treat the CPU as a black box for now, I think there are
            other questions that need to be resolved before you start thinking about how to
            describe how the CPU works
                - Eventually you will have to tell me how CPU works, but this
                can be in the form of a computer-readable spec, not necessarily a formalization
                that yields proofs
    - There are three types of kernel porting ([source](https://lwn.net/Articles/597351/)):
        - "It can be a port to a new board with an already-supported processor on it."
        - "it can be a new processor from an existing, supported processor family."
        - "The third alternative is to port to a completely new architecture, as
        with the MPPA 256 (aka K1). "
    - Which of these porting techniques is the hardest (most expensive):
    completely new architecture. Porting to a new board or new processor from
    existing processor family is not that hard, just test that the existing port
    works. You don't need to automate that.
        - Why isn't DARPA just choosing a family of chips and updating their
        submarines with that family? Is Intel going out of business anytime
        soon, their architectures are backwards compatible (64-bit is 32-bit compat).
    - From [what is linux kernel
    porting?](http://opensourceforu.com/2014/09/what-is-linux-kernel-porting/)
    * > "Porting means making something work on an environment it is not designed for."
    * > "Porting differs from development. Usually, porting doesn’t involve as much of
    coding as in development. This means that there is already some code available
    and it only needs to be fine-tuned to the desired target. There may be a need
    to change a few lines here and there, before it is up and running. But, the key
    thing to know is, what needs to be changed and where."
    - Kernel porting has two parts, we are trying to automate the first kind and
    not the second: 
        - *architecture porting*
            > architecture porting means adapting the Linux kernel to the target
            CPU, which may be ARM, Power PC, MIPS, and so on. In addition to this, SOC
            porting can also be considered as part of architecture porting. 
            > Architecture porting entails porting of initial start-up code,
            interrupt service routines, dispatcher routine, timer routine, memory
            management, and so on.
        - *board porting*
            > Whereas board porting involves writing custom drivers and
            initialisation code for devices specific to the board.

- How does porting of the Linux kernel work:
    > After spending countless hours becoming almost fluent in many of the
    supported architectures, I discovered that a well-defined skeleton shared by
    the majority of ports exists
    - can be split into two logical parts ([LWN.net](https://lwn.net/Articles/654783/))
        - part 1: boot code, "the architecture-specific code that is executed
        from the moment the kernel takes over from the bootloader until init is finally
        executed"
        - part 2: other MD kernel code: "The second part concerns the
        architecture-specific code that is regularly executed once the booting phase
        has been completed and the kernel is running normally. This second part
        includes starting new threads, dealing with hardware interrupts or software
        exceptions, copying data from/to user applications, serving system calls, and
        so on."
