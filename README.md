# FLAT-assignment

This project implements four Finite State Transducers using OpenFST in Python.

## FSTs Implemented:

1. **String Reversal FST** - Reverses input strings (e.g., "abc" → "cba")
2. **Case Conversion FST** - Converts lowercase to uppercase
3. **Digit-to-Word Converter** - Maps digits to their word representations
4. **Vowel-Consonant Identifier** - Outputs 'v' for vowels and 'c' for consonants

## Setup

1. Install Miniconda/Anaconda in WSL
2. Create environment: `conda create -n fst-assignment python=3.9`
3. Activate: `conda activate fst-assignment`
4. Install dependencies: `conda install -c conda-forge openfst python-pynini -y`
5. Run: `python main.py`

## Project Structure
- `src/` - Source code for all FSTs
- `fst_files/` - Generated FST binary files
- `tests/` - Test inputs
- `main.py` - Main executable
