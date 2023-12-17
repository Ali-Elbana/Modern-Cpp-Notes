## <font color="yellow"><u>Copying from a file to a file:</u></f>

Certainly! Copying data from one file to another in C++ involves reading from an input file stream and writing to an output file stream. Below is an example that demonstrates how to copy the contents of one file to another using standard C++ File I/O.

```cpp
#include <iostream>
#include <fstream>
#include <string>

int main() {
    // Input file stream for reading from the source file
    std::ifstream sourceFile("source.txt");

    // Output file stream for writing to the destination file
    std::ofstream destinationFile("destination.txt");

    // Check if both files are open
    if (!sourceFile.is_open() || !destinationFile.is_open()) {
        std::cerr << "Error: Unable to open files." << std::endl;
        return 1;
    }

    // Copy contents from source file to destination file
    std::string line;
    while (std::getline(sourceFile, line)) {
        destinationFile << line << '\n';
    }

    // Close the file streams
    sourceFile.close();
    destinationFile.close();

    std::cout << "File copy successful." << std::endl;

    return 0;
}
```

Explanation:

1. **Open Files:** Use `std::ifstream` to open the source file for reading (`source.txt`) and `std::ofstream` to open the destination file for writing (`destination.txt`).

2. **Check File Open Status:** Ensure that both files are successfully opened before proceeding.

3. **Copy Contents:** Use a loop to read lines from the source file (`sourceFile`) using `std::getline` and write each line to the destination file (`destinationFile`).

4. **Close Files:** Close the file streams after the copying is complete.

5. **Feedback:** Provide a message indicating the success of the file copy.

This is a basic example, and you can modify it based on your specific requirements, such as handling different data types or adding error-checking mechanisms.

---

