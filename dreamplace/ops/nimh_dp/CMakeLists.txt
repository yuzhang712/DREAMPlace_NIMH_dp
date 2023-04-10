set(OP_NAME nimh_dp)

set(TARGET_NAME ${OP_NAME})

set(INCLUDE_DIRS 
  ${CMAKE_CURRENT_SOURCE_DIR}/..
  )

set(LINK_LIBS utility_cxx
  OpenMP::OpenMP_CXX
  )

add_pytorch_extension(${TARGET_NAME}_cpp 
  src/row_height_assignment.cpp
  # src/vertical_legalization.cpp 
  # src/horizontal_legalization.cpp 
  EXTRA_INCLUDE_DIRS ${INCLUDE_DIRS}
  EXTRA_LINK_LIBRARIES ${LINK_LIBS})

install(TARGETS ${TARGET_NAME}_cpp DESTINATION dreamplace/ops/${OP_NAME})
file(GLOB INSTALL_SRCS ${CMAKE_CURRENT_SOURCE_DIR}/*.py)
install(FILES ${INSTALL_SRCS} DESTINATION dreamplace/ops/${OP_NAME})
