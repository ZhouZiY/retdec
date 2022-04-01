
add_library(cpdetect STATIC
	heuristics/elf_heuristics.cpp
	heuristics/heuristics.cpp
	heuristics/macho_heuristics.cpp
	heuristics/pe_heuristics.cpp
	cpdetect.cpp
	cptypes.cpp
	errors.cpp
	search.cpp
	signature.cpp
)
add_library(retdec::cpdetect ALIAS cpdetect)

target_compile_features(cpdetect PUBLIC cxx_std_17)

target_include_directories(cpdetect
	PUBLIC
		$<BUILD_INTERFACE:${RETDEC_INCLUDE_DIR}>
		$<INSTALL_INTERFACE:${RETDEC_INSTALL_INCLUDE_DIR}>
)

target_link_libraries(cpdetect
	PUBLIC
		retdec::fileformat
		retdec::utils
	PRIVATE
		retdec::yaracpp
		retdec::deps::tinyxml2
		retdec::deps::llvm
)

set_target_properties(cpdetect
	PROPERTIES
		OUTPUT_NAME "retdec-cpdetect"
)
