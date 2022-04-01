
add_library(demangler STATIC
	ast_ctypes_parser.cpp
	borland_ast_ctypes_parser.cpp
	borland_ast_parser.cpp
	borland_demangler.cpp
	context.cpp
	demangler_base.cpp
	itanium_ast_ctypes_parser.cpp
	itanium_demangler_adapter.cpp
	microsoft_demangler_adapter.cpp
	ms_ast_ctypes_parser.cpp
	borland_ast/array_type.cpp
	borland_ast/built_in_type.cpp
	borland_ast/char_type.cpp
	borland_ast/conversion_operator.cpp
	borland_ast/float_type.cpp
	borland_ast/function_node.cpp
	borland_ast/function_type.cpp
	borland_ast/integral_type.cpp
	borland_ast/name_node.cpp
	borland_ast/named_type.cpp
	borland_ast/node.cpp
	borland_ast/node_array.cpp
	borland_ast/pointer_type.cpp
	borland_ast/parentheses_node.cpp
	borland_ast/reference_type.cpp
	borland_ast/rreference_type.cpp
	borland_ast/qualifiers.cpp
	borland_ast/template_node.cpp
	borland_ast/type_node.cpp
)
add_library(retdec::demangler ALIAS demangler)

target_compile_features(demangler PUBLIC cxx_std_17)

target_include_directories(demangler
	PUBLIC
		$<BUILD_INTERFACE:${RETDEC_INCLUDE_DIR}>
		$<INSTALL_INTERFACE:${RETDEC_INSTALL_INCLUDE_DIR}>
)

target_link_libraries(demangler
	PUBLIC
		retdec::ctypesparser
		retdec::deps::llvm
)

set_target_properties(demangler
	PROPERTIES
		OUTPUT_NAME "retdec-demangler"
)
