# Python Roadmap: From Zero to Your Own AI Models

Oct 13, 2026 · @aarhvee

## Start here

This roadmap takes you from never having programmed to training your own neural network, and then to building almost any everyday software in Python (web services, databases, automation and tools): 10 weeks, 60 sessions, about 190 hours. No earlier programming is needed, and it does not depend on the C, C++ or C# roadmaps. All four roadmaps start on the same day (suggested: Monday 19 October 2026), and you choose which one to do on each day.

### How the sessions work

- A "Day" in the tables is one study session, not a calendar day. Do them in order, one roadmap day at a time, whenever you choose to work on Python.

- Sessions 1-5 of each week are about 3 hours. Session 6 is a 4-hour project session that ends with a review.

- Every session has the same shape, shown below. Stuck for 20 minutes? Write down what you expected and what happened, then search or ask.

| Time   | Block    | What you do                                                                                      |
|--------|----------|--------------------------------------------------------------------------------------------------|
| 10 min | Start    | Read yesterday's journal line "next first step". Retype a snippet from last session from memory. |
| 40 min | Learn    | Read or watch only the topic in the table. Notes in your own words.                              |
| 90 min | Build    | Write the exercise by hand. Type every line yourself; no copy-paste and no AI-written code.      |
| 30 min | Break it | Add a deliberate mistake, read the error message, fix it.                                        |
| 10 min | End      | Save, commit to Git, and write 3 lines: learned, confused, next first step.                      |

A session is done only when the program runs, you can explain it, and it is committed.

### Setup (about 45 minutes)

- Python 3.12 or newer from python.org, or in WSL2 (Windows' built-in Linux) with sudo apt install python3 python3-venv python3-pip. Native Windows Python also works fine for this roadmap.

- VS Code with the Python extension.

- Git, and a free GitHub account for your journal and projects.

- A free Google account for Google Colab, which gives you a GPU in the browser for the deep-learning weeks. You do not need your own GPU.

- One folder per week, and a journal.md file in it.

## The 24 sessions

The free spine is CS50P (Harvard's Python course), "Automate the Boring Stuff with Python", the official PyTorch tutorials and 3Blue1Brown for the maths. Resource names are in the last section.

### Week 1: Python basics

| Day | Start here (learn)                                                                                                          | Build                                                                                                                                                       | Done when                                                                                         |
|-----|-----------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
| 1   | What a program is. CS50P lecture 0, or "Automate the Boring Stuff" chapter 1. Install Python 3 and open the REPL (python3). | Print text with print(). Use the REPL as a calculator. Save and run hello.py.                                                                               | You can run a script and a REPL line, and say how they differ.                                    |
| 2   | Variables and data types: int, float, str, bool. Use type().                                                                | Store your name, age and height. Print them with f-strings. Convert a string to a number with int().                                                        | You can explain why "5" + "5" and 5 + 5 give different results.                                   |
| 3   | Operators (+ - \* / // % \*\*), input() and basic string methods.                                                           | A temperature converter that asks for Celsius and prints Fahrenheit. A program that asks for two numbers and prints sum, difference, product and remainder. | Both give correct answers for 5 inputs, including 0, and you can say what 7 // 2 and 7 / 2 print. |
| 4   | Conditions: if, elif, else, comparison operators, and, or, not. Python uses indentation instead of braces.                  | A grade calculator that reads a mark and prints a grade. A leap-year checker.                                                                               | You test every branch at least once.                                                              |
| 5   | Loops: for, while, range(), break, continue.                                                                                | Print the numbers 1 to 20. Print a multiplication table. Sum the digits of a number. FizzBuzz.                                                              | You can trace a loop by hand on paper and match the output.                                       |
| 6   | Project session, then review.                                                                                               | A number-guessing game: the program picks a random number, you guess, it says higher or lower and counts your attempts.                                     | The game works from start to finish and you wrote it without copying.                             |

### Week 2: building blocks and saving data

| Day | Start here (learn)                                                                       | Build                                                                                                                                       | Done when                                                                  |
|-----|------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------|
| 7   | Functions: parameters, return values, default arguments, scope.                          | is_even, max_of_three, power and is_prime as functions, each called from a test section.                                                    | Each function is tested with at least 3 inputs.                            |
| 8   | Lists and tuples: indexing, slicing, append, sort, looping over items.                   | A list of marks: sum, average, largest, smallest. Reverse a list two ways.                                                                  | You can explain what an off-by-one error is and you have none.             |
| 9   | Dictionaries and sets.                                                                   | A dictionary of names to phone numbers with lookup and delete. Remove duplicates from a list with a set.                                    | You know when to choose a list, a dict or a set.                           |
| 10  | Files and exceptions: open, with, try, except. JSON with the json module.                | Read a text file, count word frequencies, handle a missing file politely. Save a dictionary to a JSON file and load it back.                | A wrong file name prints a clear message instead of a crash.               |
| 11  | Modules and import. pip and virtual environments (python3 -m venv). List comprehensions. | Move your helper functions into utils.py and import them. Create a venv and install one package. Rewrite 3 of your loops as comprehensions. | Two files work together and you can say what a virtual environment is for. |
| 12  | Project session, then review.                                                            | An expense tracker in the terminal: add, list and total expenses, saved in a JSON file.                                                     | Data survives closing the program.                                         |

### Week 3: objects, data tools and the maths

| Day | Start here (learn)                                                                                                     | Build                                                                                                                   | Done when                                                                       |
|-----|------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------|
| 13  | Classes and objects: attributes, methods, \_\_init\_\_.                                                                | A BankAccount class with deposit, withdraw and a balance check that raises an error on overdraw.                        | Overdrawing raises and handles an error.                                        |
| 14  | NumPy: arrays, shapes, indexing, broadcasting. NumPy's "absolute beginners" guide.                                     | First do dot product and matrix multiply with plain Python lists, then repeat with NumPy and compare results and speed. | Both give the same answers and you have timed them.                             |
| 15  | pandas and Matplotlib: load a CSV, look at columns, make a line plot and a histogram.                                  | Download a small public dataset such as Iris, load it and plot two columns.                                             | You have 3 labelled plots saved as images.                                      |
| 16  | 3Blue1Brown, "Essence of Linear Algebra" (first 4 videos) and "Essence of Calculus" (first 3). Khan Academy as backup. | In NumPy: a dot product, a matrix-vector product, and the slope of x\*\*2 at a point estimated with a tiny step.        | You can explain in your own words what a vector, a matrix and a derivative are. |
| 17  | Linear regression and gradient descent (any beginner article or video).                                                | Fit a line to data with gradient descent in plain NumPy. Plot the loss falling.                                         | Your line closely matches numpy.polyfit.                                        |
| 18  | Project session, then review.                                                                                          | A mini data report: pick a public dataset, answer 3 questions with code and charts, in a Jupyter or Colab notebook.     | Someone else can run the notebook from top to bottom.                           |

### Week 4: PyTorch and your first models

| Day | Start here (learn)                                                                        | Build                                                                                                                                                                 | Done when                                                                                 |
|-----|-------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------|
| 19  | Classification: the sigmoid, loss, and the train, validation and test split. Overfitting. | A logistic regression classifier on a simple 2-class dataset, with accuracy printed.                                                                                  | Test accuracy is reported on data the model never trained on.                             |
| 20  | PyTorch tutorial, "Learn the Basics": tensors and autograd. Use Colab.                    | Do the tensor and autograd examples. Compute a gradient with .backward() and check it by hand.                                                                        | The autograd gradient equals your hand calculation.                                       |
| 21  | PyTorch tutorial: nn.Module, loss functions, optimizers and the training loop.            | Train a small neural network on a toy dataset with the standard loop.                                                                                                 | Loss decreases every epoch.                                                               |
| 22  | PyTorch tutorial: data loaders and the MNIST (or Fashion-MNIST) dataset.                  | An MNIST digit classifier in PyTorch, trained on a Colab GPU.                                                                                                         | Test accuracy is at least 97 percent for MNIST, or at least 85 percent for Fashion-MNIST. |
| 23  | Saving and loading models. Batches, learning rate and dropout.                            | Try 3 different settings of your own and write down what changed. Save the best model and load it in a fresh script.                                                  | A table of runs, and a saved model that predicts in a new script.                         |
| 24  | **Capstone** (4 hours, then review).                                                      | Train a model on data you collected yourself (for example photos of 3 objects, or a text file of names). Write a one-page report with a loss curve and test accuracy. | Reproducible from a README, tagged python-v1 in Git.                                      |

### Stretch sessions (optional, 6 more)

| Day | Start here (learn)                                                                 | Build                                                                           | Done when                                    |
|-----|------------------------------------------------------------------------------------|---------------------------------------------------------------------------------|----------------------------------------------|
| S1  | PyTorch tutorial on convolutional networks.                                        | A small CNN on Fashion-MNIST.                                                   | It beats your fully connected network.       |
| S2  | Learning-rate schedules and simple data augmentation.                              | Re-train the CNN with two improvements.                                         | A table of runs and their results.           |
| S3  | Andrej Karpathy, "Neural Networks: Zero to Hero", the micrograd video. Type along. | The tiny automatic-differentiation engine from the video.                       | It trains a tiny network from scratch.       |
| S4  | Karpathy, makemore video 1 (a character-level language model).                     | Follow along and generate new names from a list of names.                       | The model produces plausible new names.      |
| S5  | Hugging Face course, chapter 1.                                                    | Load a pre-trained model and run it on your own text or image.                  | You can explain what a pre-trained model is. |
| S6  | Project session.                                                                   | Your own idea: choose a dataset and a question, and train a model to answer it. | A short report, a saved model and a README.  |

## Part 2 (weeks 5-10): build almost anything with Python

Weeks 1-4 gave you Python and your first models. This part makes you able to build any everyday software: solve problems with algorithms, store data in a database, build web services, automate boring work, test and ship your code. Every topic starts from the basics. Days continue from 25. The stretch sessions above are optional and can be done at any point.

### Week 5: algorithms and data structures

| Day | Start here (learn)                                                          | Build                                                                                | Done when                                                    |
|-----|-----------------------------------------------------------------------------|--------------------------------------------------------------------------------------|--------------------------------------------------------------|
| 25  | Big-O: how running time grows with input size. Python's timeit module.      | Time linear search and binary search on lists of 1,000, 100,000 and 1,000,000 items. | A table of times, and you can say why one grows faster.      |
| 26  | Sorting: bubble, selection, insertion, merge and quick sort.                | Implement merge sort and quick sort. Compare them with sorted().                     | Correct on random, already-sorted, reversed and empty lists. |
| 27  | Stacks, queues and linked lists. collections.deque.                         | A Stack class, a Queue class and a balanced-brackets checker.                        | "(\[{}\])" passes and "(\[)\]" fails.                        |
| 28  | Hash tables in practice: dictionaries and sets used to solve problems fast. | Solve two-sum, group anagrams, and find the first repeated character.                | Each runs in linear time and passes your tests.              |
| 29  | Trees and recursion: binary search trees and traversals.                    | A binary search tree with insert, search and in-order print.                         | In-order output is sorted for 20 random inserts.             |
| 30  | Project session, then review. Graphs: BFS and DFS.                          | A maze solver: read a grid from a text file and print the shortest path with BFS.    | It solves 3 mazes and says so when there is no path.         |

### Week 6: SQL and databases

| Day | Start here (learn)                                                                                        | Build                                                                                                | Done when                                                                                       |
|-----|-----------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------|
| 31  | What a database is: tables, rows, columns. SQLBolt lessons 1-6. Install SQLite and DB Browser for SQLite. | Create a books table with 10 rows using CREATE TABLE, INSERT and SELECT.                             | You can query books by author and year.                                                         |
| 32  | WHERE, ORDER BY, LIMIT, COUNT, SUM, AVG, GROUP BY. SQLBolt lessons 7-12.                                  | Write 10 queries on a sample dataset, such as sales by month.                                        | Each query's answer matches a hand count on a small table.                                      |
| 33  | Relationships: primary keys, foreign keys, JOIN.                                                          | A students, courses and enrollments database. Write 5 queries that join them.                        | A query lists each student with their courses.                                                  |
| 34  | Python's sqlite3 module. Parameterized queries and why they stop SQL injection.                           | A command-line contacts app that stores data in SQLite.                                              | No query is built by joining strings, and a name like Bob'; DROP TABLE is stored as plain text. |
| 35  | Indexes and EXPLAIN QUERY PLAN. Backups.                                                                  | Insert 100,000 rows, time a lookup, add an index and time it again.                                  | You can show the speed difference and explain it.                                               |
| 36  | Project session, then review.                                                                             | Expense tracker v2: move your JSON data into SQLite and add reports (total per month, per category). | The reports match a manual total and old data was migrated.                                     |

### Week 7: the web and APIs

| Day | Start here (learn)                                                                                | Build                                                                                  | Done when                                                                      |
|-----|---------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------|--------------------------------------------------------------------------------|
| 37  | How the web works: URLs, HTTP methods, status codes, JSON. Browser developer tools (Network tab). | Use the requests library to call the free Open-Meteo weather API and print a forecast. | It works for 3 cities and handles no internet politely.                        |
| 38  | HTML and CSS basics: just enough for a page and a form. MDN Web Docs.                             | A static personal page with a form and some styling.                                   | It displays correctly in a browser and on a phone-width window.                |
| 39  | A first web API with FastAPI (or Flask): routes, path and query parameters, request models.       | A /todos API with create, read, update and delete, stored in memory.                   | You can use every endpoint from the automatic docs page.                       |
| 40  | Connect the API to SQLite. Validation and error responses.                                        | Make the todos persistent. Return clear errors for bad input.                          | Todos survive restarting the server.                                           |
| 41  | Authentication basics: hashing passwords (never store plain text), tokens, API keys.              | Register and log in users with hashed passwords and protect one endpoint.              | An unauthenticated request is refused and no password is stored in plain text. |
| 42  | Project session, then review. About 20 lines of JavaScript using fetch().                         | A notes app: your API plus a simple HTML page that lists, adds and deletes notes.      | It works in the browser with a login.                                          |

### Week 8: automation and everyday tools

| Day | Start here (learn)                                                                | Build                                                                               | Done when                                                     |
|-----|-----------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|---------------------------------------------------------------|
| 43  | Files and the operating system: pathlib, os, shutil, subprocess.                  | A file organizer that sorts a test folder by file type. Try it on a copy first.     | It sorts correctly and never overwrites a file.               |
| 44  | Command-line tools with argparse.                                                 | A tool with subcommands, for example notes add, notes list, notes delete.           | --help explains every command.                                |
| 45  | Web scraping, politely: requests, BeautifulSoup, robots.txt and rate limits.      | Scrape books.toscrape.com (a site made for practice) into a CSV file.               | The CSV has 100 rows and your scraper waits between requests. |
| 46  | CSV, JSON, YAML, Excel files (openpyxl) and regular expressions.                  | A log-file parser that uses regular expressions and prints a summary.               | It parses a 10,000-line log file correctly.                   |
| 47  | Running things on a schedule: cron, Windows Task Scheduler, the schedule library. | A daily report script that writes a summary file and shows a desktop notification.  | It runs by itself at a time you chose.                        |
| 48  | Project session, then review.                                                     | A personal automation toolkit with 3 tools, a README and a shared utilities module. | Someone else can install and run all 3 from the README.       |

### Week 9: quality and shipping

| Day | Start here (learn)                                                                                                          | Build                                                                              | Done when                                                              |
|-----|-----------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------|------------------------------------------------------------------------|
| 49  | Testing with pytest: fixtures, parametrized tests, coverage.                                                                | Write tests for your week-5 algorithms and your API.                               | At least 30 tests pass with 80 percent coverage on one module.         |
| 50  | Project layout and packaging: pyproject.toml, virtual environments, pip install -e.                                         | Package your CLI tool so pip install . gives a working command.                    | The command works from any folder.                                     |
| 51  | Git workflows: branches, pull requests, merge conflicts, .gitignore.                                                        | Create a conflict on purpose and resolve it. Open a pull request on your own repo. | The pull request is merged and the history is readable.                |
| 52  | Type hints, linting and formatting (mypy, ruff, black). Docstrings.                                                         | Add type hints to one project and fix what the tools report.                       | The type checker and linter report no errors.                          |
| 53  | Docker basics: images, containers, Dockerfile.                                                                              | Put your FastAPI app in a container.                                               | docker run starts it and you can use it from your browser.             |
| 54  | Deploying: environment variables, secrets, HTTPS. A free-tier host (for example Render or Railway; check what is free now). | Deploy your API.                                                                   | It works from your phone at a public address, and no secret is in Git. |

### Week 10: idiomatic Python and a capstone

| Day | Start here (learn)                                                                | Build                                                                                                                                                                                                    | Done when                                                                 |
|-----|-----------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------|
| 55  | asyncio, threads and processes: when to use which.                                | Download 20 pages one by one, with threads, and with asyncio. Compare the times.                                                                                                                         | A table of times and a one-line rule for choosing.                        |
| 56  | Decorators, generators, context managers and dataclasses.                         | A @timer decorator, a generator that reads a huge file lazily, and a dataclass model.                                                                                                                    | You can explain what each one does and when to use it.                    |
| 57  | Reading real code: pick a small open-source Python library and trace one feature. | Write one page of notes on how it is structured. Optionally fix a typo in its docs with a pull request.                                                                                                  | Your notes are clear enough for a friend to follow.                       |
| 58  | Capstone planning.                                                                | Choose one: (A) a full-stack app such as a habit tracker with login; (B) a data or automation tool; (C) a web service that serves your own model from week 4. Write the data model and a one-page scope. | A scope with 5 measurable goals.                                          |
| 59  | Capstone build (4 hours).                                                         | Build the core of your capstone with tests.                                                                                                                                                              | The core works and is tested.                                             |
| 60  | **Capstone** (4 hours, then review).                                              | Finish it, containerize it, write the README, and deploy it.                                                                                                                                             | A stranger can run it from the README, and it is tagged python-v2 in Git. |

## Checkpoints and what comes next

| Gate     | After  | You must have                                           | If you miss it                                              |
|----------|--------|---------------------------------------------------------|-------------------------------------------------------------|
| Basics   | Day 6  | The guessing game, written without copying              | Redo days 3-5 with new exercises                            |
| Tools    | Day 12 | An expense tracker that saves to JSON                   | Repeat days 10-11                                           |
| Data     | Day 18 | A notebook someone else can run top to bottom           | Repeat days 14-15                                           |
| Capstone | Day 24 | A model trained on your own data, README, tag python-v1 | Take a few extra sessions; shipping matters more than speed |

Gates for Part 2 (weeks 5-10):

- Day 30: a maze solver that finds shortest paths and reports when there is none.

- Day 36: the expense tracker on SQLite, with reports that match a manual total.

- Day 42: a notes app with an API, a login and a web page.

- Day 48: an automation toolkit someone else can install from your README.

- Day 54: an API deployed to a public address with no secret in Git.

- Day 60: the capstone, tagged python-v2. After it, keep building your own projects; that is where the remaining skill comes from.

After day 24: do the stretch sessions, then try a Kaggle beginner competition, or read the PyTorch documentation for the model type you want to build. If you also follow the C++ roadmap, its AI/ML track builds a small neural network by hand, which pairs well with what you did on days 16-22 here.

## Resources

These come from my own knowledge of well-known material, not pages I opened while writing, so check each link before relying on it.

| Topic  | Resource                                                                                        | Cost        |
|--------|-------------------------------------------------------------------------------------------------|-------------|
| Python | [CS50P, Harvard's Python course](https://cs50.harvard.edu/python/)                              | Free        |
| Python | [Automate the Boring Stuff with Python](https://automatetheboringstuff.com/)                    | Free online |
| Python | [The official Python tutorial](https://docs.python.org/3/tutorial/)                             | Free        |
| Data   | [NumPy: absolute beginners guide](https://numpy.org/doc/stable/user/absolute_beginners.html)    | Free        |
| Maths  | [3Blue1Brown](https://www.3blue1brown.com/): Essence of Linear Algebra and Calculus             | Free        |
| AI     | [PyTorch tutorials: Learn the Basics](https://pytorch.org/tutorials/beginner/basics/intro.html) | Free        |
| AI     | [Google Colab](https://colab.research.google.com/) (free GPU in the browser)                    | Free        |
| AI     | [Karpathy, Neural Networks: Zero to Hero](https://karpathy.ai/zero-to-hero.html)                | Free        |
| AI     | [Hugging Face course](https://huggingface.co/learn)                                             | Free        |

Added for Part 2 (also from my own knowledge, so check the links):

| Topic      | Resource                                                                                                                                          | Cost        |
|------------|---------------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| Algorithms | [Exercism Python track](https://exercism.org/tracks/python)                                                                                       | Free        |
| Algorithms | [Problem Solving with Algorithms and Data Structures using Python (Runestone)](https://runestone.academy/ns/books/published/pythonds3/index.html) | Free        |
| SQL        | [SQLBolt](https://sqlbolt.com/)                                                                                                                   | Free        |
| Web        | [MDN Web Docs](https://developer.mozilla.org/)                                                                                                    | Free        |
| Web        | [FastAPI documentation](https://fastapi.tiangolo.com/)                                                                                            | Free        |
| Tools      | [Real Python](https://realpython.com/) tutorials                                                                                                  | Mostly free |
| Tools      | [pytest documentation](https://docs.pytest.org/)                                                                                                  | Free        |
| Tools      | [Docker: Get started](https://docs.docker.com/get-started/)                                                                                       | Free        |
| Tools      | [The Missing Semester of Your CS Education (MIT)](https://missing.csail.mit.edu/)                                                                 | Free        |
| Practice   | [Scraping practice site](https://books.toscrape.com/)                                                                                             | Free        |
