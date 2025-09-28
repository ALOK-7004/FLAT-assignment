# FLAT ASSIGNMENT : A C++ Finite State Transducer Toolkit


This assignment is a C++ application developed for a Formal Languages and Automata Theory (FLAT) course. It utilizes the **OpenFST** library to build and demonstrate several finite-state transducers (FSTs) that perform various string manipulation tasks.

The application provides an interactive command-line interface to build, visualize, and run FSTs for tasks such as string reversal, case conversion, tokenization, and more.

## ✨ Features

* **String Reversal**: Reverses any given input string.
* **Case Conversion**: Converts any given string to uppercase.
* **Digit-to-Word**: Converts a string of digits into their word equivalents (e.g., "123" -> "one two three").
* **Vowel/Consonant Identifier**: Replaces each letter in a string with 'v' for a vowel or 'c' for a consonant.



## 🔧 Prerequisites

Before you begin, ensure you have the following installed on your system:
* An Ubuntu-based Linux distribution (tested on Ubuntu 24.04).
* A C++ compiler, such as `g++`.
* **Anaconda** or **Miniconda**: A Python distribution that includes `conda` for environment and package management.
* **Git** for cloning the repository.
* **Graphviz** for visualizing the FSTs.




  ## 🚀 Installation and Setup

Follow these steps to set up the environment and dependencies.

### 1. Clone the Repository
First, clone this repository to your local machine.

### 2. Set Up the Conda Environment
We will use a dedicated Conda environment to manage the OpenFST dependency.

**a. Create and activate the environment:**
```bash
conda create -n fstenv
conda activate fstenv



**b. Install OpenFST:**
This command installs the OpenFST library and its dependencies from the `conda-forge` channel.
```bash
conda install -c conda-forge openfst -y
```

**c. Install Graphviz:**
Graphviz is required to generate `.png` diagrams from the `.dot` files created by the application.
```bash
sudo apt update
sudo apt install graphviz -y


## 📁 Project Folder Structure


FLAT_assignment/
│
├── INCLUDE/      # Header files (.h) for the C++ source
├── SRC/          # C++ source files (.cpp)
├── BUILD/        # Compiled application binary and .fst files
└── DIAGRAMS/     # Generated .dot and .png diagrams of the FSTs



## 🛠️ Building and Running the Project

Make sure your `fstenv` Conda environment is active before proceeding. All commands below should be executed from the root of the `FLAT-assignment` directory.

### 1. Compile the Application
Run the following `g++` command from the root directory of the project. This command compiles all source files and links them against the OpenFST library installed in your Conda environment.

```bash
g++ -std=c++17 -I$CONDA_PREFIX/include -Iinclude -L$CONDA_PREFIX/lib src/*.cpp -lfst -o build/fst_app
```

### 2. Set the Library Path
The compiled application needs to know where to find the OpenFST shared libraries at runtime. Export the library path using this command:

```bash
export LD_LIBRARY_PATH=$CONDA_PREFIX/lib:$LD_LIBRARY_PATH
```
**Note:** You must run this command every time you open a new terminal session before running the application.

### 3. Run the Application
You can now execute the compiled program:

```bash
./build/fst_app
```

---

## 🕹️ Usage Examples

Once running, the application will present a menu of FST modules. Here are examples of each module in action.


### 1. String Reversal
```
Enter your choice (1-6) or 'q' to quit: 1
Enter input string: Biraj Kalita
🔁 Reversed string: atilaK jariB
```

### 2. Case Conversion
```
Enter your choice (1-6) or 'q' to quit: 2
Enter input string: Biraj Kalita
🔁 Case Conversion Output: BIRAJ KALITA
```

### 3. Digit to Word Converter
```
Enter your choice (1-6) or 'q' to quit: 3
Enter input string: 12345
🔁 Digit to Word Output: one two three four five 
```

### 4. Vowel/Consonant Identifier
```
Enter your choice (1-6) or 'q' to quit: 4
Enter input string: Biraj Kalita
🔁 Vowel-Consonant Output: C V C V C C C V C V C V 
```



# 🔬 Project Internals & Workflow

> *The following is a detailed breakdown of the project's internal architecture and execution flow. This section is intended for those curious about the implementation details (like instructors or fellow developers) and can be skipped for general usage.*

---

### 🧠 High-Level Overview

At its core, this project is a **modular C++ application** that demonstrates the principles of Finite State Transducers (FSTs). It is not a single, monolithic FST. Instead, it dynamically **builds a new, specialized FST in memory** for every single input string provided by the user.

The architecture is clean and separated:
* `main.cpp` acts as the **user interface** and **dispatcher**.
* Each of the other `.cpp` files in `src/` is a **specialized module** responsible for one specific task (e.g., `case_conversion.cpp`).
* `fst_utils.cpp` is a **shared helper** used by all modules to handle file I/O and diagram generation.



### ⚙️ Step-by-Step Execution Flow

When you run `./build/fst_app`, here is exactly what happens internally:

1.  **The Main Loop Starts (`main.cpp`)**: The program enters an infinite `while` loop. It prints the menu of options (1-6) and waits for user input using `std::getline`.

2.  **Task Dispatching (`main.cpp`)**: Based on the user's choice (e.g., "2" for Case Conversion), the `if-else if` block calls the corresponding function, passing the user's input string to it. For example, if the user chose "2" and typed "Hello", the code effectively runs `caseConversion("Hello");`.

3.  **Module Execution (e.g., `case_conversion.cpp`)**:
    * A new, empty `fst::StdVectorFst` object is created.
    * The code then iterates through each character of the input string ("H", "e", "l", "l", "o").
    * For each character, it creates a new state and adds an **arc** from the previous state to the new one. This arc defines the core logic of the transducer. For `caseConversion`, the arc for 'e' would have an input label of 'e' and an output label of 'E'. This creates a simple, linear chain of states that transforms the input string.
    * The final state in the chain is marked as the "accepting" state.

4.  **Artifact Generation (`fst_utils.cpp`)**: The module (e.g., `caseConversion`) now calls the `saveFSTArtifacts()` function. This is the crucial step for file creation, which is explained in detail in the next section.

5.  **Console Output**: The module calculates the final string in C++ (e.g., by converting "Hello" to "HELLO") and prints it to the console for the user to see.

6.  **Return to Main Loop**: Control returns to `main.cpp`, the "=== Done ===" message is printed, and the loop starts over by displaying the menu again.

