# 🎒 Basic Usage

### Main screen

![Part of the main screen](<../.gitbook/assets/immagine (2).png>)

1. This is a breadcrumb, it allows to navigate in directories. On mobile, it is collapsed with a dropdown.
2. The `../` directory allows to go back one level. Only available if you're not already in root dir.
3. Clicking on the icon:
   1. For directories, it changes the directory;
   2. For files, brings you to the [preview screen](basic-usage.md#undefined).
4. Clicking on the hamburger (menu) icon brings you to the [details panel](basic-usage.md#details-panel).
5. When a file is cut or copied (see [details panel](basic-usage.md#details-panel)), these two icons will be shown, allowing to paste it or to cancel the operation.
6. New Folder.
7. File upload.
8. Open the [sharing dialog](sharing-a-folder.md#web-ui) for the current folder.
9. Reloads the file list.
10. Changes the view from grid to list, and vice-versa.
11. Sort mode. Allows to choose:
    1. Alphabetical (ascending or descending)
    2. By date (ascending or descending)
    3. By size (ascending or descending)

### Details panel

![The details panel](<../.gitbook/assets/immagine (3).png>)

1. Data about the file.
2. Cut/Copy commands.
3. Rename the file.
4. Delete the file.

### Preview screen

![The preview screen](<../.gitbook/assets/immagine (1).png>)

1 And 2 go through the files, displaying their preview if they are [supported](basic-usage.md#supported-file-types-for-viewing). You can also use the arrow keys on the keyboard; on mobile, you can swipe with your finger.

3 Allows to download a file.

4 Closes the screen and goes back to the file manager.

5 Clicking on an image will enlarge it, cycling through full screen (still possible to use arrow keys/swipe) and full size.

### Supported file types for viewing

In the file system view, you can click on a file to open it. Currently pupcloud supports:

* Images, Audio, Video (when supported by the browser)
* PDF documents (for desktop browsers)
* Text-like files (txt, html, sources...)

Detection of file types is done by mime type, and viewing relies on the browser's capabilities.
