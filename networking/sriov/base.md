# How does SR-IOV works?

- speciffication that allows single PCIe device to appear as multiple separate physical PCIe devices
- introduces idea of physical functions (PFs) and virtual functions (VFs)
- PFs are full-featured PCIe devices (configuration + data in/out manipulation)
- VFs are "lightweight" functions that lack of configuration (data manipulation only)
- BIOS & OS/hypervisor support is mandatory (must be aware which devices are not full PCIe)
- up to 256 (64 in practice) VFs per single device
- VFs have to be the same type as PFs
- possibility to configure switching between VFs directly on NIC (w/o extra switch)
- MR-IOV (multiple systems reuse single VFs)

# References
[1] https://blog.scottlowe.org/2009/12/02/what-is-sr-iov/

# See also
[InfiniBand](https://en.wikipedia.org/wiki/InfiniBand)
