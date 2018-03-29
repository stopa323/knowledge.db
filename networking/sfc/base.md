## Briefly
- technique to interconnect network services in a specific manner
- packet traverses network based on order in which services have been chained 
- "physical" connection order stops matter

## Architecture
- independent from underlaying forwarding topology
- packets are classified on ingress and forwarded through the set of function for processing
- may be reclassified as the result of that processing
- single network administrative domain assumed

## SFC elements
- classifier: element that performs classification
- service function chain: ordered set of abstract service functions and ordering constraints 
that must be applied to traffic as a result of classification e.g. Firewall
- service function: a function that is responsible for speciffic treatment of received packets e.g. filtering, parental control, DPI
- service function forwarder: element responsible for forwarding traffic to one or more connected service functions according to 
information carried in SFC encapsulation
- service function path: constrained specification of where the packets assigned to a certain function path must go; provides level of
indirection between fully abstract notion and fully specified notion of where exactly which SF the packet will visit e.g.
`DPI_1 -> vFW_3 -> ACL_3 -> some_FIREWALL -> vRTR10`
- sfc encapsulation: provides sfp identification + extra metadata 
- rendered service path: sequence of actual visited SFFs & SFs
- sfc proxy: removes and inserts SFC encapsulation on behalf of sfc-unaware service function

## References
[1] https://tools.ietf.org/html/rfc7665
[2] https://www.sdxcentral.com/sdn/network-virtualization/definitions/what-is-network-service-chaining/
