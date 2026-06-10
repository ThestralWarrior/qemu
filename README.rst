This fork of QEMU implement the support for SCSI Tape Emulation.

The project is proposed during GSoC 2026 but there wasn't enough slot allocated by Google so it wasn't selected.

QEMU provides functionality to emulate SCSI hard discs and SCSI CD-ROM drives, but lacks an emulated SCSI TAPE drive. The goal of this project is to develop an emulation for a SCSI TAPE drive which is backed by a file in the host filesystem, similar to an ISO file which is used to emulate a CD-ROM drive.

This will involve writing code to emulate a SCSI TAPE drive and storing the data in a file, adding test coverage, and documenting how to use the new feature. Finally, it should be possible to backup files from the current emulated OS to tape via standard tools, e.g. tar and mt on Linux.

Current Status:
- The basic set of require set up has been done which is having the [REALIZE, UNREALIZE, INQUIRY, READ, TEST_UNIT_READY] 

Right now the current implementation is being tested to booted the MPE/iX which boots expects to see a tape after modification to seabios-hppa by Helge Deller. It being tested on an emulated HP A400 and HP B160L. It HARD Booted successfully but hits a SeaBios trap #9, at 0x0:0x11700, IIR=0x0, IIR addr=0x0:0x0 due to the wrong data is ready from the virtual tape after boot 

File: 

To Reproduce:



Fix:
Implement a TAP file format in the SCSI driver


Todo:
- Implement other SCSI command 
- Make it work with Linux utils like tar and mt
- Testing and Documentation 


Project Mentor - Helge Deller <deller@gmx.de>
