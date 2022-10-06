1. Compile addressbook.proto to C++ objects
2. Create a static library libaddressbook composed of addressbook source and header files
3. Use the symbols from libaddressbook in add_person.cc and list_people.cc. 

```
rm -rf build && mkdir build && cd build
cmake ..
cmake --build .

# In build directory
./bin/add_person_cpp
./bin/list_people_cpp
```
