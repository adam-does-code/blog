+++
title = "pdb feels like 🪄 magic" 
tags = ["til"]
date = "2026-11-12"
+++

## back to python? 

I've spent the tail end of this year doing some python code for both MCP servers and LLM work, now i've made it a goal to get better at writing _more python (and being zenful about it)_. As a result i've been playing around with the pdb. 

Not using print statements and really leverging the pdb felt overwhelming at first especially trying to figure out when to use `--pdb` vs `--trace`. I've mostly been using the trace ability but have been able to really know when to step into the function call vs keep going next. The only problem i am sometimes struggling with is printing out variables that aren't straight forward dataclasses. I ran into this problem when i was printing out a generator object that looked like: `<generator object interpolate at 0x...>` 

I thought wow well that gives me _nothing_ 

## First of all.. what is a generator? 

I then had to learn about generators in Python:

> A generator is a Python object that produces values one at a time, on demand, instead of building a whole list up front. You make one by writing a function that uses yield instead of return.

After a bit of searching i learned that we can import itertools into pdb and then use that to inspect our generator values without changing the values or modifying it so you can continue tracing: 

```
(Pdb) import itertools
(Pdb) msgs, peek = itertools.tee(msgs)
(Pdb) p list(peek)
OR 
(Pdb) p msgs.gi_frame.f_locals
```

