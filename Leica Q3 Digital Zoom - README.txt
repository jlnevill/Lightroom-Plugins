LEICA Q3 DIGITAL ZOOM CROP — Lightroom Classic Plugin
======================================================
Version 2.1


WHAT IT DOES
------------
The Leica Q3 records a full-frame 60MP DNG regardless of which digital
zoom level was set in-camera. The zoom crop is encoded in the DNG's
DefaultCropSize metadata tag. Lightroom ignores this and shows the full
frame.

This plugin reads the crop geometry directly from the DNG and applies a
matching centred crop in Lightroom's Develop module — no external tools
or manual measurements needed.

Supported zoom levels:

  1.25x — 35mm equivalent   39MP
  1.80x — 50mm equivalent   19MP
  2.70x — 75mm equivalent    8MP
  3.20x — 90mm equivalent    6MP

Native 28mm shots (no digital zoom) are detected and skipped.


INSTALLATION
------------
1.  Unzip the download. You should have a folder called:
      LeicaQ3DigitalZoom.lrplugin

2.  Copy that folder to your Lightroom modules directory:

      macOS:
        ~/Library/Application Support/Adobe/Lightroom/Modules/

      Windows:
        %APPDATA%\Adobe\Lightroom\Modules\

    (If the Modules folder does not exist, create it.)

3.  Start (or restart) Lightroom Classic.

4.  Go to File > Plug-in Manager.
    Find "Leica Q3 Digital Zoom" in the list.
    It should show a green dot and the status "Installed and running".

    If it is not listed, click Add at the bottom-left of the Plug-in
    Manager window and navigate to the .lrplugin folder manually.


APPLYING THE CROP
-----------------
1.  In the Library module, select one or more Leica Q3 DNG files.

2.  Go to Library > Plug-in Extras > Apply Q3 Digital Zoom Crop.

3.  A dialog will appear listing each selected image and its detected
    zoom level. Images with no digital zoom are shown but skipped.

4.  Click Apply. The crop is applied in Develop for all matched images.

    The crop fraction is also saved into each image's IPTC Instructions
    field (prefixed Q3Crop:) so it can be restored if needed — see below.


AFTER A DEVELOP RESET
----------------------
Lightroom's Develop > Reset command clears all develop settings
including the crop. To restore the Q3 crop after a reset:

1.  Select the image(s) in the Library module.

2.  Go to Library > Plug-in Extras >
      Re-apply Q3 Digital Zoom Crop (after Reset)

3.  The plugin reads the stored crop fraction from the IPTC Instructions
    field and re-applies the crop immediately.

    Note: this only works if "Apply Q3 Digital Zoom Crop" has been run
    on the image at least once. If the IPTC field is missing, re-run
    the main Apply step.


FILES IN THE PLUGIN
-------------------
  Info.lua                — Plugin manifest (Lightroom reads this first)
  LeicaQ3DigitalZoom.lua  — Main detection and apply logic
  LeicaQ3Reapply.lua      — Re-apply crop after a Develop Reset


TROUBLESHOOTING
---------------
Plugin not appearing in Plug-in Extras:
  - Confirm the plugin shows a green dot in File > Plug-in Manager.
  - If you updated the plugin, remove it in Plug-in Manager and re-add
    the folder to force a clean reload.
  - The menu items appear under Library > Plug-in Extras. You must be
    in the Library module to see them.

"Not a Leica Q3 image" message:
  - The plugin checks EXIF Make/Model. Confirm the file reports
    Make = "Leica Camera AG" and Model = "Leica Q3" in the Metadata panel.

"Unrecognised crop fraction" message:
  - The crop fraction read from the DNG did not match any known zoom
    level. This should not happen with an unmodified Q3 DNG. If you
    have processed the file through another application that rewrote
    the DefaultCropSize, the original crop data may be lost.

Crop not visible after applying:
  - Switch to the Develop module and check the Crop Overlay tool (R key).
    The crop should be active. If Develop shows the full frame, try
    running Apply again with the image selected.


NO EXTERNAL DEPENDENCIES
------------------------
The plugin uses only Lightroom's built-in Lua SDK and reads metadata
that Lightroom already holds in memory from the DNG. No exiftool,
no shell commands, no internet access required.
