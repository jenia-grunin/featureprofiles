# gNOI-5.2: Traceroute Test

## Summary

Validate that the device supports traceroute functionality using different
source, destination, max_ttl, do_not_fragment and L4Protocols.

## Procedure

*   Issue gnoi.system Traceroute command. Provide following parameters:

    *   Destination: populate this field with the
        *   target device loopback IP address
        *   TODO: an IP-in-IP tunnel-end-point address
        *   TODO: an address matching regular non-default route
        *   TODO: an address matching the default route
        *   TODO: an address requiring VRF fallback lookup into default vrf
        *   TODO: supervisor's physical management port address
        *   TODO: floating management address
    *   Source: populate this field with
        *   loopback IP address
        *   regular interface address
        *   TODO: an IP-in-IP tunnel-end-point address
        *   TODO: supervisor's physical management port address
        *   TODO: floating management address
    *   VRF:
        *   TODO: Set the VRF to be management VRF, TE VRF and default fallback
            VRF
    *   Max_TTL: Check the following cases of TTL values:
        *   Not set(default of 30)
        *   TODO: Set to -1: *Check if test is abandoned once TTL reaches higher
            value(of say 100)
        *   Set to 1
        *   TODO: Set to 255
    *   Do_not_fragment: Check the following cases when DF bit is:

        *   Set: *Intermediate hop router should have link MTU set to less than
            the traceroute packet size.

        *   TODO: Unset

    *   Size:

        *   Set to min packet size of 64, ethernet packet size of 1512, max mtu
            of jumbo frame 9202, and value slightly bigger than the egress
            interface MTU of a transit router to test do_not_fragment.
        *   TODO: verify these for vlan tagged vs untagged packets. May need +4
            bytes

    *   L4Protocol: set as:

        *   ICMP
        *   TCP
        *   UDP