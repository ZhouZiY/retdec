
add_library(stacofin STATIC
	stacofin.cpp
)
add_library(retdec::stacofin ALIAS stacofin)

target_compile_features(stacofin PUBLIC cxx_std_17)

target_include_directories(stacofin
	PUBLIC
		$<BUILD_INTERFACE:${RETDEC_INCLUDE_DIR}>
		$<INSTALL_INTERFACE:${RETDEC_INSTALL_INCLUDE_DIR}>
)

target_link_libraries(stacofin
	PUBLIC
		retdec::config
		retdec::common
		retdec::deps::capstone
	PRIVATE
		retdec::loader
		retdec::yaracpp
		retdec::utils
)

set_target_properties(stacofin
	PROPERTIES
		OUTPUT_NAME "retdec-stacofin"
)
