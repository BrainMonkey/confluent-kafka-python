# confluent-kafka-python
## **** keep your Confluent Kafka Python development on Windows ****

As of June 11, 2018, the day I create this repository, Confluent was not offically support Python package on Windows yet. I spent some time and managed to make the Python package working on Windows platform. In this case I could keep my development environment on Windows computer, which makes my life much easier.

If you fought the same problem like me, you probably will be  I'll try explain the details so you could actullay do it by yourself, if you don't feel confortable to install the pre-compiled dll / bin file on your system.

### Compatibility

I only work on Python 3.6 X64 version, so you might need do your compiling if you want use 32 bit version Python, or 2.7. I tested on Windows 10 as my development environment and deployed to Windows server 2012R2, the package works well on both.

### Where these files come from

#### confluent-kafka-python-0.11.4
I cloned from https://github.com/confluentinc/confluent-kafka-python, as of May 31, 2018, v 0.11.4 is the latest release
#### librdkafka-0.11.4
I cloned from https://github.com/edenhill/librdkafka, I pick the same verion as Confluent's package, v 0.11.4. PS: The librdkafka repo on Confluent is not up-to-date, some functions are not missing in the repo.
#### librdkafka-reference
A simply re-org folder include necessary header/c files for compiling, and a release folder with pre-compiled dll/lib files. You will alwasy need this for runtime anyway. 

## Prepare for installation

Clone this repo to your C driver. It's highly recommended to cloen to the folder c:\confluent-kafka-python, it will make the rest of this document much easier.

Download & install VC++ 2013 redistribution package, you can download from Microsoft @ https://www.microsoft.com/en-us/download/details.aspx?id=40784

Optional, if you want to build by youself, plase download and install OpenSSL package from https://slproweb.com/products/Win32OpenSSL.html. Again, it's a pre-compiled package, and I won't recommend you to compile OpenSSL by yourself, it will require more source codes to be downloaded to your local disk.... You can download both 32 & 64-bit but not the latest version. Version v 1.0.2 works, not the latest one.

### Set up system variables

Please set up the following 3 system variables before installing/compiling. If you clone this repo to a different location on your local driver, please change the value of variable accordingly.

INCLUDE=C:\confluent-kafka-python\librdkafka-reference

LIB=C:\confluent-kafka-python\librdkafka-reference\release

PATH=C:\confluent-kafka-python\librdkafka-reference\release

### Install Python pacakge

#### start a new command windows after setting up the system variables above
#### cd C:\confluent-kafka-python\confluent-kafka-python-0.11.4
#### python setup.py install

It'll be very quick, since it simply install the pre-compiled pyd file.

### Test package




