# tf-cpp-sample
A CMake Project For TF Inference

Build TF from source as shared lib on Ubuntu Linux

1. Install bazel

2. Clone TF from repository and build it

```
git clone https://github.com/tensorflow/tensorflow.git
cd tensorflow
```

The repo defaults to the master development branch. You can also checkout a release branch to build:
git checkout branch_name  # r1.9, r1.10, etc.

Configure the build
Configure your system build by running the following at the root of your TensorFlow source tree:
```
./configure
```

3. Build in  C++ library mode:
```
bazel build -c opt --copt=-mavx --copt=-mavx2 --copt=-mfma --copt=-mfpmath=both --copt=-msse4.2 --config=monolithic //tensorflow:libtensorflow_cc.so
```

4. Download and build protocol buffers
IMPORTANT: open tensorflow/workspace.bzl and check for protocol buffer version used in TF.
Download and build the same version. It will conflict in other case.
Install protobuf using checkinstall
call 
```
sudo ldconfig
```

to set update library cache

5. Build Eigen
6. Build absl lib

7. Set up headers and lib paths in CMakeLists.txt
8. Build the project and have fun
