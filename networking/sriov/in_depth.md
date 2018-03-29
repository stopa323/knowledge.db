## Traditional ethernet packet processing
- packet comes in to the device
- IRQ fired, core A assigned to handling all interuptions stops current work and determines to which VM packet should be passed
- interupts core B running that VM
- core B copies that packet to memory space of VM and continues processing
- core A can continue its previous operations until the next IRQ occurs

Drawbacks:
- single core handling IRQ, easily overloaded with high traffic
- each packet usualy interupts 2 cores (IRQ handling & VM memory copy)

## Intel VMDq
- breaks incomming packets into queues placed on NIC (based on MAC/VLAN TAG)
- each queue has its own interrupt allowing each core to have different queue assigned to it
- spreads workload across multiple cores improving performance

Drawbacks:
- hypervisor still has to copy packet from NIC to VM memory and vice verse

## SR-IOV
- each VF has dedicated Rx/Tx queues + "lightweight" resources like registers (just enough to be able to transfer data)
- each VM is directly assigned virtual resources (VFs) by hypervisor
- when VM boots up it probes config, hypervisor tells VM what it has and point to propper registers
- driver loads up and configures descriptors telling exactly where to copy any packet that comes in/out
- pipeline is similar to VMDq with one exception that no core is obligated to copy packet to VM memory
- instead based on descriptor configuration packet is DMAed directly to VM memory
- hypervisor does not "touch" the packet

## References
[1](https://www.youtube.com/watch?v=hRHsk8Nycdg)
