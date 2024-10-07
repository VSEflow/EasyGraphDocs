# Troubleshooting

!!! example "Work-in-progress: This section may be incomplete as it is based on customer feedback and sales support cases"

## :material-chat-question: General problems

!!! question "The live graph shows zero even though flow is present and the M12 connector is plugged in"
    1. Check if the port config if set right for both flowmeters (1/2-channel).

    2. Check if the sensor is supplied with power.

    3. If all else fails, try reconnecting the datalogging device.

!!! question "Help: I can't use the slider, it always shows the input value"
    ![bug](img/bug.png)
    
    This is a bug that happens when you use your `CTRL` key. You can fix this by pressing and holding the `CTRL` key on your keyboard and left-clicking on the bugged slider. Now release the `CTRL` key, press somewhere else in EasyGraph and then try again. It should be fixed!

## :fontawesome-brands-usb: About log.flow

!!! question "What does "internal boost converter" mean?"
    The internal boost converter allows the user to generate a stable 24V output voltage for supplying the flowmeters by only using the USB connection (and no DC-Jack!). It is a ciruit that will transform the 5V bus voltage up to 24V but with a low current capability (due to USB power draw limitations). Therefore it is advisable to only connect low power flowmeters with a total current consumption $I<50 \textrm{ mA}$ to the log.flow if using the converter. Otherwise the internal circuit will overheat and will not be able to generate a steady power supply.

    The internal boost converter is practical on mobile setups/notebooks where no external power is available.

    For reference: A testbox TB2 pulse generator uses $30  \textrm{ mA}$, while a VSI+ preampilfier uses about $36 \textrm{ mA}$.
