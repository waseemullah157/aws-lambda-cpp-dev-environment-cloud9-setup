# aws-lambda-cpp-dev-environment-cloud9-setup

```bash
sudo yum install -y gcc64-c++ libcurl-devel
sudo echo 'export CC=gcc64' >> ~/.bashrc
sudo echo 'export CXX=g++64' >> ~/.bashrc

wget https://cmake.org/files/v3.18/cmake-3.18.0.tar.gz
tar -xvzf cmake-3.18.0.tar.gz
cd cmake-3.18.0
./bootstrap
make
sudo make install

cd ~/environment
git clone https://github.com/aws/aws-sdk-cpp.git
cd aws-sdk-cpp && mkdir build && cd build
cmake .. -DBUILD_ONLY="core" \
  -DCMAKE_BUILD_TYPE=Release \
  -DBUILD_SHARED_LIBS=OFF \
  -DENABLE_UNITY_BUILD=ON \
  -DCUSTOM_MEMORY_MANAGEMENT=OFF \
  -DCMAKE_INSTALL_PREFIX=~/install \
  -DENABLE_UNITY_BUILD=ON
sudo make && make install

cd ~/environment
git clone https://github.com/awslabs/aws-lambda-cpp-runtime.git
cd aws-lambda-cpp-runtime && mkdir build && cd build
cmake .. -DCMAKE_BUILD_TYPE=Release \
  -DBUILD_SHARED_LIBS=OFF \
  -DCMAKE_INSTALL_PREFIX=~/install
sudo make && make install


```