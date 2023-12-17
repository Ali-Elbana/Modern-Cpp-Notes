## <font color="yellow"><u>Introduction:</u></f>

File I/O is the process of reading and writing data from and to files. C++ provides three classes to perform file I/O: `ifstream`, `ofstream`, and `fstream`. These classes are derived from the standard input/output streams, such as `istream`, `ostream`, and `iostream`. To use these classes, you need to include the header file `<fstream>`.

![image](https://github.com/Ali-Elbana/STL-Notes/assets/97269796/4e725523-d5e6-4922-9ea8-700fc73d7248)

---
## <font color="yellow"><u>File open modes:</u></f>

![image](https://github.com/Ali-Elbana/STL-Notes/assets/97269796/2b311323-94b9-4524-b363-44d99771ba91)
### <u>Example:</u>

```cpp
#include <iostream>
#include <fstream>

int main() 
{
    // Open file for reading
    std::ifstream inputFile("example.txt", std::ios::in);

    // Open file for writing (truncate existing content)
    std::ofstream outputFile("output.txt", std::ios::out);

    // Open file for writing (append to existing content)
    std::ofstream appendFile("append.txt", std::ios::out | std::ios::app);

    // Open file for reading and writing
    std::fstream readWriteFile("readwrite.txt", std::ios::in | std::ios::out);

    // Open binary file for reading and writing
    std::fstream binaryFile("binaryfile.dat", std::ios::in | std::ios::out | std::ios::binary);

    return 0;
}

```

<u>In the above example:</u>

- `std::ios::in` is used to open a file for reading.
- `std::ios::out` is used to open a file for writing (with truncation).
- `std::ios::app` is used to open a file for writing at the end (appending).
- `std::ios::in | std::ios::out` is used to open a file for both reading and writing.
- `std::ios::in | std::ios::out | std::ios::binary` is used to open a binary file for both reading and writing.

---
## <font color="yellow"><u>Reading from a File:</u></f>

1. **Include Necessary Header:**
   ```cpp
   #include <fstream>
   ```

2. **Open Input File Stream:**
   ```cpp
   std::ifstream inputFile("filename.txt");
   ```

3. **Check if the File is Open:**
   ```cpp
   if (inputFile.is_open()) {
       // File is open, proceed with reading
   } else {
       // Error: Unable to open the file
   }
   ```

4. **Read from File:**
   ```cpp
   int number;
   while (inputFile >> number) {
       // Process the read number
   }
   ```

5. **Close File:**
   ```cpp
   inputFile.close();
   ```

---
## <font color="yellow"><u>Writing to a File:</u></f> 

1. **Include Necessary Header:**
   ```cpp
   #include <fstream>
   ```

2. **Open Output File Stream:**
   ```cpp
   std::ofstream outputFile("output.txt");
   ```

3. **Check if the File is Open:**
   ```cpp
   if (outputFile.is_open()) {
       // File is open, proceed with writing
   } else {
       // Error: Unable to open/create the file
   }
   ```

4. **Write to File:**
   ```cpp
   outputFile << "Hello, File I/O!\n";
   outputFile << 42 << " " << 3.14 << "\n";
   ```

5. **Close File:**
   ```cpp
   outputFile.close();
   ```

---
## <font color="yellow"><u>Appending to a File:
</u></f> 

To append content to an existing file, use `std::ofstream` with the `std::ios::app` flag:

```cpp
std::ofstream outputFile("existingFile.txt", std::ios::app);
```

---
## <font color="yellow"><u>Binary File I/O:</u></f> 

For binary file I/O, use `std::ifstream` and `std::ofstream` in binary mode:

```cpp
std::ifstream binaryInputFile("binaryInput.dat", std::ios::binary);
std::ofstream binaryOutputFile("binaryOutput.dat", std::ios::binary);
```

---
## <font color="yellow"><u>Error Handling:</u></f>  

Always check for errors when performing file I/O operations. Use exceptions or check the stream state with `good()` or `fail()`.

![image](https://github.com/Ali-Elbana/STL-Notes/assets/97269796/200d8384-64da-4881-b4a9-80733b3f425e)

![image](https://github.com/Ali-Elbana/STL-Notes/assets/97269796/a811c0d3-13a3-4eb4-bbd6-34afd24e8bd7)
### Example:

```cpp
#include <iostream>
#include <fstream>

int main() {
    // Writing to a file
    std::ofstream outputFile("example.txt");
    
    if (outputFile.is_open()) {
        outputFile << "Hello, File I/O!\n";
        outputFile << 42 << " " << 3.14 << "\n";
        outputFile.close();
    } else {
        std::cerr << "Error: Unable to open/create the file for writing.\n";
        return 1;
    }

    // Reading from a file
    std::ifstream inputFile("example.txt");

    if (inputFile.is_open()) {
        int number;
        while (inputFile >> number) {
            // Process the read number
            std::cout << "Read: " << number << "\n";
        }
        inputFile.close();
    } else {
        std::cerr << "Error: Unable to open the file for reading.\n";
        return 1;
    }

    return 0;
}
```

---
## <font color="yellow"><u>Flags:</u></f>

The flags can be combined using the bitwise operator OR (`|`). Some common flags are:
- `std::ios::in`: Open for input operations.
- `std::ios::out`: Open for output operations.
- `std::ios::binary`: Open in binary mode.
- `std::ios::ate`: Set the initial position at the end of the file.
- `std::ios::app`: All output operations are performed at the end of the file, appending the content to the current content of the file.
- `std::ios::trunc`: If the file is opened for output operations and it already existed, its previous content is deleted and replaced by the new one.

---
## <font color="yellow"><u>Clear flags:</u></f>

In the context of File I/O in C++, the `clear()` function is not directly related to files; instead, it is a member function of the `std::basic_ios` class, which is the base class for `std::istream` and `std::ostream` (the base classes for input and output streams). The primary purpose of `clear()` in File I/O is the same as in general I/O streams: to clear the error state flags.

When working with files, you typically use file streams (`std::ifstream` for reading, `std::ofstream` for writing, and `std::fstream` for both). These file streams are derived from the `std::istream` and `std::ostream` classes, which, in turn, inherit from `std::ios_base`. The `clear()` function is part of `std::ios_base`, and it's used to reset the error state flags.

Here's a brief explanation in the context of File I/O:
### `clear()` in File I/O:

- **Purpose:** Resets the error state flags associated with the file stream.
- **Syntax:**

  ```cpp
  void clear();
  ```

- **Example:**

  ```cpp
  #include <iostream>
  #include <fstream>

  int main() {
      std::ifstream inputFile("example.txt");

      // Simulate an error by attempting to open a non-existent file
      if (!inputFile.is_open()) {
          std::cerr << "Error: Failed to open file." << std::endl;
          inputFile.clear(); // Clear the error state flags

          // Optionally, take corrective actions or handle the error
      }

      // Continue with other file operations...

      return 0;
  }
  ```

In this example, `clear()` is used to clear the error state flags if there's an issue opening the file. After calling `clear()`, you might take corrective actions or handle the error based on your application's logic.

Remember, `clear()` itself doesn't fix the underlying issue causing the error; it simply resets the stream's error state so that you can continue working with it.

---

