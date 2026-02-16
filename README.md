# Source SDK 2013 B.C.

This is my personal fork of the multiplayer Source SDK.

## New Features

### Nine-Slice Scaling
By setting `PaintBackgroundType` on a panel to `3`, you can now utilize [nine-slice scaling](https://en.wikipedia.org/wiki/9-slice_scaling)
to scale rectangular images while preserving the sizes of corners and sides. This is useful for drawing things like bordered rounded rectangles.

#### Caveats
Rendering is currently broken if you attempt to draw a rectangle smaller than 2 times the corner size on either axis. This can be remedied
by later adding three-slice scaling, but is a minor enough issue that this can wait.

#### Usage
Here's an example that changes the health display's background from the standard 4-corners rendering to a complex nine-slice texture.

```
HudHealth
{
    "fieldName"		"HudHealth"
    "xpos"	"16"
    "ypos"	"432"
		  "wide"	"102"
		  "tall"  "36"
		  "visible" "1"
		  "enabled" "1"

    // enable nine-slice scaling
		  "PaintBackgroundType"	"3"
    // texture that is scaled
    "Texture1" "vgui/hud/my-texture"
    // texture dimensions - this assumes your border exists at (0, 0) and is 32x32 pixels
    // these can be omitted if the whole image is the atlas you want to draw
    "TextureBorderX" "0"
    "TextureBorderY" "0"
    "TextureBorderWide" "32"
    "TextureBorderTall" "32"
    // this defines the number of pixels from the edge of the image to not scale
    // setting this to 4 means 4x4px corners, 4px wide vertical sides, and 4px tall horizontal sides
    "TextureBorderWeight" "4"

		  "text_xpos" "8"
		  "text_ypos" "20"
		  "digit_xpos" "50"
		  "digit_ypos" "2"
	}
```
