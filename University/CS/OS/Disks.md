# Disks
#cs 

Hard disks are a form of persistent storage (non-volatile)

### Geometry

- Track: Circle on a platter
- Sector: Chunk of a track
- Cylinder: all track of fixed radius on all platters
- Generally only one head active at a time
- Disk positioning system: Moves head to a track and keeps it there


Seek time refers to sending the disk head radially along the track to find the sector its looking for.

The largest point of delay in disk operations.

Seek: 
- 4 phases
	- Speedup
	- Coast at constant velocity
	- Slowdown
	- Settle - takes most time
		- Must settle in right place


### Performance

Components of total transfer time:
- Rotational Delay
- Seek Delay
- Transfer time


Seeking entire disk is less expensive due to amortization than seeking a segment of it. 

#### Common numbers

- Capacity: Terrabytes
- Platters: 8
- Number of cylinders: 10 thousands or more
- Sectors per track: ~1000
- RPM: 10,000
- Transfer rate: 50-150MB
- MTBF: ~1 million hours


### Interface to disk

A modern disk drive is non-volatile storage consisting of a large number of sectors (512-byte blocks), each of which can be read or written.

Sectors are numbered from 0 to n-1 for n sectors, so it helps to view the disk as an array of sectors, where 0 to n-1 is the address space.

The disk does some cool things under the hood (invisible to OS):
- Zoning
- Skewing
- Sparing
