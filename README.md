# CKDF-WG
The Common Keyboard Format Descriptor working group.

This is a community effort to build a new, common format to define the physical and electrical characteristics of keyboards.

# Why does this exist?

An entire ecosystem of tooling exists to make custom keyboards, from web-based layout editors, to PCB and case generation tools, to rendering pipelines, to the actual firmware that runs on the keyboards themselves.  Many of these tools are entirely manual processes, and others use KLE or other loosely defined common formats to bootstrap keyboard initialization and then use internal formats for further work.

There exists no fully-speced keyboard definition format that can be used to layout, design, and finally implement a keyboard across multiple tools.

# What about KLE?

KLE, or the keyboard-layout-editor.com format, is the only real common standard that exists for sharing keyboard definitions.  The [project](https://github.com/ijprest/keyboard-layout-editor) hasn't seen any major updates in several years, and the KLE format itself doesn't match most common JSON file format conventions and has several opportunities to create a more portable and understandable format.  The KLE author has [another project, called kle-serial](https://github.com/ijprest/kle-serial) which provides a more user-friendly api to consuming the files, but it's a runtime only lib and isn't specified as a format.  The KLE format also lacks any deeper description of a keyboard implementation beyond a single physical layout, and doesn't fully describe an implementation in a deep enough way for a firmware or layout tool to take it and build upon it.

# Are there any other options?

The [VIA specification](https://caniusevia.com/docs/specification) is probably the next most relevant candidate to be a generic keyboard definition format.  The closed-source nature and specific focus (defining keyboards to be used in VIA for QMK-based boards) makes it a poor choice for projects to use as a generic format, because it doesn't have any guarantee of future support nor does it have mechanisms for extending the format beyond what wilba can provide.

# What are the top level goals?

Ideally, this working group would produce a well specified format that can fully or partially define a keyboard or components of a keyboard.

*This format should provide flexibility to define either a component for people to build off (e.g. a common 60% PCB layout), some set of components for tool interchange, or to fully specify an entire project including case characteristics.*

Things we may want to define within this file include:
* Physical key layout
* Additional optional layouts
* Default and common keymaps
* LED configuration, including PKRGB, underglow, and indicator LEDS
* Auxilary input and output types, such as rotary encoders, joysticks and OLED screens
* PCB physical properties (USB port location, mounting screw locations)
* Case constraints
* Specific case characteristics (e.g. bezel sizes and fillets, or even a full 3D model of case components)
* Electrical characteristics - which MCU is used, and which GPIOs are used for which inputs and outputs to assist with firmware implementation

# What will this format be?

Without a reason to do something else, this will be a JSON based format.
