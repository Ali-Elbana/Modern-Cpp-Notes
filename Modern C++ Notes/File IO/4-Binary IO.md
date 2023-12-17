## <font color="yellow"><u>Binary I/O in C++ File Handling:</u></f>  

1. **Opening a File in Binary Mode:**
   - To perform binary I/O, open the file in binary mode by adding `std::ios::binary` to the open mode.
   ```cpp
   std::ofstream outFile("binaryFile.bin", std::ios::binary);
   std::ifstream inFile("binaryFile.bin", std::ios::binary);
   ```

2. **Writing Binary Data to a File:**
   - Use the `write()` function to write binary data to a file.
   ```cpp
   int dataToWrite[] = {1, 2, 3, 4, 5};
   outFile.write(reinterpret_cast<char*>(dataToWrite), sizeof(dataToWrite));
   ```

3. **Reading Binary Data from a File:**
   - Use the `read()` function to read binary data from a file.
   ```cpp
   int dataRead[5];
   inFile.read(reinterpret_cast<char*>(dataRead), sizeof(dataRead));
   ```

4. **Checking End-of-File (EOF):**
   - Binary files may not have a distinct EOF marker. Use the `good()` function to check for the end of the file.
   ```cpp
   while (inFile.good()) {
       // Read binary data
   }
   ```

5. **Seeking Positions in Binary Files:**
   - Use `seekg()` and `seekp()` for positioning in binary files.
   ```cpp
   inFile.seekg(2 * sizeof(int), std::ios::beg);  // Move to the third element
   ```

6. **Closing the File:**
   - Always close the file after performing I/O operations.
   ```cpp
   outFile.close();
   inFile.close();
   ```

---
## <font color="yellow"><u>Example:</u></f>  

```cpp
#include <iostream>
#include <fstream>

int main() {
    // Writing binary data to a file
    std::ofstream outFile("binaryFile.bin", std::ios::binary);
    int dataToWrite[] = {1, 2, 3, 4, 5};
    outFile.write(reinterpret_cast<char*>(dataToWrite), sizeof(dataToWrite));
    outFile.close();

    // Reading binary data from the file
    std::ifstream inFile("binaryFile.bin", std::ios::binary);
    int dataRead[5];
    inFile.read(reinterpret_cast<char*>(dataRead), sizeof(dataRead));

    // Displaying the read data
    for (int i = 0; i < 5; ++i) {
        std::cout << dataRead[i] << " ";
    }

    inFile.close();
    return 0;
}
```

In this example, an array of integers is written to a binary file and then read back. The `reinterpret_cast` is used to convert the integer array to a character array for writing and reading binary data.

---
