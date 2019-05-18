set(TARGET TF_CPP_SAMPLE)
set(CMAKE_CXX_STANDARD 14)

include_directories(
        "/usr/local/cuda/include"
    )

set(TF_LIB_DIR "<your_tf_src_dir>tensorflow/bazel-bin/tensorflow/")

link_directories(${TF_LIB_DIR})

include_directories("<your_tf_src_dir>/tensorflow/")
include_directories("<your_tf_src_dir>/tensorflow/bazel-genfiles/")
include_directories("<your_eigen_install_dir>/Eigen/eigen-git-mirror-3.3.7/install/include/eigen3/")
include_directories("<your_absl_install_dir>/absl/")


add_executable(${TARGET}
    ${PROJECT_SOURCE_DIR}/source/TensorFlowInference.cpp)
target_link_libraries(${TARGET}
     tensorflow_cc
)