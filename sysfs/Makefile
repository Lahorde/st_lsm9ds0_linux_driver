obj-m += lsm9ds0_acc_mag.o
obj-m += lsm9ds0_gyr.o

ccflags-y := -DDEBUG

all:
		make -C /lib/modules/$(shell uname -r)/build M=$(PWD)  modules 

clean:
		make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean
