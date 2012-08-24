# Copyright (C) 2007-2012 LuaDist.
# Created by Peter Kapec
# Redistribution and use of this file is allowed according to the terms of the MIT license.
# For details see the COPYRIGHT file distributed with LuaDist.
# Please note that the package source code is licensed under its own license.

project ( simulua C )
cmake_minimum_required ( VERSION 2.8 )
include ( cmake/dist.cmake )

# Build and install C modules
include_directories ( lib )

install_lua_module ( rng lib/ranlib.c lib/mt.c lib/rng.c lib/rng.def )
install_lua_module ( cdf lib/dcdflib.c lib/ipmpar.c lib/cdf.c lib/cdf.def )
install_lua_module ( binomial lib/binomial.c lib/binomial.def )
install_lua_module ( queue lib/queue.c lib/queue.def )
install_lua_module ( stack lib/stack.c lib/stack.def )
install_lua_module ( simulua simulua.lua )

# Build Simulua standalone interpreter
add_executable (simulua etc/simulua.c etc/slinit.c lib/rng.c lib/ranlib.c lib/mt.c lib/cdf.c
lib/dcdflib.c lib/ipmpar.c lib/binomial.c lib/queue.c lib/stack.c )
target_link_libraries ( simulua ${LUA_LIBRARIES} )

# Install all files and documentation
install_doc ( docs/ )
install_example ( examples/ )
