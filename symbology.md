# Symbology
There are nine forms of loads and sources, consisting of the convolution of three voltage classes:
- V CLASS (A) - unregulated voltage, e.g. MAX 28.0V MIN 21.0V
- V CLASS (B) - limited voltage, e.g. 12.8V ±2V, 36.0V ±0.5V
- V CLASS (C) - variable voltage, e.g. 11.0-13.0V, 0.0-25.0V

and three current classes:
- I CLASS (1) - unregulated current, e.g. MAX 1.0A
- I CLASS (2) - limited current, e.g. 2.5A ±0.1A
- I CLASS (3) - variable current, e.g. 0.0-5.0A

Compatibility is hierarchical, for example a Class B source can power a Class A load, all else permitting, but not the other way around.

All class 1 supplies are capable of PWM regulation of their output.

The only valid sources are B1, B2, and C3. A1 is an invalid state for a source OR a load. Other loads are viable, but most are unlikely besides B1 and C2.

For constants, the load's allowable input range needs to be broader than the source's output range.
For variables this relationship is flipped, the variable source needs to be able to supply a broader range than the variable range requested by the load.

Some examples of source labels include:
- B1 - 11.1V ±1.5V, MAX 3.0A (a 3S lithuim ion battery)
- B1 - 12.0V ±0.5V, MAX 10.0A (an AC-DC power adapter)
- B2 - 42.0V ±1V, 2.5A ±0.1A (an LED power supply) [^1]
- C3 - 0-28.0V, 0-15.0A (a benchtop power supply)

Some examples of load labels include:
- A2 - MAX 28.0V MIN 21.0V, 2.0A ±2.0A (an LED without dimming)
- A3 - MAX 28.0V MIN 21.0V, 0.0-4.0A (an LED with dimming circuit) [^2]
- B1 - 24.0V ±3.0V, MAX 25.0A (a 3D printer)
- B2 - 5.0V ±0.5V, 0.2A ±0.1A (a prototype circuit with short circuit protection)
- C1 - 0 - 12.0V, MAX 1.5A (a variable speed fan) [^3]
- C2 - 9.6V - 12.6V, 0.5A ±0.5A (a 3S lithium ion battery to be charged)

[^1]: The B marker does not convey that an LED power supply will decrease its voltage when regulating current. Maybe it should be an A2 (MAX 42V) instead of a B2, but this doesn't carry the nuance that an LED load can fry if operated in constant voltage range near its MAX value while an LED supply can safely operate in constant voltage mode at its MAX value.
[^2]: Any LED with a dimming circuit should still be able to run off a compatible class 2 source, there should be a way of conveying that such a load will work on a class 2 source but will have more features on a class 3 source.
[^3]: Any variable speed fan should be able to run off a fixed source, which is not conveyed. Additionally, PWM may be better for fans than variable voltage, perhaps all supplies should be capable of PWM when operating in constant voltage mode, making this fan and similar loads into B1s instead.
