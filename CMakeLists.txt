set(LLVM_LINK_COMPONENTS
  Core
  ExecutionEngine
  MC
  MCJIT
  Support
  native
  )

#CC="clang" CXX="clang++" CFLAGS="-std=c++11 -fPIC" LDFLAGS="-shared"
add_definitions( "-std=c++11 -fPIC -shared" )
add_clang_executable(ast_exporter_bin
  ast_exporter_bin.cpp
  AttrParameterVectorStream.cpp
  FileServices.cpp
  FileUtils.cpp
  SimplePluginASTAction.cpp )

add_dependencies(ast_exporter_bin  clang-headers  )

target_link_libraries(ast_exporter_bin
  clangAST
  clangBasic
  clangCodeGen
  clangDriver
  clangFrontend
  clangTooling
  LLVMSupport
  )
