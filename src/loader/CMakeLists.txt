
add_library(loader STATIC
	utils/range.cpp
	utils/overlap_resolver.cpp
	utils/name_generator.cpp
	image_factory.cpp
	loader/pe/pe_image.cpp
	loader/image.cpp
	loader/coff/coff_image.cpp
	loader/segment.cpp
	loader/intel_hex/intel_hex_image.cpp
	loader/macho/macho_image.cpp
	loader/raw_data/raw_data_image.cpp
	loader/segment_data_source.cpp
	loader/elf/elf_image.cpp
)
add_library(retdec::loader ALIAS loader)

target_compile_features(loader PUBLIC cxx_std_17)

target_include_directories(loader
	PUBLIC
		$<BUILD_INTERFACE:${RETDEC_INCLUDE_DIR}>
		$<INSTALL_INTERFACE:${RETDEC_INSTALL_INCLUDE_DIR}>
)

target_link_libraries(loader
	PUBLIC
		retdec::fileformat
		retdec::common
		retdec::utils
)

set_target_properties(loader
	PROPERTIES
		OUTPUT_NAME "retdec-loader"
)
