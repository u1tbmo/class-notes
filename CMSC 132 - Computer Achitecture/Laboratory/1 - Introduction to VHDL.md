# VHDL

- VHSIC (Very High Speed Integrated Circuit) Hardware Description Language
- Programming language used for the specification, modeling, synthesis, and simulation of digital logic circuits
- Used in electronic design automation to describe digital and mixed-signal systems such as programmable gate arrays and integrated circuits
- Enforces strong data typing
## Advantages of VHDL

- Behavior of the required system is described (modeled) and tested (simulated) before translating into real hardware.
- Description of both non-concurrent and concurrent systems.
## Features of VHDL
- Describes logical circuit models
- Strongly-typed and case-insensitive
- Has file input and output capabilities
- Supports the whole design process
    - System level
    - RT level
    - Logic level
    - Circuit level (to some extent)
- Suitable for specification in behavioral and structural domains
- Precise simulation semantics is associated with the language constructs
# GHDL
- A VHDL compiler that can execute VHDL programs in Linux
# Compiling and Running VHDL Programs using GHDL

```vhdl
-- Hello world program
use std.textio.all; -- Imports the standard textio package

-- Defines a design entity, without any ports
entity hello_world is
end hello_world;

architecture behaviour of hello_world is
begin
  process
    variable l: line;
  begin
    write(l, String'("Hello World!"));
    writeline(output, 1);
    wait;
  end process;
end behaviour;
```

