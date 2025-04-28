FAQ:
- where are the keymaps declared?
The keymaps are declared in the following files:

config/eyelash_sofle.keymap: This file contains the keymap declaration for the eyelash_sofle board. It defines the layers and bindings for the keyboard.

eyelash_sofle.keymap: This file also contains keymap definitions, including layer bindings and sensor bindings, for the eyelash_sofle configuration.

Both files define the keymap structure, including layers, key bindings, and sensor bindings, for the keyboard.


- what does &trans mean? What would happen if I press this button and layer combination?
In ZMK, &trans is a special keycode that stands for "transparent." It means that the key does not have a specific binding on the current layer and will "fall through" to the same key position on the next lower active layer. If no lower layer has a binding for that key, the key will effectively do nothing.

    Behavior When Pressing &trans
    If a lower layer is active and has a binding for the same key position:
    
    The key will behave as defined in the lower layer.
    If no lower layer has a binding for the same key position:
    
    The key will do nothing when pressed.
    Example
    Suppose you have the following layers:
    
    Layer 1
    Layer 0
    If Layer 1 is active and you press the first key (&trans), it will "fall through" to Layer 0 and trigger &kp ESC.
    If Layer 0 also had &trans for the same key, pressing it would do nothing.
    In your keymap, pressing a key bound to &trans will depend on the bindings in the lower layers. If no lower layer defines a behavior for that key, it will have no effect.


- what does &sys_reset mean? What would happen if I press this button and layer combination?
In ZMK, &sys_reset is a key behavior that triggers a system reset when pressed. This effectively reboots the microcontroller running the keyboard firmware.

What Happens When You Press &sys_reset?
Immediate Reset: The keyboard's microcontroller will immediately reset, restarting the firmware.
No Persistent Changes: This does not erase any settings or configurations unless explicitly programmed to do so. It simply reboots the device.
Example in Your Keymap
In your keymap, &sys_reset is defined in layer_2 of eyelash_sofle.keymap:

If you press the key bound to &sys_reset while layer_2 is active, the keyboard will reboot immediately. This can be useful for debugging or applying changes that require a restart.


- what does &soft_off mean? What would happen if I press this button and layer combination?
In ZMK, &soft_off is a key behavior that puts the keyboard into a low-power "soft off" state. This is typically used to conserve battery power when the keyboard is not in use.

What Happens When You Press &soft_off?
Low-Power State: The keyboard will enter a low-power mode, turning off most of its functionality, including Bluetooth and RGB lighting (if enabled).
Wake-Up: To wake the keyboard from this state, you usually need to press a specific key or reset the keyboard, depending on your hardware configuration.
Example in Your Keymap
In your keymap, &soft_off is defined in layer_2 of eyelash_sofle.keymap:

If you press the key bound to &soft_off while layer_2 is active, the keyboard will enter the low-power "soft off" state. This is useful for saving battery when the keyboard is not in use.


- what does &bootloader mean? What would happen if I press this button and layer combination?
In ZMK, &bootloader is a key behavior that triggers the keyboard's microcontroller to enter bootloader mode. Bootloader mode is used to flash new firmware onto the keyboard.

What Happens When You Press &bootloader?
Enter Bootloader Mode: The keyboard's microcontroller will immediately switch to bootloader mode. This mode allows the device to accept new firmware uploads via tools like nrfutil or west.
Keyboard Stops Functioning Temporarily: While in bootloader mode, the keyboard will not function as a regular input device until it is restarted or new firmware is flashed.
Flashing Firmware: You can use this mode to upload new firmware to the keyboard.
Example in Your Keymap
In your keymap (config/eyelash_sofle.keymap), &bootloader is defined in layer_2:

If you press the key bound to &bootloader while layer_2 is active, the keyboard will immediately enter bootloader mode. This is useful for updating the firmware or debugging. To exit bootloader mode, you typically need to reset the keyboard (e.g., by unplugging and replugging it).


- what does &RGB_EFF mean? What would happen if I press this button and layer combination?
In ZMK, &rgb_ug RGB_EFF is a key behavior that cycles through the available RGB lighting effects for the keyboard's underglow. This behavior is typically used to change the visual effects of the RGB lighting, such as switching between static colors, breathing effects, rainbow effects, or other animations.

What Happens When You Press &rgb_ug RGB_EFF?
Cycle RGB Effects: Pressing the key bound to &rgb_ug RGB_EFF will switch the RGB underglow to the next available lighting effect in the predefined sequence.
Wrap Around: Once the last effect in the sequence is reached, pressing the key again will cycle back to the first effect.
Example in Your Keymap
In your keymap (config/eyelash_sofle.keymap), &rgb_ug RGB_EFF is defined in layer_1:

If you activate layer_1 and press the key bound to &rgb_ug RGB_EFF, the RGB underglow effect will change to the next effect in the sequence. This is useful for customizing the keyboard's appearance dynamically.


- what does &RGB_EFR mean? What would happen if I press this button and layer combination?
In ZMK, &rgb_ug RGB_EFR is a key behavior that reverses the current RGB lighting effect. This means it cycles the RGB effect in the opposite direction compared to &rgb_ug RGB_EFF.

What Happens When You Press &rgb_ug RGB_EFR?
Reverse RGB Effect: Pressing the key bound to &rgb_ug RGB_EFR will switch the RGB underglow to the previous effect in the sequence of available lighting effects.
Wrap Around: If the first effect in the sequence is active, pressing this key will wrap around to the last effect.
Example in Your Keymap
In your keymap (config/eyelash_sofle.keymap), &rgb_ug RGB_EFR is defined in layer_1:

If you activate layer_1 and press the key bound to &rgb_ug RGB_EFR, the RGB lighting effect will cycle to the previous effect in the sequence. This is useful for quickly navigating backward through the available RGB effects.


- what does &RGB_SPI mean? What would happen if I press this button and layer combination?
In ZMK, &rgb_ug RGB_SPI is a key behavior that increases the speed of the current RGB lighting effect. This is used to make animations, such as breathing or rainbow effects, run faster.

What Happens When You Press &rgb_ug RGB_SPI?
Increase Animation Speed: Pressing the key bound to &rgb_ug RGB_SPI will increase the speed of the active RGB lighting effect.
Effect-Specific Behavior: The exact impact depends on the currently active RGB effect. For example:
In a breathing effect, the breathing cycle will speed up.
In a rainbow effect, the colors will transition faster.
Example in Your Keymap
In your keymap (config/eyelash_sofle.keymap), &rgb_ug RGB_SPI is defined in layer_1:

If you activate layer_1 and press the key bound to &rgb_ug RGB_SPI, the speed of the current RGB lighting effect will increase. This is useful for customizing the appearance of your keyboard's RGB animations dynamically.