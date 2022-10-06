set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

add_executable(add_person_cpp add_person.cc)
target_link_libraries(add_person_cpp PUBLIC addressbook ${PROTOBUF_LIBRARY})
target_link_options(add_person_cpp PUBLIC "-pthread")

add_executable(list_people_cpp list_people.cc)
target_link_libraries(list_people_cpp PUBLIC addressbook ${PROTOBUF_LIBRARY})
target_link_options(list_people_cpp PUBLIC "-pthread")