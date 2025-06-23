# My little OS kernel development journey

I've always found quite an interest in low level systems. For the largest part of that time though, I knew very close to nothing. I would try researching information but never found much.

Until around a year ago (mid-2024) when I found the [OSDev wiki](https://osdev.wiki) (or at least the [original version](https://wiki.osdev.org), the one I linked is a newer fork). I followed the barebones C tutorial (at the time having only known the bare basics of C, practically nothing) and got a "Hello World" running.

![A screenshot of my original Hello World OS](/assets/helloworld.webp)

It wasn't a lot, and most of it was copied, but I was proud. This later went on to form [SpecOS](https://github.com/UnmappedStack/SpecOS), my original kernel, which was originally 32 bit but became 64 bit. It had a raw FAT32 filesystem without a VFS, memory management, some basic drivers, and a kernelspace shell. Yet I hated it. The one thing it was missing? Running userspace programs. And that is what I wanted.

Around this time, I also started to build up a small but powerful community on Discord (shameless plug: [join here](https://discord.gg/hPg9S2F2nD) lol), and they helped me a *lot*.

A few months later, I begun on [PotatOS](https://github.com/UnmappedStack/PotatOS). It was a *lot* better. It reached userspace, and could run ELF64 executables! It also had a VFS (lettered, aka `C:/`, `D:/` etc), and was non-UNIX-like. I was quite happy with it - it even had a from-scratch LibC.

![A screenshot of PotatOS getting a syscall](/assets/potatos-syscall.png)

I was happy with it, but I wanted to do yet another OS for a few major reasons:
 - I didn't love the codebase, it was messy
 - There were still some random bugs
 - I wanted a UNIX-like OS so that porting software could be easier

And so, I begun [TacOS](https://github.com/UnmappedStack/TacOS)! This is my latest into OS development and I'm very happy with it so far. It's not perfect, but it can do what's important. It runs DOOM! I've ported Doom to it, a Vim-like text editor called Dim, and have my own libc (which I plan to replace with newlib) and a simple set of userspace utilities including a shell (in userspace this time :P).

![TacOS running DOOM](https://github.com/UnmappedStack/TacOS/raw/main/screenshots/screenshot2.webp)

I've learned about file systems (particularly VFSes), memory management (virtual and physical), scheduling (mostly round robin so far), and have seen some other people's amazing projects. I can't wait to get TacOS further and start running more powerful ports!

Hopefully this blog post was at least a little interesting, it was my first one so it might not be perfect, I'm not much of a writer but do want to write up my progress somewhere.

### If my article was interesting...
<iframe src="subscribe.html" style="border: 0px solid transparent"></iframe>
