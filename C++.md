# C++ 

## STL

* vector

```c++
// insert an element into the beginning of the vector
v.insert(v.begin, element);
```

* unordered_map

```c++
#include <iostream>
#include <unordered_map>

int main() {
    // Create an unordered_map with int keys and string values
    std::unordered_map<int, std::string> myMap;

    // Insert key-value pairs
    myMap[1] = "One";
    myMap[2] = "Two";
    myMap[3] = "Three";

    // Access elements using the [] operator
    std::cout << "myMap[2]: " << myMap[2] << std::endl; // Output: "myMap[2]: Two"

    // Check if a key exists
    if (myMap.find(4) != myMap.end()) {
        std::cout << "Key 4 exists in the map." << std::endl;
    } else {
        std::cout << "Key 4 does not exist in the map." << std::endl;
    }

    // Iterating over the unordered_map
    for (const auto& pair : myMap) {
        std::cout << "Key: " << pair.first << ", Value: " << pair.second << std::endl;
    }

    // Remove an element by key
    myMap.erase(2);

    // Size of the unordered_map
    std::cout << "Size of myMap: " << myMap.size() << std::endl;

    return 0;
}
```

the difference between unordered_map and map in C++

