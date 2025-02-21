# Portalese

## Structure

```mermaid
architecture-beta
    service source(disk)[Portalese source code]

    group compilation(disk)[GLaDOS]

    service lexer(database)[Lexer] in compilation
    service parser(database)[Parser] in compilation
    service compiler(database)[Compiler] in compilation
    service linker(database)[Linker] in compilation

    source:R -- L:lexer
    lexer:R -- L:parser
    parser:B -- T:compiler
    compiler:R -- L:linker
    linker:R -- L:binary

    service binary(disk)[Binary executable]

    group runtimeEnvironment(server)[ASEC]

    service processor(server)[Processor] in runtimeEnvironment
    service runtime(server)[Runtime] in runtimeEnvironment

    binary:R -- L:runtime
    runtime:R -- L:processor

    group re2(server)[ASEC]

    service interpreter(server)[Interpreter if time allows it] in re2

    source:L -- R:interpreter
```

*ASEC: Aperture Science Enrichment Center*

## Language

C-based language with a syntax similar to C and a few features from other languages.

## Features

- Integer and floating point numbers
- Strings
- Variables
- Functions
- Conditions
- Loops
- Custom data types (if time allows it)
- I/O (if time allows it)
- References (if time allows it)

## Standards

The following standards will be defined:

- Formal grammar in PEG
- Custom executable format
- Custom instruction set
