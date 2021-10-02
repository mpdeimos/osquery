# Copyright (c) 2014-present, Facebook, Inc.
# All rights reserved.
#
# This source code is licensed in accordance with the terms specified in
# the LICENSE file found in the root directory of this source tree.

function(snappyMain)
  set(library_root "${CMAKE_CURRENT_SOURCE_DIR}/src")

  add_library(thirdparty_snappy
    "${library_root}/snappy-internal.h"
    "${library_root}/snappy-stubs-internal.h"
    "${library_root}/snappy-c.cc"
    "${library_root}/snappy-sinksource.cc"
    "${library_root}/snappy-stubs-internal.cc"
    "${library_root}/snappy.cc"
  )

  target_link_libraries(thirdparty_snappy PRIVATE
    thirdparty_c_settings
  )

  target_include_directories(thirdparty_snappy PRIVATE
    "${library_root}"
  )

  target_include_directories(thirdparty_snappy SYSTEM INTERFACE
    "${library_root}"
  )
endfunction()

snappyMain()
