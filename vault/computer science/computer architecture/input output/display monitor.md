- computers reserve a region in ram to interact with a display monitor
- this region is called **screen memory map**
- screen memory map is defined by the display monitor, based on its physical properties
- if the monitor has many pixels, it requires more memory
- if the monitor is black and white, it requires less memory

![[display monitor 2025-07-16 18.44.27.excalidraw]]

# pixel
- an pixel can assume from two states (black and white), to 16,581,375 states (rgb)
- rgb pixel is composed of 3 bytes:
	- r: 00000000
	- g: 00000000
	- b: 00000000
# screen memory map for rgb pixel
- if a display has 10x10 rgb pixels, it will need:
	- 10x10 = 100 pixels
	- 100x3 = 300 bytes
	- 300x8 = 2,400 bits
- 2400 bits of memory or 300 bytes of memory
- in a 32 bit system, 75 registers (2400/32) are required
- each 32 bit register can store 1.34 pixels
- to improve efficiency, each color can be stored separately
- each 32 bit register can store 4 colors (32/8)
	- so you need at least 3 register
	- to store at least 4 pixels
	- efficiently
	- ram\[0]\[00-07]: red pixel 1
	- ram\[0]\[08-15]: red pixel 2
	- ram\[0]\[16-23]: red pixel 3
	- ram\[0]\[23-31]: red pixel 4
	- ram\[1]\[00-07]: green pixel 1
	- ram\[1]\[08-15]: green pixel 2
	- ram\[1]\[16-23]: green pixel 3
	- ram\[1]\[23-31]: green pixel 4
	- ram\[2]\[00-07]: blue pixel 1
	- ram\[2]\[08-15]: blue pixel 2
	- ram\[2]\[16-23]: blue pixel 3
	- ram\[2]\[23-31]: blue pixel 4
- you need 75 **r**egisters (100**p** x 3**r**/4**p**) to store 100 **p**ixels
