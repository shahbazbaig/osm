Install climate data operators (cdo) on Ubuntu with netCDF4 and hdf5 support
Nikolay Koldunov
koldunovn@gmail.com
@oceanographer
CDOs can be installed from Ubuntu repositories, but they are compiled without netCDF4 and HDF5 support. As a result you can get:

Unsupported file type (library support not compiled in)

error. To solve this we have to compile cdo by ourselves.

Uninstal cdo if you have them installed from Ubuntu repositories:

sudo apt-get purge cdo

Install netcdf andf HDF5 libraries:

sudo apt-get install libnetcdf-dev libhdf5-dev


Download latest stable version of cdo from here

Unpack it

cd to unpacked directory

If you want to install cdo in to your system directory:

./configure --enable-netcdf4  --enable-zlib --with-netcdf=/usr/ --with-hdf5=/usr/
make
sudo make install

If you don't have administrative rights, of would like to have installation of cdo in other folder for any other reason, you can provide prefix:

./configure --enable-netcdf4  --enable-zlib --prefix=/dir/where/to/put/cdo --with-netcdf=/usr/ --with-hdf5=/usr/
make
make install

In the last case you should also add this path to your $PATH in .bashrc file:

export PATH=/dir/where/to/put/cdo/bin:$PATH

note bin at the end!

Hope it will work for you :)
