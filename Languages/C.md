# C Roadmap: From Zero to Systems Programming

Oct 13, 2026 · @aarhvee

## Start here

This roadmap takes you from never having programmed to writing real C programs: algorithms, command-line tools, a shell, network servers and small embedded programs: 11 weeks, 66 sessions, about 210 hours. No earlier programming is needed, and it does not depend on the C++, Python or C# roadmaps. All four roadmaps start on the same day (suggested: Monday 19 October 2026), and you choose which one to do on each day.

C is the language that shows you how a computer really works: memory, addresses, bytes and the stack. That makes it the base for game engines, security work and fast AI code.

### How the sessions work

- A "Day" in the tables is one study session, not a calendar day. Do them in order, one roadmap day at a time, whenever you choose to work on C.

- Sessions 1-5 of each week are about 3 hours. Session 6 is a 4-hour project session that ends with a review.

- Stuck for 20 minutes? Write down what you expected and what happened, then search or ask.

| Time   | Block    | What you do                                                                                                     |
|--------|----------|-----------------------------------------------------------------------------------------------------------------|
| 10 min | Start    | Read yesterday's journal line "next first step". Retype a snippet from last session from memory.                |
| 40 min | Learn    | Read or watch only the topic in the table. Notes in your own words, with a memory drawing where it applies.     |
| 90 min | Build    | Write the exercise by hand. Type every line yourself; no copy-paste and no AI-written code.                     |
| 30 min | Break it | Add a deliberate bug (off-by-one, double free, leak). Find it with printing, then with GDB or AddressSanitizer. |
| 10 min | End      | Compile with warnings on, commit to Git, and write 3 lines: learned, confused, next first step.                 |

A session is done only when the code builds with -Wall -Wextra, runs correctly, and is committed. If you run out of time, cut the "Learn" block, never "Break it".

### Setup (about 1 hour)

- **WSL2** is Windows' built-in way to run a real Linux (Ubuntu) next to Windows. Install it by opening PowerShell as administrator, running wsl --install, and restarting. On macOS or Linux, skip this.

- In the Ubuntu terminal: sudo apt update && sudo apt install build-essential gdb valgrind cmake ninja-build git clang clang-tidy clang-format. On macOS, install Xcode command line tools and use lldb where I say gdb.

- VS Code with the C/C++ extension (and the WSL extension on Windows). Keep your projects inside the Linux home folder (~/), not under /mnt/c.

- Compile with gcc -std=c17 -Wall -Wextra -Wpedantic -g file.c -o file. From week 4 add -fsanitize=address,undefined.

- Open [Compiler Explorer](https://godbolt.org/) in a tab; you will use it to see assembly from week 6.

- Practise security exercises only inside a virtual machine, on your own programs or on legal practice sites such as OverTheWire. Never test systems you do not own or have written permission to test.

- One Git repository with a folder per week and a journal.md.

## Part 1 (weeks 1-3): programming from zero, in C

This part teaches what a variable, a data type, a condition, a loop, a function and an array are, using C. The free spine is Harvard's CS50x (its first weeks) together with Beej's Guide to C. If a day takes longer than planned, it becomes the first block of the next day; never skip a day.

### Week 1: your first programs

| Day | Start here (learn)                                                                                                        | Build                                                                                                                                                    | Done when                                                                          |
|-----|---------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------|
| 1   | What a program is and what a compiler does. CS50x lecture 1 (first 30 minutes). Do the setup from the Start here section. | Write hello.c with printf. Compile it with gcc hello.c -o hello and run it. Change the message and run it again.                                         | You can explain the cycle: edit, compile, run.                                     |
| 2   | Variables and data types: int, float, double, char. Beej's Guide to C, the variables and types chapter.                   | Declare one variable of each type and print each with printf (%d, %f, %c). Print 7 / 2 and 7 / 2.0 and explain the difference.                           | You can say what each type stores and why 7 / 2 is 3.                              |
| 3   | Operators (+ - \* / %) and reading input with scanf.                                                                      | A temperature converter: ask for Celsius, print Fahrenheit. A program that asks for two numbers and prints their sum, difference, product and remainder. | Both programs give correct answers for 5 inputs you try, including 0.              |
| 4   | Conditions: if, else, else if, comparison (== != \< \>) and logical (&& \|\| !) operators.                                | A program that reads a mark and prints a grade. A program that says whether a number is positive, negative or zero.                                      | You test each branch at least once and can spot a = written instead of ==.         |
| 5   | Loops: while, for, do while, break, continue.                                                                             | Print the numbers 1 to 20. Print a multiplication table. Sum the digits of a number.                                                                     | You can trace a loop by hand on paper and match the output.                        |
| 6   | Project session, then review. Learn Git basics too: git init, git add, git commit.                                        | A number-guessing game: the program picks a random number with rand(), you guess, it says higher or lower and counts your attempts.                      | The game works start to finish, you wrote it without copying, and it is committed. |

### Week 2: functions, arrays and thinking in steps

| Day | Start here (learn)                                                                                  | Build                                                                                                                                          | Done when                                                            |
|-----|-----------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------|
| 7   | Functions: parameters, return values, prototypes, scope. CS50x lecture 1 (functions part).          | is_even, max_of_two, power and is_prime as functions called from main.                                                                         | Each function is tested from main with at least 3 inputs.            |
| 8   | Arrays: declaring, indexing from 0, looping over elements. CS50x lecture 2.                         | Read 5 numbers into an array. Print them, their sum, their average, the largest and the smallest.                                              | You can explain what an off-by-one error is and you do not have one. |
| 9   | Strings as arrays of char ending with '\0'. The ctype.h functions.                                  | Count vowels in a word. Reverse a string. Check whether a word is a palindrome.                                                                | They work on empty, 1-letter and long words.                         |
| 10  | Algorithmic thinking: linear search, binary search, bubble sort. CS50x lecture 3.                   | Implement all three on an array of 10 numbers. Print the array after each pass of bubble sort.                                                 | You can say why binary search needs sorted data.                     |
| 11  | Debugging: reading compiler errors and warnings (-Wall -Wextra), printf debugging, tracing by hand. | Take 5 programs you wrote, add 1 deliberate mistake to each, and find it using only error messages and printf.                                 | You found all 5 and wrote one line about how each error looked.      |
| 12  | Project session, then review.                                                                       | A grade manager: a menu loop where you add marks, list them, print the average and the highest, and quit. Use arrays and at least 4 functions. | The menu handles bad input without crashing.                         |

### Week 3: structs, recursion, number systems, a first look at pointers, files

| Day | Start here (learn)                                                                                                                          | Build                                                                                                                         | Done when                                                                                                                |
|-----|---------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------|
| 13  | struct and enum. Beej's Guide to C, the structs chapter.                                                                                    | A Student struct (name, roll number, marks). An array of 5 students, printed in a table.                                      | You can add a new field to the struct without breaking other code.                                                       |
| 14  | Recursion: a function that calls itself.                                                                                                    | Factorial, Fibonacci, sum of digits and power, each recursively. Draw the call stack for factorial(4) on paper.               | Your drawing matches the program's output.                                                                               |
| 15  | Binary and hexadecimal: how a computer stores a number.                                                                                     | A program that prints any number from 0 to 255 in binary and in hex. Convert 5 numbers by hand, then check with your program. | Your 5 hand conversions are right.                                                                                       |
| 16  | Pointers, first look: a pointer is a variable that holds an address. Use & and \*. It is fine if it feels odd; week 5 explains it properly. | Print the address of a variable. Change a variable through a pointer. Write swap(int \*a, int \*b).                           | swap works and you can draw it as boxes and arrows.                                                                      |
| 17  | Files: fopen, fgets, fprintf, fclose. Command-line arguments (argc, argv).                                                                  | Write names to a text file, then read them back. Print the number of lines in a file given on the command line.               | Re-running the program keeps the data from before.                                                                       |
| 18  | **Checkpoint 0** (3 to 4 hours).                                                                                                            | A contacts book: add, list, search and delete contacts, saved to a file. Use a struct, an array, functions and file I/O.      | It works after you close and re-open it. Then, from memory in 30 minutes: FizzBuzz, reverse a string, check for a prime. |

## Part 2 (weeks 4-7): C and the machine

By the end of week 7 you can explain where every byte of a C program lives, and you can write a small tool in pure C that survives the sanitizers (AddressSanitizer and UndefinedBehaviorSanitizer find memory mistakes at run time). The main reading is Beej's Guide to C, the book C Programming: A Modern Approach by K. N. King, and the book Computer Systems: A Programmer's Perspective (CS:APP).

### Week 4: the compiler, bits and the call stack

| Day | Start here (learn)                                                                           | Build                                                                                                                                                                                                                  | Done when                                                                        |
|-----|----------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------|
| 19  | Beej's Guide to C on how compiling works. Look inside the hello program you wrote.           | Compile hello.c stage by stage with gcc -E, -S, -c, then link. Open the .s file and run objdump -d on the .o. Set up a CMake project for it.                                                                           | You can say what the .i, .s, .o and executable files contain.                    |
| 20  | CS:APP chapter 2.1-2.3 (bits, integers, two's complement). Beej's chapter on types.          | Print sizeof and the min/max of 10 integer types from stdint.h. Dump the bytes of an int and a float through unsigned char \*. Detect endianness (byte order).                                                         | A table of 10 types in your notes, and the byte dump matches what you predicted. |
| 21  | Beej's chapter on bitwise operators.                                                         | bitflags.h: set, clear, toggle, test on a uint32_t. Pack 8 entity flags (grounded, poisoned, ...) into one byte. Extract version, header length and TTL from a hand-written 20-byte IPv4 header with shifts and masks. | Assert-based tests pass, including bit 0 and bit 31.                             |
| 22  | A GDB tutorial: break, run, next, step, bt, print, x, info frame.                            | Step through your recursive factorial in GDB and draw the stack for depth 4 on paper.                                                                                                                                  | Your drawing matches info frame and bt for depth 4.                              |
| 23  | Beej's chapter on the preprocessor and multiple files. Learn include guards, static, extern. | Split bitflags into .h and .c, add main.c and a test file. Build with CMake and -Wall -Wextra -Werror.                                                                                                                 | Clean build, zero warnings, tests run with one command.                          |
| 24  | Project session, then review.                                                                | Project: hexdump. Read a file in chunks and print offset, hex bytes and ASCII, like xxd. Take the file name from argv.                                                                                                 | diff against xxd output is empty on 3 test files (empty, 1 byte, 1 MB).          |

### Week 5: pointers, strings and the heap

| Day | Start here (learn)                                                               | Build                                                                                                                                         | Done when                                                                               |
|-----|----------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|
| 25  | King chapters 11-12, or Beej's chapter on pointers.                              | Swap two ints through pointers. Walk an array with pointer arithmetic. Print the address of every variable and draw them.                     | You predict the output of 5 pointer snippets before running them, and get 5 of 5.       |
| 26  | King chapter 13 (strings). Read the man pages for strlen, strcpy, strncpy.       | Implement my_strlen, my_strcpy, my_strcmp, my_strdup with pointers only.                                                                      | They match libc on empty, 1-character and 10,000-character strings.                     |
| 27  | Beej's chapter on malloc and free. Learn what AddressSanitizer reports.          | A growable array of ints with push that doubles with realloc, and a free function.                                                            | ASan and Valgrind report no leaks and no errors after 100,000 pushes.                   |
| 28  | CS:APP 3.10 (buffer overflow) for context only. Read how to read an ASan report. | Write 6 tiny buggy programs: use-after-free, double free, heap overflow, stack overflow, uninitialized read, off-by-one. Run each under ASan. | For each one, a one-line note: what the report says and which line is the cause.        |
| 29  | Row-major layout. King chapter 8 on arrays if needed.                            | Store a matrix as one flat float array with index = row \* cols + col. Write alloc, fill, transpose, naive multiply.                          | A 3x3 result matches your hand calculation. Time for 512x512 is written in the journal. |
| 30  | Project session, then review.                                                    | A mini library with IntVec (push, pop, insert, remove, free) and StrBuf (append, clear). Keep data, len, cap in a struct.                     | 20 unit tests pass under ASan and UBSan. Zero leaks.                                    |

### Week 6: structs, alignment, function pointers and first assembly

| Day | Start here (learn)                                                                     | Build                                                                                                                                                                           | Done when                                                                      |
|-----|----------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------|
| 31  | King chapter 16 and CS:APP 3.9 (data alignment). Look up offsetof.                     | Print sizeof and offsetof for 5 structs. Reorder the fields of one to remove padding. Make a Vertex (position, normal, uv) and a packed network header.                         | A table of padding bytes before and after reordering.                          |
| 32  | King chapter 17 (function pointers) and the man page for qsort.                        | Sort an array of entities by distance with qsort. Build a state machine with an array of function pointers.                                                                     | Both work with no warnings.                                                    |
| 33  | King chapter 17 (linked lists).                                                        | Singly linked list: push front, push back, find, remove, reverse. Then make it doubly linked.                                                                                   | Tests cover the empty list and the 1-node list. ASan clean.                    |
| 34  | memcpy and memmove man pages. Learn void \* and element size.                          | A generic Vec that stores any element size using void \* and memcpy.                                                                                                            | It stores 1,000 Vertex structs and 1,000 floats and reads them back correctly. |
| 35  | CS:APP 3.1-3.7 (registers, mov, lea, call, ret, stack frames). Open Compiler Explorer. | Write 5 small functions. Compare -O0 and -O2 assembly. Annotate each line of one function in comments.                                                                          | You can explain every line of a 15-line function's assembly out loud.          |
| 36  | Project session, then review.                                                          | Project: stack_explorer. A program with 3 nested calls that prints the addresses of its locals, arguments and return address. Compare with x/16gx \$rsp in GDB. Draw the frame. | An annotated frame diagram is committed to the repo and matches GDB.           |

### Week 7: files, the OS, a first look at memory bugs, and Checkpoint 1

| Day | Start here (learn)                                                                    | Build                                                                                                                                                                                                                | Done when                                                                                                                                                                      |
|-----|---------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 37  | fopen, fread, fwrite, fseek man pages. Why you do not write raw structs to disk.      | Design a binary file format: magic bytes, version, record count, then records with fixed-width fields. Write a writer and a reader.                                                                                  | A round-trip test passes and your hexdump from day 24 shows your magic bytes.                                                                                                  |
| 38  | Linux basics: file descriptors, errno, system calls. Man pages for open, read, write. | A cat clone using only open, read, write, close. Run it under strace.                                                                                                                                                | You can name every system call in the strace output.                                                                                                                           |
| 39  | CS:APP 3.10 again, now hands-on. Work inside a VM.                                    | In your own toy program, a 16-byte buffer sits next to an authenticated flag. Overflow it with a long input and watch the flag flip in GDB. Then fix it with bounded copies and compile with the stack protector on. | The flaw is reproduced, then the fix resists the same input, and you can explain what a canary is.                                                                             |
| 40  | Any hash table explainer, plus the djb2 hash function.                                | A hash table in C: djb2 hash, separate chaining, insert, find, delete, resize.                                                                                                                                       | 10,000 inserts and lookups pass. ASan clean. Collision count is printed.                                                                                                       |
| 41  | assert, clang-tidy, valgrind --leak-check=full.                                       | Write tests for every library from weeks 4-7. Add a make check target that builds with sanitizers and runs them all.                                                                                                 | One command runs all tests, all green.                                                                                                                                         |
| 42  | **Checkpoint 1** (4 hours, from a blank file).                                        | Build cdump: read your day-37 binary format, validate every length with bounds checks, store records in your hash table, print statistics.                                                                           | Zero warnings, ASan clean, tag checkpoint-1 in Git. Then answer in writing: stack vs heap, why padding exists, what ret does, what use-after-free is, why strncpy is not safe. |

## Part 3 (weeks 8-11): C everywhere, from algorithms to servers and small devices

Parts 1 and 2 gave you the language and the machine. This part makes you useful in almost any C project: classic algorithms, the Linux operating system, networking, and tiny embedded devices. Each topic starts from the basics. Days continue from 43. The main extra reading is Beej's Guide to Network Programming and the free book Operating Systems: Three Easy Pieces (OSTEP).

### Week 8: data structures and algorithms in C

| Day | Start here (learn)                                                                         | Build                                                                                   | Done when                                                              |
|-----|--------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|------------------------------------------------------------------------|
| 43  | Big-O: how running time grows with input size. The clock() function.                       | Time linear search and binary search on arrays of 1,000, 100,000 and 1,000,000 numbers. | A table of times, and you can say why one grows faster.                |
| 44  | Sorting: insertion sort, merge sort, quick sort. The qsort comparator.                     | Implement merge sort and quick sort. Compare with qsort.                                | Correct on random, sorted, reversed and empty arrays.                  |
| 45  | Stacks and queues, as arrays and as linked lists.                                          | A stack, a queue and a ring buffer.                                                     | All tests pass under ASan, including the full and empty cases.         |
| 46  | Binary search trees.                                                                       | Insert, search, in-order print and delete, then free the whole tree.                    | ASan reports no leaks after 1,000 random operations.                   |
| 47  | Heaps and priority queues.                                                                 | A min-heap and heap sort.                                                               | Heap sort matches qsort on 10 random arrays.                           |
| 48  | Project session, then review. Graphs: adjacency lists, BFS, DFS, Dijkstra's shortest path. | Find the shortest route on a small map file, using your heap for Dijkstra.              | It prints the correct route for 3 maps and reports when there is none. |

### Week 9: Linux, processes and a shell

| Day | Start here (learn)                                                                                            | Build                                                                                      | Done when                                                        |
|-----|---------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|------------------------------------------------------------------|
| 49  | The command line in depth: pipes, redirection, grep, find, file permissions. MIT's "Missing Semester" course. | Ten useful one-liners, and a bash script that backs up a folder.                           | The script works on a test folder and you can explain each pipe. |
| 50  | Processes: fork, exec, wait. OSTEP chapter on process creation.                                               | A program that starts ls in a child process and waits for it.                              | You can explain what each of the three calls does.               |
| 51  | Pipes and redirection at the system-call level: pipe, dup2.                                                   | Re-implement ls \| wc -l yourself with two child processes.                                | The output matches the shell's version.                          |
| 52  | Signals: SIGINT, handlers, what is safe inside a handler.                                                     | A program that shuts down cleanly when you press Ctrl+C.                                   | It closes its files and prints a summary on Ctrl+C.              |
| 53  | Threads with pthread: create, join, mutexes. ThreadSanitizer (-fsanitize=thread).                             | A parallel sum with N threads. Add an unsynchronized counter first and catch it with TSan. | TSan reports the race, and the fixed version is clean.           |
| 54  | Project session, then review.                                                                                 | minishell: a prompt that runs commands, supports cd, pipes and Ctrl+C handling.            | It runs 10 different commands and a 3-stage pipeline correctly.  |

### Week 10: networking and servers

| Day | Start here (learn)                                                                        | Build                                                                                                    | Done when                                                          |
|-----|-------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------|
| 55  | IP addresses, ports, TCP, DNS. Beej's Guide to Network Programming, the first chapters.   | Use getaddrinfo to print the IP addresses of a hostname.                                                 | It matches nslookup for 3 names.                                   |
| 56  | A TCP client: socket, connect, send, recv. Partial reads.                                 | A client that sends a raw HTTP request to example.com and prints the reply.                              | You can see the status line and headers.                           |
| 57  | A TCP server: bind, listen, accept.                                                       | An echo server and its client.                                                                           | Five clients in a row work with no leaked sockets.                 |
| 58  | HTTP basics: request line, headers, status codes. Path traversal and why it is dangerous. | A tiny web server that serves files from one folder.                                                     | A browser shows your page, and a request for ../secret is refused. |
| 59  | Many clients at once: a thread per client, against poll().                                | Turn the echo server into a poll()-based server.                                                         | It serves 100 clients without a thread per client.                 |
| 60  | Project session, then review.                                                             | A key-value store server: a text protocol (SET, GET, DEL), an in-memory hash table and saving to a file. | A restart keeps the data, and a fuzzed input does not crash it.    |

### Week 11: small devices, other people's code and a capstone

| Day | Start here (learn)                                                                                        | Build                                                                                                                                               | Done when                                                    |
|-----|-----------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------|
| 61  | What a microcontroller is. Arduino basics. Use the free Wokwi online simulator, so no hardware is needed. | Blink an LED.                                                                                                                                       | The LED blinks at the rate you set.                          |
| 62  | Digital input and output, button debouncing, timing with millis().                                        | A button that cycles through three LED patterns.                                                                                                    | One press changes the pattern once, with no flicker.         |
| 63  | Analog sensors and serial output.                                                                         | Read a simulated temperature sensor and print readings.                                                                                             | Readings change when you change the sensor in the simulator. |
| 64  | Programming with tiny memory: no malloc, static buffers, bit flags.                                       | A traffic-light state machine with no dynamic allocation.                                                                                           | It cycles correctly and uses fixed-size buffers only.        |
| 65  | Reading other people's C: pick a small open-source program, for example a coreutils tool such as wc.      | Trace main and one feature, and write one page of notes.                                                                                            | Your notes explain the structure to a friend.                |
| 66  | **Capstone** (4 hours, then review).                                                                      | Choose one: a polished minishell; the key-value server with tests and a fuzzing run; or a simulated embedded project of your own. Write the README. | ASan clean, README, tagged c-v2 in Git.                      |

## Checkpoints and what comes next

| Gate         | After  | You must have                                                                                                          | If you miss it                          |
|--------------|--------|------------------------------------------------------------------------------------------------------------------------|-----------------------------------------|
| Checkpoint 0 | Day 18 | A contacts book that saves to a file, and FizzBuzz, string reverse and a prime check written from memory in 30 minutes | Repeat week 3 before starting week 4    |
| Checkpoint 1 | Day 42 | cdump in pure C, ASan clean, written answers on stack, heap, padding, ret, use-after-free                              | Redo the weakest week's project session |

Gates for Part 3 (weeks 8-11):

- Day 48: Dijkstra's shortest path on a small map, with your own heap and no leaks.

- Day 54: minishell running a 3-stage pipeline and handling Ctrl+C.

- Day 60: a key-value store server that keeps its data across restarts.

- Day 66: the capstone, ASan clean, tagged c-v2.

After day 42: if you follow the C++ roadmap, its memory and performance weeks will feel familiar. Otherwise, read more of Beej's Guide to C and CS:APP, write a small shell or a tiny HTTP server in C, and read the source of a small open-source C program such as a coreutils tool.

## Resources

These come from my own knowledge of well-known material, not pages I opened while writing, so check each link and edition before relying on it.

| Topic             | Resource                                                                                                        | Cost |
|-------------------|-----------------------------------------------------------------------------------------------------------------|------|
| Basics            | [CS50x, Harvard's introduction to computer science](https://cs50.harvard.edu/x/)                                | Free |
| C                 | [Beej's Guide to C](https://beej.us/guide/bgc/)                                                                 | Free |
| C                 | K. N. King, C Programming: A Modern Approach                                                                    | Paid |
| Machine           | Bryant and O'Hallaron, Computer Systems: A Programmer's Perspective (CS:APP), [site](https://csapp.cs.cmu.edu/) | Paid |
| Machine           | [Compiler Explorer](https://godbolt.org/)                                                                       | Free |
| Security practice | [OverTheWire](https://overthewire.org/wargames/) and [pwn.college](https://pwn.college/) (legal practice sites) | Free |
| Tools             | GDB, Valgrind and AddressSanitizer documentation                                                                | Free |

Added for Part 3 (also from my own knowledge, so check the links):

| Topic             | Resource                                                                                | Cost |
|-------------------|-----------------------------------------------------------------------------------------|------|
| Operating systems | [Operating Systems: Three Easy Pieces (OSTEP)](https://pages.cs.wisc.edu/~remzi/OSTEP/) | Free |
| Networking        | [Beej's Guide to Network Programming](https://beej.us/guide/bgnet/)                     | Free |
| Linux             | [The Missing Semester of Your CS Education (MIT)](https://missing.csail.mit.edu/)       | Free |
| Linux             | The Linux Programming Interface by Michael Kerrisk                                      | Paid |
| Embedded          | [Wokwi online simulator](https://wokwi.com/)                                            | Free |
| Algorithms        | Algorithms by Sedgewick and Wayne, or Grokking Algorithms                               | Paid |
