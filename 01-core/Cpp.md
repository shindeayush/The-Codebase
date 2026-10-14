# C++ Roadmap: From Zero to Games, AI and Security

Oct 13, 2026 · @aarhvee

## Start here

This roadmap takes you from never having programmed to writing fast, safe C++ for games, AI/ML tools, security tools, desktop apps, servers and almost anything else: 23 weeks, 138 sessions, about 440 hours. No earlier programming is needed, and it does not depend on the C, Python or C# roadmaps (the C roadmap covers some of the same ideas in a different style, and doing both is fine). All four roadmaps start on the same day (suggested: Monday 19 October 2026), and you choose which one to do on each day.

It uses modern C++ (C++20) from the first day. You learn the standard library (std::string, std::vector) before bare pointers, then learn how memory works, then classes and templates, then speed, and finally one specialization track: Game, AI/ML or Cybersecurity.

### How the sessions work

- A "Day" in the tables is one study session, not a calendar day. Do them in order, one roadmap day at a time, whenever you choose to work on C++.

- Sessions 1-5 of each week are about 3 hours. Session 6 is a 4-hour project session that ends with a review.

- Stuck for 20 minutes? Write down what you expected and what happened, then search or ask.

| Time   | Block    | What you do                                                                                                 |
|--------|----------|-------------------------------------------------------------------------------------------------------------|
| 10 min | Start    | Read yesterday's journal line "next first step". Retype a snippet from last session from memory.            |
| 40 min | Learn    | Read or watch only the topic in the table. Notes in your own words, with a memory drawing where it applies. |
| 90 min | Build    | Write the exercise by hand. Type every line yourself; no copy-paste and no AI-written code.                 |
| 30 min | Break it | Add a deliberate bug (off-by-one, double free, leak). Find it with printing, then with GDB or a sanitizer.  |
| 10 min | End      | Compile with warnings on, commit to Git, and write 3 lines: learned, confused, next first step.             |

A session is done only when the code builds with -Wall -Wextra, runs correctly, and is committed. If you run out of time, cut the "Learn" block, never "Break it".

### Setup (about 1 hour)

- **WSL2** is Windows' built-in way to run a real Linux (Ubuntu) next to Windows. Install it by opening PowerShell as administrator, running wsl --install, and restarting. On macOS or Linux, skip this.

- In the Ubuntu terminal: sudo apt update && sudo apt install build-essential gdb valgrind cmake ninja-build git clang clang-tidy clang-format. On macOS, install Xcode command line tools and use lldb where I say gdb.

- VS Code with the C/C++ extension (and the WSL extension on Windows). Keep your projects inside the Linux home folder (~/), not under /mnt/c.

- Compile with g++ -std=c++20 -Wall -Wextra -Wpedantic -g file.cpp -o file. From week 4 add -fsanitize=address,undefined.

- Open [Compiler Explorer](https://godbolt.org/) in a tab; you will use it to see assembly from week 5.

- Practise security exercises only inside a virtual machine, on your own programs or on legal practice sites such as OverTheWire. Never test systems you do not own or have written permission to test.

- One Git repository with a folder per week and a journal.md.

## Part 1 (weeks 1-3): programming from zero, in C++

This part teaches what a variable, a data type, a condition, a loop, a function and a collection are. The free spine is learncpp.com, read in order; chapter numbers follow its current layout, and cppreference.com is the lookup reference. If a day takes longer than planned, it becomes the first block of the next day; never skip a day.

### Week 1: your first programs

| Day | Start here (learn)                                                                                                            | Build                                                                                                                                                    | Done when                                                                          |
|-----|-------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------|
| 1   | What a program is and what a compiler does. learncpp chapters 0 and 1.1-1.3. Do the setup from the Start here section.        | Write hello.cpp that prints a line with std::cout. Compile it with g++ -std=c++20 hello.cpp -o hello and run it. Change the message and run it again.    | You can explain the cycle: edit, compile, run.                                     |
| 2   | Variables and data types: int, double, char, bool, std::string, auto. learncpp chapters 1.4-1.5 and 4.                        | Declare one variable of each type and print it. Print 7 / 2 and 7 / 2.0 and explain the difference. Print sizeof of each type.                           | You can say what each type stores and why 7 / 2 is 3.                              |
| 3   | Operators and input: + - \* / %, std::cin, std::getline. learncpp chapters 1.6 and 6.                                         | A temperature converter: ask for Celsius, print Fahrenheit. A program that asks for two numbers and prints their sum, difference, product and remainder. | Both give correct answers for 5 inputs you try, including 0.                       |
| 4   | Conditions: if, else, switch, comparison (== != \< \>) and logical (&& \|\| !) operators. learncpp chapter 8, first sections. | A program that reads a mark and prints a grade. A program that says whether a number is positive, negative or zero.                                      | You test each branch at least once and can spot a = written instead of ==.         |
| 5   | Loops: while, for, do while, break, continue. learncpp chapter 8, loops sections.                                             | Print the numbers 1 to 20. Print a multiplication table. Sum the digits of a number.                                                                     | You can trace a loop by hand on paper and match the output.                        |
| 6   | Project session, then review. Learn Git basics: git init, git add, git commit.                                                | A number-guessing game: the program picks a random number with \<random\>, you guess, it says higher or lower and counts your attempts.                  | The game works start to finish, you wrote it without copying, and it is committed. |

### Week 2: functions, collections and thinking in steps

| Day | Start here (learn)                                                                                                          | Build                                                                                                                                                      | Done when                                                            |
|-----|-----------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------|
| 7   | Functions: parameters, return values, default arguments, scope, overloading. learncpp chapters 2 and 11 (overloading part). | is_even, max_of_two, power and is_prime as functions, called from main.                                                                                    | Each function is tested from main with at least 3 inputs.            |
| 8   | std::vector and std::array: indexing from 0, push_back, size, range-based for. learncpp chapters 16 and 17.                 | Read 5 numbers into a vector. Print them, their sum, their average, the largest and the smallest.                                                          | You can explain what an off-by-one error is and you do not have one. |
| 9   | std::string in depth and the \<algorithm\> header: sort, find, reverse, count. learncpp chapter 5 and 18.                   | Count vowels in a word. Reverse a string. Check whether a word is a palindrome. Sort a vector of numbers with std::sort.                                   | They work on empty, 1-letter and long words.                         |
| 10  | References and const: pass by value against pass by reference. learncpp chapter 12, first sections.                         | Write swap(int &a, int &b). Write a function that takes a const std::vector\<int\> & and returns its sum, and say why it does not copy.                    | You can explain when a copy happens and when it does not.            |
| 11  | struct and enum class. learncpp chapter 13.                                                                                 | A Student struct (name, roll number, marks). A std::vector\<Student\> printed in a table, sorted by marks.                                                 | You can add a new field to the struct without breaking other code.   |
| 12  | Project session, then review.                                                                                               | A grade manager: a menu loop where you add marks, list them, print the average and the highest, and quit. Use a vector, a struct and at least 4 functions. | The menu handles bad input without crashing.                         |

### Week 3: files, organizing code, recursion and checks

| Day | Start here (learn)                                                                                                                                                        | Build                                                                                                                                         | Done when                                                                                                                |
|-----|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------|
| 13  | Files and streams: std::ifstream, std::ofstream, std::getline. learncpp chapter 28.                                                                                       | Write names to a text file, then read them back. Print the number of lines in a file given on the command line (argc, argv).                  | Re-running the program keeps the data from before.                                                                       |
| 14  | Splitting code into headers and source files, include guards, namespaces. Learn what CMake is. learncpp chapter 2 (headers part) and the official CMake tutorial, step 1. | Move your functions into utils.h and utils.cpp. Build the project with a CMakeLists.txt.                                                      | The project builds with cmake and runs.                                                                                  |
| 15  | Maps and sets: std::map, std::unordered_map, std::set. cppreference pages.                                                                                                | A word-frequency counter for a text file. Remove duplicates from a vector with a set.                                                         | The counts match sort \| uniq -c on the same file.                                                                       |
| 16  | Recursion: a function that calls itself.                                                                                                                                  | Factorial, Fibonacci, sum of digits and power, each recursively. Draw the call stack for factorial(4) on paper.                               | Your drawing matches the program's output.                                                                               |
| 17  | Debugging and checking: reading compiler errors and warnings (-Wall -Wextra), assert, and a first unit test with Catch2 or GoogleTest.                                    | Take 5 programs you wrote, add 1 deliberate mistake to each, and find it using only error messages and std::cout. Add 5 tests to one project. | You found all 5 mistakes and the tests run with one command.                                                             |
| 18  | **Checkpoint 0** (3 to 4 hours).                                                                                                                                          | A contacts book: add, list, search and delete contacts, saved to a file. Use a struct, a vector, functions, multiple files and file I/O.      | It works after you close and re-open it. Then, from memory in 30 minutes: FizzBuzz, reverse a string, check for a prime. |

## Part 2 (weeks 4-5): memory and the machine

By the end of week 5 you can explain where every byte of a C++ program lives and read the assembly of a small function. From now on, compile with -fsanitize=address,undefined: AddressSanitizer and UndefinedBehaviorSanitizer find memory mistakes while the program runs.

### Week 4: bits, pointers, the heap and the stack

| Day | Start here (learn)                                                                                                                                                  | Build                                                                                                                                                                                                                  | Done when                                                                         |
|-----|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|
| 19  | Binary, hexadecimal and the bitwise operators (& \| ^ ~ \<\< \>\>). learncpp's bit manipulation chapter.                                                            | bitflags.h: set, clear, toggle, test on a uint32_t. Pack 8 entity flags (grounded, poisoned, ...) into one byte. Extract version, header length and TTL from a hand-written 20-byte IPv4 header with shifts and masks. | Assert-based tests pass, including bit 0 and bit 31.                              |
| 20  | Pointers: address-of (&), dereference (\*), nullptr, pointer arithmetic, pointer against reference. learncpp chapter 12 (pointers) and chapter 17 (C-style arrays). | Swap two ints through pointers. Walk an array with pointer arithmetic. Print the address of every variable and draw them.                                                                                              | You predict the output of 5 pointer snippets before running them, and get 5 of 5. |
| 21  | The stack and the heap: new, delete, new\[\], delete\[\], leaks. learncpp chapter 19.                                                                               | An array of n ints on the heap. A growable int array with new\[\] that doubles its size. A matrix stored as one flat heap array with index = row \* cols + col, with a naive multiply timed at 512x512.                | ASan and Valgrind report no leaks and no errors.                                  |
| 22  | How to read an AddressSanitizer report.                                                                                                                             | Write 6 tiny buggy programs: use-after-free, double free, heap overflow, stack overflow, uninitialized read, off-by-one. Run each under ASan.                                                                          | For each one, a one-line note: what the report says and which line is the cause.  |
| 23  | A GDB tutorial: break, run, next, step, bt, print, x, info frame.                                                                                                   | Step through your recursive factorial in GDB and draw the stack for depth 4 on paper.                                                                                                                                  | Your drawing matches info frame and bt for depth 4.                               |
| 24  | Project session, then review.                                                                                                                                       | Project: hexdump. Read a file in binary chunks with std::ifstream and print offset, hex bytes and ASCII, like xxd. Take the file name from argv.                                                                       | diff against xxd output is empty on 3 test files (empty, 1 byte, 1 MB).           |

### Week 5: layout, assembly, callbacks and binary files

| Day | Start here (learn)                                                                       | Build                                                                                                                                                                                                                                | Done when                                                                                                                                                                                        |
|-----|------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 25  | Struct layout: sizeof, alignof, padding, alignas, offsetof. CS:APP 3.9 (data alignment). | Print sizeof and offsetof for 5 structs. Reorder the fields of one to remove padding. Make a Vertex (position, normal, uv).                                                                                                          | A table of padding bytes before and after reordering.                                                                                                                                            |
| 26  | CS:APP 3.1-3.7 (registers, mov, lea, call, ret, stack frames). Open Compiler Explorer.   | Write 5 small functions. Compare -O0 and -O2 assembly. Annotate each line of one function in comments.                                                                                                                               | You can explain every line of a 15-line function's assembly out loud.                                                                                                                            |
| 27  | Function pointers, std::function and lambdas. learncpp chapter 20.                       | Sort entities by distance with std::sort and a lambda. Build a state machine with a table of function pointers.                                                                                                                      | Both work with no warnings.                                                                                                                                                                      |
| 28  | Binary file I/O, fixed-width types (\<cstdint\>), byte order (endianness).               | Design a binary file format: magic bytes, version, record count, then records with fixed-width fields. Write a writer and a reader.                                                                                                  | A round-trip test passes and your hexdump shows your magic bytes.                                                                                                                                |
| 29  | Why unchecked copies are dangerous. CS:APP 3.10 for context. Work inside a VM.           | In your own toy program, a 16-byte char buffer sits next to an authenticated flag. Overflow it with a long input and watch the flag flip in GDB. Then fix it with std::string or std::span, and compile with the stack protector on. | The flaw is reproduced, then the fix resists the same input, and you can explain what a canary is.                                                                                               |
| 30  | **Checkpoint 1** (4 hours, from a blank file).                                           | Build cdump: read your day-28 binary format, validate every length with bounds checks, store records in a std::unordered_map, print statistics.                                                                                      | Zero warnings, ASan and UBSan clean, tag checkpoint-1 in Git. Then answer in writing: stack vs heap, why padding exists, what ret does, what use-after-free is, why an unchecked copy is unsafe. |

## Part 3 (weeks 6-10): core C++

By the end of week 10 you write C++ that owns its memory through objects, never through bare new and delete, and you understand the standard library well enough to rebuild parts of it. From now on, the project session has three flavours (Game, Cyber, AI/ML): build the one matching your main goal and read the other two.

### Week 6: classes and ownership

| Day | Start here (learn)                                                               | Build                                                                                                                                     | Done when                                                 |
|-----|----------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------|
| 31  | learncpp chapters 14-15 (classes, constructors, destructors, initializer lists). | A Buffer class that owns heap memory with raw new\[\] and delete\[\]. Log every constructor and destructor call.                          | The destructor runs at scope exit and ASan is clean.      |
| 32  | learncpp chapter 21 (operator overloading).                                      | Vec2 and Vec3 classes with +, -, \* by scalar, dot, length. Pass by const &.                                                              | 10 tests pass and the code has no needless copies.        |
| 33  | Copy constructor, copy assignment, the rule of three.                            | First show the double free that the default shallow copy causes. Then add a deep copy constructor and assignment to Buffer.               | ASan flags the bug before the fix and is silent after it. |
| 34  | learncpp chapter 22 (move semantics, 22.1-22.5).                                 | Add move constructor and move assignment to Buffer. Count copies and moves with a logger. Return a Buffer from a factory function.        | The logger shows zero copies in the factory.              |
| 35  | learncpp chapter 22 (smart pointers). The rule of zero.                          | Rewrite Buffer with std::unique_ptr\<uint8_t\[\]\>. Write FileHandle, an RAII wrapper for a file descriptor.                              | There is no manual delete or close left in the code.      |
| 36  | Project session, then review.                                                    | Pick one: Game AssetCache (shared_ptr plus weak_ptr); Cyber MappedFile (RAII around mmap); AI/ML AlignedBuffer (64-byte aligned storage). | 12 tests pass, no leaks, no raw new or delete.            |

### Week 7: errors, inheritance and vtables

| Day | Start here (learn)                                                                     | Build                                                                                                                                                                                      | Done when                                                                                                                                                                                     |
|-----|----------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 37  | learncpp chapters 9 and 27 (error handling, exceptions). noexcept and std::optional.   | A binary-file parser that reports errors with exceptions and std::optional. Throw in the middle of parsing on purpose.                                                                     | ASan shows no leaks and the file handle closes when an exception passes through.                                                                                                              |
| 38  | learncpp chapter 24 (inheritance, access, construction order).                         | An Entity base with Player and Enemy derived classes. Print constructor and destructor order.                                                                                              | You predict the printed order before running.                                                                                                                                                 |
| 39  | learncpp chapter 25 (virtual functions, override, pure virtual, virtual destructors).  | Add a virtual update() and loop over std::vector\<std::unique_ptr\<Entity\>\>. Remove the virtual destructor to see the leak. Cause object slicing on purpose.                             | UBSan and ASan are clean with the fixed version, and you can explain slicing.                                                                                                                 |
| 40  | Compiler Explorer: compile a class with a virtual function and find the indirect call. | Re-implement a vtable by hand with a struct of function pointers and compare it with the compiler's assembly.                                                                              | An annotated listing shows the vptr load and the indirect call. You can explain why overwriting a vptr would give control of execution, and why final and compiler hardening reduce the risk. |
| 41  | Game Programming Patterns, "Component" chapter.                                        | A Layer interface with Dense and ReLU implementations and a forward() function. Check sizeof with and without virtual functions. Then refactor Entity into components held by composition. | A 3-line note: when inheritance wins, when composition wins.                                                                                                                                  |
| 42  | Project session, then review.                                                          | Pick one: Game scene of 1,000 entities; Cyber PacketHandler hierarchy parsing TCP, UDP and ICMP from byte buffers with bounds-checked reads; AI/ML Model made of Layer objects.            | 15 tests pass, and the run is clean under ASan and Valgrind.                                                                                                                                  |

### Week 8: templates and generic code

| Day | Start here (learn)                                                   | Build                                                                                                                                                                  | Done when                                                     |
|-----|----------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------|
| 43  | learncpp chapters 11 and 26 (function and class templates).          | clamp\<T\>, Stack\<T\>, Array\<T, N\>.                                                                                                                                 | They work with int, float and one of your structs.            |
| 44  | cppreference: concepts. Learn non-type parameters and static_assert. | Constrain Stack\<T\> and a dot() function with std::floating_point and your own concept.                                                                               | A wrong type gives a short, readable compile error.           |
| 45  | learncpp chapter 18 (iterators).                                     | Give your container begin() and end() with a real iterator class.                                                                                                      | std::sort and std::accumulate run on it.                      |
| 46  | NumPy or Eigen docs on shape and strides, for the idea only.         | Tensor\<T\>: shape, strides, storage in std::vector\<T\>, indexing with operator().                                                                                    | It works for float, double and int8_t, with tests.            |
| 47  | The idea of a view: a transpose can reuse the same data.             | Element-wise ops, matmul, reshape, and a zero-copy transpose by swapping strides.                                                                                      | matmul equals your day-21 matrix multiply on the same inputs. |
| 48  | Project session, then review.                                        | mini-core library: Vec2/3/4 and Mat4 (Game), Tensor\<T\> (AI/ML), and ByteReader with read_u16_be, read_u32_be and bounds checks (Cyber). Build all three small parts. | All three have tests and a timing printed with std::chrono.   |

### Week 9: modern C++

| Day | Start here (learn)                                                                                                                | Build                                                                                                 | Done when                                                       |
|-----|-----------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------|
| 49  | learncpp chapter 20 (lambdas) and cppreference \<algorithm\>.                                                                     | Process a vector\<Entity\> using only algorithms and lambdas: transform, find_if, erase-remove.       | No hand-written for loop is left in that file.                  |
| 50  | cppreference: std::span, std::ranges, std::views, std::string_view.                                                               | Change ByteReader to take std::span\<const std::byte\>. Add one range pipeline.                       | No pointer-plus-length pairs remain in your APIs.               |
| 51  | cppreference: std::variant, std::optional, structured bindings, constexpr.                                                        | Model a packet as a std::variant of TCP, UDP and ICMP. Make parse() return a result type.             | Every branch is handled with std::visit and a test covers each. |
| 52  | GitHub Actions docs: build and test a CMake project.                                                                              | A workflow that builds and runs tests with ASan and UBSan on every push.                              | The workflow runs green on GitHub.                              |
| 53  | C++ Core Guidelines: sections P (philosophy), R (resources), ES (expressions). clang-tidy modernize and cppcoreguidelines checks. | Fix the top 20 clang-tidy findings across your repo.                                                  | The finding count drops and tests still pass.                   |
| 54  | Project session, then review.                                                                                                     | Extend your parser or mini-core with a result type, std::span inputs and a fuzz-ready entry function. | 20 tests pass, ASan and UBSan clean.                            |

### Week 10: rebuild what the STL does, and Checkpoint 2

| Day | Start here (learn)                                                                                                       | Build                                                                                                                                                                                           | Done when                                                                                                                                                                                                                                        |
|-----|--------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 55  | How std::vector works: capacity, reallocation, iterator invalidation.                                                    | MyVector\<T\> with the rule of five.                                                                                                                                                            | It works with int and std::string, with tests, ASan clean.                                                                                                                                                                                       |
| 56  | How hash tables work: hashing, buckets, collisions, resizing.                                                            | MyHashMap\<K, V\> with chaining.                                                                                                                                                                | 10,000 inserts and lookups give the same answers as std::unordered_map.                                                                                                                                                                          |
| 57  | Move-only types.                                                                                                         | MyUnique\<T\>, a tiny copy of std::unique_ptr.                                                                                                                                                  | Moving works, copying does not compile, and nothing leaks.                                                                                                                                                                                       |
| 58  | Benchmarking basics: std::chrono, warm-up, stopping the optimizer from deleting your test. Google Benchmark quick-start. | Benchmark MyVector against std::vector, and MyHashMap against std::unordered_map.                                                                                                               | A table of timings and one sentence on why the standard library is faster or slower.                                                                                                                                                             |
| 59  | Review day. Redo anything from weeks 6-9 you could not do from memory.                                                   | Write a one-page summary: the rule of zero, five and three; what a vtable is; what std::move does.                                                                                              | You can explain each point out loud without notes.                                                                                                                                                                                               |
| 60  | **Checkpoint 2** (4 hours, from a blank file).                                                                           | Pick one: Game mini-ECS with 10,000 entities and a movement system; Cyber binary-packet parser library with a fuzz-ready entry function; AI/ML Tensor\<float\> with a 2-layer MLP forward pass. | RAII only, 15 or more tests, zero warnings, ASan and UBSan clean, README, tag checkpoint-2. Then answer in writing: rule of zero vs five, what is in a vtable, what std::move does, why destructors are virtual, templates vs virtual functions. |

## Part 4 (weeks 11-13): performance, concurrency and networking

By the end of week 13 you can measure a program, find its bottleneck, and make it several times faster with allocators, data layout, threads and SIMD (doing the same operation on several numbers at once). This is the part that makes your C++ useful for game engines, fast tensor code and security tooling. Every claim you make here must come from a measurement saved in your journal.

### Week 11: memory, cache, profiling and allocators

| Day | Start here (learn)                                                          | Build                                                                                                                                                | Done when                                                                                                    |
|-----|-----------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| 61  | CS:APP chapter 6.1-6.5 (the memory hierarchy).                              | Benchmark row-major against column-major traversal of a 4096x4096 array. Benchmark array-of-structs against struct-of-arrays when summing one field. | A table of times, and a note explaining each gap with the 64-byte cache line.                                |
| 62  | perf (Linux) or Instruments (macOS), and valgrind --tool=callgrind.         | Profile your day-21 matrix multiply and find the hot loop.                                                                                           | You can name the top 3 functions by time and the line that dominates.                                        |
| 63  | Search for "bump allocator" and alignment rounding: (p + a - 1) & ~(a - 1). | An Arena with alloc(size, align) and reset().                                                                                                        | Every returned pointer is aligned, and 1 million small allocations are faster than new (record the numbers). |
| 64  | Free-list pool allocators. cppreference: placement new.                     | Pool\<T\> with a free list, acquire() and release().                                                                                                 | 1 million acquire/release cycles run with no leak and a stable time.                                         |
| 65  | Mike Acton, "Data-Oriented Design and C++" (CppCon 2014 talk).              | Rewrite your Checkpoint 2 project's storage as struct-of-arrays. Benchmark 100,000 entities.                                                         | The speedup against the old layout is measured and written down.                                             |
| 66  | Project session, then review.                                               | memlab: your allocators, a small benchmark harness and a README with a results table. Add a counting operator new that reports leaks.                | The README shows new vs arena vs pool timings, reproducible with one command.                                |

### Week 12: concurrency

| Day | Start here (learn)                                                                                      | Build                                                                                                                                                                                                       | Done when                                                                            |
|-----|---------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|
| 67  | cppreference: std::thread. C++ Concurrency in Action (Williams), chapters 2-3.                          | Sum 100 million integers across N threads. Then write an unsynchronized shared counter on purpose.                                                                                                          | ThreadSanitizer (-fsanitize=thread) reports the race and the fixed version is clean. |
| 68  | std::mutex, std::scoped_lock, std::condition_variable. Learn the four deadlock conditions.              | A bounded blocking queue.                                                                                                                                                                                   | 4 producers and 4 consumers move 1 million items with a clean TSan run.              |
| 69  | std::atomic. Start with the default sequentially-consistent ordering, then one acquire/release example. | A lock-free counter and a spinlock. Compare them with a mutex.                                                                                                                                              | A benchmark table, and you can explain why the atomic is faster or slower here.      |
| 70  | std::future, std::async, std::jthread.                                                                  | A ThreadPool that returns futures. Use it to compute matrix rows in parallel.                                                                                                                               | The speedup on your core count is measured and written down.                         |
| 71  | Search for "false sharing" and alignas(64).                                                             | Two counters on adjacent cache lines, then separated by padding. Time both.                                                                                                                                 | The measured difference is recorded and you can draw the cache-line picture.         |
| 72  | Project session, then review.                                                                           | jobsys: worker threads running a graph of jobs with dependencies. Use it for one real task: per-frame jobs (Game), parallel batches (AI/ML), or a parallel scan of many files for a byte signature (Cyber). | TSan clean, results correct, speedup measured at 4 or more threads.                  |

### Week 13: SIMD, optimization, networking and Checkpoint 3

| Day | Start here (learn)                                                                       | Build                                                                                                                            | Done when                                                                                                                                                                    |
|-----|------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 73  | What SIMD is. Compiler Explorer with -O3 -march=native and GCC's -fopt-info-vec.         | Write dot product and saxpy loops. Check whether the compiler vectorized them.                                                   | You can point at vector instructions in the assembly.                                                                                                                        |
| 74  | Intel Intrinsics Guide (immintrin.h). On Apple Silicon, the Arm NEON intrinsics instead. | An AVX2 (or NEON) dot product with a scalar loop for the leftover elements. Check CPU support at runtime.                        | Matches the scalar result within a small epsilon and is faster.                                                                                                              |
| 75  | Algorithmica "Algorithms for Modern Hardware", the matrix multiplication chapter.        | Matmul in five steps: naive, loop reorder, tiling, SIMD, threads. Measure GFLOPS at each step on 1024x1024.                      | A table of all five steps, and the final version is at least 5x faster than naive.                                                                                           |
| 76  | Beej's Guide to Network Programming: sockets, bind, listen, accept, send, recv.          | A TCP echo server and client in C++ with an RAII Socket class. Handle partial reads and writes.                                  | 100 clients in a row work with no leaked descriptors.                                                                                                                        |
| 77  | libFuzzer docs (-fsanitize=fuzzer,address).                                              | Write a length-prefixed message parser with a deliberate bug. Write a fuzz target and let libFuzzer find the crash. Then fix it. | libFuzzer finds the crash, you save the crashing input, and 5 minutes of fuzzing after the fix finds nothing.                                                                |
| 78  | **Checkpoint 3** (4 hours).                                                              | Deliver three things: allocators with benchmarks, a TSan-clean thread pool, and a matmul at least 5x faster than naive.          | All three tagged checkpoint-3. Then answer in writing: what a cache line is, what false sharing is, why struct-of-arrays can be faster, what TSan finds, what a fuzzer does. |

## Part 5 (weeks 14-17): bridge week, then one primary track

Week 14 gives you a small taste of all three fields so you can choose with evidence. Weeks 15-17 (days 85-102) are one deep capstone in the field you choose. Choose by asking: which of the three projects would you most want to show someone? Do you own an NVIDIA GPU (only needed for the optional CUDA extension)? Which field do you want to work in first? You can do the other two tracks later with the same core.

### Week 14: bridge week (two days per field)

| Day | Start here (learn)                                                                               | Build                                                                                                     | Done when                                                                              |
|-----|--------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------|
| 79  | raylib quick-start and its examples. Game Programming Patterns, "Game Loop" chapter.             | A window with a moving player, keyboard input and delta time.                                             | The loop runs at a steady 60 frames per second.                                        |
| 80  | Same chapter: fixed timestep.                                                                    | Add 500 entities that bounce, stored in the Pool from day 64.                                             | Frame time stays flat as entities spawn and die.                                       |
| 81  | 3Blue1Brown neural network videos (the first two) for intuition.                                 | A 2-layer neural network forward pass using your Tensor\<float\>.                                         | Output shapes are right and results match a NumPy version on the same weights.         |
| 82  | Backpropagation for a dense layer, on paper first.                                               | Add backward pass and gradient descent. Train on a toy dataset such as XOR or two spirals.                | Loss falls steadily and accuracy is above 95 percent on the toy set.                   |
| 83  | The ELF file format overview (man page elf(5)). Run readelf -h and readelf -S on a small binary. | Parse an ELF64 header and its section table from raw bytes with your ByteReader. Bounds-check every read. | Your output matches readelf on 3 binaries. Truncated files give an error, not a crash. |
| 84  | Project session. Choose your primary track.                                                      | Write your track decision in journal.md with three reasons, then draft the capstone scope in one page.    | A one-page capstone plan with 5 measurable goals.                                      |

### Track A: Game development (days 85-102)

Capstone: a 2D game or engine demo with 5,000 live entities at 60 frames per second, built on your own ECS and allocators. Days 85-90 are week 15, days 91-96 are week 16, days 97-102 are week 17.

| Day    | Start here (learn)                                                     | Build                                                                                        | Done when                                                                  |
|--------|------------------------------------------------------------------------|----------------------------------------------------------------------------------------------|----------------------------------------------------------------------------|
| 85     | Game Programming Patterns, "Data Locality" chapter.                    | Sparse-set or archetype ECS: create, destroy, add and remove components.                     | 10,000 entities update in under 1 ms on your machine, or you know why not. |
| 86     | Same, systems and queries.                                             | Movement, lifetime and render systems that iterate component arrays.                         | Systems never chase pointers; the profile shows linear access.             |
| 87     | Search for "spatial hash grid" collision.                              | A spatial hash for broad-phase collision, then circle and box narrow-phase.                  | 5,000 entities collide with no frame above 16 ms.                          |
| 88     | raylib textures, sounds and audio.                                     | An asset manager with handles and shared_ptr caching.                                        | Loading the same asset twice reuses it.                                    |
| 89     | Game Programming Patterns, "State" and "Command" chapters.             | Player state machine and an input command queue.                                             | Replaying a recorded command list reproduces the same run.                 |
| 90     | Project session, then review.                                          | Playable vertical slice: player, enemies, collision, score.                                  | 3 friends can play it for 5 minutes without a crash.                       |
| 91     | Your jobsys from day 72.                                               | Run the update systems on worker threads.                                                    | Frame time improves and TSan is clean.                                     |
| 92     | Your allocators from days 63-64.                                       | Per-frame arena for temporary data, pool for bullets and particles.                          | Zero heap allocations per frame, checked with a counting operator new.     |
| 93     | Search for "A star pathfinding".                                       | A\* on a grid with a binary heap.                                                            | 100 agents path-find without exceeding the frame budget.                   |
| 94     | LearnOpenGL, the "Getting started" chapters (optional rendering path). | Optional: draw a textured quad with OpenGL, or batch sprites in raylib.                      | Draw calls are batched and the count is displayed.                         |
| 95     | Tracy profiler or perf.                                                | Profile a full frame and fix the biggest cost.                                               | The before-and-after frame times are in the README.                        |
| 96     | Project session, then review.                                          | Add levels loaded from your own binary format, with a validating loader.                     | A corrupt level file is rejected cleanly.                                  |
| 97-101 | The polish list from your capstone plan.                               | One goal per day: balance, sound, menu, save and load, build for a second OS or WebAssembly. | Each day ends with a tagged commit.                                        |
| 102    | **Final capstone review.**                                             | Record a 2-minute demo video, finish the README with benchmarks, tag v1.0.                   | A stranger can build and run it from the README in 10 minutes.             |

### Track B: AI/ML systems (days 85-102)

Capstone: a neural network trained and run in C++ with your own tensor library, with a fast matmul and an int8 inference path. Dataset: MNIST handwritten digits, which you download yourself.

| Day    | Start here (learn)                                                                                                                          | Build                                                                        | Done when                                                    |
|--------|---------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------|--------------------------------------------------------------|
| 85     | Karpathy's llm.c repository (read the README and the C training loop).                                                                      | Load MNIST files (IDX format) into Tensor\<float\> with a validating reader. | The first 10 images print as ASCII and match the labels.     |
| 86     | Softmax and cross-entropy loss.                                                                                                             | Implement them with a numerically stable softmax.                            | A gradient check against finite differences passes.          |
| 87     | Backprop derivation for dense layers.                                                                                                       | Dense layer with forward and backward using your matmul.                     | A gradient check passes on a small layer.                    |
| 88     | SGD and mini-batches.                                                                                                                       | A training loop with mini-batches and shuffled data.                         | Training loss decreases over 5 epochs.                       |
| 89     | Weight initialization. Learning-rate choices.                                                                                               | Tune until the MLP reaches about 97 percent test accuracy.                   | Test accuracy is printed and saved.                          |
| 90     | Project session, then review.                                                                                                               | Save and load model weights in your own binary format.                       | A reloaded model gives identical predictions.                |
| 91     | Your day-75 matmul.                                                                                                                         | Plug the SIMD and threaded matmul into Dense.                                | Training is at least 3x faster than the naive version.       |
| 92     | Memory reuse in training.                                                                                                                   | Preallocate activations and gradients in an arena.                           | Allocations per training step drop to zero.                  |
| 93     | Quantization overview, int8 symmetric scheme.                                                                                               | Quantize weights to int8_t with a per-layer scale.                           | The quantization error per layer is printed.                 |
| 94     | Integer matmul with int32 accumulation.                                                                                                     | An int8 inference path.                                                      | Accuracy drops by less than 1 point and inference is faster. |
| 95     | Profiling with perf.                                                                                                                        | Find and fix the top cost in inference.                                      | Before-and-after timings in the README.                      |
| 96     | Project session, then review.                                                                                                               | Add a command-line tool: train, eval, predict image.pgm.                     | It works from a clean clone with a single build command.     |
| 97-101 | Choose one: libtorch or ONNX Runtime C++ API; a tiny attention layer; or CUDA with the NVIDIA CUDA programming guide (needs an NVIDIA GPU). | One extension, built over 5 days, compared against your CPU version.         | A table of speed and accuracy against your baseline.         |
| 102    | **Final capstone review.**                                                                                                                  | README with charts, benchmarks and a design note, tag v1.0.                  | A stranger can reproduce your accuracy number.               |

### Track C: Cybersecurity, defensive and analysis (days 85-102)

Capstone: binscan, a command-line static analysis tool that parses binary files safely, reports risky constructs and ships with a fuzzed parser. This track builds the skills used in malware analysis, vulnerability research and secure development. Work only on your own files, public samples and legal practice platforms.

| Day    | Start here (learn)                                                                                          | Build                                                                                                | Done when                                                                      |
|--------|-------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------|
| 85     | elf(5) man page. Your day-83 parser.                                                                        | Extend the ELF parser to program headers, symbols and imported functions.                            | Output matches readelf and nm on 5 binaries.                                   |
| 86     | String extraction and entropy.                                                                              | Print printable strings and compute entropy per section.                                             | High-entropy sections are flagged on a packed sample you create yourself.      |
| 87     | The Capstone disassembly library docs.                                                                      | Disassemble .text with Capstone and print the first 100 instructions.                                | Matches objdump -d for the same range.                                         |
| 88     | Lists of unsafe C functions (gets, strcpy, sprintf) and CERT C rules.                                       | Detect calls to unsafe imported functions in a binary.                                               | You flag known-unsafe functions in your own day-22 buggy programs.             |
| 89     | Hardening flags: stack protector, PIE, RELRO, NX.                                                           | Report which protections a binary has, as checksec does.                                             | Matches checksec or readelf on 5 binaries.                                     |
| 90     | Project session, then review.                                                                               | Combine the above into one CLI with JSON output and exit codes.                                      | 20 tests pass, including truncated and malformed files that must not crash.    |
| 91     | Your libFuzzer notes from day 77.                                                                           | Write fuzz targets for your ELF parser and ByteReader.                                               | The fuzzer runs 10 minutes with ASan and finds nothing, or finds bugs you fix. |
| 92     | Seed corpora and coverage reports.                                                                          | Build a seed corpus and view coverage with llvm-cov.                                                 | Coverage of parser code is above 80 percent.                                   |
| 93     | libpcap and the pcap file format.                                                                           | A reader for .pcap files you capture on your own network, parsing Ethernet, IP, TCP and UDP headers. | Packet counts match Wireshark on the same capture.                             |
| 94     | Bounds-checking patterns and std::span.                                                                     | Make every parser read go through a checked reader.                                                  | A review shows no unchecked pointer arithmetic left.                           |
| 95     | Ghidra (free) introduction.                                                                                 | Open one of your own binaries in Ghidra and compare its view with your tool's output.                | A short note on three things Ghidra finds that your tool does not.             |
| 96     | Project session, then review.                                                                               | Add a signature rule engine: byte patterns with wildcards, loaded from a file, scanned with threads. | Scans a 100 MB file correctly and you have a measured time.                    |
| 97-101 | pwn.college or OverTheWire (legal practice sites) for guided reverse-engineering and secure-coding modules. | Work through modules on reverse engineering and memory-safety defenses. Write up each one.           | 5 written solutions in your repo.                                              |
| 102    | **Final capstone review.**                                                                                  | README with usage, a threat model and fuzzing results, tag v1.0.                                     | A stranger can build it and run it on a sample in 10 minutes.                  |

## Part 6 (weeks 18-23): build anything with C++

Parts 1-5 made you strong in the language and one specialization. This part makes you able to build almost any kind of C++ software: algorithms, desktop apps, command-line tools, servers, and well-designed, tested projects. Each topic starts from the basics. Days continue from 103.

### Week 18: algorithms and data structures with the STL

| Day | Start here (learn)                                                             | Build                                                                      | Done when                                                           |
|-----|--------------------------------------------------------------------------------|----------------------------------------------------------------------------|---------------------------------------------------------------------|
| 103 | Big-O and the complexity guarantees of STL containers on cppreference.         | Benchmark vector, list and deque for insert, search and iterate.           | A table of times, and a sentence on why vector usually wins.        |
| 104 | Sorting and searching: std::sort, binary_search, lower_bound.                  | Write a merge sort template and compare it with std::sort.                 | Correct on random, sorted, reversed and empty input.                |
| 105 | Trees, heaps and std::priority_queue. std::set and std::map as balanced trees. | A binary search tree template with insert, find and in-order traversal.    | Tests pass and ASan is clean.                                       |
| 106 | Graphs: adjacency lists, BFS, DFS, Dijkstra with priority_queue.               | Find the shortest route on a small map file.                               | It prints the correct route for 3 maps and says when there is none. |
| 107 | Dynamic programming: memoization, then tables.                                 | Solve the knapsack and longest-common-subsequence problems.                | Both match answers you worked out by hand on small cases.           |
| 108 | Project session, then review.                                                  | Solve 15 problems from the Exercism C++ track or similar, each with tests. | A log of each problem, your approach and its complexity.            |

### Week 19: desktop apps

| Day | Start here (learn)                                                                                                    | Build                                                                      | Done when                                                         |
|-----|-----------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------|-------------------------------------------------------------------|
| 109 | What a GUI framework is: widgets and the event loop. Install Qt and Qt Creator (check the open-source license terms). | A window with a button and a label.                                        | Clicking the button changes the label.                            |
| 110 | Layouts, and Qt's signals and slots.                                                                                  | A calculator interface.                                                    | The calculator gives correct answers and the window resizes well. |
| 111 | Lists, file dialogs and saving.                                                                                       | A notes app with a list, an editor and open and save dialogs.              | You can open, edit and save a file.                               |
| 112 | Keeping the interface responsive: do not block the UI thread. QtConcurrent or QThread.                                | A file search with a progress bar that runs in the background.             | The window stays responsive during a long search.                 |
| 113 | Packaging an app for another computer (the Qt deploy tools).                                                          | Make a build that runs on a computer without Qt installed.                 | A friend can run it.                                              |
| 114 | Project session, then review.                                                                                         | A desktop to-do or notes app that stores data in SQLite (Qt's SQL module). | Data survives restarting and the app is tested by someone else.   |

### Week 20: tools, libraries and package managers

| Day | Start here (learn)                                                                | Build                                                                                   | Done when                                                           |
|-----|-----------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|---------------------------------------------------------------------|
| 115 | CMake properly: targets, find_package, FetchContent, install.                     | A project with a library and an executable that use each other.                         | It builds and installs on a clean folder.                           |
| 116 | A package manager: vcpkg or Conan.                                                | Add fmt, spdlog and nlohmann/json to a project through the package manager.             | A fresh clone builds with one command.                              |
| 117 | JSON, command-line parsing (CLI11 or cxxopts) and logging.                        | A tasks command-line tool with subcommands, JSON storage and logging.                   | --help is clear and data survives restarts.                         |
| 118 | HTTP clients with libcurl or cpr.                                                 | A weather command-line tool using the free Open-Meteo API.                              | It works for 3 cities and handles no internet politely.             |
| 119 | Cross-platform code: std::filesystem, paths, line endings, Windows against Linux. | A tool that copies only changed files between two folders.                              | It works on your OS and the code has no hard-coded path separators. |
| 120 | Project session, then review.                                                     | Release your tool: README, install target and a GitHub Actions workflow that builds it. | A friend can download and run the build.                            |

### Week 21: networking and servers

| Day | Start here (learn)                                                                 | Build                                                             | Done when                                                   |
|-----|------------------------------------------------------------------------------------|-------------------------------------------------------------------|-------------------------------------------------------------|
| 121 | Asio basics: io_context and asynchronous operations.                               | An asynchronous timer that prints every second.                   | You can explain what runs when.                             |
| 122 | Asio TCP sockets.                                                                  | An asynchronous echo server and client.                           | 50 clients work at once on one thread.                      |
| 123 | Protocol design: framing, length prefixes, JSON, a first look at Protocol Buffers. | A chat protocol with length-prefixed JSON messages.               | A malformed message is rejected without a crash.            |
| 124 | A small HTTP server with cpp-httplib or Boost.Beast.                               | A REST service with /items create, read, update and delete.       | You can use it with curl.                                   |
| 125 | SQLite from C++: prepared statements and an RAII wrapper.                          | A small wrapper class and a migration step.                       | No statement is built by joining strings and nothing leaks. |
| 126 | Project session, then review.                                                      | A chat server and client with rooms and history stored in SQLite. | Clean under ASan and TSan with 10 clients.                  |

### Week 22: design and quality

| Day | Start here (learn)                                                                                                      | Build                                                                  | Done when                                                     |
|-----|-------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|---------------------------------------------------------------|
| 127 | SOLID principles and dependency injection in C++.                                                                       | Refactor the chat server so its parts depend on interfaces.            | You can swap the storage class without changing the rest.     |
| 128 | Design patterns in practice: Observer, Strategy, Factory, State, Command (Game Programming Patterns, Refactoring Guru). | Implement three of them in small examples.                             | You can say what problem each one solves.                     |
| 129 | Testing in depth: mocks with GoogleMock, coverage with gcov or llvm-cov.                                                | Raise one module to 80 percent line coverage.                          | The coverage report shows it.                                 |
| 130 | The debugging toolbox: core dumps, GDB in depth, sanitizers, logging.                                                   | Fix 3 bugs that someone else planted (or that you planted a week ago). | Each bug has a one-line root-cause note.                      |
| 131 | Continuous integration: GitHub Actions on Linux, Windows and macOS, plus clang-format and clang-tidy.                   | A workflow that builds and tests on two operating systems.             | It is green on both.                                          |
| 132 | Project session, then review.                                                                                           | Refactor and document the chat server, with a short architecture note. | A friend can find where any feature lives in under 5 minutes. |

### Week 23: capstone

| Day | Start here (learn)                                                                | Build                                                                                                                                                                    | Done when                                              |
|-----|-----------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------|
| 133 | Capstone planning. The "Build your own X" project list is a good source of ideas. | Choose any project you care about, such as a terminal text editor, a tiny database, a CHIP-8 emulator, a 2D renderer, a REST server or a Qt app. Write a one-page scope. | A scope with 5 measurable goals.                       |
| 134 | Build session 1.                                                                  | The data model and core logic with tests.                                                                                                                                | The core works and is tested.                          |
| 135 | Build session 2.                                                                  | The user interface or protocol.                                                                                                                                          | You can use the main feature end to end.               |
| 136 | Build session 3.                                                                  | Persistence, errors and logging.                                                                                                                                         | Bad input and failures are handled.                    |
| 137 | Build session 4.                                                                  | Polish, documentation and packaging.                                                                                                                                     | A build exists that a friend can run.                  |
| 138 | **Capstone review** (4 hours).                                                    | README, demo video, tests and a CI workflow, tag cpp-v2 in Git.                                                                                                          | A stranger can build it from the README in 10 minutes. |

## Checkpoints and what comes next

Five gates keep you honest. If you miss a gate, spend extra sessions on the missing piece before moving on; do not push ahead with a gap.

| Gate         | After   | You must have                                                                                                          | If you miss it                                        |
|--------------|---------|------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------|
| Checkpoint 0 | Day 18  | A contacts book that saves to a file, and FizzBuzz, string reverse and a prime check written from memory in 30 minutes | Repeat week 3 before starting week 4                  |
| Checkpoint 1 | Day 30  | cdump in C++, ASan and UBSan clean, written answers on stack, heap, padding, ret, unsafe copies                        | Redo the weakest week's project session               |
| Checkpoint 2 | Day 60  | A flavoured mini-project in RAII-only C++ with 15 or more tests                                                        | Add a week on classes and templates                   |
| Checkpoint 3 | Day 78  | Allocators, a TSan-clean thread pool, matmul 5x faster than naive                                                      | Repeat the matmul and thread-pool days                |
| Capstone     | Day 102 | Tagged v1.0, README, benchmarks, demo                                                                                  | Take extra sessions; shipping matters more than speed |

Gates for Part 6 (weeks 18-23):

- Day 108: a log of 15 solved problems with approaches and complexity.

- Day 114: a desktop app with SQLite that someone else has tested.

- Day 120: a command-line tool released with a README and a CI build.

- Day 126: a chat server and client, clean under ASan and TSan.

- Day 132: the refactored, documented chat server.

- Day 138: the capstone, tagged cpp-v2.

### Your portfolio at the end

- One Git repository with all 17 weeks, a daily journal and five tags.

- Three libraries you wrote: containers and allocators, tensor and math, parser and reader.

- One capstone with a README, benchmarks and a demo.

- Written answer sheets for the checkpoints, which also serve as interview preparation.

### After day 102

- Take a second track from Part 5 as a 4-week capstone. The shared core makes it much faster.

- Go deeper: Game Engine Architecture (Gregory) for games, Programming Massively Parallel Processors for GPU work, a binary-analysis book and Ghidra for security.

- Keep a 30-minute daily habit: one CppCon talk a week, and one pull request to an open-source C or C++ project per month.

- Keep reading code: raylib and small parts of llama.cpp are good, readable C and C++.

## Resources

These come from my own knowledge of well-known material, not pages I opened while writing, so check each link and edition before relying on it.

| Area        | Resource                                                                                                                                  | Cost |
|-------------|-------------------------------------------------------------------------------------------------------------------------------------------|------|
| C++ basics  | [learncpp.com](https://www.learncpp.com/)                                                                                                 | Free |
| C++         | [cppreference](https://en.cppreference.com/)                                                                                              | Free |
| C++         | [C++ Core Guidelines](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)                                                       | Free |
| C++         | Anthony Williams, C++ Concurrency in Action (book)                                                                                        | Paid |
| Machine     | Bryant and O'Hallaron, Computer Systems: A Programmer's Perspective (CS:APP), [site](https://csapp.cs.cmu.edu/)                           | Paid |
| Machine     | [Compiler Explorer](https://godbolt.org/)                                                                                                 | Free |
| Performance | [Algorithmica: Algorithms for Modern Hardware](https://en.algorithmica.org/hpc/)                                                          | Free |
| Performance | Mike Acton, "Data-Oriented Design and C++", CppCon 2014 (YouTube)                                                                         | Free |
| Networking  | [Beej's Guide to Network Programming](https://beej.us/guide/bgnet/)                                                                       | Free |
| Game        | [Game Programming Patterns](https://gameprogrammingpatterns.com/)                                                                         | Free |
| Game        | [raylib](https://www.raylib.com/) and [LearnOpenGL](https://learnopengl.com/)                                                             | Free |
| AI/ML       | [llm.c by Andrej Karpathy](https://github.com/karpathy/llm.c)                                                                             | Free |
| AI/ML       | 3Blue1Brown, neural networks series (YouTube)                                                                                             | Free |
| AI/ML       | Hwu and Kirk, Programming Massively Parallel Processors (book, for CUDA)                                                                  | Paid |
| Security    | [pwn.college](https://pwn.college/) and [OverTheWire](https://overthewire.org/wargames/) (legal practice sites)                           | Free |
| Security    | Ghidra, [ghidra-sre.org](https://ghidra-sre.org/)                                                                                         | Free |
| Tools       | [CMake tutorial](https://cmake.org/cmake/help/latest/guide/tutorial/index.html), AddressSanitizer, ThreadSanitizer, libFuzzer (LLVM docs) | Free |

Added for Part 6 (also from my own knowledge, so check the links):

| Topic      | Resource                                                                      | Cost                                       |
|------------|-------------------------------------------------------------------------------|--------------------------------------------|
| Algorithms | [Exercism C++ track](https://exercism.org/tracks/cpp)                         | Free                                       |
| Desktop    | [Qt documentation](https://doc.qt.io/)                                        | Free (check the open-source license terms) |
| Tools      | [vcpkg](https://vcpkg.io/)                                                    | Free                                       |
| Networking | [Asio](https://think-async.com/Asio/)                                         | Free                                       |
| Design     | [Refactoring Guru: design patterns](https://refactoring.guru/design-patterns) | Free                                       |
| Projects   | [Build Your Own X](https://github.com/codecrafters-io/build-your-own-x)       | Free                                       |
