
add_library(debugformat STATIC
	debugformat.cpp
	dwarf.cpp
	pdb.cpp
)
add_library(retdec::debugformat ALIAS debugformat)

target_compile_features(debugformat PUBLIC cxx_std_17)

target_include_directories(debugformat
	PUBLIC
		$<BUILD_INTERFACE:${RETDEC_INCLUDE_DIR}>
		$<INSTALL_INTERFACE:${RETDEC_INSTALL_INCLUDE_DIR}>
)

target_link_libraries(debugformat
	PUBLIC
		retdec::demangler
		retdec::loader
		retdec::fileformat
		retdec::common
		retdec::pdbparser
		retdec::deps::llvm
)

set_target_properties(debugformat
	PROPERTIES
		OUTPUT_NAME "retdec-debugformat"
)
