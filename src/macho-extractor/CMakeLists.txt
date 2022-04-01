
add_library(macho-extractor STATIC
	break_fat.cpp
)
add_library(retdec::macho-extractor ALIAS macho-extractor)

target_compile_features(macho-extractor PUBLIC cxx_std_17)

target_include_directories(macho-extractor
	PUBLIC
		$<BUILD_INTERFACE:${RETDEC_INCLUDE_DIR}>
		$<INSTALL_INTERFACE:${RETDEC_INSTALL_INCLUDE_DIR}>
)

target_link_libraries(macho-extractor
	PUBLIC
		retdec::deps::llvm
	PRIVATE
		retdec::utils
		retdec::deps::rapidjson
)

set_target_properties(macho-extractor
	PROPERTIES
		OUTPUT_NAME "retdec-macho-extractor"
)
