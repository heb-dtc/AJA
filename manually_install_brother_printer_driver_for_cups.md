### Manual installation of Brother printer driver

1. make sure `cups` is installed and running on your system.
2. Brother distribute its drivers as `.deb` or `.rpm` package. To install them on archlinux, some extra tooling is needed to extract the file from these archives. This method explains how to use the `.rpm` file.
3. install the `rpmextract` tool.
4. download the LPR printer driver for the printer on the brother website. Make sure to choose the `rpm` file.
5. download the CUPSwrapper printer driver for the printer on the brother website. Make sure to choose the `rpm` file.
6. use `rpmextract.sh` to extract the content of both `.rpm` file.
7. copy the content of these file into the system.
8. run the `cupswrapper` script. (it was part of the file extracted from the rpm package!). This will install the driver and make it available via cups.
9. some of these drivers are 32 bits binaries so it might be necessary to have the 32 bit version of glibc installed on the system (on archlinux this is done via the multilib packages).

