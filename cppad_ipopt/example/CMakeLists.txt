# -----------------------------------------------------------------------------
# CppAD: C++ Algorithmic Differentiation: Copyright (C) 2003-22 Bradley M. Bell
#
# CppAD is distributed under the terms of the
#              Eclipse Public License Version 2.0.
#
# This Source Code may also be made available under the following
# Secondary License when the conditions for such availability set forth
# in the Eclipse Public License, Version 2.0 are satisfied:
#       GNU General Public License, Version 2.0 or later.
# -----------------------------------------------------------------------------
# Inherit build type from ../CMakeList.txt

# Local include directories to search (not in package_prefix/include)
INCLUDE_DIRECTORIES( ${CMAKE_CURRENT_SOURCE_DIR}/../src )

# Local link directories to search (not in external packages)
LINK_DIRECTORIES( ${CMAKE_CURRENT_BINARY_DIR}/../src ${ipopt_LIBRARY_DIRS} )

# add_executable(<name> [WIN32] [MACOSX_BUNDLE] [EXCLUDE_FROM_ALL]
#                 source1 source2 ... sourceN
# )
# BEGIN_SORT_THIS_LINE_PLUS_2
SET(source_list
    example.cpp
    get_started.cpp
    ode_check.cpp
    ode_check.hpp
    ode_fast.hpp
    ode_fast_check.cpp
    ode_problem.hpp
    ode_run.hpp
    ode_simple.hpp
    ode_simple_check.cpp
)
# END_SORT_THIS_LINE_MINUS_2

set_compile_flags( cppad_ipopt_example "${cppad_debug_which}" "${source_list}" )
#
ADD_EXECUTABLE( cppad_ipopt_example EXCLUDE_FROM_ALL ${source_list} )

# List of libraries to be linked into the specified target
TARGET_LINK_LIBRARIES(cppad_ipopt_example
    cppad_ipopt
    ${cppad_lib}
    ${ipopt_LIBRARIES}
    ${colpack_libs}
)

#
# check_cppad_ipopt_example
add_check_executable(check_cppad_ipopt example)
