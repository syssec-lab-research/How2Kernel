ifneq (${KERNELRELEASE},)
obj-m += smash.o

else
KERNEL_SOURCE := ../../kernel_source/linux-4.18.16/
ccflags-y := -fno-stack-protector -fno-stack-protector-all
PWD := $(shell pwd)
default:
	# Compile for the same architecture as the host machine
	$(MAKE) -C $(KERNEL_SOURCE) SUBDIRS=${PWD} modules
arm:
	# Cross compile for arm64/aarch64 architecture - Cross compiler needed !!!  
	ARCH=arm64 CROSS_COMPILE=aarch64-linux-gnu- $(MAKE) -C $(KERNEL_SOURCE) SUBDIRS=${PWD} modules
clean:
	# Cleans the Directory - removes all the files that were created
	$(MAKE) -C $(KERNEL_SOURCE) SUBDIRS=${PWD} clean
endif
