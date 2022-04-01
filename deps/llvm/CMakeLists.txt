

find_package(Threads REQUIRED)
find_package(LLVM CONFIG REQUIRED)

list(APPEND CMAKE_MODULE_PATH "${LLVM_CMAKE_DIR}")
include(HandleLLVMOptions)
add_definitions(${LLVM_DEFINITIONS})

llvm_map_components_to_libnames(LLVM_LIB_LIST
	DebugInfoDWARF
	BitWriter
	IRReader
	Object
	BinaryFormat
	InstCombine
	Support
	Demangle
	ipo
	AsmParser
	BitReader
	MCParser
	CodeGen
	ScalarOpts
	TransformUtils
	Analysis
	Target
	Core
	MC
	Object
	Passes
)

add_library(llvm INTERFACE)
add_library(retdec::deps::llvm ALIAS llvm)
add_dependencies(llvm llvm-project)

target_include_directories(llvm INTERFACE ${LLVM_INCLUDE_DIRS})

target_link_libraries(llvm INTERFACE ${LLVM_LIB_LIST} Threads::Threads)

