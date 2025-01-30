## Panels

![mainwin](img/main_new2.png "Main EasyGraph window with panels")

The software's user interface is based on panels in a main window. By default, the main window consists of the big [**Live graph panel**](uiguide.md#live-graph-panel) in the middle, the [**device management panel**](#device-management-panel) on the left and a [**Live value panel**](uiguide.md#live-value-panel) on the right, but additional windows can be toggled using the [Window menu](uiguide.md#window). You can drag the panels out of the window by dragging on the title bar of each panel and dropping them. To re-dock them, press and hold the `SHIFT` key while dragging and use the overlay to position it. 

Previously saved recordings are shown in the [**recordings panel**](uiguide.md#recordings-panel) and open up as tabs of the [**Live graph panel**](uiguide.md#live-graph-panel). You can identify them by the `File:` prefix in the title bar.

### Live graph panel

#### Plot navigation

The plot window shows an XY-Plot of the measured data. While the X-Axis refers to the time, the Y-Axis refers to the actual value. There may be multiple seperate Y-Axes on the left and right side of the plot. This is useful to seperately display the different units of flowrate, volume and analog values. 

!!! info inline end "Hint: This applies to both the live plot and the file viewer"

Use your mouse to navigate the plot window:

- Clicking and dragging with the left mouse button on the plot moves it. 
- Clicking and dragging with the left mouse button on an axis moves this axis only
- Double left clicking in an axis auto-adjusts it and also recovers [Auto-Scroll or AutoScale](uiguide.md#controls) functionality.
- Clicking and dragging with the right mouse button selects a region to zoom into
- Scrolling on an axis or the plot zooms in/out

Refer to the following video:

<video controls autoplay loop src="img/ui_easygraph.mp4" style="border-radius: 20px;"> </video> 

#### Controls

![ctrl](img/controls.png "Controls of the live graph panel")

- **Running/Pause button:** Start or pause the incoming data stream. All samples during a pause will be discarded. Alternatively you can disable the Auto-Scroll feature (see below) to visually pause the plot while still keeping the data stream running.

- **Trigger button:** Enables or disables the trigger functionality that can be configured using the [trigger menu](uiguide.md#trigger-menu) which can be opened by right-clicking this button. The trigger functionality will start a recording automatically if a certain condition is met.

- **Record button:** Manually start or stop a recording. Optionally use a right-click to customize the filename before starting the recording. Active/finished recordings will be shown in the [recordings panel](uiguide.md#recordings-panel).

- **Clear button:** Clear all historic data in the live graph panel. This leaves you with an empty plot window.

- **Auto-Scroll Feature:** The Auto-Scroll feature will make the right side of the plot sticky with the current time. This means that the most right value will always be the most recently recorded value. As a consequence the plot will automatically scroll as time progresses. In most cases, it should be kept on. When zooming using the right mouse button, this feature will be disabled. When double clicking the X-Axis, this feature will be re-enabled. Before you can move the plot in the X direction, you will need to disable the feature.

- **Auto-Scale Feature:** The Auto-Scale feature will automatically adjust the Y-Axes according to the visible data in the plot. It is also dependent on the selected history time. The feature can sometimes be distracting (for very small value changes) and you should consider turning it off and manually setting the expected Y-Ranges using the scroll wheel and dragging.

- **Lock-Min Feature:** The Lock-Min feature will lock/fix the current minimum value (e.g. `0`) of the flow axis. This option can be used in combination with the **Auto-Scale** feature to allow the maximum value to scale automatically while keeping the X-Axis in view and to not automatically zoom in too much. It is disabled by default. 

- **History slider:** The selected time on the history slider will set the visible range of the plot. It controls how long you can look into the past. In case you use log.flow and have set the [sample rate setting](devices.md#measurement-configuration) to `Automatic`, the history time will also (inversely proportional) affect the sample rate.

#### Limits

To keep the RAM usage of the software moderate and the performance high, the maximum number of samples shown in the plot is limited. Therefore the visible samples will be removed if they exceed a buffer size of 2^19 (524288) samples. Please note that recordings are not affected by this limit as the memory is allocated dynamically (as long as there is enough free RAM).

If you plan to take long recordings, it is therefore advisable to reduce the sample rate of the connected device.

#### Trigger Menu

![dataloggermenu](img/datalogmenu.png){align=right}

The **Trigger** context menu contains options about the trigger functionality. Open it by right-clicking in the `Trigger` button. The trigger can automatically start and stop a recording if one or multiple predefined condiditions are true. 

Before enabling the trigger using the `Enable Trigger` checkbox or by pressing the `Trigger` button [in the live graph panel](uiguide.md#controls), configure the trigger options below. You can optionally turn on a notification sound that plays through the speakers when the trigger starts or stops the recording (Checkbox `Play sound on trigger`).

**Trigger mode:** First you need to specify the trigger mode. This influences whether the trigger functionality will be disabled after the first successful trigger (`OneShot`) or stay active for subsequent triggers (`Repeating`/`Continuous`).

- **Repeating:** Retrigger when condition turns false and true again
- **Continuous:** Retriggers while condition is true

**Recording duration:** Next you set the recording duration using the slider. The total duration is the sum of the recording duration and the pre-trigger duration that you set in the next step.

!!! tip "Tip: Custom duration"
    You can set a custom duration in seconds by performing a left mouse click on the slider while holding down the `CTRL` key on the keyboard. This allows you to manually enter a value using the keyboard. Save by pressing `Enter`. 

**Pre-Trigger duration:** This optional feature allows you to add values to the recording that happened before the trigger started. This gives you the chance to see what happened in the system before the trigger condition became true. After setting a non-zero value and enabling the trigger, the pre-trigger buffer (= ring buffer) will fill up will samples. Once full, you are ready to record!

**TRIGGER CONDITIONS**

The trigger will fire the configured condition is true. The condition itself is a simple mathematical comparison that you can configure using a dropdown menu. The available options are layed out in the following table:

| Comparator 1 | Operators | Operator description | Comparator 2 |
| --- | --- | --- | --- |
| Live Value | =  | equal to | Entered value |
| Live Value | != | not equal to | Entered value |
| Live Value | > | greater than |Entered value   |
| Live Value | >= | greater or equal than | Entered value  |
| Live Value | < | smaller than | Entered value  |
| Live Value | <= | smaller or equal than | Entered value  |

Change the trigger comparator value by entering your threshold into the input field. Alternatively you can adjust the trigger value in the live graph panel by dragging the line that says `Trigger`. For this you can enable to show the trigger cursor without enabling the trigger itself using the option `Show Trigger Cursor` to manually adjust the value and see where it is compared to the current live plot data.

![triggerline](img/triggercursor.png "Drag here to adjust trigger comparator value")

### Device Management Panel

Use the **device management panel** to establish a connection to a datalogging device. Before attempting to connect to a device, make sure you [added the necessary serial keys](gettingstarted.md#software-activation).

Depending on the device type, it either can be automatically connected or manually:

- To connect to a log.flow datalogger or an USB-IO-Link master for IO.flow®, use the `Auto-Connect` button. 
- To connect to an evaluation unit (display or FU-converter) via an USB-RS232-Adapter, use the `More` button and choose the matching COM-Port

!!! success "Make sure the device is connected properly to the computer and turned on"

| ![connectbtn](img/connectbtn.png){ loading=lazy } | ![manual](img/manualconn.png){ loading=lazy } |
|---|---|
| `Auto-Connect` button | `More` button for manual connection |

When the connection is established, it will be added to the device list below the `Auto-Connect` button. An active device connection is indicated by the red device entry. The currently measured values will be shown in the **Live value panel** and the **Live graph panel**. 

You can add multiple devices at the same time to record or display them together in the live plot. By right clicking on the device entry you can launch the device specific settings panel in order to change some settings or to disconnect/remove the device. Refer to the relevant [device section of this manual](devices.md) for more information.

![devmulti](img/devmulti.png "Device manager with multiple devices connected"){ loading=lazy } 


??? info "Info: What are the gray device menu entries?"
    If there is a gray device menu entry, this means that the connection of the device has been lost for whatever reason (for example disconnecting the USB cable). Right-Click and remove the device from the list in this case.


#### Channel Settings

![chentry](img/channelentry.png){ loading=lazy }

Below each device you will find all available data channels. By default, all channels will automatically be added to the live plot. You can toggle them by clicking on each entry. The arrow icon (:octicons-arrow-right-16:) means that the channel was added to the live plot, a minus icon (:material-minus:) means that it is disabled. Instead of clicking you can also drag-drop the channels into the plot window.

Next to the channel name you will find the following channel options: 

- **Change plot axis:** You can manually select the Y-Axis the data will be referenced to. This is useful to seperate data with different units (e.g. l/min and Hz).
- **Modify plot color:** Select the color in which this plot is drawn. 
- **Edit channel description:** Change the channel text and unit. Here you will only change the **unit label** that is shown below the value. To actually convert the value to other units, use the [math settings](#math-settings) (factor and summand). 
- **Math settings:** Set a custom summand and factor to modify the incoming value mathematically before plotting/recording it.

##### Math settings

![mathunit](img/mathunitmenu_pic.png){align=right width=40%}

Using the **Math settings** you can set channel specific unit calculations. 

If you expand the `Load..` menu, you can save/restore your math presets and use calculation functions:

- **Save to preset..:** Save the current factor, summand and unit to a preset with a user-definable name. It is recommended that you choose a name that helps you differentiate this preset later, e.g. include the channel type, flowmeter name, IPF, unit or testbench no.

- **Load preset..:** Load a previously saved preset. Left-click shows a list of all presets. Right-click on a specific preset in this list shows a menu with an option to permanently delete the preset. 

- **Calculate [...] from [...]:** Using this button, the frequency/count value can be converted into the corresponding flowrate/volume value just by using the K-Factor of the flowmeter. 

- **Look-up from database..:** Using this option, you can easily choose a VSE flowmeter's default K-Factor if you don't know the average/mean K-Factor of the specific device. 

### Recordings panel

![fileinfo](img/recctx.png){ align=right}

The recordings panel lists all active, finished and imported recordings. Fresh recordings only persist in temporary RAM and you have to [export](uiguide.md#filetypes-importexport) them in order to keep them after the program exits. You will see different icons besides the filename to show different states of the file:

- :fontawesome-solid-tape:: File is currently recording
- :material-content-save:: File is unsaved and needs saving
- :octicons-check-16:: File was saved successfully.
- :fontawesome-solid-clock-rotate-left:: Dataset was imported from old filetype [pre-v2.2 .bin file]

To manage a recording, right click on the list item. You can open or close the file and also open its property panel where all of the metadata of this file is shown. You can simply edit the fields. After editing you will need to re-save the file as it is not automatically updated on your hard disk.

!!! info "Hint: Close file to edit name"
    To edit a file's name, you will need to close the file's tab if it is open.

![prop](img/proppanel.png "Example of a property panel")

#### Filetypes + Import/Export

There are four different import/export file types available:

File type | File extension | Advantages | Disadvantages | Recommended
--- | --- | --- | --- | ---
[Protocol Buffers :material-link:](https://protobuf.dev/) | pb.bin  | Fastest, small size | Not portable to other programs | :octicons-check-16:
Excel Sheet | xlsx | Widely supported filetype, Excel graphs | Very slow, row limits, RAM usage high, No reimport | |
XML file | xml | Fast, Readable format | Very verbose and huge filesize | |
PDF file | pdf | Looks good, fast to create report | No actual data, only image of plot, No reimport | :octicons-check-16: 

##### PDF report

This is what the exported PDF report looks like:

![pdfreport](img/2K%20Multispeed%20Test_1.webp){width=50%}
![pdfreport](img/2K%20Multispeed%20Test_2.webp){width=70%}
![pdfreport](img/2K%20Multispeed%20Test_3.webp){width=70%}

### Live value panel

![livevals](img/livevalues.png){ align=right}

The **live value panel** contains the current values from the datalogging device. The number of visible channels depends on the selected channels in the `Device management` panel. The plotted channels can be composed of multiple devices. The channel names are automatically adapted to the connected device. 

You can change the **number of visible decimal places** seperately for Volume and Flow in the [Settings menu](uiguide.md#settings). This setting does not affect the recoding resolution or internal value. 

For all channels that display a volume, the value display will have a `Reset Volume` button to quickly set the volume back to zero.

If you have a small screen or a lot of channels active simultaneously, you can use the `Compact` checkbox in the top right corner to make the value display smaller.

![livevals](img/compact.png)

!!! tip "Middle Mouse Click"
    Quickly hide/disable unused channels by clicking on them with the middle mouse button. You can re-enable them via the [device management](uiguide.md#device-management-panel). Disabled channels will NOT be recorded - only the plots that are visible in the live window.

#### Cursor measurement

Cursor measurement can be enabled either by using the `Measure` button in the live graph or file graph panel. Once activated, the [Auto-Scroll and AutoScale](uiguide.md#controls) functions are disabled automatically. After enabling, movable cursors appear in the live plot window. You can move them by left clicking and dragging the lines or their little rectangle handles at the plot's edges. 

Below the **live values** in the rightmost panel, you will find the measured values between the cursor lines. Here you can also select the channel, that you want to measure on, using the combo box. The time values are indepentent of the axes. The measurement is grouped into three sections: 

- In the first section the time values at the X-Axis cursors are shown together with the difference (`delta`) between them. 
- The second section contains the values of the Y-Axis cursors based on the selected channel. Their difference is also shown here. 
- The third section will display a statistical evaluation of all measured values between the X-Axis cursors. You can see the maximum, minimum, difference and average of all values in-between.

![cursors](img/cursors.png)

### File browser panel

You can show the **file browser panel** by enabling the option in the main menu bar using `File` :material-arrow-right: `Open via File Browser`. This will display an explorer-like file browser to open files. Using `Open` you can use the windows default file browser.

In the topmost layer the file browser will list all attached harddrives and network drives. Additionally commonly used directories such as `Desktop`,  `User` and `Documents` will be shown. 

While directories are always shown, files are only shown if the filetype is compatible with **EasyGraph**. Supported file extensions are: `pb.bin` and `xml`. Import files (recordings) by double clicking on them. The program will then scan the file and verify, that it is compatible. If all checks pass, the file will be shown in the [Recordings panel](uiguide.md#recordings-panel).

![navbuttons](img/navbtn_content.png)

You can use the buttons at the top to perform certain actions:

- :material-refresh: **Refresh:** Reload the current directory and re-list all files
- :material-home: **Home:** Go to `Computer` (home directory)
- :material-undo: **Up:** Go up one directory layer until you reach the topmost layer with all drives and shortcuts

By right-clicking on supported files you can open a context menu to `Open`, `Rename` or `Delete` them:

![ctx_menu](img/contextfilemenu.png)

## Main menu bar

This section will go over every option in the main menu bar. 

### File

![filemenu](img/filemenu.png){align=right}

**:material-folder: Open:** Use the explorer to select a recording that you want to re-import. Supported filetypes are `bin` and `xml`.

**:material-folder: Open via file browser:** Use the integrated file manager to select a recording that you want to re-import. Supported filetypes are `bin` and `xml`.

**:fontawesome-solid-floppy-disk: Save all unsaved recordings:** Opens an explorer window to select the directory you want to save all unsaved recordings into. This does ***not*** check for existing files so it is advised to choose an empty directory.

---

**:octicons-x-16: Close:**: Closes the open file plot tab.

**:octicons-x-16: Discard:**: Removes the open file plot from the recording list, effectively deleting it. If the file is already saved, this will only remove the file from the application (closing it), the real file on the HDD remains untouched.

**:fontawesome-solid-floppy-disk: Save:**: Saves the file as a protobuf file at the last known file save location (or where is was imported from)

**:fontawesome-solid-floppy-disk: Save as...:**: Saves the file as a selectable filetype. See [filetypes](uiguide.md#filetypes-importexport) for more information.

**:octicons-info-16: Properties**: Shows the metadata of the open plot file.

---

**:octicons-x-12: Exit:** Closes the application.

!!! failure "Close with unsaved recordings"
    If you are closing the application while having unsaved recordings, a popup will appear that asks you to either save or discard the files. You can also cancel the closing and save them manually yourself. 

    ![confirmclose](img/confimclose.png)

    - **Close:** Discard all recordings and close the program
    - **Abort:** Don't close the program to check manually
    - **Save:** Save all unsaved recordings into a directory and close after this


### License

Using the license menu you can manage all of your serial keys. Use the relevant menu item to manage them.

- Manage log.flow keys for [log.flow activation](gettingstarted.md#logflow-activation)
- Manage EasyGraph key for [online activation](gettingstarted.md#online-activation) 

### Settings

![plot](img/settingsmenu.png){align=right}

The settings menu contains options to change the behavour of the application and customize the appearance of the plot window:

**GENERAL SETTINGS**

:octicons-checkbox-16: **Allow device settings during recording**: While recording the device settings (right-clicking on device name) is normally prohibited. This setting can override this.

!!! warning "Not recommended"
    Using this setting is not recommended because device parameters should not be touched during an active recording. This may also cause an uneven sample rate as there can be samples missing when parameters are synchronized between the pc and the device.

**VISUAL SETTINGS**

:octicons-sliders-16: **Line thickness:** Change the line width of all plots to make it thicker/thinner

:octicons-sliders-16: **Flowrate decimals:** Adjust the number of displayed decimal places in the [live value panel](#live-value-panel) for frequency type measurements

:octicons-sliders-16: **Volume decimals:** Adjust the number of displayed decimal places in the [live value panel](#live-value-panel) for counter type measurements

:octicons-sliders-16: **Analog decimals:** Adjust the number of displayed decimal places in the [live value panel](#live-value-panel) for analog type measurements

:octicons-checkbox-16: **Show Markers on each datapoint:** Display a circle for every sample to see the actual timing of received datapoints from the dataloggers

!!! info "Hint: Decimal places $\neq$ Precision"
    The decimal places sliders do **not** affect the recoding resolution or internal value. 

**PANEL VISIBILITY**

:octicons-checkbox-16: **Show Live Value Panel:** Displays the [live value panel](#live-value-panel) panel on the right that contains the live values of all datalogging streams in text form. The cursor measurement results are also displayed here.

:octicons-checkbox-16: **Show Device Manager:** Show the [device management panel](#device-management-panel) on the left in order to connect to or manage datalogging devices.

:octicons-checkbox-16: **Show File Browser:** Show the integrated file browser to open files.

:octicons-checkbox-16: **Show Recordings Panel:** Show the bottom left panel that contains all recordings and imported datasets.

:octicons-checkbox-16: **Show Performance Meters:** Show performance meters for the application in the top menu bar. The measured values are rendering performance (in FPS/Hz), CPU Load (in %) and RAM usage (in MB).

![perf](img/perfmeters.png "Performance meters")


**STARTUP BEHAVIOUR**

:octicons-checkbox-16: **Skip Startup Logo Animation:** Check to not show the logo animation to save some seconds on program start.

![winloc2](img/winloc.png){align=right}


:octicons-sliders-16: **Set default window startup location:** Using this feature, you can save the main EasyGraph window size and starting location that will be set at every program launch. To save the current location and size, simply press `Save`. To delete the custom starting location, press the `Delete` button. If no custom location is set (and thus no `Delete` button is visible), EasyGraph will start centered on the main monitor with some margin on each side. 

You can use the Window Start Location feature for example to launch EasyGraph in fullscreen mode on another monitor.

It is not recommended to use this feature if you are frequently changing monitor configurations (e.g. docking your mobile workstation).

If the window is not visible after program start, close it using its taskbar icon and press and hold the `Shift` key during the next program start. This will reset the start location to default.

??? question "Help! I can't see the EasyGraph window after starting the application!"
    If you used the **Set default window startup location:** feature before and changed the monitor configuration, it is possible that the main EasyGraph window is positioned out of the screen bounds. In this case close EasyGraph using the taskbar or task manager and hold shift during the next program launch. This will set the window position to default for this start and you can delete the custom window start position. 

**POWERSAVING**


![powersave](img/powersave.png){align=right}

The powersave mode was implemented to limit hardware ressource usage when idle or unused. When the main window gets unfocused (e.g. another program is used on the PC), EasyGraph can throttle the framerate to save power. When powersaving is active and the window is unfocused, a green indicator is shown in the top area of the live graph panel. 

There are three different powersave modes for the unfocused program state. When focused, rendering is always performed at full speed. 

![powersavethrottle](img/powersavethrottle.png){align=right}

:octicons-sliders-16: **Mode:** Change the amount of powersaving the program will try to achieve:

- Off: Always render at full speed (0% power saving)
- Normal/Throttle: Lower framerate to _6 fps_ (~50% power saving) :material-arrow-right: `default`
- Maximum: Stop rendering (~95% power saving)

!!! success "Remark: Recording performance is not affected when unfocused or minimized!"

### Help

In the **Help** menu you can find helpful options, such as:

- Open this documentation
- Search for software updates (:material-earth: Internet Access required!)
- Option to reset math presets
- Option to restore the default window layout

### Update Check

On each program start the software will check for software updates. Updates can contain new features, more device support, bugfixes and stability improvements. If a new update is available, a window will be shown with information about the changes and a link to the download page. 

![update](img/update.png)

The update (`msi` file) must be installed manually. You will be redirected to our download portal where you will need to enter your customer id and the product/license key.

You can also invoke the update checker manually by clicking on the version number in the top right corner or using the [Help menu](uiguide.md#help).
