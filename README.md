This is a set of config files to be used in conjunction with the Ender 3 V3 SE and the CoPrint KCM Multicolor Kit.

Typically for the Ender 3 V3 SE you would need to use the marlin based chromapad or chromakit.  This mod however allows you to use the cheaper KCM kit instead.

This mod requires you to have klipper running on a raspi, configured to control this printer.  There are plenty of guides on how to get this setup initially.  Once you have it up and running, you can drag, drop and tweak these configs.

These configs are for the NON RUNOUT SENSOR chromaheads and do not have the autoload macro or any of the macro adjustments needed for the runout sensor.  Please keep that in mind.

These configs are drag and drop however some things to keep in mind:
- You will need to create your own mesh
- You will need to add your own z offset.  In these configs you can find the entry for this under the startprint macro in cp_macro.cfg
- INPUT SHAPING IS SUPPORTED PLEASE SEE BELOW
- You will need to enter your own serial IDs for not only the chroma equipment but also your printers MCU
- Changes were made the filament_cut macro to allow for more time before retraction
- Custom load and unload macros defined below
- Max speed tuned for 250mm/s and 2500mm/s

Input Shaping:
Input shaping is enabled by default however it required dependencies:
- numpy `~/klippy-env/bin/pip install numpy`
- matplotlib `~/klippy-env/bin/pip install matplotlib`
Once you've installed those, restart klipper and run the `SHAPER_CALIBRATE` command and it should now work.  If you run into issues saving your values, enter them manually under the extruder section in the chromahead.cfg.

Custom loading macros:
Honestly we are really spoiled with the auto load macro from user Mjsfech on the discord channel.  Here is what I have so far:

`INITIAL_LOAD_SOLO` - This will move the selectred extruder forward 150mm.  This is basically just to pull the filament in to get started.
`INITIAL_LOAD` - Same as above however it cycles through the first 4 extruders
