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
#
# BEGIN_SORT_THIS_LINE_PLUS_2
SET(source_list
    code_gen_fun.cpp
    file.cpp
    function.cpp
    jacobian.cpp
    jac_as_fun.cpp
    sparse_jacobian.cpp
    sparse_jac_as_fun.cpp
)
# END_SORT_THIS_LINE_MINUS_2

set_compile_flags(example_code_gen_fun "${cppad_debug_which}" "${source_list}" )
#
ADD_EXECUTABLE(example_code_gen_fun EXCLUDE_FROM_ALL ${source_list})

# List of libraries to be linked into the specified target
TARGET_LINK_LIBRARIES(example_code_gen_fun
    ${cppad_lib}
    ${colpack_libs}
)
#
# check_example_code_gen_fun
add_check_executable(check_example code_gen_fun)
