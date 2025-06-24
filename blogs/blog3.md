# The time I tried rewriting my OS in Rust (and why I went back to C)

A little while ago, I made a [HackerNews post about TacOS](https://news.ycombinator.com/item?id=43778081). It got a fair bit of attention (at the time of writing it's still the 81st top post of 2025), but one comment stood out to me:

![A screenshot of a hacker news comment](/assets/hn-comment.png)

Not a bad point. Why don't I use Rust? Well, at the *start* there were a few main reasons:
 - C is simple. Kernels are complex, so I wanted to keep things that didn't need to be complex, simple.
 - I just am more used to C. I had previously used Rust in smaller projects such as a toy compiler, but not enough to be comfortable with its ins and outs. Meanwhile, I was (and still am) more comfortable with C.

But, literally 11 days later, I decided something. I *did* want to do a rewrite in Rust, but not because of Rust itself. See, TacOS is my 3rd OS project, and while it's a lot better than my older ones, it still has some bits of code from my older projects, and those bits of code are not good at all. They pollute the codebase. The reason? All of them were written in C, so it was too easy to use my old code. Reimplementing it in Rust, however, forced me to rewrite it.

Rust also had some added benefits:
 - It has a built in `alloc` and `core` crate (which `std` builds upon) which can work in a freestanding environment. This meant all I needed was my own basic physical memory manager, and I was golden, no need to implement things like `Box<>`, `Vec<>`, or others.
 - Of course, it's ~~memory safe~~ slightly less prone to memory bugs. In userspace, sure it's memory safe. But in a kernelspace environment, there's only so much memory safety you can have. Of course, you need to rawdog some parts, which is where C shines, and so I needed *a lot* of `unsafe {}` blocks, especially for memory management (raw pointer dereferencing isn't really an option).

I got a bit through the Rust rewrite, not super far though. I had flanterm on the framebuffer and serial output, I had a physical memory manager, a paging mechanism, and a TempFS (I never got to a VFS in the rewrite). Not even to userspace.

It was at around this point that I decided to go back to the C version and fully delete the Rust rewrite branch. Rust just felt too limited with it's "safety" features and overall wasn't well suited to OSDev. I'm also just not used to it enough compared to C, to be able to use it in a low level environment.

Honestly, I feel like trying the rewrite really made me appreciate C more. Dennis Ritchie, you've done me proud!

### If my article was interesting...
<iframe src="https://unmappedstack.dev/subscribe.html" style="border: 0px solid transparent; width: 100vw; height: 500%"></iframe>
