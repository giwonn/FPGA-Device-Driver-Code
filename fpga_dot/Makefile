#Makefile for a basic kernel module

obj-m   := fpga_dot_driver.o

KDIR    :=$(IMX_KERNEL_PATH)
PWD     :=$(shell pwd)
APP		:= fpga_test_dot

all: driver app
#all: driver 

driver:
	$(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules ARCH=arm

app:
	arm-none-linux-gnueabi-gcc -static -o $(APP) $(APP).c

install:
	cp -a fpga_dot_driver.ko /home/suhak/nfsroot
	cp -a $(APP) /home/suhak/nfsroot
clean:
	rm -rf *.ko
	rm -rf *.mod.*
	rm -rf *.o
	rm -rf $(APP)
	rm -rf Module.symvers
	rm -rf modules.order
	rm -rf .tmp*
	rm -rf .fpga*
