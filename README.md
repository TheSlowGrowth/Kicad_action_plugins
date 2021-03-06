# KiCad Action Plugin(s)


This repo contains Kicad pcbnew Action Plugins()

## Replicate layout

This plugin has been tested on Windows 7 Kicad nightly 2017-09-19 revision dddaa7e69. 

This plugin has been developed as a complex plugin according the [Python Plugin Development for Pcbnew](https://github.com/KiCad/kicad-source-mirror/blob/master/Documentation/development/pcbnew-plugins.md).

within the plugin folder only *.py files are required for operation.

While the action plugin works within pcbnew, the `replicatelayout` module can be used also in pcbnew scripting console or even without pcbnew running. For example look at lines 210, 211 in `replicatelayout.py`. Additionally the `replicatelayout.py` module if run standalone will test itself aginst known correct layouts (provided within the plugin folder). This is to ease testing if pcbnew API changes in the future. The `replicatelayout` module does not work with Kicad 4.0.7 as the Python API lacks certain methods.

This plugin replicates layout section. The replication is based upon hierarchical sheets.
Basic requirement for replication is that the section for replication is completely contained within one hierarchical sheet, and replicated sections are just a copy of the same sheet. Plugin also replicates module text layout (References, Values and other text bound to a module). The example can be seen in this two pictures.

![Top sheet schematics](https://raw.githubusercontent.com/MitjaNemec/Kicad_action_plugins/master/screenshots/Replicate_layout_0.png)
![Hierarchical sheet to replicate](https://raw.githubusercontent.com/MitjaNemec/Kicad_action_plugins/master/screenshots/Replicate_layout_1.png)

Once the section for replication (pivot section) has been laid out (modules, tracks and zones placed) you need to select any of the modules within this section and run the plugin.

The plugin will ask for x and y offset (in mm) with respect to pivot section where replicated sections will be placed. Additionally you can choose wheather you want to replicate also zones and/or tracks. By default only tracks and zones which are contained in bounding box constituted by all the modules in the section will be replicated. You can seledt to replicate also zones and tracks which intersect this bounding box. Additionally tracks and zones already laid out in replicated bounding boxes can be removed (useful when updating)

![Bounding box, contained, intersecting definitions](https://raw.githubusercontent.com/MitjaNemec/Kicad_action_plugins/master/screenshots/Replicate_layout_2.png)

Example of replication of only contained tracks and zones

![Replication of only contained tracks and zones](https://raw.githubusercontent.com/MitjaNemec/Kicad_action_plugins/master/screenshots/Contained.gif)

Example of replication including intersecting zones and tracks

![Replication including intersecting zones and tracks](https://raw.githubusercontent.com/MitjaNemec/Kicad_action_plugins/master/screenshots/Intersecting.gif)

Example of replication of module layout only (no tracks or zones)

![Replication of modules only](https://raw.githubusercontent.com/MitjaNemec/Kicad_action_plugins/master/screenshots/No_tracks_or_zones.gif)


