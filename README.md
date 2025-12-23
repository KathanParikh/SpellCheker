# Spell Checker

A high-performance C++ spell checker using an optimized Trie data structure with intelligent word suggestions.

## Features

- ✅ **Fast Dictionary Loading**: Uses optimized Trie structure with memory pooling
- ✅ **Intelligent Suggestions**: Provides word suggestions based on edit distance
- ✅ **Interactive Correction**: Allows users to interactively fix misspelled words
- ✅ **Colored Output**: Highlights misspelled words in red for easy identification
- ✅ **Memory Efficient**: Optimized with lookup tables and hash sets

## How It Works

The spell checker uses:
1. **Trie Data Structure**: For efficient word storage and retrieval
2. **Edit Distance Algorithm**: To find similar words (Levenshtein distance)
3. **Hash Set**: For O(1) word lookups
4. **DFS Search**: To traverse the Trie and generate suggestions

## Time Complexity Analysis

### Dictionary Operations
- **Loading Dictionary**: O(N × L) where N = number of words, L = average word length
- **Trie Insertion**: O(L) per word, where L = word length
- **Word Lookup (Hash Set)**: O(1) average case
- **Word Search (Trie)**: O(L) where L = word length

### Spell Checking Operations
- **Text Parsing**: O(M) where M = total characters in input text
- **Checking Single Word**: O(1) using hash set
- **Finding Suggestions**: O(D × L²) where D = dictionary size, L = word length
  - Limited to max 10 suggestions for performance
- **Edit Distance Calculation**: O(L₁ × L₂) where L₁, L₂ = lengths of two words
  - Optimized with space O(L₂) using rolling array

### Overall Performance
- **Best Case**: O(M) - All words are correct, only need to check
- **Worst Case**: O(M + K × D × L²) where K = number of incorrect words
- **Space Complexity**: O(N × L) for Trie + O(N) for hash set

## Files

- `main.cpp` - Main spell checker implementation
- `dictionary.txt` - Dictionary file with valid words (one word per line)
- `input.txt` - Input text file to check for spelling errors

## Setup

1. Make sure you have a C++ compiler (g++, clang++, or MSVC)
2. Ensure `dictionary.txt` contains a list of valid words (one per line)
3. Create an `input.txt` file with text to check

## Compilation

### Using g++
```bash
g++ -std=c++17 -O2 main.cpp -o spellchecker
```

### Using Visual Studio (MSVC)
```bash
cl /EHsc /std:c++17 /O2 main.cpp /Fe:spellchecker.exe
```

## Usage

The spell checker supports **3 different input methods**:

### 1. Default Mode (input.txt)
```bash
.\spellchecker.exe
```
Reads from `input.txt` and saves corrections back to it.

### 2. Custom File
```bash
.\spellchecker.exe document.txt
```
Check any text file and save corrections to the same file.

### 3. Help
```bash
.\spellchecker.exe --help
```
Display usage instructions.

## What Happens Next

The program will:
- Display your text with misspelled words highlighted in red
- Interactively prompt you to correct each misspelled word
- Show suggestions for corrections
- Save the corrected text

## Interactive Commands

When prompted for a correction:
- **Number (0-9)**: Select a suggested word
- **c**: Enter a custom correction
- **i**: Ignore the word (keep as is)

## Example

Input text in `input.txt`:
```
This is a sampel text with speling mistakes.
```

Output will highlight "sampel" and "speling" in red and suggest:
- sampel → sample
- speling → spelling

## Configuration

You can modify the dictionary file name in the code:
```cpp
// In DictionaryManager::loadDictionary()
ifstream file("dictionary.txt");  // Change filename here
```

## Performance Optimizations

- Memory pooling for Trie nodes
- Pre-allocated hash tables
- Lookup table for character validation
- Early termination in edit distance calculation
- Limited suggestion count (max 10)

## Requirements

- C++17 or higher
- Standard C++ library

## License

MIT License - see [LICENSE](LICENSE) file for details

Copyright (c) 2025 Kathan Parikh

## Author

Created by Kathan Parikh