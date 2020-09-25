AES Finder
==========

Utility to find AES keys in running process memory. Works for 128, 192 and 256-bit keys.


Usage
-----

Use gcc/clang:

    g++ -O3 -march=native -fomit-frame-pointer aes-finder.cpp -o aes-finder

To search for keys in process with id = 123, execute following:

    ./aes-finder -123

To search for keys in any process with name chrome.exe, execute following:

    ./aes-finder chrome.exe

Now you can see what kind of AES keys are used in your favorite application!

### sshd on Linux

    $ sudo ./aes-finder sshd
    Searching PID 3307 ...
    Searching PID 10428 ...
    Searching PID 10430 ...
    [0x7fc39b3132d0] Found AES-128 encryption key: df435cfcd8830df858203c0ad2db51ca
    [0x7fc39b313450] Found AES-128 encryption key: 0ad922797aba3078841bc298104bb39a
    Done!

Notes
-----

* does not work on whitebox AES keys
* 32-bit binary can search only in 32-bit processes, 64-bit binary can search in both - 32 and 64-bit ones
* "encryption key" means that this key can be used for encryption or decryption
* "decryption key" means that this key most likely is used only for decryption
* on Linux requires at least v3.2 kernel (process_vm_readv syscall)

License
-------

Public Domain. Do whatever you want!
This is just a fork of https://github.com/mmozeiko/aes-finder
