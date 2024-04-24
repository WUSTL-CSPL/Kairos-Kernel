Linux kernel
============

For building the kernel with DFA options (Please use Ubuntu 20.04 as it ships with Linux kernel version 5.11):


1. Download the repository

    ```
    $ git clone https://github.com/WUSTL-CSPL/Shore-Kernel ~/Shore-Kernel 
    ```

2. Install the following dependencies:
    ```
    $ sudo apt-get install git fakeroot build-essential ncurses-dev xz-utils libssl-dev bc flex libelf-dev bison dwarves zstd
    ```

3. Copy the config file from current Ubuntu Distro
    ```
    $ cd ~/Shore-Kernel 
    $ cp /boot/config-$(uname -r) .config
    ```


4. Enable `Shore Scheduling` in the .config file
    ```
    $ make menuconfig
    ```
    Enable the `Shore Scheduling` class in the menuconfig GUI Menu


5. Disable the trusted keys for compilation
    ```
    $ scripts/config --disable SYSTEM_TRUSTED_KEYS
    ```

6. Then issue `make` command (-j8 for multi-threading) and choose __default__ options for any prompt options
    ```
    $ make -j8
    ```

7. Upon sucessfully make, issue make modules_install (may require sudo)
    ```
    $ sudo make modules_install
    ```

8. Then issue make install (require sudo)
    ```
    $ sudo make install
    ```

9. Reboot the system.
    Press and hold **_shift_** while boot, choose advanced option and choose the newly compiled kernel to boot (linux 5.11.0+ in our case).
