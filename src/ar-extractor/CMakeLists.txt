
add_library(ar-extractor STATIC
	archive_wrapper.cpp
	detection.cpp
)
add_library(retdec::ar-extractor ALIAS ar-extractor)

target_compile_features(ar-extractor PUBLIC cxx_std_17)

target_include_directories(ar-extractor
	PUBLIC
		$<BUILD_INTERFACE:${RETDEC_INCLUDE_DIR}>
		$<INSTALL_INTERFACE:${RETDEC_INSTALL_INCLUDE_DIR}>
)

target_link_libraries(ar-extractor
	PUBLIC
		retdec::utils
		retdec::deps::llvm
	PRIVATE
		retdec::deps::rapidjson
)

set_target_properties(ar-extractor
	PROPERTIES
		OUTPUT_NAME "retdec-ar-extractor"
)
