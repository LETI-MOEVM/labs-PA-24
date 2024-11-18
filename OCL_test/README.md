
Установка OpenCL-драйвера для процессора
========================================

Установить OpenCL-драйвер для процессора полезно, даже если у вас есть видеокарта, т.к. на нем удобно тестировать приложение (драйвер видеокарты гораздо чаще может повиснуть вместе с ОС).

Windows
-------
Скачайте [прямая ссылка для Windows](http://registrationcenter-download.intel.com/akdlm/irc_nas/vcp/13794/opencl_runtime_18.1_x64_setup.msi)
Установите

Linux (Рекомендуется Ubuntu 18.04 или 20.04)
----------------------------------

Скачайте [прямая ссылка для Ubuntu](http://registrationcenter-download.intel.com/akdlm/irc_nas/vcp/15532/l_opencl_p_18.1.0.015.tgz)
``sudo apt-get install -yq cpio``
``tar -xzf l_opencl_p_18.1.0.015.tgz``
``sudo ./l_opencl_p_18.1.0.015/install.sh``
Проведите установку.

Если у вас довольно новый процессор, например i7-8550U, то драйвер может его не поддерживать - ```clCreateContext``` вернет ошибку ```CL_DEVICE_NOT_AVAILABLE```, в таком случае поставьте свежий драйвер [отсюда](https://github.com/intel/compute-runtime/releases) (включает в т.ч. драйвер для встроенной Intel GPU).


Установка OpenCL-драйвера для видеокарты
========================================
Поставьте драйвер стандартным образом - скачав инсталлятор с официального сайта вендора вашей видеокарты.

Для nvidia проверить что выдаёт команда 
nvidia-smi

Windows
-------
https://github.com/KhronosGroup/OpenCL-Guide/blob/main/chapters/getting_started_windows.md

Linux
-----
sudo apt install opencl-headers ocl-icd-opencl-dev -y

https://github.com/KhronosGroup/OpenCL-Guide/blob/main/chapters/getting_started_linux.md

==============================================
Проверка окружения
==============================================

 ``mkdir build``
 ``cd build``
 ``cmake ..``
 ``make -j4``
 ``./enumDevices`` должно увидеть хотя бы одну OpenCL-платформу, например:

```
Number of OpenCL platforms: 1
Platform #1/1
    Platform name: NVIDIA CUDA
    Platform vendor: NVIDIA Corporation
      Number of OpenCL dev-s: 1
    >> DEVICE #1/1
    Device name: NVIDIA GeForce RTX 4060
    Dev type :: GPU 
   Global memory: 7820Mb
   Local memory: 48K
   
```


