% The OSI Model
% Vithushan Sutharsan

# Introduction

The OSI model is often used to talk about networks in parallel with the TCP/IP
model (the differences are minor). The OSI model describes a network with the
following seven layers: application, presentation, session, transport, network,
data-link, physical. Now networking solves the problem of how two or more hosts
should communicate. Hence to understand the OSI model we must look at how each
layer provides an abstraction to facilitate this communication.

# The Physical Layer

We can start moving through this abstraction by first looking at how two hosts
would communicate, then on to how multiple hosts would communicate. There
must be a physical connection between the hosts for signals to be transmitted to
each other. This is the physical layer, the standards on this layer then define
over what physical medium the hosts communicate and how bits would be
represented over this physical medium during this communication. The standards
we commonly use on this layer are defined by [IEEE 802](https://www.ieee802.org/).
Although these standards are more complex, we might start understanding the
physical layer by thinking about a very primal standard we made ad hoc. Let's
say host X and Y want to communicate and agree on the following standard: both
are connected to the ends of one wire; when X wants to send a `1` bit, it sets
the voltage on the wire to +5V, and when it wants to send a `0` bit, it sets
the voltage to -5V. The host must update the wire every millisecond. Host Y
agrees to read the voltage on the wire every millisecond, and records +5V as a
`1` bit and -5V as `0`. We could represent this communication with a
time-sequence diagram, ignoring the voltage changes as the hosts have already
agreed to the standard.

```
           Host X        Physical Link         Host Y        
    send 0   |                                   |           
 ----------->|-___            0                  |           
             |    -__________________________    | receive 0 
             |                               --->|---------->
             |                                   |           
    send 1   |                                   |           
 ----------->|-___            1                  |           
             |    -__________________________    | receive 1 
             |                               --->|---------->
             |                                   |           
```

The physical layer by itself would pose a few problems, primarily because
electric signals can be interfered with and the clocks of the hosts may not be
in sync.
