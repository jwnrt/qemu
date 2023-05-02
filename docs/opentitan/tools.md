# OpenTitan QEMU tools

All the OpenTitan tools and associated files are stored in the `scripts/opentitan` directory.

## Execution wrappers

Launching a QEMU VM with the right option switches may rapidly become complex due to the number
of options and the available features. Several helper tools are provided in the `scripts/opentitan`
directory to help with these tasks.

* [`pyot.py`](pyot.md) can be used to run unit tests and OpenTitan tests
* `otboot.sh` is a wrapper script to build image files and execute a ROM/ROM_EXT/BL0 execution
  session.
* `otrun.sh` is a wrapper script to build image files and execute an OpenTitan test.
* `ottests.sh` is a wrapper script to execute many OpenTitan tests and report a list of successes
   and failures.

## Companion file management

* [`otptool.py`](otptool.md) can be used to generate an OTP image from a OTP VMEM file and can be
  used to decode (some of the) encoded data in the OTP image.
* [`flashgen.py`](flashgen.md) can be used to generate a flash image with either a ROM_EXT and BL0
  signed files, or a single OpenTitan signed test files.
* `swexit.py` is a tiny Python script to generate the simplest RISC-V executable (with no need for
  a RISC-V toolchain) that is used to ensure the QEMU OpenTitan machine can start up and quit.

## Development

* [`checkregs.py`](checkregs.md) is an internal tool design to check the discrepancies between
   OpenTitan generated register definition files and their QEMU counterparts. It is only useful to
   develop the machine itself.
* `devproxy.py` is a Python module that provides an API to remote drive the [DevProxy](devproxy.md)
  communication interface.
* [`gdbreplay.py`](gdbreplay.md) is a basic GDB server that can be used to replay Ibex execution
  stream from a QEMU execution trace.
* `mbbdef.py`] is a simple Python tool to extract multi-bit bool definition from OpenTitan' HJSON
  configuration file
* `ot-format.sh` is a simple shell wrapper to run clang-format (code formatter) on OpenTitan files
* `ot-tidy.sh` is a simple shell wrapper to run clang-tidy (C linter) on OpenTitan files
* `present.py` implements the Present 128-bit scrambler/descrambler used in OTP image files for
  HW digest verification.
* `treillis/` directory contains the test application to test the [GPIO](gpio.md) device.
* [`uartmux.py`](uartmux.md) is a tiny stream wrapper to help dealing with multiple QEMU output
  streams, typically multiple virtual UARTs.

## Python modules

* Available from `scripts/jtag` and `scripts/opentitan/ot`
* [JTAG mailbox](jtagmbx.md) provides an API to access the system side of the mailbox over JTAG/DMI
* [LC DMI](lc_ctrl_dmi.md) provides an API to control the Life Cycle controller over JTAG/DMI

## Configuration files

* `darjeeling-ocd.cfg` is a sample configuration file for OpenOCD to connect to the JTAG interface
* `clang-format.yml` is the configuration file for clang-format used for all OpenTitan and Ibex
  source files
* `clang-tidy.yml` is the configuration file for clang-tidy used for all OpenTitan and Ibex source
  files
* `.flake8` is the configuration file for the Python Flake8 linter for OT tools
* `.pylintrc` is the configuration file for the Python PyLint linter for OT tools