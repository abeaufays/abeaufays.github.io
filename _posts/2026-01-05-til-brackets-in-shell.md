---
layout: post
title: TIL you can use curly braces in a shell
---

You can use curly braces to do multiple operations at once in a shell.  
For example, you can do `touch {a,b,c}.md` to create 3 files `a.md`, `b.md` and `c.md`.  
It also works with more complex commands such as:  
`mkdir -p test/{a,b,c}/{template,content}/init.lua`   

To get this tree:  
```
tree test
test
├── a
│   ├── content
│   │   └── init.lua
│   └── template
│       └── init.lua
├── b
│   ├── content
│   │   └── init.lua
│   └── template
│       └── init.lua
└── c
    ├── content
    │   └── init.lua
    └── template
        └── init.lua
```


*I think this is a very simple thing that I may have learned in school then forgot about...*
