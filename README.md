# RA [11-03-2024]: What a *** is this !!!!!  

What am I doing for the past few hours. Just like wasting so much time I think so. But thats fine.
Just want to cross compile a hello world program into raspberry pi 4 or 0.

    >> lscpu

    Architecture: aarch64
    Byte Order: Little Endian
    CPU(s): 4
    On-line CPU(s) list: 0-3
    Thread(s) per core: 1
    Core(s) per socket: 4
    Socket(s): 1
    Vendor ID: ARM
    Model: 3
    Model name: Cortex-A72
    Stepping: r0p3
    CPU max MHz: 1500.0000
    CPU min MHz: 600.0000
    BogoMIPS: 108.00
    L1d cache: 128 KiB
    L1i cache: 192 KiB
    L2 cache: 1 MiB
    Vulnerability Itlb multihit: Not affected
    Vulnerability L1tf: Not affected
    Vulnerability Mds: Not affected
    Vulnerability Meltdown: Not affected
    Vulnerability Mmio stale data: Not affected
    Vulnerability Retbleed: Not affected
    Vulnerability Spec store bypass: Vulnerable
    Vulnerability Spectre v1: Mitigation; __user pointer sanitization
    Vulnerability Spectre v2: Vulnerable
    Vulnerability Srbds: Not affected
    Vulnerability Tsx async abort: Not affected
    Flags: fp asimd evtstrm crc32 cpuid
The first issue which I faced is when I cross compiled with the gcc mingw compiler and I'm not able to run it on the RPi4. Then I resolved. I forgot how I resolved it. Let me think again update here. 
Then I came to know about the toolchain. It's a kind of bull**. I already done a set up with the MSVC compiler but I hated that, it can be used only for the windows.

> Frustrated..... dot dot dot...

![enter image description here](https://fcit.usf.edu/matrix/wp-content/uploads/2016/09/50012-700.png)

Nothing.... Its literally nothing. even after spending so much of time. And watched some scenes of 'Seventh continent' movie by Michel Heneke. Thinking of existential crisis. Not due to this. Being a Nihilist, thinking like that is so common. 
Just leave those CMake stuffs. I don't want to complicate things now. run,

    g++ helloworld.cpp
    (or)
    gcc helloworld.c
It's a **Segmentation fault**
What am I doing? A helloworld program with 'Segmentation fault'. 
Even tried to debug with GDB, but before even starting the program, it occurred.

> Ranting continues...

Yes, the problem is the toolchain. But I found this today. Some useful stuff. Found something meaningful,

    revanth@raspberrypi:~/helloworld $ gcc -dumpmachine
    arm-linux-gnueabihf
You know what is this? **arm-linux-gnueabihf** is the toolchain need to be used in the host. This command I given in the target. So its like this toolchain of host and target should match.

https://developer.arm.com/downloads/-/arm-gnu-toolchain-downloads

From here, I downloaded the toolchain, Build it, yes!!!, Now the .out file is generated.

    root@raspberrypi:/home/revanth/helloworld# ./helloworld.out
    ./helloworld.out: /lib/arm-linux-gnueabihf/libc.so.6: version `GLIBC_2.34' not found (required by ./helloworld.out)

What is this? The next fu** error (I mean functional error.... eeeeeeeeee). 
1. Copied the whole lib folder locally to target to match libc.so.6. Nothing worked. (In between setting LD_LIBRARY_PATH to this path crashed the ls command also... What a fu**nction is this?)
2. You know what ChatGPT said, wait I'll show you,

> It seems like you're encountering an issue with the GLIBC version mismatch. GLIBC (GNU C Library) is a crucial library for Linux systems, and your program seems to require version `GLIBC_2.34`, which is not available on your system.
> 
> Here are a few steps you can take to address this issue:
> 
> 1.  **Update GLIBC**: If possible, update your system's GLIBC version to at least 2.34. This might involve upgrading your Linux distribution
> or manually updating GLIBC, which can be complex and risky.
>     
> 2.  **Compile on a Compatible System**: Compile your program on a system with the GLIBC version compatible with your target system. This
> ensures that your program is linked against the correct GLIBC version.
>     
> 3.  **Static Linking**: Consider statically linking your program against the GLIBC library. This embeds the necessary library code into
> your executable, eliminating external dependencies. However, this
> might increase the size of your executable.
>     
> 4.  **Docker or Containerization**: Utilize Docker or another containerization technology to package your application along with its
> dependencies. This allows you to run your program in an isolated
> environment with the required GLIBC version.
>     
> 5.  **Compatibility Libraries**: Sometimes, compatibility libraries or packages are available that provide older versions of GLIBC alongside
> newer ones. You can install these libraries to fulfill the
> dependencies of your program.

![enter image description here](https://blog.glugmvit.com/assets/images/docker-logo.png)

*I DONT WANT TO PLAY WITH THIS BLUE WHALE NOW !!!*

Need some hack for the day..... Searching Searching..... Tata bye bye. Good night.... 

# RA[12-03-2024]: Just a peaceful living being... 

The is a new day. Lets start from first.... 😎

Feeling demotivated of my README.md?

Stop searching motivation everyday and everything. It's okay to be express frustration. So that we can focus on what we want by keeping our mind free.

Let try to find a solution today for this. 

![enter image description here](https://grace-being.com/wp-content/uploads/2021/11/Suffering-Buddha-quotes11-min-1024x577.jpg)
