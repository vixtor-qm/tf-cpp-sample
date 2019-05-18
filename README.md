# tf-cpp-sample
A CMake Project For TF Inference

Build TF from source as shared lib on Ubuntu Linux

Install the following build tools to configure your development environment.
Install Python and the TensorFlow package dependencies
sudo apt install python-dev python-pip  # or python3-dev python3-pip
Install the TensorFlow pip package dependencies (if using a virtual environment, omit the --user argument):
pip install -U --user pip six numpy wheel setuptools mock
pip install -U --user keras_applications==1.0.6 --no-deps
pip install -U --user keras_preprocessing==1.0.5 --no-deps
The dependencies are listed in the setup.py file under REQUIRED_PACKAGES.
Install Bazel
Install Bazel, the build tool used to compile TensorFlow.
Add the location of the Bazel executable to your PATH environment variable.
Install GPU support (optional, Linux only)
There is no GPU support for macOS.
Read the GPU support guide to install the drivers and additional software required to run TensorFlow on a GPU.
Note: It is easier to set up one of TensorFlow's GPU-enabled Docker images.
Download the TensorFlow source code
Use Git to clone the TensorFlow repository:
git clone https://github.com/tensorflow/tensorflow.git
cd tensorflow

The repo defaults to the master development branch. You can also checkout a release branch to build:
git checkout branch_name  # r1.9, r1.10, etc.
Configure the build
Configure your system build by running the following at the root of your TensorFlow source tree:
./configure


2. Build C++ library mode:
bazel build -c opt --copt=-mavx --copt=-mavx2 --copt=-mfma --copt=-mfpmath=both --copt=-msse4.2 --config=monolithic //tensorflow:libtensorflow_cc.so

3. IMPORTANT: open tensorflow/workspace.bzl and check for protocol buffer version.
Download and build protocol buffers of the the same version.
Install protobuf using checkinstall

call 
sudo ldconfig to set update library cache

4. Build Eigen
5. Build absl lib

6. Set up headers and lib paths in CMakeLists.txt
7. Build the project and have fun