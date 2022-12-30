# How its made

```bash
mkdir demolib
cd demolib
lake init demolib lib
mkdir Demolib
touch Demolib/X.lean
```

# How to use

In make another directory for lean executable

```bash
cd ~
mkdir consumer
cd consumer
lake init consumer exe
```

Main.lean

```
import Demolib

def main : IO Unit :=
  IO.println s!"Hello, {hello}!"
```

Add the line `require demolib from git "https://github.com/userJY/demolibLean.git"`

lakefile.lean

```
import Lake
open Lake DSL

require demolib from git "https://github.com/userJY/demolibLean.git"

package «democonsumer» {
  -- add package configuration options here
}

lean_lib «Democonsumer» {
  -- add library configuration options here
}

@[default_target]
lean_exe «democonsumer» {
  root := `Main
}
```

Or pulling the library locally with `require demolib from "~/demolib"` where `~/demolib` is path of the directory 

```
import Lake
open Lake DSL

require demolib from "~/demolib"

package «democonsumer» {
  -- add package configuration options here
}

lean_lib «Democonsumer» {
  -- add library configuration options here
}

@[default_target]
lean_exe «democonsumer» {
  root := `Main
}
```
