
add_library(rtti-finder STATIC
	rtti/rtti_gcc_parser.cpp
	rtti/rtti_msvc_parser.cpp
	vtable/vtable_finder.cpp
	rtti_finder.cpp
)
add_library(retdec::rtti-finder ALIAS rtti-finder)

target_compile_features(rtti-finder PUBLIC cxx_std_17)

target_include_directories(rtti-finder
	PUBLIC
		$<BUILD_INTERFACE:${RETDEC_INCLUDE_DIR}>
		$<INSTALL_INTERFACE:${RETDEC_INSTALL_INCLUDE_DIR}>
)

target_link_libraries(rtti-finder
	PUBLIC
		retdec::loader
		retdec::common
		retdec::utils
)

set_target_properties(rtti-finder
	PROPERTIES
		OUTPUT_NAME "retdec-rtti-finder"
)
