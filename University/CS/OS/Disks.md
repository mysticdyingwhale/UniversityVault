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

- Capacity: Terabytes
- Platters: 8
- Number of cylinders: 10 thousands or more
- Sectors per track: ~1000
- RPM: 10,000
- Transfer rate: 50-150MB
- MTBF: ~1 million hours


### Interface to disk

A modern disk drive is non-volatile storage consisting of a large number of sectors (512-byte blocks), each of which can be read or written.

The disk maps logical sector numbers to physical sectors. 

Sectors are numbered from 0 to n-1 for n sectors, so it helps to view the disk as an array of sectors, where 0 to n-1 is the address space. 

The disk does some things under the hood (invisible to OS):
- Zoning
	- puts more sectors on longer tracks
- Skewing
	-  sector 0 position varies by track
- Sparing
	- flawed sectors remapped elsewhere

### Performance Example

Spindle Speed: 12,000 RPM
Avg. Seek Time: 12ms
Transfer Rate: 128 MB/s
Sector: 512 bytes

Example Questions:
1. What is the throughput if doing 500 sector reads spread randomly over the disk and serviced in FIFO order?
2. Same q, but sequential reads

Answers:
1. Throughput = $\frac{\text{bytes}}{\text{time}} = \frac{500 \times 512 \text{ bytes}}{500 \text{ random reads}}$


We get rotational delay by:
$\frac{\text{minutes}}{12000 \text{rotations}} \times \frac{60s}{\text{min}} \times \frac 12 = \frac{60s}{24000 \text{half-rotations}} = \frac{1s}{400 \text{half-rotations}} = 2.5\frac{ms}{\text{half-rotation}}$ 

We get transfer time by:
$512 \text{bytes} \times \frac{1s}{128MB} \times 512 \text{bytes} = 4ms$

Seek time given as 12ms

$1 \text{ read} = \text{rotation delay + seek time + transfer time} = 2.5 \text{ms} + 12  \text{ms} + 4  \text{ms}$

Throughput = $\frac{\text{bytes}}{\text{time}} = \frac{500 \times 512 \text{ bytes}}{(14.5+4)500} = \frac{512B}{14.5ms} = 35 kbps$


2. Throughput = $\frac{\text{bytes}}{\text{time}} = \frac{500 \times 512 \text{ bytes}}{1 \text{ sequential read}}$

Avg rotational delay is the same

Seek time given as 12ms


We get transfer time by:
$512 \text{bytes} \times \frac{1s}{128MB} \times 500 \times 512 \text{bytes} = 2ms$


Throughput = $\frac{\text{bytes}}{\text{time}} = \frac{500 \times 512 \text{ bytes}}{16.5ms} = 15mbps$


