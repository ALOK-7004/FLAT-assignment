FLAT Assignment - Finite State Transducers
A C++ implementation of various Finite State Transducers (FSTs) using the OpenFST library for text processing and transformation tasks.

📁 Project Structure
text
FLAT_ASSIGNMENT/
├── BUILD/
│   ├── FST_APP                 # Compiled executable
│   ├── case_conversion.fst     # Case conversion FST binary
│   ├── digit_to_word.fst       # Digit to word FST binary
│   ├── string_reversal.fst     # String reversal FST binary
│   └── vowel_consonant.fst     # Vowel-consonant FST binary
├── Diagrams/
│   ├── case_conversion.dot     # Case conversion graph source
│   ├── case_conversion.png     # Case conversion visualization
│   ├── digit_to_word.dot       # Digit to word graph source
│   ├── digit_to_word.png       # Digit to word visualization
│   ├── string_reversal.dot     # String reversal graph source
│   ├── string_reversal.png     # String reversal visualization
│   ├── vowel_consonant.dot     # Vowel-consonant graph source
│   └── vowel_consonant.png     # Vowel-consonant visualization
├── INCLUDE/
│   ├── case_conversion.h       # Case conversion header
│   ├── digit_to_word.h         # Digit to word header
│   ├── fst_utils.h             # FST utilities header
│   ├── string_reversal.h       # String reversal header
│   └── vowel_consonant.h       # Vowel-consonant header
└── SRC/
    ├── case_conversion.cpp     # Case conversion implementation
    ├── digit_to_word.cpp       # Digit to word implementation
    ├── fst_utils.cpp           # FST utilities implementation
    ├── main.cpp                # Main application
    ├── string_reversal.cpp     # String reversal implementation
    └── vowel_consonant.cpp     # Vowel-consonant implementation
🚀 Features
Implemented FSTs:
String Reversal FST

Reverses input strings (e.g., "hello" → "olleh")

Case Conversion FST

Converts text between cases (e.g., lowercase to uppercase)

Digit-to-Word Converter FST

Converts digits to their word equivalents (e.g., "123" → "one two three")

Vowel-Consonant Identifier FST

Identifies and processes vowels and consonants in text

🛠️ Build Instructions
Prerequisites
C++ compiler (g++ recommended)

OpenFST library

Graphviz (for visualization)

Compilation
bash
g++ -std=c++17 -Iinclude -L/path/to/openfst/lib src/*.cpp -lfst -o build/FST_APP
Running the Application
bash
./build/FST_APP
📊 Visualizations
The project includes automatic diagram generation:

.dot files: Graphviz source files for FST structures

.png files: Rendered visualizations of each FST

🔧 Components
Core Files:
main.cpp: Application entry point and menu system

fst_utils.cpp: Common FST utilities and helper functions

Individual FST modules: Separate implementations for each transducer

Output Files:
FST_APP: Main executable

.fst files: Compiled finite state transducers

Visualizations: Graph diagrams of each FST structure

📝 Usage
The application provides an interactive interface to:

Build and execute different FSTs

Process input strings through selected transducers

Generate visual representations of the FSTs

Save FST binaries for later use

🎯 Educational Purpose
This project demonstrates practical implementation of:

Finite State Transducer concepts

OpenFST library usage

C++ programming with FSTs

Automata theory applications

Text processing algorithms

