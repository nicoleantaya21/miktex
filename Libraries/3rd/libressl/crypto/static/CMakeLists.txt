## CMakeLists.txt                                       -*- CMake -*-
##
## Copyright (C) 2015-2018 Christian Schenk
## 
## This file is free software; you can redistribute it and/or modify
## it under the terms of the GNU General Public License as published
## by the Free Software Foundation; either version 2, or (at your
## option) any later version.
## 
## This file is distributed in the hope that it will be useful, but
## WITHOUT ANY WARRANTY; without even the implied warranty of
## MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
## General Public License for more details.
## 
## You should have received a copy of the GNU General Public License
## along with this file; if not, write to the Free Software
## Foundation, 59 Temple Place - Suite 330, Boston, MA 02111-1307,
## USA.

use_static_crt()

add_library(${libressl_crypto_lib_name} STATIC ${crypto_sources})

prevent_all_warnings_on_bad_code_target(${libressl_crypto_lib_name})

set_property(TARGET ${libressl_crypto_lib_name} PROPERTY FOLDER ${MIKTEX_CURRENT_FOLDER})

target_include_directories(${libressl_crypto_lib_name}
  PUBLIC
    ${public_include_directories}
)

if (MIKTEX_NATIVE_WINDOWS)
  target_link_libraries(${libressl_crypto_lib_name}
    PUBLIC
      Ws2_32.lib)
endif()
