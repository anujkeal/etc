# ETC EPISODE 02 — HOW DOES CODE BECOME A RUNNING PROGRAM?

**Revision:** 2 — revised after editorial review  
**Target runtime:** 12–13 minutes  
**Narration target:** approximately 1,400–1,500 words, with 45–75 seconds of intentional terminal demonstrations and visual-only beats  
**Audience:** Curious general viewers; no programming background assumed  
**Central question:** How does a line written by a human become an operation performed by a processor?  
**Premise:** Follow one small C program — from source code to a running process — and watch a real compiler turn an addition into a processor instruction.  
**Single running example:** One C program that adds 2 and 3, then prints the result.  
**Narrative analogy:** A restaurant order moving through a kitchen. Use it consistently as an explanatory analogy, never as a literal description of computer hardware.

---

# 1. RESEARCH BRIEF

## The actual path shown

This episode follows one concrete route: a small C program built with GCC on a Linux x86-64 system.

1. The programmer writes C source code.
2. The C preprocessor handles directives such as `#include`.
3. GCC compiles the program into assembly language.
4. The assembler produces an object file containing machine-code sections and symbol information.
5. The linker combines the program's object code and arranges references to external functions and libraries. In this example, `printf` is dynamically linked.
6. The operating system starts a process from the executable and prepares its execution environment.
7. The processor executes machine instructions; the program uses registers and memory while it runs.
8. The program prints `5`.

The exact output shown in the demo was produced in a Linux x86-64 environment using GCC 14.2.0. Assembly syntax and register names will differ across architectures, compiler versions, and options.

## Single program used throughout

```c
#include <stdio.h>

int add(int a, int b) {
    return a + b;
}

int main(void) {
    int result = add(2, 3);
    printf("%d\\n", result);
    return 0;
}
```

**Bug check:** The format string must contain the C escape sequence `\n` — one backslash followed by n. Do not place two backslashes before n in the actual C source.

## Verified real demonstration

Environment used for the captured sample:

- GCC 14.2.0
- Debian GNU/Linux environment
- x86-64 target
- Build at `-O0` for a readable, unoptimised teaching example

Commands:

```bash
gcc --version
gcc -E main.c -o main.i
gcc -S -O0 main.c -o main.s
gcc -c -O0 main.c -o main.o
nm -u main.o
gcc -O0 main.c -o main
./main
objdump -d main
```

Observed output:

```text
$ ./main
5
```

Relevant real assembly from `main.s`:

```asm
add:
    movl    %edi, -4(%rbp)
    movl    %esi, -8(%rbp)
    movl    -4(%rbp), %edx
    movl    -8(%rbp), %eax
    addl    %edx, %eax
    popq    %rbp
    ret
```

Relevant disassembly from the linked executable:

```asm
1143: 8b 55 fc    mov    -0x4(%rbp),%edx
1146: 8b 45 f8    mov    -0x8(%rbp),%eax
1149: 01 d0       add    %edx,%eax
114b: 5d          pop    %rbp
114c: c3          ret
```

The important reveal is the `add` instruction. The C expression `a + b` has become an instruction encoded for the target processor.

The exact assembly is environment-specific. Record the terminal on the creator's own machine if the video is meant to show their actual setup. Label any supplied sample with its compiler and architecture.

The object file reports an unresolved external symbol:

```text
$ nm -u main.o
                 U printf
```

This is a useful visual clue: the object file still refers to `printf`. The final executable in this Linux example is dynamically linked. The static link step records the required dynamic-linking information; the dynamic loader participates when the program starts.

## Key factual qualifications

- This is one C/GCC/Linux example, not a universal pipeline for every programming language or operating system.
- GCC's `-E`, `-S`, and `-c` options let us stop at preprocessing, assembly generation, and object-file creation respectively.
- Assembly is a human-readable representation of instructions. The object file contains encoded machine instructions plus metadata and symbol/relocation information.
- The linker connects program components. Dynamic linking can defer the actual loading and resolution of shared-library symbols until program startup.
- The operating system creates a process and establishes its memory environment. A program is not simply copied wholesale into physical RAM.
- The CPU executes instructions for its instruction-set architecture. The video will not teach the full architecture or microarchitecture.
- The restaurant analogy is only a mental model. A compiler does not literally read a recipe, and a CPU does not literally cook.

---

# 2. SOURCE REGISTER

| ID | Source | Organisation | Use |
|---|---|---|---|
| S1 | [GCC 14.2 — Overall Options](https://gcc.gnu.org/onlinedocs/gcc-14.2.0/gcc/Overall-Options.html) | GNU Project | Meaning of `-E`, `-S`, and `-c` |
| S2 | [GCC 14.2 — Preprocessor Options](https://gcc.gnu.org/onlinedocs/gcc-14.2.0/gcc/Preprocessor-Options.html) | GNU Project | Preprocessor behaviour |
| S3 | [System V ABI — Program Loading](https://gabi.xinuos.com/elf/07-loading-intro.html) | Generic ABI | Executable loading and process image |
| S4 | [System V ABI — Program Headers](https://gabi.xinuos.com/elf/08-pheader.html) | Generic ABI | ELF program segments |
| S5 | [System V ABI — Dynamic Linking](https://gabi.xinuos.com/elf/09-dynamic.html) | Generic ABI | Dynamic linker and symbol resolution |
| S6 | [Intel 64 and IA-32 Software Developer's Manuals](https://www.intel.com/content/www/us/en/developer/articles/technical/intel-sdm.html) | Intel | Instruction set and processor behaviour |
| S7 | [GNU Binutils — objdump](https://sourceware.org/binutils/docs/binutils/objdump.html) | GNU Project | Disassembly of object files and executables |
| S8 | [GNU Binutils — nm](https://sourceware.org/binutils/docs/binutils/nm.html) | GNU Project | Displaying symbols in object files |

---

# 3. NARRATIVE OUTLINE

| Time | Chapter | Narrative purpose | Visual proof |
|---|---|---|---|
| 00:00–00:55 | The impossible journey | Create the mystery | Code on screen, then real terminal result |
| 00:55–02:00 | One tiny program | Establish the only example and the kitchen analogy | Show the complete C program |
| 02:00–03:20 | Preparing the order | Explain preprocessing and compiler work | Run GCC preprocessing and show output |
| 03:20–05:25 | The translation | Reveal assembly and the real `add` instruction | Record `gcc -S`; highlight `addl` |
| 05:25–06:35 | The unfinished package | Explain object files and linking | `nm -u main.o`; link the executable |
| 06:35–08:10 | Opening the kitchen | Explain process creation and program loading | Launch program; show process/memory concept |
| 08:10–10:15 | The processor does the work | Explain instruction, registers and addition | Disassemble executable; animate operands |
| 10:15–11:20 | Where the working data lives | Explain registers, stack and memory without a jargon dump | Follow arguments and result |
| 11:20–12:30 | From code to result | Reconstruct the whole path and resolve the mystery | One continuous end-to-end animation |

---

# 4. COMPLETE SCRIPT AND VISUAL TIMELINE

## SCENE 01 — YOU PRESS RUN. WHAT ACTUALLY RUNS?

**Timestamp:** 00:00–00:55

**Narration:**

You write a few lines of code. You press Run. A moment later, your screen displays a result.

It feels almost instant.

But your computer has not simply looked at your code and understood what you meant.

There is a journey between those lines of text and the tiny electrical operations happening inside a processor.

And we can actually watch part of that journey.

Today, we're going to take one small program — one that adds two numbers and prints the answer — and follow it all the way from a source-code file to a running program.

Not with a cartoon explanation.

With a real compiler, real machine instructions, and a real result.

**Visual direction:**

Start with a close-up of the Run button. Cut to the program's output: `5`. Rewind the image. The number travels backwards through a CPU, an executable file, assembly, and source code. Freeze on the original code.

**On-screen text:** FROM CODE TO EXECUTION

**Sound design:** One keyboard click. A short, restrained impact on the word "real". Music begins with a curious pulse.

**Research references:** S1, S6, S7.

---

## SCENE 02 — ONE ORDER, ONE PROGRAM

**Timestamp:** 00:55–02:00

**Narration:**

Here is our entire program.

It has one job: take the numbers two and three, add them, and print five.

Think of it like placing an order in a restaurant.

You write the order in a language you understand. But the person who receives it cannot simply turn your handwriting into a finished meal. The order has to pass through a kitchen, where each person and each station has a specific job.

A computer program follows a similar chain.

Our source code is the order. The compiler prepares instructions for a particular kind of machine. Other tools connect the pieces. The operating system prepares a place for the program to run. And finally, the processor carries out the instructions.

The analogy isn't literal, but it gives us a map.

Let's follow this one program.

**Visual direction:**

Show the corrected C source code in a clean editor. Highlight only the three important parts: `add`, `printf`, and `main`. Beside it, introduce a minimal restaurant-kitchen diagram: order → preparation → station setup → work being carried out. Keep this same visual metaphor available as a small recurring motif throughout the video.

**On-screen text:** ONE PROGRAM. ONE JOURNEY.

**Sound design:** Quiet kitchen ambience blends into a subtle electronic rhythm.

**Research references:** S1.

---

## SCENE 03 — THE COMPUTER PREPARES THE ORDER

**Timestamp:** 02:00–03:20

**Narration:**

Before the compiler translates our program, the first step is preparation.

Look at the very first line:

`#include <stdio.h>`

It tells the C preprocessor to bring in the declarations from the standard input and output header.

In our restaurant analogy, this is like attaching the instruction sheet for a service the kitchen will need.

The preprocessor handles that instruction before the main compilation work.

We can see it ourselves.

Open the terminal and run:

`gcc -E main.c -o main.i`

Now we have a preprocessed file.

It contains far more text than our original program, because the included header has been processed too.

That is the first reveal: the compiler does not simply take the exact few lines we typed and turn them directly into a finished application.

The source goes through preparation first.

**Visual direction:**

Record a real terminal running the exact command. Show the file `main.i` appearing. Open it briefly and search for `int main`. Do not scroll through pages of header declarations. Return to the kitchen analogy: the order now has the required reference sheet attached.

**On-screen text:** `gcc -E main.c -o main.i`

**Sound design:** A paper-sheet movement, then a quiet confirmation tone.

**Research references:** S1, S2.

---

## SCENE 04 — THE TRANSLATION: WATCH THE ADDITION CHANGE

**Timestamp:** 03:20–05:25

**Narration:**

Now comes the part where the transformation becomes visible.

Our C code says:

`return a + b;`

A human understands that immediately.

But the processor needs instructions encoded for its own architecture.

Let's ask GCC to stop after generating assembly:

`gcc -S -O0 main.c -o main.s`

Open the file.

This is assembly language: a readable representation of low-level instructions.

And look at this line:

`addl %edx, %eax`

There it is.

The addition we wrote in C has become an instruction called `add`.

The values are placed in processor registers. The instruction tells the processor to add one value to another and keep the result.

This is the moment the mystery starts to become concrete.

We began with:

`a + b`

And the compiler produced an instruction that the target processor understands.

The kitchen order has been translated into a set of precise steps for this particular machine.

But we are not finished. Assembly is still a readable representation. The machine needs the encoded instructions, not the words on the screen.

**Visual direction:**

This is the major proof scene. Record the actual terminal:

`gcc -S -O0 main.c -o main.s`

Open `main.s`, find the `add` function, and highlight the exact line `addl %edx, %eax`. Animate the two incoming values entering two register blocks; the add instruction combines them. Use the actual captured output, not recreated pseudo-assembly. Add a small label: "GCC 14.2 · Linux x86-64 · -O0" if using the supplied sample; replace it with the creator's actual environment if recording locally.

**On-screen text:** `a + b` → `addl %edx, %eax`

**Sound design:** Music drops back while the assembly line appears. One precise click as the two values combine.

**Research references:** S1, S6.

---

## SCENE 05 — THE OBJECT FILE IS STILL WAITING

**Timestamp:** 05:25–06:35

**Narration:**

The next tool is the assembler.

It turns the assembly representation into an object file containing encoded machine instructions and information the next stage needs.

Let's create one:

`gcc -c -O0 main.c -o main.o`

Now inspect its unresolved symbols:

`nm -u main.o`

The terminal shows:

`U printf`

That letter is telling us something useful: this object file still refers to a function called `printf`, but that reference has not been fully connected here.

Our program needs that function to display the answer.

This is where the linker comes in.

Think of it as the station manager making sure the order is connected to the services it needs.

The linker produces the executable and records the information needed to connect dynamically linked libraries when the program starts.

Now we have something the operating system can launch.

**Visual direction:**

Show `main.o` appearing. Run `nm -u main.o` and highlight `U printf`. Animate a cable connecting the program to the output-library service. Then run `gcc -O0 main.c -o main`. Show the executable file. Do not imply every library is copied directly into the executable; label this example as dynamically linked.

**On-screen text:** OBJECT FILE → LINKER → EXECUTABLE

**Sound design:** A small connection sound as the reference is resolved; no dramatic effects.

**Research references:** S5, S8.

---

## SCENE 06 — THE OPERATING SYSTEM OPENS THE WORKSPACE

**Timestamp:** 06:35–08:10

**Narration:**

We now have an executable file.

But a file sitting on a drive is not yet a running program.

When we launch it, the operating system prepares a process — a running instance of that program.

Think of opening a kitchen station for a new order.

The operating system sets up the space the program needs. It arranges the program's code and data in its memory environment, prepares the initial execution state, and makes sure the program can use the resources it needs.

In this Linux example, the executable also relies on a dynamic loader to prepare its shared-library dependencies.

There are several details hidden behind that one action, but the key idea is simple:

The operating system turns the executable into a process that is ready to run.

Now the processor has a program to execute.

**Visual direction:**

Record launching `./main`. Freeze the terminal. Transition to a clean process diagram: executable file → process container. Show code, data, stack, and shared-library regions as labelled blocks inside a virtual memory space. Keep technical labels on screen rather than narrating every term. This is a simplified Linux/ELF example, not a universal operating-system layout.

**On-screen text:** EXECUTABLE → RUNNING PROCESS

**Sound design:** A soft startup sound, then a stable rhythmic pulse.

**Research references:** S3, S4, S5.

---

## SCENE 07 — THE PROCESSOR FINALLY GETS TO WORK

**Timestamp:** 08:10–10:15

**Narration:**

Now let's look at the processor.

It does not receive the C expression `a + b`.

It receives machine instructions — encoded operations designed for its instruction set.

Our assembly line was:

`addl %edx, %eax`

The processor has small, extremely fast storage locations called registers. The values needed for this addition are placed there.

The add instruction tells the processor to combine them.

Two and three become five.

We can inspect the finished executable too.

Run:

`objdump -d main`

This tool displays the machine instructions in a readable assembly form.

Find the `add` function.

You can see the instruction encoded in the executable itself.

So this is not an animation invented for the video. It is a real instruction in the program we just built.

The processor follows instructions like these, along with many others, to make the program work.

**Visual direction:**

Record `objdump -d main` and find the `<add>:` label. Highlight the actual `add` instruction and its bytes. Animate register A holding 2, register B holding 3, and the destination becoming 5. Label this register animation as a simplified explanation. Do not suggest that every CPU internally executes one instruction at a time; avoid the full microarchitecture detour.

**On-screen text:** MACHINE INSTRUCTION → RESULT: 5

**Sound design:** A tight, restrained pulse. A clean tonal resolution when 5 appears.

**Research references:** S6, S7.

---

## SCENE 08 — WHERE DOES THE PROGRAM KEEP ITS WORK?

**Timestamp:** 10:15–11:20

**Narration:**

A program needs more than instructions. It needs somewhere to keep the information it is working with.

Some values are held in registers inside the processor. Other values live in memory.

Our function receives two numbers, uses them in the addition, and returns the result to the part of the program that called it.

The program also needs to keep track of where it is in its work — which function is running, where to return, and what data is currently needed.

The operating system gives the process its own memory environment, while the processor moves values between registers and memory as the instructions require.

Think back to our kitchen.

The instructions are the order. The registers are the small working space right beside the chef. Main memory is the larger storage area nearby.

The analogy is imperfect, but it helps explain why a running program needs both instructions and data.

**Visual direction:**

Show the function call from `main` to `add`. Animate 2 and 3 entering the function, the addition, and 5 returning. Show registers as a small work surface and process memory as a larger storage area. Avoid exact latency claims or overly detailed memory hierarchy graphics.

**On-screen text:** INSTRUCTIONS + DATA + MEMORY

**Sound design:** Calm, steady music. A subtle return sound as the result moves back to `main`.

**Research references:** S3, S6.

---

## SCENE 09 — THE WHOLE JOURNEY

**Timestamp:** 11:20–12:30

**Narration:**

Let's follow the journey one final time.

We wrote a C program.

The preprocessor handled its included header. GCC translated the source into assembly. The assembler produced an object file. The linker connected the program with the library information it needed. The operating system started a process. And the processor executed the machine instructions.

One small program. Several layers working together.

Other programming languages and platforms can take different routes. Some use bytecode and interpreters. Some use just-in-time compilation. Some produce native machine code in different ways.

But the underlying challenge is the same: turning instructions written by people into operations a machine can carry out.

So the next time you press Run and see a number appear, remember what happened behind that simple click.

Your code did not magically become a program.

It passed through a chain of tools, software, and hardware — until the processor could do the work.

**Visual direction:**

Create one continuous, clean pipeline using the same kitchen motif from Scene 2:

SOURCE CODE → PREPROCESSOR → COMPILER → ASSEMBLER → OBJECT FILE → LINKER → OPERATING SYSTEM → PROCESSOR → OUTPUT

Return to the real terminal. Run `./main`. The output `5` appears. Pull back to reveal the complete pipeline behind it. End on ETC identity.

**On-screen text:** FROM HUMAN CODE TO MACHINE EXECUTION

**Sound design:** Bring back the opening music motif, now resolved. End with a short pause and ETC logo.

**Research references:** S1–S8.

---

# 5. FACT-CHECK REPORT

| Claim | Status | Qualification |
|---|---|---|
| GCC's `-E` stops after preprocessing | Verified | GCC documentation |
| GCC's `-S` produces assembly and stops before assembly into an object file | Verified | GCC documentation |
| GCC's `-c` produces object files without linking | Verified | GCC documentation |
| The shown x86-64 assembly contains `addl %edx, %eax` | Verified by actual local build | GCC 14.2.0, Linux x86-64, `-O0`; not universal output |
| `nm -u main.o` shows `printf` as an unresolved external symbol | Verified by actual local build | Exact output depends on object format and toolchain |
| The example executable is dynamically linked | Verified by local `file` output | This specific Linux build |
| The operating system creates a process from an executable | Verified | Details vary by operating system and executable format |
| The processor executes encoded machine instructions | Verified | The ISA and microarchitecture differ by processor |
| Every language follows this exact pipeline | Explicitly rejected | The example is C with GCC on Linux |

---

# 6. EDITORIAL NOTES

- The previous version's two-program structure has been removed. One C program is followed from beginning to end.
- The restaurant-kitchen analogy is introduced once and carried through the explanation. It remains an analogy, not a literal hardware model.
- Spoken jargon has been reduced. Technical labels such as object file, process, registers, and linker are introduced only when needed. Terms such as AST, ELF, ISA, and out-of-order execution are not required in narration.
- The Python detour has been removed. Other language strategies are acknowledged briefly near the end without introducing a second program.
- The C string is corrected to `printf("%d\\n", result);` in the actual source representation: exactly one backslash before n.
- Real terminal captures should replace any recreated terminal visuals. If the creator's machine differs, record its actual compiler output and label the architecture and compiler version.
- The sample assembly was produced with `-O0` for readability. Optimised builds may look substantially different.
- The dynamic-linking explanation is deliberately concise. The linker records dynamic dependencies; the runtime loader participates in loading shared libraries and resolving symbols.

---

# 7. FINAL RUNTIME AND EDITORIAL CHECK

- **Target runtime:** 12–13 minutes.
- **Narration delivery assumption:** approximately 125–135 words per minute.
- **Narration target:** approximately 1,400–1,500 words; recount after the final spoken edit.
- **Visual-only time:** approximately 45–75 seconds for terminal captures, pauses, and transformations.
- **Runtime validation:** record a full read-through and time it. Do not infer exact duration from the outline.
- **Production proof:** record the actual GCC commands, generated assembly, unresolved-symbol output, disassembly, and program result.
- **Editorial status:** REVISED DRAFT — the C string bug is corrected; the single-program narrative, analogy, real terminal proof, and jargon reduction are implemented. Final approval requires a timed read-through and local terminal capture on the creator's target machine.
