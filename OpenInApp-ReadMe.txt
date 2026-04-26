Open in External App — Lightroom Classic Plugin
================================================

WHAT IT DOES
------------
Opens selected raw files in a configured external application (e.g. Iridient
Developer). When you quit the external app, the plugin automatically detects
any new .tif files saved alongside the originals and imports them into your
Lightroom catalog.


INSTALLATION
------------
1. Download and unzip OpenInApp.lrplugin.zip.
   You will get a folder called OpenInApp.lrplugin.

2. In Lightroom Classic, go to:
   File > Plug-in Manager

3. Click Add at the bottom left.

4. Navigate to and select the OpenInApp.lrplugin folder, then click Add Plug-in.

5. The plugin should appear in the list with a green dot and status "Installed
   and running".


CONFIGURATION
-------------
1. In the Plug-in Manager, click on Open in External App in the left list.

2. In the panel on the right, set the App path to the full path of your
   application bundle. For example:

     /Applications/Iridient Developer.app

   You can type the path directly or click Browse... to navigate to the app.

3. Click Done.


USAGE
-----
1. In the Lightroom Library, select one or more raw files.

2. Go to:
   File > Plug-in Extras > Open Selected in External App

3. Your external app will open with the selected files.

4. Edit and save your files as .tif in the same folder as the originals.

5. Quit the external app.

6. The plugin will detect the new .tif files and import them into your
   Lightroom catalog automatically. A confirmation dialog will tell you
   how many files were imported.


NOTES
-----
- Only raw files are passed to the external app. Non-raw files and virtual
  copies in your selection are silently skipped.

- The plugin watches for .tif files saved alongside the originals (same
  folder, same base filename). For example:
    DSC_0001.NEF  →  looks for  DSC_0001.tif

- The import only happens after the external app is fully quit, not just
  when a file is saved.

- If you keep the external app open permanently and never quit it, the
  auto-import will not trigger. In that case, use Lightroom's built-in
  Library > Synchronize Folder manually.

- A keyboard shortcut can be assigned to the menu item via:
  System Settings > Keyboard > Keyboard Shortcuts > App Shortcuts
  Application: Adobe Lightroom Classic
  Menu Title:  Open Selected in External App
