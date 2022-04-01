
add_library(unpacker STATIC
	decompression/lzma/lzma_data.cpp
	decompression/nrv/nrv2d_data.cpp
	decompression/nrv/nrv2b_data.cpp
	decompression/nrv/nrv2e_data.cpp
	decompression/lzmat/lzmat_data.cpp
	signature.cpp
)
add_library(retdec::unpacker ALIAS unpacker)

target_compile_features(unpacker PUBLIC cxx_std_17)

target_include_directories(unpacker
	PUBLIC
		$<BUILD_INTERFACE:${RETDEC_INCLUDE_DIR}>
		$<INSTALL_INTERFACE:${RETDEC_INSTALL_INCLUDE_DIR}>
)

target_link_libraries(unpacker
	PUBLIC
		retdec::loader
)

set_target_properties(unpacker
	PROPERTIES
		OUTPUT_NAME "retdec-unpacker"
)
