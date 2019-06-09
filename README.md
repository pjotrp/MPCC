# MPCC
Optimized Parallelized Matrix Pearsons Correlation Coefficient

The code presented here is an attempt to provide an algorithm to perform Pearsons Correlation Coefficient calculations at a large scale for data sets arranged as rows or columns in rectangular matrices. This particular algorithm was designed to be performant in the presence of missing data.

The initial code considers implementation on a multicore (single node) shared memory machine with thread level parallelism and vectorization capability.
In future versions of this code, we hope to expand the algorithm to include distributed memory parallelism.

### Install the R package from Github

```R
library(devtools)
install_github("DannyArends/MPCC", ref="cleanrpack")
```

### Dependencies

#### Install libiomp5 and libiomp-dev

Get OMP for multi-threading support

```
sudo apt-get install libiomp5 libiomp-dev
```

#### Install Intel MKL

Install the Intel MKL using the following steps

```
## Add the intel keys to the GPG
wget https://apt.repos.intel.com/intel-gpg-keys/GPG-PUB-KEY-INTEL-SW-PRODUCTS-2019.PUB
sudo apt-key add GPG-PUB-KEY-INTEL-SW-PRODUCTS-2019.PUB

## Add the MKL deb repository
sudo sh -c 'echo deb https://apt.repos.intel.com/mkl all main > /etc/apt/sources.list.d/intel-mkl.list'

# Update and install MKL 64 bit
sudo apt-get update
sudo apt-get install intel-mkl-64bit-2018.2-046
```

### Installing the R package

Install the naive version into R

```
R CMD INSTALL MPCC
```

MKL optimized version and naive version into R

```
R CMD INSTALL --configure-args='--with-mkl-home=/opt/intel/compilers_and_libraries_2018.2.199/linux/mkl/' MPCC
```

### Loading the package into R

```R
library("MPCC")
```
    
### Documentation

```R
library(MPCC)              # Load the library
?MPCC                      # Show the general help for MPCC
?PCC                       # Show the help for the PCC function
```

