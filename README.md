
for L01F kernel 

Source fixed example)
In file included from drivers/video/msm/mdss/mdss_mdp_trace.h:255:0,
                 from drivers/video/msm/mdss/mdss_mdp.c:61:
include/trace/define_trace.h:79:43: fatal error: ./mdss_mdp_trace.h: No such file or directory

$ find . -name mdss_mdp_trace.h
./drivers/video/msm/mdss/mdss_mdp_trace.h

$ vi ./drivers/video/msm/mdss/Makefile
CFLAGS_mdss_mdp.o += -Idrivers/video/msm/mdss

How to make dt.img
$ dtbTool -s 2048 -o arch/arm/boot/dt.img -p scripts/dtc/ arch/arm/boot/

How to remake boot.img

1. unpack boot.img 
$ mkboot boot.img boot

2. repack boot.img 
$ cp ./lineage-17.1/arch/arm/boot/zImage boot/kernel
$ cp ./lineage-17.1/arch/arm/boot/dt.img boot/dt.img
$ mv boot.img boot.img.old
$ mkboot boot boot.img

3. for secure booting error (bump)
$ python2 open_bump.py boot.img
$ mv boot_bumped.img boot.img

