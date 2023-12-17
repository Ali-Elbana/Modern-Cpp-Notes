
## <font color="yellow"><u>ifstream (Input File Stream):</u></f> 

#### 1. `tellg()` - Get Current Position:
   - `std::streampos tellg();`
   - Returns the current position of the get pointer (read position) in the file.

   ```cpp
   // Example - Get current position
   std::streampos currentPosition = inputFile.tellg();
   ```

#### 2. `seekg()` - Set Position:
   - `void seekg(std::streampos pos);`
   - Moves the get pointer to the specified absolute position in the file.

   ```cpp
   // Example - Set position to a specific absolute position
   inputFile.seekg(targetPosition);
   ```

#### 3. `seekg()` - Set Position Relative to Current Position:
   - `void seekg(std::streamoff off, std::ios_base::seekdir way);`
   - Moves the get pointer by a specified offset relative to the current position.

   ```cpp
   // Example - Set position relative to the current position
   inputFile.seekg(offset, std::ios_base::cur);
   ```

---
## <font color="yellow"><u>ofstream (Output File Stream):</u></f>  
#### 1. `tellp()` - Get Current Position:
   - `std::streampos tellp();`
   - Returns the current position of the put pointer (write position) in the file.

   ```cpp
   // Example - Get current position
   std::streampos currentPosition = outputFile.tellp();
   ```

#### 2. `seekp()` - Set Position:
   - `void seekp(std::streampos pos);`
   - Moves the put pointer to the specified absolute position in the file.

   ```cpp
   // Example - Set position to a specific absolute position
   outputFile.seekp(targetPosition);
   ```

#### 3. `seekp()` - Set Position Relative to Current Position:
   - `void seekp(std::streamoff off, std::ios_base::seekdir way);`
   - Moves the put pointer by a specified offset relative to the current position.

   ```cpp
   // Example - Set position relative to the current position
   outputFile.seekp(offset, std::ios_base::cur);
   ```

---
## <font color="yellow"><u>Note:</u></f> 

- The `tellg()` and `tellp()` functions return a `std::streampos` type, representing the position in the file.
- The `seekg()` and `seekp()` functions are used to set the position for reading and writing, respectively.
- Examples demonstrate how to use these functions to navigate and modify file content in both input and output modes.

---
