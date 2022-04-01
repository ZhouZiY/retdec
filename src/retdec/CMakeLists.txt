
add_library(retdec STATIC
    retdec.cpp
)
add_library(retdec::retdec ALIAS retdec)

target_compile_features(retdec PUBLIC cxx_std_17)

target_include_directories(retdec
	PUBLIC
		$<BUILD_INTERFACE:${RETDEC_INCLUDE_DIR}>
		$<INSTALL_INTERFACE:${RETDEC_INSTALL_INCLUDE_DIR}>
)

target_link_libraries(retdec
	PUBLIC
		retdec::common
		retdec::deps::capstone
		retdec::deps::llvm
	PRIVATE
		retdec::bin2llvmir
		retdec::llvmir2hll
		retdec::config
)

set_target_properties(retdec
	PROPERTIES
		OUTPUT_NAME "retdec-retdec"
)
