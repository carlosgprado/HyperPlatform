HyperPlatform
==============

Introduction
-------------
HyperPlatform is an Intel VT-x based hypervisor (a.k.a. virtual machine monitor)
aiming to provide a thin platform for research on Windows. HyperPlatform is 
capable of monitoring a wide range of events, including but not limited to, 
access to virtual/physical memory and system registers, occurrence of interrupts
and execution of certain instructions.

Researchers are free to selectively enable and/or disable any of those event
monitoring and implement their own logic on the top of HyperPlatform. Some 
potential applications are:
- Analyzing kernel mode rootkit
- Implementing virtual-machine-based intrusion prevention system (VIPS) 
- Reverse-engineering the Windows kernel 

Two of those ideas are already implemented: MemoryMon detecting execution of
kernel memory, and GuardMon monitoring some of PatchGuard activities. See their
project pages for more details:
- https://github.com/tandasat/MemoryMon
- https://github.com/tandasat/GuardMon


Advantages
-----------
HyperPlatform is designed to be easy to read and extend by researchers,
especially those who are familiar with Windows. For instance:
- HyperPlatform run on Windows 7, 8.1 and 10 in both 32 and 64 bit architectures
  without any special configuration (except for enabling Intel-VT technology).
- HyperPlatform compiles in Visual Studio and can be debugged though Windbg
  just like a regular software driver.
- Source code of HyperPlatform is written and formatted in existing styles
  (Google C++ Style Guide and clean-format), and well commented.
- HyperPlatform has no dependencies, supports use of STL and is released under
  a relaxed license.

For more details, see the HyperPlatform User's Documents.
- https://github.com/tandasat/HyperPlatform/tree/master/Documents


Build
------
To build HyperPlatform, the following are required.
- Visual Studio Community 2015 Update 1
 - https://www.visualstudio.com/en-us/news/vs2015-update1-vs.aspx
- Windows Software Development Kit (SDK) for Windows 10
 - https://dev.windows.com/en-us/downloads/windows-10-sdk
- Windows Driver Kit (WDK) 10
 - https://msdn.microsoft.com/en-us/windows/hardware/hh852365.aspx


Installation and Uninstallation
--------------------------------
Download an archive file for compiled files form the release page.
- https://github.com/tandasat/HyperPlatform/releases

To install the driver, extract the archive file and use the 'sc' command. For
installation:

    >sc create HyperPlatform type= kernel binPath= C:\Users\user\Desktop\HyperPlatform.sys
    >sc start HyperPlatform

For uninstallation:

    >sc stop HyperPlatform
    >sc delete HyperPlatform


Note that the system must support the Intel VT-x and EPT technology to
successfully install the driver. See a "Using VMware Workstation" section in the
User's Documents.


Output
-------
All logs are printed out to DbgView and saved in C:\Windows\HyperPlatform.log.


Supported Platforms
----------------------
- x86 and x64 Windows 7, 8.1 and 10
- The system must support the Intel VT-x and EPT technology


License
--------
This software is released under the MIT License, see LICENSE.
