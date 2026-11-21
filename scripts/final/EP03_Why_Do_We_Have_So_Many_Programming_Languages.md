# Why Do We Have So Many Programming Languages?

ETC: Exploring Technology & Computing. Documentary script package, written to the script_engine rules (Who_to_write, RESEARCH_PROTOCOL, SCRIPT_FORMAT, QUALITY_CHECKLIST, EDITORIAL_GUARDRAILS, INPUT_TEMPLATE).

**Status:** Ready for table read. **Table read pending — runtime is an estimate.** Demo code was actually run (Appendix A); nothing has been recorded or filmed.

## 1. PROJECT OVERVIEW

- **Working title:** Why Do We Have So Many Programming Languages?

- **Target duration:** 10+ minutes (requested). This cut: about 14 minutes (see section 9). Two optional cuts bring it to about 12 minutes.

- **Estimated narration word count:** 1,646

- **Audience:** Curious general viewers with no IT background.

- **Central question:** If every general-purpose language can compute the same things, why does the world keep producing new ones?

- **One-sentence premise:** Languages differ not in what they can compute but in who pays: the machine, the programmer, or the user who suffers the mistakes.

- **Viewer takeaway:** A language is a decision about trade-offs, and attempts to merge all languages into one only work where one buyer or one domain can set the terms.

- **Narrative approach:** Problem, failed cure, investigation. The video opens on a real event (the US Department of Defense counting 450 languages and commissioning one to replace them), follows the people who tried to unify or to specialise, runs three real demonstrations, and returns to the opening puzzle. One recurring framework, "three bills" (machine, programmer, mistakes), is used consistently.

- **Scope and exclusions:** General-purpose and a few domain languages, 1954 to today. Excludes esoteric languages, language-design theory, type systems, paradigms (object-oriented, functional), AI code generation and a ranking of the "best" language. Interpretation: the title is read as "why does the number keep growing, and why did unification attempts not stop it."

## 2. RESEARCH BRIEF

**Key concepts.** A programming language is a notation that a program (a compiler or interpreter) turns into the processor's instructions. A compiler translates before the program runs; an interpreter carries out instructions as it goes; a just-in-time (JIT) compiler translates busy parts while the program runs. Turing-complete means able to compute everything a Turing machine can, memory limits aside.

**Why the number is puzzling.** Church and Turing (1936) gave different definitions of computation that picked out the same functions. Virtually all programming languages are Turing-complete, so they differ in cost, not capability.

**Mechanism of the argument: three bills.** (1) Machine time. (2) Programmer time to write and read. (3) Cost of mistakes. This is the writer's explanatory framework, not an established theory. Limits: the bills are not a strict trade-off (Fortran lowered programmer effort while keeping code nearly as fast as hand-coded), and real programs mix languages.

**Evidence chain.** Fortran (1954-57) lowered programmer cost without large machine cost. COBOL (1959) lowered the cost of being understood and aimed to be machine-independent. PL/I (1963-65) tried to serve all users and did not displace Fortran or COBOL. C (1969-73) let an operating system be written above assembly; its lack of bounds checking has security costs, and Microsoft reported roughly 70% of its CVE-assigned vulnerabilities were memory-safety issues. Rust (2006 on) moves that checking to compile time. JavaScript (1995) and Python (1989) show circumstance shaping design. SQL (1974) shows a domain-specific language. The DoD's Ada effort (1975-83) is the unification attempt that frames the story.

**Misconceptions to avoid.** "Interpreted languages are always slow" (V8 compiles JavaScript just in time; our run shows JavaScript near C). "JavaScript was written in 10 days" (a prototype was). "Reading past an array always crashes in C" (it is undefined behaviour; our runs printed a different number each time). "Rust makes bugs impossible" (only a class, and not inside unsafe blocks).

**Limitations and uncertainties.** DoD language counts used different methods in 1974/77 and 1994. HOPL's 8,945 counts every era and experiment, not languages in current use. The Ada mandate dates rest on one secondary source. The three-bills thesis and the "merging works where one buyer or domain sets the terms" conclusion are interpretations supported by cases, not tested results.

**Central demonstration.** One job (count primes below 2,000,000, same algorithm) in C, JavaScript and Python with real timings; the same out-of-bounds read in C, Python and JavaScript; and the same data question in SQL and Python. All run for this project (Appendix A).

## 3. SOURCE REGISTER

All sources accessed 21 Nov 2026. "n/d" means no date shown on the page. Snippet-only access is noted.

| ID      | Source title                                                                                              | Author/organisation                                                          | Date                        | URL                                                                                                                                                     | Claims supported              |
|---------|-----------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------|-----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------|
| S01     | Online Historical Encyclopaedia of Programming Languages                                                  | HOPL (hopl.info)                                                             | n/d                         | https://hopl.info/                                                                                                                                      | C01                           |
| S02     | A Survey of Computer Programming Languages Currently Used in the Department of Defense (IDA Paper P-3054) | Hook, Brykczynski, McDonald, Nash, Youngblut; Institute for Defense Analyses | Jan 1995                    | https://apps.dtic.mil/sti/tr/pdf/ADA294001.pdf (abstract: https://apps.dtic.mil/sti/html/tr/ADA294001/index.html)                                       | C02, C33                      |
| S03     | Ada (programming language)                                                                                | Wikipedia                                                                    | archived 2016; current page | https://webarchive.library.unt.edu/web/20160706052325/https://en.wikipedia.org/wiki/Ada\_(programming_language) ; https://www.wikipedia.com/wiki/Ada_83 | C03, C04, C32                 |
| S04     | Ada Programming Language                                                                                  | AcqNotes                                                                     | updated 19 Jul 2017         | https://acqnotes.com/acqnote/careerfields/ada-programming-language                                                                                      | C34 (single secondary source) |
| S05     | The Church-Turing Thesis                                                                                  | Stanford Encyclopedia of Philosophy                                          | rev. 18 Dec 2023            | https://plato.stanford.edu/ENTRIES/church-turing/                                                                                                       | C05                           |
| S06     | Turing completeness                                                                                       | Wikipedia                                                                    | n/d                         | https://en.wikipedia.org/wiki/Turing_completeness                                                                                                       | C06                           |
| S07     | The FORTRAN Automatic Coding System                                                                       | Backus et al., Western Joint Computer Conference                             | 1957                        | https://www.softwarepreservation.org/projects/FORTRAN/paper/BackusEtAl-FortranAutomaticCodingSystem-1957.pdf (partial text only)                        | C07                           |
| S08     | Fortran (IBM history)                                                                                     | IBM                                                                          | n/d                         | https://ibm.com/history/fortran                                                                                                                         | C08, C09, C11, C12            |
| S09     | A Technological Review of the FORTRAN I Compiler                                                          | F. E. Allen                                                                  | 1982                        | https://www.softwarepreservation.org/projects/FORTRAN/paper/Allen-technological_review_FORTRAN-1982.pdf (snippet)                                       | C07, C11                      |
| S10     | John Backus (biographical history)                                                                        | MacTutor, St Andrews                                                         | n/d                         | https://mathshistory.st-andrews.ac.uk/SH/backus_sh.pdf                                                                                                  | C10                           |
| S11     | COBOL                                                                                                     | Wikipedia                                                                    | n/d                         | https://en.wikipedia.org/wiki/COBOL                                                                                                                     | C13, C14                      |
| S12     | CODASYL                                                                                                   | Wikipedia                                                                    | n/d                         | https://en.wikipedia.org/wiki/CODASYL                                                                                                                   | C15                           |
| S13     | Jean Sammet, accidental computer programmer                                                               | IEEE Spectrum                                                                | n/d                         | https://spectrum.ieee.org/jean-sammet-accidental-computer-programmer                                                                                    | C16                           |
| S14     | Biography of Grace Murray Hopper                                                                          | Yale University                                                              | n/d                         | https://president.yale.edu/biography-grace-murray-hopper                                                                                                | C15                           |
| S15     | PL/I                                                                                                      | Wikipedia                                                                    | n/d                         | https://en.wikipedia.org/wiki/PL/I                                                                                                                      | C18                           |
| S16     | Lessons from PL/I: A Most Ambitious Programming Language                                                  | BLOG@CACM                                                                    | n/d                         | https://cacm.acm.org/blogs/blog-cacm/274388-lessons-from-pl-i-a-most-ambitious-programming-language/fulltext                                            | C17, C19                      |
| S17     | The Development of the C Language                                                                         | Dennis M. Ritchie                                                            | 1993                        | https://www.nokia.com/bell-labs/about/dennis-m-ritchie/chist.html (abstract and opening lines read)                                                     | C20                           |
| S18     | Dennis M. Ritchie                                                                                         | Britannica                                                                   | n/d                         | https://www.britannica.com/biography/Dennis-M-Ritchie ; https://www.britannica.com/print/article/1532873                                                | C20                           |
| S19     | Dennis Ritchie                                                                                            | Lemelson-MIT                                                                 | n/d                         | https://lemelson.mit.edu/resources/dennis-ritchie                                                                                                       | C20, C21                      |
| S20     | NAE Memorial Tribute: Dennis M. Ritchie                                                                   | B. W. Kernighan                                                              | 2016                        | https://www.nationalacademies.org/read/23394/chapter/40                                                                                                 | C20                           |
| S21     | A proactive approach to more secure code                                                                  | Microsoft Security Response Center                                           | Jul 2019                    | https://www.microsoft.com/en-us/msrc/blog/2019/07/a-proactive-approach-to-more-secure-code                                                              | C23                           |
| S22     | Why Rust for safe systems programming                                                                     | Microsoft Security Response Center                                           | Jul 2019                    | https://www.microsoft.com/msrc/blog/2019/07/why-rust-for-safe-systems-programming                                                                       | C23, C24, C26                 |
| S23     | Rust (programming language)                                                                               | Wikipedia                                                                    | n/d                         | https://en.wikipedia.org/wiki/Rust\_(programming_language)                                                                                              | C25                           |
| S24     | rust-prehistory                                                                                           | Graydon Hoare                                                                | Nov 2016                    | https://github.com/graydon/rust-prehistory                                                                                                              | C25                           |
| S25     | How JavaScript Was Created (Speaking JavaScript, ch. 4)                                                   | Axel Rauschmayer, O'Reilly                                                   | 2014                        | https://www.oreilly.com/library/view/speaking-javascript/9781449365028/ch04.html                                                                        | C27, C28                      |
| S26     | New JavaScript Engine Module Owner                                                                        | Brendan Eich                                                                 | 2011                        | https://brendaneich.com/2011/06 (snippet)                                                                                                               | C28                           |
| S27     | Foreword for "Programming Python"                                                                         | Guido van Rossum, python.org                                                 | May 1996                    | https://python.org/doc/essays/foreword                                                                                                                  | C29                           |
| S28     | General Python FAQ                                                                                        | Python Software Foundation                                                   | n/d                         | https://docs.python.org/3.3/faq/general.html                                                                                                            | C29                           |
| S29     | PEP 744: JIT Compilation                                                                                  | Brandt Bucher, python.org                                                    | 2024                        | https://peps.python.org/pep-0744/                                                                                                                       | C36                           |
| S30     | Firing up the Ignition interpreter                                                                        | V8 project                                                                   | n/d                         | https://v8.dev/blog/ignition-interpreter                                                                                                                | C35                           |
| S31     | 50 Years of Queries                                                                                       | Donald Chamberlin, CACM                                                      | n/d                         | https://cacm.acm.org/research/50-years-of-queries                                                                                                       | C30                           |
| S32     | The relational database                                                                                   | IBM                                                                          | n/d                         | https://www.ibm.com/fr-fr/history/relational-database                                                                                                   | C31                           |
| S33     | The COBOL Programming Language at 60                                                                      | The Register                                                                 | 16 Sep 2019                 | https://www.theregister.com/2019/09/16/cobol_at_60/                                                                                                     | C17                           |
| D01-D04 | Demo runs (Appendix A)                                                                                    | This project                                                                 | 21 Nov 2026                 | n/a                                                                                                                                                     | C22, C36-C38                  |

**Claim ledger.** Confidence: H high, M medium.

| ID  | Claim (precise wording)                                                                                                                                               | Sources  | Conf. | Qualification                                                                    |
|-----|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|-------|----------------------------------------------------------------------------------|
| C01 | HOPL lists 8,945 programming languages                                                                                                                                | S01      | H     | Counts every era and experiment, not languages in use                            |
| C02 | A 1977 study identified 450 as the minimum probable number of general-purpose languages and dialects used in the DoD                                                  | S02      | H     | The report's abstract dates the estimate to 1974; narration says "mid-seventies" |
| C03 | The DoD reviewed existing languages, concluded in 1977 none met the requirements, and commissioned Ada to supersede 450+                                              | S03      | M     | Wikipedia; consistent with S02                                                   |
| C04 | Many of those languages were obsolete or hardware-dependent                                                                                                           | S03      | M     | Stated for embedded-system projects                                              |
| C05 | Church and Turing (1936) gave very different definitions of computation that pick out the same functions                                                              | S05      | H     |                                                                                  |
| C06 | Virtually all programming languages are Turing-complete if finite memory is ignored                                                                                   | S06      | M     |                                                                                  |
| C07 | Backus's IBM team began FORTRAN in 1954 to make scientific problems far easier to prepare for the 704, with efficient output                                          | S07, S09 | H     |                                                                                  |
| C08 | Backus described machine-language programming as hand-to-hand combat with the machine                                                                                 | S08      | M     | Reported by IBM; original not checked                                            |
| C09 | A project planned for six months took three years                                                                                                                     | S08      | M     |                                                                                  |
| C10 | The first FORTRAN compiler was delivered in April 1957                                                                                                                | S10, S08 | H     |                                                                                  |
| C11 | Its output ran nearly as fast as hand-crafted code                                                                                                                    | S08, S09 | H     |                                                                                  |
| C12 | Skeptics doubted compiled code could match hand-written code                                                                                                          | S08      | M     |                                                                                  |
| C13 | A Pentagon meeting on 28-29 May 1959 began the common business language effort; the DoD sponsored it                                                                  | S11      | H     |                                                                                  |
| C14 | Business languages were proliferating and a survey suggested a common one would make conversion far cheaper                                                           | S11      | M     |                                                                                  |
| C15 | COBOL drew heavily on FLOW-MATIC, which used English words for commands                                                                                               | S12, S14 | H     |                                                                                  |
| C16 | The 1959 aim was a problem-oriented, machine-independent business language                                                                                            | S13      | M     | Paraphrased, no quote used                                                       |
| C17 | COBOL was the most widely used language by about 1970                                                                                                                 | S16, S33 | M     |                                                                                  |
| C18 | IBM wanted one language for all users; committee formed Oct 1963; first definition Apr 1964; renamed PL/I in 1965                                                     | S15      | M     |                                                                                  |
| C19 | PL/I aimed to combine Fortran, ALGOL and COBOL strengths, did not replace them, and was reportedly used for Multics and Sabre                                         | S16      | M     | "Reportedly" is in the narration                                                 |
| C20 | Unix started in assembly; B suited the PDP-11 poorly; Ritchie developed C in 1972; Unix was rewritten in C by 1973                                                    | S17-S20  | H     |                                                                                  |
| C21 | Writing Unix in C became the basis for its portability over later years                                                                                               | S19      | M     | Early Unix still had machine-specific code                                       |
| C22 | Reading element 8 of a 5-element C array compiled with no error and printed a different value on each run; Python raised IndexError; JavaScript gave undefined        | D02      | H     | Undefined behaviour in C; values not guaranteed                                  |
| C23 | About 70% of vulnerabilities Microsoft assigned a CVE each year were memory-safety issues                                                                             | S21, S22 | H     | Microsoft data, 2006-2018                                                        |
| C24 | MSRC wrote that had that software been written in Rust, 70% of these issues would most likely have been eliminated                                                    | S22      | H     | Their claim, about a category                                                    |
| C25 | Hoare began Rust in 2006 as a personal project; Mozilla sponsored it from 2009                                                                                        | S23, S24 | H     |                                                                                  |
| C26 | Rust is memory safe except where code is explicitly marked unsafe                                                                                                     | S22      | H     |                                                                                  |
| C27 | Netscape hired Eich with a Scheme promise; after the Sun/Java deal management required Java-like syntax, ruling out Perl, Python, Tcl and Scheme                      | S25      | M     |                                                                                  |
| C28 | Eich wrote a prototype in ten days in May 1995                                                                                                                        | S25, S26 | H     | Prototype, not finished language                                                 |
| C29 | Van Rossum started Python as a hobby project in Christmas week 1989; ABC's lack of extensibility was one of its biggest problems; he wanted Amoeba system-call access | S27, S28 | H     |                                                                                  |
| C30 | Codd proposed the relational model in 1970; Chamberlin and Boyce published SEQUEL in 1974                                                                             | S31      | H     |                                                                                  |
| C31 | Database systems translate high-level queries into efficient execution plans automatically                                                                            | S32      | M     |                                                                                  |
| C32 | Ada (Green proposal, Ichbiah, CII Honeywell Bull) was chosen May 1979, named after Ada Lovelace, standardised 1983                                                    | S03      | M     |                                                                                  |
| C33 | A 1994 survey found 37 third-generation languages; Ada was the most common in weapons-system modernisation; experts count languages differently                       | S02      | H     | Different counting method from 1970s estimate                                    |
| C34 | A 1987 DoD rule required Ada where over 30% of a project was new code, often waived; effectively removed 1997                                                         | S04      | M     | One secondary source; re-check                                                   |
| C35 | V8 compiles JavaScript to native code just in time                                                                                                                    | S30      | H     |                                                                                  |
| C36 | CPython executes bytecode in an interpreter; a JIT is experimental and off by default (3.13 on); the demo used 3.12.3                                                 | S29, D01 | H     |                                                                                  |
| C37 | Prime-count timings: C 0.186 s, Node 0.207 s, Python 4.525 s (medians of 3)                                                                                           | D01      | H     | One task, one machine                                                            |
| C38 | SQL and Python loop return identical top-three totals                                                                                                                 | D03      | H     | After fixing a tie in first-run data                                             |

## 4. NARRATIVE OUTLINE

| Time  | Chapter                         | Narrative purpose                                           | Question answered                      | Transition                                                                   |
|-------|---------------------------------|-------------------------------------------------------------|----------------------------------------|------------------------------------------------------------------------------|
| 00:00 | 1\. The count                   | Real event and puzzle: 450 languages, one cure, 8,945 today | What is the problem?                   | The number should not be possible if languages are equally powerful          |
| 00:50 | 2\. Same power, different bills | Church-Turing; introduce three bills                        | Why would languages differ at all?     | Test the first bill on one job                                               |
| 01:52 | 3\. The machine's bill (demo)   | Real timings in C, Node, Python                             | What does speed depend on?             | Python pays and "buys something"; where did the programmer's bill come from? |
| 03:23 | 4\. Fortran                     | Programmer's bill; bills are not a strict trade-off         | How did languages get easier to write? | Fortran was for formulas, not payroll                                        |
| 04:29 | 5\. COBOL                       | Readability; first unification attempt; DoD as sponsor      | Who else needed a language?            | Why not merge everything?                                                    |
| 05:25 | 6\. PL/I                        | Unification across domains fails                            | Can one language serve all?            | A different pressure, from systems                                           |
| 06:14 | 7\. C and Unix                  | Control close to hardware                                   | Why trade supervision for control?     | Show what lost supervision looks like                                        |
| 07:05 | 8\. The mistakes bill (demo)    | Real out-of-bounds runs; Microsoft's 70%                    | What does a mistake cost?              | Someone moved the check to compile time                                      |
| 08:24 | 9\. Rust                        | Mistakes bill moves to the programmer                       | Can the bill be moved?                 | Some languages exist for circumstance                                        |
| 09:26 | 10\. JavaScript and Python      | Deadline and holiday origins                                | Do accidents shape languages?          | Some are built for one question                                              |
| 10:30 | 11\. SQL (demo)                 | Domain-specific language                                    | Why give up generality?                | Return to the Pentagon                                                       |
| 11:28 | 12\. Ada                        | Resolve the opening: what happened to the cure              | Did the cure work?                     | Pull the pattern together                                                    |
| 12:32 | 13\. The answer                 | Answer the central question; unifier scoreboard             | Why so many languages?                 | End                                                                          |

## 5. COMPLETE SCRIPT AND VISUAL TIMELINE

**Recurring device (conceptual visualisation):** a small "ledger" strip in the lower corner with three icons, Machine, Programmer, Mistakes. It appears in scene 2 and the icon for the scene's topic lights up with a soft tick. It is a visual aid for the framework, not a literal measurement.

**Demo note for the editor:** every number, output and code sample shown on screen must come from a fresh recording on the production machine, using the files in Appendix A. The figures in the narration (0.19 s, 4.5 s, about 24 times) come from the run documented in Appendix A and must be updated to match the recording. The C numbers in scene 8 differ on every run; use whatever the recording shows.

## SCENE 01 — The count

**Timestamp:** 00:00–00:50

**Narration:**

In the 1970s, the United States Department of Defense counted its programming languages. Only the ones inside its own projects. A 1977 study put the minimum at four hundred and fifty: languages and dialects, many of them obsolete or tied to one particular machine. The department reviewed the options, concluded that none fit, and commissioned a brand-new language to replace the lot. Today, counting every era and every experiment, one online encyclopedia lists eight thousand, nine hundred and forty-five. How does one organization end up with four hundred and fifty languages? And what happened to the cure?

**Visual direction:**

Black screen, silence, then the cover page of IDA Paper P-3054 (real document, DTIC) fades up with the "450" sentence highlighted. Cut to a conceptual grid of small tiles filling the frame as the narrator says "four hundred and fifty" (labelled conceptual: one tile is one language or dialect). The grid collapses into a single tile labelled "Ada". Then a real screen capture of hopl.info with its count; the number is enlarged and the tile grid explodes outward to fill the frame again.

**On-screen text:** "US Department of Defense, 1977 study: at least 450" and "HOPL, hopl.info: 8,945 (all eras, in use or not)".

**Sound design:** Low ambient tone. A single soft tick when the tiles collapse. Silence for one beat before the last question.

**Research references:** C01, C02, C03, C04

## SCENE 02 — Same power, different bills

**Timestamp:** 00:50–01:52

**Narration:**

Here is what makes those numbers odd. In 1936, Alonzo Church and Alan Turing, working separately, each pinned down what it means to calculate something. Their definitions looked nothing alike, yet they described exactly the same set of calculations. Almost every general-purpose language since is built to reach that full set. Whatever Python can calculate, C can calculate, given enough memory and time. So languages don't differ in what they can do. They differ in who pays. Read the history through three bills. The machine's bill: seconds of processor time. The programmer's bill: hours to write the thing and read it again. And the mistakes bill: what happens, and to whom, when the code is wrong. Let's run one job through three languages and watch the first bill arrive.

**Visual direction:**

Conceptual diagram: on the left a lambda-calculus expression, on the right a tape-and-head machine; arrows from both land in one circle labelled "the same calculations". Language names (text only) sit inside the circle. Then the three ledger icons appear one by one as each bill is named, each with a one-line label. The Machine icon stays lit at the end.

**On-screen text:** "1936", "Church / Turing", "Machine: seconds", "Programmer: hours", "Mistakes: harm". Small note: "Equivalent in principle, memory limits aside."

**Sound design:** Light ticks as each icon appears. Music bed starts here, restrained.

**Research references:** C05, C06

## SCENE 03 — The machine's bill

**Timestamp:** 01:52–03:23

**Narration:**

The job: count every prime number below two million. Same method everywhere: try dividing each number by smaller odd numbers. First, C, compiled with gcc, which translates the code into the processor's own instructions before the program runs. A little under a fifth of a second. JavaScript, in Node: about the same. Python: four and a half seconds. Roughly twenty-four times longer, for the identical answer, one hundred and forty-eight thousand, nine hundred and thirty-three primes. Why does JavaScript, a language people call slow, keep pace with C? Speed belongs to the implementation as much as the language. Node's engine translates the busy parts of a program into machine instructions as it runs. The standard Python, version 3.12, uses an interpreter, a program that carries out your instructions one at a time. That's the machine's bill, and Python pays it in full. Hold on to that. Python is buying something with it.

**Visual direction:**

Real screen recording, three terminals side by side, each showing the actual source file from Appendix A (about 15 lines each, algorithm visibly identical). Run each in turn with a running timer overlay. Each prints 148933. Then a simple bar chart of the three medians. Then a conceptual animation (labelled) of three pipelines: ahead-of-time compile (C), compile while running (V8), step-by-step interpreter (CPython 3.12).

**On-screen text:** Result "148933". Chart labels with measured medians. Environment note: "Ubuntu 24.04, x86-64, 1 vCPU sandbox; gcc 13.3.0 -O2; Node v22.23.5; CPython 3.12.3; median of 3 runs, whole-process time. One task, not a ranking."

**Sound design:** Keyboard and terminal ticks. Quiet during Python's four-second run so the wait is felt (the 20-second visual-only beat).

**Research references:** C35, C36, C37

## SCENE 04 — Fortran: lowering the programmer's bill

**Timestamp:** 03:23–04:29

**Narration:**

The programmer's bill has an origin: 1954, at IBM. Programs for the IBM 704 were written in the machine's own numeric codes, work John Backus described as hand-to-hand combat with the computer. His team wanted scientists to write something close to ordinary formulas and let a program, a compiler, produce the machine instructions. Skeptics doubted translated code could ever keep up with code written by hand. A project meant to take six months took three years. When the compiler shipped in April 1957, IBM reports, its output ran nearly as fast as the hand-crafted kind. Fortran cut the programmer's bill sharply without wrecking the machine's. So the bills aren't a fixed trade: a better tool can lower two at once. But Fortran was built for formulas. Payroll and inventories were a different world.

**Visual direction:**

Archival material: cover of the IBM Fortran programmer's primer and the first page of the 1957 Backus et al. paper (check usage rights for any IBM or archive images). Then a conceptual animation (labelled): a mathematical formula enters a box marked "compiler" and a block of machine instructions comes out. Finally the Programmer icon dims (cost down) while the Machine icon stays nearly level, then both dim: the visual proof that the bills are not a strict trade.

**On-screen text:** "IBM 704", "1954: project begins", "April 1957: compiler delivered".

**Sound design:** Music steady; soft tick on the Programmer icon.

**Research references:** C07, C08, C09, C10, C11, C12

## SCENE 05 — COBOL: the cost of being understood

**Timestamp:** 04:29–05:25

**Narration:**

In 1959, a meeting at the Pentagon took on that world. Languages for business were multiplying, and a survey suggested a common one would make switching machines far cheaper. The committee, CODASYL, set out to specify one that was independent of any manufacturer's computer, and it leaned heavily on Grace Hopper's FLOW-MATIC, whose instructions used ordinary English words. The result, COBOL, read almost like a memo. Notice which bill it lowered: not machine time, not mistakes, but the effort of being understood, by managers, by auditors, by the next person to open the file. And notice the sponsor: the same Department of Defense that, fifteen years later, would be counting four hundred and fifty.

**Visual direction:**

Archival: public-domain photograph of Grace Hopper (verify source and licence) and the title page of the December 1959 COBOL specification. A dated timeline strip (conceptual) joins 1959 to the 1970s DoD count from scene 1, with the two DoD labels linked by a thin line to underline the irony. No code on screen (not run here).

**On-screen text:** "28–29 May 1959, Pentagon" and "CODASYL".

**Sound design:** Steady bed; a single tick on the Programmer icon.

**Research references:** C13, C14, C15, C16, C02

## SCENE 06 — PL/I: one language for everyone

**Timestamp:** 05:25–06:14

**Narration:**

In 1963, IBM had its own tidy idea. It was preparing System/360, one family of machines to replace several incompatible ones. So why not one language for all its users? A committee started by trying to extend Fortran, and the design grew to absorb COBOL's strengths and ALGOL's. The first definition appeared in April 1964; the name PL/I came a year later. But Fortran and COBOL were still evolving, with vast stocks of working programs and loyal users. PL/I found its niche. It never replaced what it was built to merge. It became one more language.

**Visual direction:**

Conceptual diagram (labelled): three overlapping circles, Fortran, COBOL, ALGOL, merge into a fourth circle PL/I. The three originals then reappear beside it, still present, so the viewer sees the count go from three to four.

**On-screen text:** "System/360", "PL/I: first definition April 1964".

**Sound design:** Music steady; the "tick" returns when the fourth circle remains.

**Research references:** C18, C19

## SCENE 07 — C and Unix: control close to the machine

**Timestamp:** 06:14–07:05

**Narration:**

At Bell Labs in New Jersey, the pressure came from another direction. Ken Thompson and Dennis Ritchie were building an operating system, Unix. An operating system is the program that runs all the others, so it has to work close to the hardware, and that meant assembly language: one machine's native tongue. B, Thompson's earlier language, made poor use of the new machine's features, so in 1972 Ritchie extended it into C. By 1973, Unix had been rewritten in it. Over the following years that choice paid off as portability: a system written in C could follow its compiler onto other machines.

**Visual direction:**

Terminal recording of the real assembly from Appendix A, item D04: the three-line C function beside the x86-64 instructions gcc produced. Caption it as one machine's native tongue; a different processor would give different instructions. Then archival photograph of Thompson and Ritchie at a PDP-11 (verify licence). End on a two-box diagram (conceptual): one C source file flowing into compilers for two different machines.

**On-screen text:** "Bell Labs, 1969–1973", "x86-64 output from gcc 13.3.0, -O1 (real run)".

**Sound design:** Terminal ticks; music slightly warmer.

**Research references:** C20, C21, D04

## SCENE 08 — The mistakes bill

**Timestamp:** 07:05–08:24

**Narration:**

C offered nearly total control and almost no supervision. Here is a list of five numbers, and a program that asks for the eighth. In C, it compiles without complaint and prints a number. Run it again. A different number. Again. Different once more. The program is reading memory that isn't part of the list, and C's rules promise nothing about what happens next. C has tools that catch this, but you have to switch them on. Python refuses: an index error, with the line number. JavaScript hands back the word undefined and carries on. Three languages, three answers to one mistake. When Microsoft's security engineers examined the flaws they fixed, about seventy percent of those given an official public ID each year were memory safety problems of this kind. The mistakes bill isn't hypothetical. Users pay it.

**Visual direction:**

Real terminal recording from Appendix A (oob.c, oob.py, oob.js). Show the five-element array literally as five boxes with the eighth requested. Run the C program three times: three different numbers. Then the Python traceback, then Node's "undefined". Then the same C file built with AddressSanitizer showing its real error report. Finish on the Microsoft MSRC chart or a clean redraw credited to MSRC data (check reuse rights).

**On-screen text:** "C: undefined behaviour — output not guaranteed", "~70% of Microsoft CVEs: memory safety (MSRC, 2006–2018)". Footnote: "Values shown are from one recorded run."

**Sound design:** Silence under the three C runs, letting the changing numbers speak. Low tone on the last line; the Mistakes icon lights.

**Research references:** C22, C23

## SCENE 09 — Rust: moving the mistakes bill

**Timestamp:** 08:24–09:26

**Narration:**

Graydon Hoare began Rust in 2006 as a personal project while working at Mozilla, which sponsored it from 2009. Its bet is that the compiler can take over the mistakes bill. Before the program ever runs, Rust's compiler checks how every piece of memory is used and, outside blocks the programmer marks as unsafe, refuses to build code that breaks the rules. Microsoft's own security engineers argued in 2019 that had the affected code been written in Rust, about seventy percent of those security issues would most likely have been eliminated. That's a claim about a category of bugs, not a guarantee for any one program. And the bill didn't vanish. It moved, from users to the programmer, who must satisfy the compiler before anything runs.

**Visual direction:**

Screen capture of the relevant MSRC post heading and the sentence being referenced (real document, short excerpt only). Then a conceptual slider animation (labelled): the Mistakes icon's cost moves from the "user" side to the "programmer's desk" side while the Programmer icon brightens slightly. No compiler output is shown because Rust was not available in the test environment; if the production team wants a real Rust compiler error, record it on their own machine and state the rustc version on screen.

**On-screen text:** "Rust: personal project 2006; Mozilla 2009" and "Outside unsafe blocks".

**Sound design:** Tick on the Mistakes icon as it slides; music resolves slightly.

**Research references:** C24, C25, C26

## SCENE 10 — A deadline and a holiday

**Timestamp:** 09:26–10:30

**Narration:**

Some languages are shaped by circumstance. In 1995, Netscape hired Brendan Eich with the promise of putting Scheme, an elegant academic language, into its browser. Then came a deal with Sun Microsystems to bring Java to the browser, and management decided the new scripting language had to look like Java. That ruled out Perl, Python, Tcl and Scheme itself. Eich wrote a working prototype in ten days in May 1995. Python had the opposite origin: a hobby project for the Christmas week of 1989. Guido van Rossum had helped create a teaching language, ABC, whose lack of extensibility, he said, was one of its biggest problems. He wanted a scripting language that could reach into the Amoeba operating system. One language came from a deadline. The other came from a holiday.

**Visual direction:**

Split screen, two panels. Left: a calendar strip for May 1995 with ten days highlighted (conceptual, labelled as Eich's recollection of the dates not being precisely confirmed), then archival Netscape Navigator imagery (verify licence). Right: a December 1989 calendar with the Christmas week highlighted and a simple "ABC → Python" lineage arrow with the word "Amoeba" as the target. Panel captions: "Deadline" and "Holiday".

**On-screen text:** "May 1995: prototype", "Dec 1989: hobby project".

**Sound design:** Two slightly different music colours, one tighter and one looser, crossfaded.

**Research references:** C27, C28, C29

## SCENE 11 — SQL: giving up generality

**Timestamp:** 10:30–11:28

**Narration:**

Not every language wants to be general. In 1970, Edgar Codd proposed keeping data in plain tables. In 1974, Donald Chamberlin and Raymond Boyce at IBM published SEQUEL, a language for asking questions of such tables in near-English. Here is one: the three regions with the highest total sales. In SQL, that is a single statement. You never write a loop or keep a running total. You describe the result, and the database system works out how to produce it. The Python version, spelling out each step, reaches the same answer. A language built around tables was never meant to write an operating system.

**Visual direction:**

Real screen recording of sql_demo.py from Appendix A. Show the ten-row table first, then the SQL statement typed, then its three-row result. Then scroll the Python loop version, then both results side by side with a check mark. Highlight that the SQL has no loop or dictionary; do not claim it is shorter (both are about five lines).

**On-screen text:** The query and both results as in Appendix A. Note: "SQLite 3.45.1, Python 3.12.3."

**Sound design:** Typing sounds; a soft tick as the two results match.

**Research references:** C30, C31, C38

## SCENE 12 — Ada: what happened to the cure

**Timestamp:** 11:28–12:32

**Narration:**

Back to the Department of Defense. In May 1979, after a design competition, a proposal from a team led by Jean Ichbiah at CII Honeywell Bull won, and the language was named Ada, after Ada Lovelace. It was standardized in 1983. A 1994 survey of the department's major systems found thirty-seven high-level languages in use, against that mid-seventies estimate of at least four hundred and fifty, and Ada was the most common language among the weapons systems it sampled. The two counts weren't measured the same way, but the drop was steep. It happened inside one organization, with one buyer, one set of requirements, and the authority to insist. And even there, the rule requiring Ada for new projects loosened, and by 1997 it was effectively gone.

**Visual direction:**

Return to the IDA report from scene 1; this time highlight the abstract's "37" and "450" together. Conceptual two-bar chart (labelled, with a footnote that the counts used different methods). Then a short timeline (conceptual): 1975 working group, 1979 selection, 1983 standard, 1987 rule, 1997 rule effectively removed.

**On-screen text:** "Mid-1970s: at least 450", "1994 survey: 37", footnote "Different counting methods; compare with care."

**Sound design:** Music thins out for the last two sentences.

**Research references:** C32, C33, C34

## 6. ENDING

## SCENE 13 — The answer

**Timestamp:** 12:32–14:09

**Narration:**

So why so many languages? Because every language is a decision about who pays. Fortran spent years of engineering to lower the programmer's bill. Python spends processor time to buy readability and safety. C gave up supervision to get close to the machine, and Rust took supervision back, at the programmer's desk. SQL gave up generality to answer one kind of question well. And the world keeps changing the prices: new hardware, new places for code to run, new kinds of mistakes worth making impossible. That is how one department ends up with four hundred and fifty languages: hundreds of projects, each paying its bills differently. Look at the people who tried to merge everything. COBOL won its field. PL/I aimed at everything and never displaced what it set out to absorb. Inside the Pentagon the list shrank; outside it, new languages kept arriving. Merging works where one buyer or one domain can set the terms. Nobody has ever set the terms for everything. Every language in this story began as someone's answer to a bill that was too high. There is no reason to expect the next one to be different.

**Visual direction:**

Return to the tile grid from scene 1. As each language is named, its tile lights and slides into a cluster under the bill it chose to lower (conceptual, labelled). Then a three-row scoreboard (conceptual): COBOL, one domain, became dominant; PL/I, all domains, did not displace others; Ada, one buyer, the count fell. Final shot: the full tile grid with the counter at 8,945 and one new empty tile appearing at the edge, held for two seconds, then cut to black.

**On-screen text:** The scoreboard rows and "Interpretation, not a tested result" as a small footnote.

**Sound design:** Music resolves; one last tick as the empty tile appears; two seconds of silence at the end.

**Research references:** C01, C02, C17, C19, C33, plus the framework notes in section 8.

**How the ending answers the central question.** The opening asked how one organization ends up with 450 languages and what happened to the cure. The ending answers the first directly (hundreds of projects, each paying the three bills differently) and the second with the scoreboard (the cure worked where one buyer or domain could set the terms, and not where it could not). It returns to the opening image of the tile grid and the 8,945 count.

## 7. FACT-CHECK REPORT

I checked the final narration wording against the sources in section 3 and the demo runs in Appendix A. This is my own check, not an independent review.

| Claim ID                                                                 | Scene    | Status                      | Notes or correction                                                                                                                                                                |
|--------------------------------------------------------------------------|----------|-----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| C01                                                                      | 1, 13    | Verified with qualification | Counts every era and experiment; narration says so                                                                                                                                 |
| C02                                                                      | 1, 5, 12 | Verified with qualification | Body of the report says 1977 study; abstract says 1974 estimate. Narration uses "1977 study" in scene 1 and "mid-seventies" elsewhere                                              |
| C03, C04                                                                 | 1        | Verified with qualification | Wikipedia only for the review and "none fit" point                                                                                                                                 |
| C05, C06                                                                 | 2        | Verified with qualification | "Given enough memory and time" added for the finite-memory caveat                                                                                                                  |
| C07-C12                                                                  | 4        | Verified with qualification | C08, C09, C12 rest on IBM's own history page; original Backus statement not checked                                                                                                |
| C10                                                                      | 4        | Verified                    | April 1957 delivery                                                                                                                                                                |
| C13-C16                                                                  | 5        | Verified with qualification | Paraphrase used; no quotation marks                                                                                                                                                |
| C17                                                                      | 13       | Verified with qualification | Two secondary sources                                                                                                                                                              |
| C18                                                                      | 6        | Corrected                   | An earlier draft said "under the name PL/I" in April 1964; the name came in 1965. Fixed                                                                                            |
| C19                                                                      | 6        | Verified with qualification | Multis and Sabre use dropped from narration; "vast stocks of working programs and loyal users" is a paraphrase of the CACM blog's argument                                         |
| C20                                                                      | 7        | Verified                    |                                                                                                                                                                                    |
| C20 (Kernighan)                                                          | 7        | Removed                     | An earlier draft said nobody had written an operating system in a high-level language before. Multics (PL/I) and the Burroughs B5000 (ALGOL) counter that, so the line was removed |
| C21                                                                      | 7        | Verified with qualification | "Over the following years"                                                                                                                                                         |
| C22                                                                      | 8        | Verified                    | Own runs, three C runs printed different values                                                                                                                                    |
| C23                                                                      | 8        | Verified                    |                                                                                                                                                                                    |
| C24, C26                                                                 | 9        | Verified with qualification | Their claim, a category, "outside unsafe"                                                                                                                                          |
| C25                                                                      | 9        | Verified                    |                                                                                                                                                                                    |
| C27, C28                                                                 | 10       | Verified with qualification | Prototype only; the exact dates come from Eich's recollection                                                                                                                      |
| C29                                                                      | 10       | Corrected                   | An earlier draft said ABC's "biggest flaw"; the source says "one of its biggest problems". Fixed                                                                                   |
| C30, C31                                                                 | 11       | Verified                    |                                                                                                                                                                                    |
| C32                                                                      | 12       | Verified with qualification | "CII Honeywell Bull", not "Honeywell"                                                                                                                                              |
| C33                                                                      | 12       | Verified with qualification | Different counting methods are stated in the narration                                                                                                                             |
| C34                                                                      | 12       | Needs further verification  | Single secondary source; "loosened" and "effectively gone" should be confirmed                                                                                                     |
| C35-C37                                                                  | 3        | Verified                    | Own run; timings are environment-specific                                                                                                                                          |
| C38                                                                      | 11       | Verified                    | First run exposed a tie (West and South both 210) that made SQL and Python disagree; data changed so totals are distinct                                                           |
| Thesis (three bills; merging works where one buyer or domain sets terms) | 2, 13    | Verified with qualification | Writer's interpretation, supported by the cases; framed as a reading, not a result                                                                                                 |

## 8. EDITORIAL NOTES

**Important simplifications.** Codd's "relations" are described as plain tables. "Compiler", "interpreter" and just-in-time translation are explained in one sentence each. Rust's checking is described only for memory use and excludes unsafe blocks. The Church-Turing result is described as "the same set of calculations".

**Disputed or uncertain points.** (1) The DoD figure is a minimum estimate, dated 1974 in the report's abstract and 1977 in its body. (2) The 1970s and 1994 DoD counts used different methods. (3) HOPL's 8,945 includes every era and experiment. (4) Ada's role in the later drop is plausible (it was the most common language in the weapons-system sample) but causation is not shown, so the narration only says the drop happened inside one organization. (5) The Ada rule dates come from one secondary source. (6) Eich's ten days were a prototype, and exact dates are his recollection.

**Writer's interpretation.** The three-bills framework, and the conclusion that unification works only where one buyer or one domain can set the terms, are my reading of the cases. They are not an established result. If a reviewer wants it softened, change "Read the history through three bills" in scene 2 and the last third of scene 13.

**Analogy limits (stated in the script).** The bills are not a strict trade-off (scene 4), and moving a bill does not remove it (scene 9). Not stated in the script: real programs often mix languages, so "who pays" is usually per component, not per project.

**Removed or changed during fact-checking.** The "first whole operating system in a high-level language" claim (Multics in PL/I and the Burroughs B5000 in ALGOL are counterexamples). The April 1964 PL/I naming. "Biggest flaw" about ABC. A language-popularity statistic for JavaScript (secondary source, not needed). The SQL demo's first run disagreed with Python because two regions tied; data was changed and the tie is disclosed here.

**Scope limitations.** No esoteric languages, no object-oriented or functional paradigms, no AI-assisted coding, no coverage outside the US and IBM-centred histories (for example ALGOL's European origins, or Lisp).

**Visuals requiring technical review.** Scene 3 pipeline animation (ahead-of-time vs just-in-time vs interpreter). Scene 7 assembly caption (x86-64 output differs from PDP-11 and from ARM). Scene 9 "unsafe" caption.

**Check again before publication.** C34 (Ada rule dates). C08 and C09 (IBM's account of Backus's phrase and the six-month plan). The licence for every archival image (IBM primer cover, Hopper photo, Thompson and Ritchie photo, Netscape screenshots, MSRC chart). Eich's own 2008 "Popularity" post was only seen in search snippets and should be read in full.

**Not done here.** No recorded narration, no timed table read, no footage. No Rust code was run (Rust is not installed in the test environment), so scene 9 deliberately shows no compiler output.

## 9. FINAL RUNTIME CHECK

- **Total estimated narration words:** 1,646

- **Assumed narration speed:** 130 words per minute (the engine's planning default); range 125–140.

- **Estimated spoken duration:** about 12 minutes 40 seconds at 130 wpm.

- **Estimated visual-only pauses and transitions:** about 89 seconds (demo runs, reveals, silences), concentrated in scenes 3, 8 and 11.

- **Estimated final runtime:** about 14:09; range roughly 13:15 (140 wpm) to 14:40 (125 wpm).

- **Is the requested duration realistic?** The request was 10+ minutes, so yes, with room to spare. If a tighter cut is wanted, scene 6 (about 0:49) and scene 11 (about 0:58) can be removed without breaking the argument, giving roughly 12:20. Nothing was padded to reach the length.

**Table read pending — runtime is an estimate.** Per-scene timestamps in section 5 must be re-timed after a real read-aloud and the demo recordings.

| Scene | Words | Est. narration | Visual-only | Start–end   |
|-------|-------|----------------|-------------|-------------|
| 01    | 97    | 0:45           | 0:05        | 00:00–00:50 |
| 02    | 129   | 1:00           | 0:03        | 00:50–01:52 |
| 03    | 153   | 1:11           | 0:20        | 01:52–03:23 |
| 04    | 133   | 1:01           | 0:05        | 03:23–04:29 |
| 05    | 114   | 0:53           | 0:03        | 04:29–05:25 |
| 06    | 99    | 0:46           | 0:03        | 05:25–06:14 |
| 07    | 102   | 0:47           | 0:04        | 06:14–07:05 |
| 08    | 138   | 1:04           | 0:16        | 07:05–08:24 |
| 09    | 126   | 0:58           | 0:03        | 08:24–09:26 |
| 10    | 131   | 1:00           | 0:04        | 09:26–10:30 |
| 11    | 104   | 0:48           | 0:10        | 10:30–11:28 |
| 12    | 127   | 0:59           | 0:05        | 11:28–12:32 |
| 13    | 193   | 1:29           | 0:08        | 12:32–14:09 |

## 10. QUALITY ASSESSMENT (QUALITY_CHECKLIST.md)

This is the writer's own review; items that depend on a real table read, recording or image licensing are marked not done.

| Section                              | Result               | Notes                                                                                                                                             |
|--------------------------------------|----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| A. Promise and premise               | Passed               | The opening promises an answer to the DoD puzzle and scene 13 delivers it                                                                         |
| B. Research and evidence             | Passed with caveats  | Sources are real and were retrieved; some were read only in part (S07, S09, S17, S26) and C34 rests on one secondary source                       |
| C. Story and structure               | Passed               | One caution: scenes 4–7 are four history scenes in a row (about 3:40) with no demo between them; the ledger icons and archival visuals carry them |
| D. Explanation and accessibility     | Passed               | Terms (compiler, interpreter, operating system, assembly) defined at first use; "CVE" is replaced by "official public ID"                         |
| E. Retention and pacing              | Not fully checked    | No timed read-aloud; opening has no channel intro                                                                                                 |
| F. Visual storytelling               | Passed with caveats  | Demos are real runs; conceptual visuals are labelled; image licences not checked                                                                  |
| G. Narration quality                 | Not fully checked    | Read-aloud rhythm and names (Ichbiah, Chamberlin) need a real table read                                                                          |
| I. Editorial guardrails              | Passed               | One analogy (three bills) used consistently with stated limits; real demonstrations; code run and outputs recorded; no claim of table read        |
| J. Tension and retention stress test | Passed with one risk | Each chapter adds a new person, mechanism or demo; the middle risk is scenes 5–6, where the only new fact is a failed or partial unification      |

**Decision: READY for table read, then production, subject to the pre-publication checks in section 8.** I am not marking it production-ready, because a table read, a recording of the demos and image-rights checks have not been done.

**Final editor's questions**

1.  *Most memorable idea:* a language is a decision about who pays, and the unification attempts split by scope (one domain worked, everything did not).

2.  *Section most likely to lose a first-time viewer:* scene 5 or 6, history without a demo.

3.  *Weakest factual claim:* the Ada rule dates (C34), then the interpretive thesis.

4.  *What can be removed:* scenes 6 and 11.

5.  *Does the viewer leave with a better mental model?* I think so, but that is untested with real viewers.

## APPENDIX A. DEMO FILES AND VERIFIED OUTPUTS

**Environment (D01-D04):** Ubuntu 24.04.5, Linux 6.18.44, x86_64, 1 vCPU sandbox; gcc 13.3.0 (Ubuntu 13.3.0-6ubuntu2~24.04.1); Node v22.23.5; CPython 3.12.3; SQLite 3.45.1 (via Python's sqlite3 module). Run on 21 Nov 2026. Re-record on the production machine.

**D01 — primes.c** (compiled with gcc -O2 -o primes_c primes.c)

\#include \<stdio.h\>  
  
int is_prime(int n) {  
if (n \< 2) return 0;  
if (n % 2 == 0) return n == 2;  
for (int d = 3; (long long)d \* d \<= n; d += 2)  
if (n % d == 0) return 0;  
return 1;  
}  
  
int main(void) {  
int count = 0;  
for (int n = 2; n \< 2000000; n++)  
if (is_prime(n)) count++;  
printf("%d\n", count);  
return 0;  
}

**primes.py**

def is_prime(n):  
if n \< 2:  
return False  
if n % 2 == 0:  
return n == 2  
d = 3  
while d \* d \<= n:  
if n % d == 0:  
return False  
d += 2  
return True  
  
count = 0  
for n in range(2, 2000000):  
if is_prime(n):  
count += 1  
print(count)

**primes.js** (node primes.js)

function isPrime(n) {  
if (n \< 2) return false;  
if (n % 2 === 0) return n === 2;  
for (let d = 3; d \* d \<= n; d += 2) {  
if (n % d === 0) return false;  
}  
return true;  
}  
  
let count = 0;  
for (let n = 2; n \< 2000000; n++) {  
if (isPrime(n)) count++;  
}  
console.log(count);

**Measured output** (whole-process wall time, 3 runs each, via a Python subprocess harness):

C (gcc -O2) output=148933 runs=\[0.184, 0.186, 0.187\] median=0.186s  
JavaScript (Node) output=148933 runs=\[0.298, 0.165, 0.207\] median=0.207s  
Python (CPython) output=148933 runs=\[4.684, 4.404, 4.525\] median=4.525s

Ratio Python to C: 4.525 / 0.186 = about 24. Node's first run (0.298 s) was an outlier; this is one task on one machine and is not a language ranking.

**D02 — out-of-bounds read**

\#include \<stdio.h\>  
  
int main(int argc, char \*\*argv) {  
int a\[5\] = {10, 20, 30, 40, 50};  
int i = argc + 6; /\* 7: two past the end of the array \*/  
printf("%d\n", a\[i\]);  
return 0;  
}

a = \[10, 20, 30, 40, 50\]  
i = 7  
print(a\[i\])

const a = \[10, 20, 30, 40, 50\];  
const i = 7;  
console.log(a\[i\]);

Results: gcc -o oob_c oob.c compiled with exit code 0 and no warnings. Three runs printed -1792287255, -1861671412, -2020085970, each with exit code 0. Built with gcc -O2 -Wall it printed 1634145754, again with no warning. Python exited with status 1 and IndexError: list index out of range pointing at line 3. Node printed undefined with exit code 0. Built with gcc -g -fsanitize=address, the C program stopped with ERROR: AddressSanitizer: stack-buffer-overflow ... READ of size 4 ... in main oob.c:6. The C values are undefined behaviour and will differ on other runs and machines.

**D03 — SQL and Python**

import sqlite3  
  
rows = \[  
("North", 120), ("South", 80), ("East", 200), ("North", 90),  
("West", 150), ("South", 130), ("East", 40), ("West", 70),  
("North", 30), ("East", 110),  
\]  
  
\# --- Version 1: SQL (describe the answer) ---  
db = sqlite3.connect(":memory:")  
db.execute("CREATE TABLE sales (region TEXT, amount INTEGER)")  
db.executemany("INSERT INTO sales VALUES (?, ?)", rows)  
query = """  
SELECT region, SUM(amount) AS total  
FROM sales  
GROUP BY region  
ORDER BY total DESC  
LIMIT 3  
"""  
sql_result = db.execute(query).fetchall()  
print("SQL :", sql_result)  
  
\# --- Version 2: Python loop (describe the steps) ---  
totals = {}  
for region, amount in rows:  
totals\[region\] = totals.get(region, 0) + amount  
ranked = sorted(totals.items(), key=lambda kv: kv\[1\], reverse=True)  
py_result = ranked\[:3\]  
print("Python :", py_result)  
print("Same answer:", sql_result == py_result)

Output: SQL : \[('East', 350), ('North', 240), ('West', 220)\], Python : \[('East', 350), ('North', 240), ('West', 220)\], Same answer: True. Totals by region: North 240, South 210, East 350, West 220. (In the first run, West was 210 and tied with South, and the two versions broke the tie differently; the data was changed.)

**D04 — assembly for scene 7** (gcc -O1 -S -masm=intel -fno-asynchronous-unwind-tables -fno-ident add.c)

int add(int a, int b) {  
return a + b;  
}

add:  
endbr64  
lea eax, \[rdi+rsi\]  
ret

This is x86-64 output from gcc 13.3.0. Other processors and compilers give different instructions.