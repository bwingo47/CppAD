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
# Build the example/optimize directory tests
#
#
# BEGIN_SORT_THIS_LINE_PLUS_2
SET(source_list
    compare_op.cpp
    conditional_skip.cpp
    cumulative_sum.cpp
    forward_active.cpp
    nest_conditional.cpp
    optimize.cpp
    optimize_twice.cpp
    print_for.cpp
    reverse_active.cpp
)
# END_SORT_THIS_LINE_MINUS_2

set_compile_flags( example_optimize "${cppad_debug_which}" "${source_list}" )
#
ADD_EXECUTABLE(example_optimize EXCLUDE_FROM_ALL ${source_list})
#
# List of libraries to be linked into the specified target
TARGET_LINK_LIBRARIES(example_optimize
    ${cppad_lib}
    ${colpack_libs}
)
#
# check_example_optimize
add_check_executable(check_example optimize)
