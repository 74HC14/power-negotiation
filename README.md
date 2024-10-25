# Power Negotiation
This is a repo describing an experimental protocol for negotiating 5-50V DC power demand between source and load, for systems in the 0-40A range. Lower voltages might be possible by having additional power supply lines. Higher voltages and currents may be possible. Loads will be able to be placed in parallel, while sources will be able to be placed in series. Sources may be as simple as batteries or fixed supplies, or as complicated as variable power supplies that can set a voltage and/or current output.

### Hardware
The key power connector of this protocol will be the DA7W2 D-sub connector, with male plugs on the load, and female sockets on the source, as to reduce short-circuit risk. The two large pins carry the power, while the 5 smaller pins carry the communication signals. Other connectors, such as the DB9W4 D-sub, might be an option for multi-rail supplies. All cables will have a single plug on one end, and a single socket on the other end, and have no electronics contained. There will also be splitter boxes, which are required to plug loads in parallel, and combiner boxes, which are required to plug sources in series. Each communication line in these boxes will be commoned together, no active electronics is required in these splitter and combiner boxes.

Inside the load and source will be load or source circuit board respectively, referred to as "key"s. The source key alone has the capability to measure current. There needs to be a MOSFET present to shut off the current flow, in a standardised location in either the source or load key. Both keys have the capability to measure the voltage of the power rail. It Is likely that the keys will contain LEDs for diagnostics and status. The keys may be connected to external hardware, such as buttons, displays, sensors, and such, or they may communicate to another MCU board.

The source key's communication lines are optically isolated from its power rails, in order to allow series loads. The communication lines on all keys need to have adequate protection circuitry, to be robust against shorting to other pins.

### Firmware
The protocol itself is undecided. A bus protocol like CAN or RS485 is most likely, but a distance optimised form of I2C may work also.

The firmware will handle negotiation between the load and source for current, voltage, possibly also noise and voltage, and various types of fault detection.

The load key would need to have brown-out fault prevention.

### Symbology
While no connection of sources and loads will cause damage under this protocol, not all sources and loads are compatible. An LED light load might require a constant current, while a source might only be able to provide a constant voltage, or a variable source can provide from 5 to 36V, but a battery wants to charge up to 48V, as examples. While the presence of diagnostic LEDs should indicate to the end user whether they can expect their system to be working (e.g. if their battery is charging), but language-agnostic symbols for establishing compatibility to the end user beforehand are a requirement.
