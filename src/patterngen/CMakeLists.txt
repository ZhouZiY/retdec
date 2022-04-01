
add_library(patterngen STATIC
	pattern_extractor/pattern_extractor.cpp
	pattern_extractor/types/symbol_pattern.cpp
)
add_library(retdec::patterngen ALIAS patterngen)

target_compile_features(patterngen PUBLIC cxx_std_17)

target_include_directories(patterngen
	PUBLIC
		$<BUILD_INTERFACE:${RETDEC_INCLUDE_DIR}>
		$<INSTALL_INTERFACE:${RETDEC_INSTALL_INCLUDE_DIR}>
)

target_link_libraries(patterngen
	PUBLIC
		retdec::deps::yaramod
	PRIVATE
		retdec::fileformat
		retdec::utils
)

set_target_properties(patterngen
	PROPERTIES
		OUTPUT_NAME "retdec-patterngen"
)
