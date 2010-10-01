# Copyright (C) 2007-2009 LuaDist.
# Created by Peter Kapec
# Redistribution and use of this file is allowed according to the terms of the MIT license.
# For details see the COPYRIGHT file distributed with LuaDist.
# Please note that the package source code is licensed under its own license.

PROJECT(simulua C)
CMAKE_MINIMUM_REQUIRED(VERSION 2.8)
INCLUDE(dist.cmake)

# Build and install C modules
INCLUDE_DIRECTORIES(lib)

ADD_LUA_MODULE(rng lib/ranlib.c lib/mt.c lib/rng.c lib/rng.def )
ADD_LUA_MODULE(cdf lib/dcdflib.c lib/ipmpar.c lib/cdf.c lib/cdf.def )
ADD_LUA_MODULE(binomial lib/binomial.c lib/binomial.def )
ADD_LUA_MODULE(queue lib/queue.c lib/queue.def )
ADD_LUA_MODULE(stack lib/stack.c lib/stack.def )

# Build Simulua standalone interpreter
#~ ADD_EXECUTABLE (simulua
#~ 	etc/simulua.c etc/slinit.c
#~ 	lib/rng.c lib/ranlib.c lib/mt.c lib/cdf.c lib/dcdflib.c lib/ipmpar.c lib/binomial.c lib/queue.c lib/stack.c
#~ )
#~ TARGET_LINK_LIBRARIES(simulua ${LUA_LIBRARIES})

# Install Lua modules
INSTALL (FILES simulua.lua DESTINATION ${INSTALL_LMOD})
INSTALL (TARGETS rng cdf binomial queue stack DESTINATION ${INSTALL_CMOD})

# Install all files and documentation
INSTALL (DIRECTORY docs/ DESTINATION ${INSTALL_DOC})
INSTALL (DIRECTORY examples/ DESTINATION ${INSTALL_EXAMPLE})
