# My love/hate relationship with UNIX-likes

![A pdp11 running Unix](/assets/pdp11.jpeg)

Ahhh Unix. How I wish I was alive early enough to be a hobbyist on a PDP-11 in the early 70s, using the original Unix shell. I guess that's not much of a problem though, I just use it's derived OSes instead. I personally run good ol' Arch Linux, and Linux is probably the most iconic Unix-like to still be commonplace.

Through my OS development journey I've kinda gone backwards and forwards on Unix. Do I hate it for exec/fork? Do I love it for it's flexible VFS? Are Unix devs insane or genius? Am I bipolar? Have I forgotten to take my Unix-derived craziness pills?

Here are my thoughts on the pros and cons of Unix-likes, both on the technical side and the not-so-technical side.

## The Unix-style VFS
***Goooooood***. You can't tell me you don't want to mount your USB at `/dev/sda241` while frantically trying to find your drives with `lsblk` while being scared you'll overwrite it (yes this is a massive exaggeration, it's probably the best solution). 

NT has kinda gone back and forth in following this. At the start, they had a completely lettered VFS, where you mount drives corresponding to a letter. Now, they internally use Unix-style mounting, but still have an abstraction over the top with lettered mounting.

Personally, I like Unix-style mounting for a VFS. It's flexible. Not as simple to implement, but far easier to use, and the speed only takes quite a minor decrease. Plus, there's so many ways to implement it internally such as a node graph or a mountpoint list. It kinda is just the solution that makes the most sense.

## exec()/fork()
I have one question for you, Ritchie. When you were planning out exec/fork, *were you high??* `exec/fork` is literally the worst method I could think of. It's slow, it's memory inefficient, it's more prone to bugs than `spawn()` due to being less simple...

And yes, I get it. It's to follow the Unix philosophy (or at least one of their many philosophies, not the good old "do one thing and do it well"): be flexible. But the tradeoff just isn't worth it!

The only reason I would use exec/fork instead of spawn in my kernel (which I currently *am* doing) is that it makes porting some software a bit easier.

## Unix devices
This is just the best way to handle devices. Anybody who says otherwise hasn't read up on it enough or hasn't implemented it.

There's nothing more to say. It's great.

## Less technically, though?
"I don't really love how many hobby OSes are Unix-like, do something original". This seems to be a pretty common sentiment. But here's my view. Why does it matter if you're doing the same as everyone else? It's not like you're trying to make the next big thing (I hope not at least). You're trying to understand your system and the technology that makes it all possible. And in many cases, said system *is* Unix like. So isn't it fulfilling the entire purpose of OSDev by making something that helps you understand what you use yourself?


### If my article was interesting...
<iframe src="subscribe.html" style="border: 0px solid transparent"></iframe>
