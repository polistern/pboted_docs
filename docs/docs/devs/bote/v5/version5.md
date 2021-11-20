# Protocol version 5 (DRAFT)

!!! warning "Warning"

    While the 5th version of the I2P-Bote protocol is in draft state, there may be some inconsistency. 

!!! note "Note"

    All changes concerning version 5 are marked with comment `[VER 5]`
    At the moment, not all protocol changes are used by **pboted**

At the moment, *PeerList* packets of 5th version have been implemented to support current types of I2P destination.   
PeerList packets of 4th version are supported, older Java nodes respond but do not send requests due to protocol restrictions at DSA I2P destinations.

Full support of 5th version of I2P-Bote protocol is expected in **pboted** of version 1.0.0.

You can see the implementation details in this section.

Proposals for improving the 5th version of the protocol are accepted for consideration.
