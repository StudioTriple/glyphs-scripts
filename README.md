# Glyphs scripts

An assortment of scripts for the [Glyphs font editor](http://glyphsapp.com/). 

## Script list

- **Add Extremes to Selection:** Adds extreme points to selected paths.
- **Add Tangent Nodes at a Specific Angle:** Insert points on the tangents at a specific angle. Optionally extrude the path in the same direction, creating a block shadow effect. Needs Vanilla.
- **Copy Master into Sublayer:** Copies a master into a sublayer of another master for the selected glyphs. Useful for creating COLR/CPAL color fonts. Based on [@mekkablue](https://github.com/mekkablue/Glyphs-Scripts)'s Copy Layer to Layer script. Needs Vanilla.
- **Interpolate Path with Itself:** Interpolates the path with itself. The fixed half will be the one with the start point. This script will be improved in the near future.
- **Make Next Node First:** Moves the start point of the selected  path(s) to the next oncurve node. Specially useful if assigned to a keyboard shortcut.
- **Make Previous Node First:** Moves the start point of the selected  path(s) to the previous oncurve node. Specially useful if assigned to a keyboard shortcut.
- **Open All Nodes:** Opens all nodes for the selected paths (or all paths if none are selected).
- **Open Selected Nodes:** Opens the selected nodes.
- **Rename Glyphs and Update Features:** Renames glyphs and updates all classes and features. Will match either the entire glyph name or the dot suffix. Needs Vanilla.
- **SVG Export and SVG Import:** Generates SVGs from inside Glyphs and reimports them for creating SVG color fonts. More information below. Needs Vanilla and Drawbot.

### SVG Export.py

1) Before running the script, define which masters should be exported and their colors in JSON files and place them alongside your .glyphs file. Let’s call the following example `acquamarine.json`:

```json
{
	"Extrude": [ 15, 54, 69 ], // RGB value for solid fill
	"Regular": [ 1, 187, 226 ],
	"Bevel B": {               // this is a gradient fill
		"startPoint": [0,0],   // x,y coordinate
		"endPoint": [0,550],   // x,y coordinate
		"colors": [
			[ 168, 231, 244 ], // first RGB color
			[ 195, 241, 249 ]  // second RGB color
		],                     // add more colors as needed
		"locations": [0,1]     // location of each color in gradient
	}
}
```

2) Run the script and type the name of the JSON file on the window. The script will create a subfolder with the same name and place all SVGs inside it.

### SVG Import.py

1) On a copy of your original .glyphs file, create a master for each one of the color schemes files you exported with the previous script. For example, if you have a subfolder called “acquamarine”, create a master named “Acquamarine” and assign to it a custom axis value. The name is case-insensitive.

2) After creating all masters, create an instance for each one of them so they will be exported. To do so, got o **Font Info** > **Instances** > **+** > **Add Instance for each Master**.

3) Run the script. 

In a nutshell, for each master, it will check if there is a subfolder with the same name as the master, create a layer named *svg* and import the SVG file into it.


## Installing

Download or clone this repository and put it into the Scripts folder. To find this folder, go to Script > Open Scripts Folder (⌘⇧Y) in Glyphs. After placing the scripts there, hold down the Option key and go to Script > Reload Scripts (⌘⌥⇧Y). The scripts will now be visible in the Script menu.

Some scripts require Tal Leming’s Vanilla. To install it, go to the menu Glyphs > Preferences > Addons > Modules and click the Install Modules button.

## License

Copyright 2018 Henrique Beier (@harbortype). Some code samples by Rainer Erich Scheichelbauer (@mekkablue) and Luisa Leitenperger.

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at

[http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.