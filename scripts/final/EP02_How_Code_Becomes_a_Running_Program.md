# ETC EPISODE 02 — HOW DOES CODE BECOME A RUNNING PROGRAM?

**Working title:** How Does Code Become a Running Program?  
**Target duration:** 12 minutes 45 seconds (approx.)  
**Estimated narration:** approximately 1,500 words, plus visual-only beats  
**Audience:** Curious general viewers; no programming background assumed  
**Central question:** How does human-written source code become operations carried out by a processor?  
**Premise:** Follow one small program through the software layers that translate, prepare, load, and execute it — while discovering why different programming languages take different routes.  
**Viewer takeaway:** A program does not simply jump from readable text into the CPU. A language implementation, compiler or interpreter, linker, operating system, runtime, memory system, and processor architecture cooperate to make it run.

---

# 1. RESEARCH BRIEF

## Core explanation

A computer program begins as source code written according to a programming language's rules. What happens next depends on the language and its implementation.

For a conventional native C program built with GCC, the familiar toolchain can include preprocessing, compilation, assembly, and linking. The linker combines object files and required library references into an executable or another output form.

For the standard CPython implementation of Python, source code is compiled into Python bytecode. The CPython bytecode interpreter executes that bytecode. This is a different route from directly compiling a C source file into a native executable for the target platform.

An operating system then creates a process from an executable. On ELF-based systems, executable and shared-object files describe segments used to create a process image; dynamic linking can resolve references among program components. The operating system establishes the program's virtual address space and execution environment.

At the processor level, machine instructions are encoded according to an instruction-set architecture (ISA). The CPU fetches instructions and performs the operations they specify. Registers hold values and state; instructions may also read and write memory. Real processors use sophisticated techniques such as pipelining, caching, speculation, and out-of-order execution, so a simple fetch/decode/execute animation is a teaching model, not a literal account of every modern CPU's internal timing.

## Important distinctions and misconceptions to avoid

- A programming language is not the same thing as one implementation of that language.
- "Compiled" and "interpreted" are not mutually exclusive categories for every language implementation.
- CPython compiles Python source to bytecode; its interpreter executes that bytecode. Python bytecode is not the same thing as the target CPU's native machine code.
- A compiler may produce an intermediate representation or assembly rather than a final executable.
- Assembly and machine code are related but not identical: assembly is a human-readable representation; machine instructions are encoded for a particular ISA.
- Linking and loading are different operations.
- An executable file is not simply copied in full into physical RAM. The operating system establishes a process image and virtual-memory mappings; details vary by OS and executable format.
- The CPU does not understand Python, C, JavaScript, or human intention. It implements an instruction-set architecture.
- "The CPU fetches, decodes, and executes one instruction at a time" is an oversimplification of modern processors. Use it only as a conceptual introduction, then qualify it.
- Do not claim all languages or all computers follow the exact C/GCC or CPython paths shown here.

## Main demonstration

Use one tiny C program to demonstrate a native compilation pipeline, then contrast it with a tiny Python program running under CPython.

C example:

```c
#include <stdio.h>

int main(void) {
    int result = 2 + 3;
    printf("%d\\n", result);
    return 0;
}
```

Build command:

```bash
gcc main.c -o main
```

Python example:

```python
def add(a, b):
    return a + b

print(add(2, 3))
```

Keep the explanation conceptual. Do not claim every compiler emits identical assembly or that every Python implementation behaves exactly like CPython.

---

# 2. SOURCE REGISTER

| ID | Source | Organisation | Use in this script |
|---|---|---|---|
| S1 | [GCC — Overall Options](https://gcc.gnu.org/onlinedocs/gcc/Overall-Options.html) | GNU Project | GCC's preprocessing, compilation, assembly, and linking stages |
| S2 | [GCC — Invoking GCC](https://gcc.gnu.org/onlinedocs/gcc/Invoking-GCC.html) | GNU Project | Normal GCC invocation and compilation pipeline |
| S3 | [CPython — Compiler design](https://github.com/python/cpython/blob/main/InternalDocs/compiler.md) | Python / CPython project | CPython source-to-bytecode stages: tokenization, parsing, AST, control-flow graph, bytecode |
| S4 | [Python — Execution model](https://docs.python.org/3/reference/executionmodel.html) | Python Documentation | Code blocks, execution frames, runtime and interpreter terminology |
| S5 | [CPython — The bytecode interpreter](https://github.com/python/cpython/blob/main/InternalDocs/interpreter.md) | Python / CPython project | How CPython's bytecode interpreter executes code objects |
| S6 | [System V ABI — Program Loading and Dynamic Linking](https://gabi.xinuos.com/elf/07-loading-intro.html) | Generic ABI documentation | Executable files, process images, segments, loading and dynamic linking |
| S7 | [System V ABI — Program Loading](https://gabi.xinuos.com/elf/08-pheader.html) | Generic ABI documentation | Program headers and segments used to prepare a process image |
| S8 | [System V ABI — Dynamic Linking](https://gabi.xinuos.com/elf/09-dynamic.html) | Generic ABI documentation | Dynamic linker and resolving symbolic references |
| S9 | [Intel 64 and IA-32 Software Developer's Manuals](https://www.intel.com/content/www/us/en/developer/articles/technical/intel-sdm.html) | Intel | Processor architecture, programming environment, instruction set and execution resources |
| S10 | [RISC-V Unprivileged ISA Specification](https://docs.riscv.org/reference/isa/_attachments/riscv-unprivileged.pdf) | RISC-V International | Instruction fetch and instruction-defined memory operations; a separate ISA example |

---

# 3. NARRATIVE OUTLINE

| Time | Chapter | Purpose |
|---|---|---|
| 00:00–00:45 | The impossible gap | Create the mystery: readable code versus hardware operations |
| 00:45–01:40 | The language humans write | Establish source code, language rules, and the machine's instruction set |
| 01:40–02:45 | Before translation | Explain tokens, parsing, and program structure through CPython |
| 02:45–04:50 | The compiler's journey | Demonstrate GCC's C pipeline |
| 04:50–05:45 | Connecting the pieces | Explain object files, libraries, and linking |
| 05:45–07:20 | Not every language takes the same road | Explain CPython bytecode and interpreter execution |
| 07:20–08:35 | From file to process | Explain executable loading and the operating-system role |
| 08:35–10:25 | The processor takes over | Explain ISA, instructions, registers, and execution |
| 10:25–11:30 | Memory and the running program | Explain process memory and runtime state |
| 11:30–12:45 | The whole journey | Reassemble the layers and resolve the opening question |

---

# 4. COMPLETE SCRIPT AND VISUAL TIMELINE

## SCENE 01 — THE GAP BETWEEN CODE AND HARDWARE

**Timestamp:** 00:00–00:45

**Narration:**

Look at these five characters.

`2 + 3`.

To you, they are almost effortless to understand. You see two numbers and an operation. You already know the answer.

Now imagine asking a computer to do the same thing.

You could write a line of code. Press Run. And, almost instantly, the answer appears.

But look closer.

The processor inside your computer does not read Python or C the way you do. It does not look at a plus sign and understand addition as an idea.

So what happens between the moment you write a line of code and the moment the computer actually performs the operation?

There is an entire chain of software and hardware working behind that simple result.

**Visual direction:**

Begin on a completely black screen. A cursor types `2 + 3`. The expression expands into a clean code editor. Camera pushes through the text, revealing a motherboard and CPU package. Freeze before reaching the chip. Then show the question: **HOW DOES CODE BECOME ACTION?**

Do not show a fake literal stream of binary entering a CPU. The transition is conceptual.

**On-screen text:** HOW DOES CODE BECOME ACTION?

**Sound design:** A single keyboard tap, low restrained pulse, then a brief drop to silence before the central question.

**Research references:** S9, S10.

---

## SCENE 02 — HUMANS WRITE LANGUAGES; MACHINES IMPLEMENT INSTRUCTIONS

**Timestamp:** 00:45–01:40

**Narration:**

Programmers write instructions using programming languages.

Languages such as C and Python give humans ways to express calculations, decisions, repetition, and data.

But a programming language is not the processor's native instruction set.

A processor is designed around an instruction-set architecture — an agreed description of the instructions it can execute, the registers it exposes, and how those instructions interact with memory.

That architecture is specific. An instruction encoded for one processor architecture is not automatically understood by another.

This creates a translation problem.

The code must be processed by software that understands the programming language and knows how to produce something the target system can use.

And that software is not always the same kind of tool.

**Visual direction:**

Split the frame. Left: readable C and Python code. Right: an abstract instruction-set reference and a processor block diagram. In the middle, show a software toolchain as a bridge. Label the ISA as the contract between machine instructions and processor design.

**On-screen text:** SOURCE CODE → LANGUAGE IMPLEMENTATION → MACHINE EXECUTION

**Sound design:** A quiet mechanical rhythm begins as the bridge forms.

**Research references:** S9, S10.

---

## SCENE 03 — BEFORE A PROGRAM CAN BE TRANSLATED

**Timestamp:** 01:40–02:45

**Narration:**

Before a language implementation can do anything useful with source code, it has to work out what that code means according to the language's rules.

Let's use Python as an example.

Imagine writing:

`print(2 + 3)`

The implementation does not simply search for familiar words and guess what you intended.

A compiler front end first breaks the source into meaningful pieces called tokens. These tokens are then parsed according to the language grammar.

The result can be represented as a structured form called an abstract syntax tree.

Think of it as a map of the program's structure.

The implementation can now distinguish the function call from the addition inside it. It can reason about the relationships between the pieces instead of treating the source as one long string of characters.

In CPython, this process continues through compiler stages that eventually produce Python bytecode.

But bytecode is not yet the processor's native instruction set.

That distinction will matter in a moment.

**Visual direction:**

Show `print(2 + 3)` as text. Highlight tokens one by one: `print`, parentheses, `2`, plus, `3`. Rearrange them into a simple tree: function call → addition → two values. Then transform the tree into a compact bytecode-like visual. Clearly label the diagram **CONCEPTUAL — CPYTHON COMPILATION**; do not invent exact bytecode instructions.

**On-screen text:** SOURCE → TOKENS → STRUCTURE → BYTECODE

**Sound design:** Subtle clicks as tokens separate; soft tonal movement as the syntax tree forms.

**Research references:** S3, S4.

---

## SCENE 04 — THE C COMPILER: A DIFFERENT ROUTE

**Timestamp:** 02:45–04:50

**Narration:**

Now let's follow a different path.

This time, we will use C and the GNU Compiler Collection, better known as GCC.

Here is a tiny program:

```c
#include <stdio.h>

int main(void) {
    int result = 2 + 3;
    printf("%d\\n", result);
    return 0;
}
```

When we run a command such as:

`gcc main.c -o main`

GCC can carry out several stages.

The first is preprocessing.

The preprocessor handles directives such as the include line in our example. It expands the source according to preprocessing rules, including bringing in declarations from included headers.

Next comes compilation proper.

The compiler analyses the program and translates it into a lower-level representation. Depending on the compiler and options, this can involve optimisations and the generation of assembly language.

Assembly is more closely related to the processor's instruction set, but it is still a human-readable representation.

Then comes assembly.

An assembler turns assembly instructions into an object file containing encoded machine instructions and other information needed by later stages.

And this is important: an object file is not necessarily the finished program.

It may still contain references to functions or data that have not yet been connected.

The stages are not magic. They are a toolchain, with each component doing a specific job.

**Visual direction:**

Use the actual C source code on screen. Animate a pipeline with four clear stations:

1. **PREPROCESSOR** — show `#include <stdio.h>` expanding into a simplified header/declaration representation. Do not flood the screen with the entire real header.
2. **COMPILER** — source structure becomes a clean assembly-style view.
3. **ASSEMBLER** — assembly lines become bytes grouped into an object-file icon.
4. **OBJECT FILE** — show a file labelled `main.o`.

Use the exact command `gcc main.c -o main` in a terminal-style inset. Explain that real outputs vary with compiler version, target architecture, and options.

**On-screen text:** PREPROCESS → COMPILE → ASSEMBLE

**Sound design:** Each stage gets one restrained mechanical transition. Keep narration dominant.

**Research references:** S1, S2.

---

## SCENE 05 — WHY THE OBJECT FILE ISN'T THE END

**Timestamp:** 04:50–05:45

**Narration:**

Our object file contains machine instructions, but a complete program often depends on code that lives elsewhere.

In our example, the program calls `printf`.

That function is provided by a library.

The linker connects the pieces. It combines object files, considers the libraries the program needs, and resolves references between them.

The result may be an executable file that the operating system can load.

There is a useful distinction here.

Compilation translates code. Linking connects the program's components. Loading prepares a program to run.

They are related stages, but they are not the same operation.

And the file that comes out of the linker still has not performed the calculation on your screen.

It is a prepared description of a program — not a running process.

**Visual direction:**

Show `main.o` on the left and a library block on the right. Draw reference lines from the program's external function call to the library symbol. The linker assembles the connected pieces into an executable labelled `main`. Avoid implying that every library is copied into every executable; distinguish static and dynamic linking only visually as alternatives if needed.

**On-screen text:** OBJECT FILES + LIBRARY REFERENCES → LINKER → EXECUTABLE

**Sound design:** Two separate rhythms resolve into one stable tone.

**Research references:** S1, S6, S8.

---

## SCENE 06 — PYTHON TAKES ANOTHER ROUTE

**Timestamp:** 05:45–07:20

**Narration:**

So is that what happens to every program?

No.

Let's return to Python.

In the standard CPython implementation, source code is compiled into Python bytecode. The bytecode interpreter then executes those instructions.

That means the word "interpreted" does not mean the source file is necessarily read as plain text, one character at a time, every time a line runs.

There is a compilation step here too.

But Python bytecode is designed for the Python interpreter. It is not the same thing as native machine code for your processor.

The interpreter itself is software running on the computer. It is ultimately made of instructions that the processor can execute.

So when CPython runs your Python program, the processor executes the interpreter's native instructions. Those instructions implement the behaviour of the Python bytecode.

This is why the simple argument — compiled languages versus interpreted languages — can be misleading.

Different language implementations use different combinations of compilation, interpretation, virtual machines, and sometimes just-in-time compilation.

The important question is not only, "What language is this?"

It is also, "Which implementation is running it, and what execution strategy does that implementation use?"

**Visual direction:**

Return to the Python example. Show source code becoming bytecode, then entering a clearly labelled **CPYTHON BYTECODE INTERPRETER**. Show the interpreter as a native application running on the operating system. Use two layers: Python bytecode instructions inside the interpreter; native CPU instructions underneath. Keep the two instruction sets visually distinct.

**On-screen text:** PYTHON SOURCE → BYTECODE → CPYTHON INTERPRETER

**Sound design:** A softer, more fluid sequence than the GCC pipeline. Briefly pause on the distinction between bytecode and machine code.

**Research references:** S3, S4, S5.

---

## SCENE 07 — THE OPERATING SYSTEM CREATES A PROCESS

**Timestamp:** 07:20–08:35

**Narration:**

Let's return to the native executable we built with GCC.

When you launch it, the operating system has a major job to do.

It must create a process — a running instance of the program — and prepare the environment in which it can execute.

On an ELF-based system, executable files contain information describing the segments needed to create a process image.

The operating system uses that information to establish the program's memory layout.

The process receives a virtual address space. Its code, data, stack, and other regions are arranged according to the executable format and operating-system rules.

If the program uses shared libraries, a dynamic linker may also need to load those libraries and resolve references before normal execution proceeds.

Notice what is happening.

The operating system is not asking the CPU to understand a file full of C code.

It is preparing a process with the code and resources needed for execution.

And that process is kept separate from the process running another application.

**Visual direction:**

Show an executable file opening into a process container. Map labelled regions: **CODE**, **DATA**, **HEAP**, **STACK**. Show a shared library being mapped into the process as a separate component. Use a virtual-address-space diagram, not a literal physical RAM map. Label this as a simplified ELF/Linux-style example, not a universal layout for every operating system.

**On-screen text:** EXECUTABLE → PROCESS → VIRTUAL ADDRESS SPACE

**Sound design:** A controlled low-frequency build as the process container forms.

**Research references:** S6, S7, S8.

---

## SCENE 08 — NOW THE PROCESSOR CAN DO ITS WORK

**Timestamp:** 08:35–10:25

**Narration:**

Now we reach the hardware.

The processor does not receive the original line:

`int result = 2 + 3;`

It executes machine instructions encoded for its instruction-set architecture.

At a conceptual level, the processor fetches an instruction, works out what the instruction means, and carries out the required operation.

Some instructions perform arithmetic. Others move data, compare values, change the flow of a program, or interact with memory.

The processor has registers — very small, very fast storage locations inside the CPU — that hold values and execution state.

An instruction might use values in registers, perform an addition, and place the result into another register.

A different instruction might read data from memory or write a value back.

This is the level at which the program's operations become real hardware activity.

But there is one more important detail.

Modern processors are far more sophisticated than a simple three-step animation suggests.

They may overlap work, predict branches, execute operations out of order, and use several levels of cache to keep data close to the processor.

The architecture defines the behaviour that software can rely on. The physical processor may use many internal techniques to achieve that behaviour efficiently.

So the CPU is not translating your Python or C code.

It is executing instructions that have already been prepared for the machine — directly, or as part of the interpreter that is running your program.

**Visual direction:**

Begin with a conceptual instruction represented as an encoded bit pattern. Transition to a CPU diagram with three labelled conceptual stages: **FETCH**, **DECODE**, **EXECUTE**. Show a value moving through registers during an addition. Then widen the view to show a modern CPU pipeline with multiple operations overlapping. Add a clear note: "Conceptual model — modern CPUs are more complex." Avoid showing a literal single-file queue as if all processors execute one instruction at a time.

**On-screen text:** INSTRUCTION → PROCESSOR OPERATION

**Sound design:** A restrained clock-like pulse becomes a layered, precise rhythm. Avoid exaggerated sci-fi effects.

**Research references:** S9, S10.

---

## SCENE 09 — MEMORY IS PART OF THE STORY

**Timestamp:** 10:25–11:30

**Narration:**

A running program is not just a list of instructions.

It also needs data.

Think about our small example. The program has a result to calculate, values to work with, and a function to call.

Some values may be held temporarily in processor registers. Other data lives in memory.

The operating system gives each process a virtual address space. The processor and memory-management hardware translate the addresses used by the program into locations in the system's memory hierarchy.

That hierarchy includes CPU registers, caches, and main memory. Each level has different capacity, speed, and purpose.

When a program asks for data, the processor may find it in a nearby cache, or it may need to access a lower level of the memory hierarchy.

This is one reason performance is not simply about how many instructions a program contains.

Where data lives, how often it is reused, and how the processor accesses it can make a major difference.

The program is now a living process: instructions being executed, values being changed, memory being accessed, and the operating system managing the environment.

**Visual direction:**

Show a process with a small data value moving between a virtual address, memory hierarchy, cache, and CPU register. Keep the hierarchy qualitative; do not invent exact latency numbers. Show the result value changing from 2 and 3 to 5. Make clear that the diagram is conceptual.

**On-screen text:** CODE + DATA + PROCESS STATE

**Sound design:** Calm, steady pulse; subtle sound when the result changes.

**Research references:** S7, S9, S10.

---

## SCENE 10 — THE MOMENT A PROGRAM BECOMES REAL

**Timestamp:** 11:30–12:45

**Narration:**

Let's return to where we started.

A few characters on a screen.

`2 + 3`.

They look simple because the language hides the complexity from us.

But behind that simplicity is a chain of transformations and responsibilities.

A language implementation analyses the source. A compiler or interpreter prepares it for execution. A linker may connect the program to other components. The operating system creates a process and prepares its memory environment. And the processor executes machine instructions that make the program's operations happen.

The exact path depends on the language, its implementation, the compiler or runtime, the operating system, and the processor architecture.

There is no single universal pipeline.

But the central idea is this:

A computer does not magically understand the code we write.

We build layers of software that translate our intentions into precise instructions — and layers of hardware that carry those instructions out.

The next time you press Run, remember: the program you see is only the beginning of the story.

**Visual direction:**

Reassemble the full chain from left to right:

**SOURCE CODE → LANGUAGE IMPLEMENTATION → COMPILER / INTERPRETER → LINKING / RUNTIME → OPERATING SYSTEM → PROCESSOR + MEMORY → OUTPUT**

Show the original expression `2 + 3` again. The result **5** appears. Pull back to reveal the entire layered system behind it. End on a clean ETC title card.

**On-screen text:** CODE DOESN'T BECOME ACTION BY MAGIC. IT PASSES THROUGH LAYERS.

**Sound design:** Resolve the music into a warm, understated final note. Leave a short pause before the ETC logo.

**Research references:** S1–S10.

---

# 5. FACT-CHECK REPORT

| Claim | Status | Qualification |
|---|---|---|
| GCC can perform preprocessing, compilation, assembly, and linking | Verified | Exact pipeline and output depend on invocation and options |
| CPython compiles Python source into bytecode | Verified | This describes CPython; do not universalise to every Python implementation |
| CPython's bytecode interpreter executes code objects | Verified | Interpreter internals evolve between versions |
| Python bytecode is not native CPU machine code | Verified with qualification | The interpreter itself is native software executed by the processor |
| ELF executable files describe segments used to create process images | Verified | Applies to ELF-based systems; not every OS uses ELF |
| Dynamic linking resolves references among program components | Verified | Exact loader and linking behaviour is platform-dependent |
| CPUs execute instructions defined by an ISA | Verified | Different processor architectures have different instruction sets |
| A simple fetch/decode/execute sequence describes all modern CPU internals | Not stated as literal fact | Presented only as a conceptual model and explicitly qualified |
| Programs use registers and memory during execution | Verified | Exact use and mapping depend on architecture and implementation |
| Every language follows the same source-to-executable path | Rejected | Script explicitly explains implementation-specific routes |

# 6. EDITORIAL NOTES

- The documentary uses GCC and CPython as two concrete examples, not as universal models for all languages.
- The C example is illustrative. Exact assembly and optimisation results vary by compiler version, target architecture, and build options.
- The operating-system section uses ELF as a concrete executable-format example. It should be visually labelled as an ELF-based system, not as a description of every OS.
- The fetch/decode/execute sequence is a conceptual teaching model. Modern processors overlap and reorder internal work while maintaining the architectural behaviour software relies on.
- Avoid presenting binary streams, CPU diagrams, or memory layouts as literal photographs of internal activity.
- If a real terminal demonstration is recorded, show the compiler command and the resulting executable on the actual target system. Do not imply that every platform uses the same command or file extension.
- This script intentionally does not attempt to teach every compiler optimisation, linker relocation, operating-system scheduler, or CPU microarchitecture detail. Those subjects could each support their own episode.

# 7. FINAL RUNTIME CHECK

- **Target:** approximately 12:45.
- **Narration speed assumption:** approximately 125–140 words per minute.
- **Narration estimate:** approximately 1,500 words; recount and time a spoken recording before locking the edit.
- **Visual-only moments:** approximately 30–45 seconds distributed across transitions and demonstrations.
- **Expected finished runtime:** approximately 12–14 minutes, depending on delivery and edit pace.
- **Runtime verdict:** Appropriate for the requested 10–15+ minute range. Do not add filler to reach a longer duration.

**Editorial status:** REVISE AFTER TABLE READ — the research basis and structure are prepared; record a timed read-through, validate every demonstration against the target toolchain, and perform the final spoken-word and citation audit before publication.
