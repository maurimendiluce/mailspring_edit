# mailspring_edit

A personal collection of plugins and a theme for [Mailspring](https://getmailspring.com/), packaged as ready-to-install zip files. It is set up for Windows, but the plugins are plain Mailspring packages and work on any platform Mailspring supports.

Everything lives in the [`mailspring_edit/`](mailspring_edit) folder.

## What's included

| Package | Type | What it does | Source |
| --- | --- | --- | --- |
| `mailspring-open-in-window.zip` | Plugin (v0.1.0) | Opens a message in its own window with a single click on the thread list. | Written for this repo |
| `mailspring-pdf-viewer.zip` | Plugin (v0.2.2) | Shows a PDF attachment inline, inside the message, with Mailspring's built-in viewer. | Written for this repo |
| `mailspring-popout-toolbar.zip` | Plugin (v0.2.0) | Adds Trash, Move to folder and Labels buttons to a message's own window. | Written for this repo |
| `upcoming-events.v1.0.zip` | Plugin (v0.1.0) | Sidebar listing your calendar events for the next 14 days. | Third party |
| `mailspring-sort-inbox-main.zip` | Plugin (v1.1.0) | Airmail-style Sort & Filter menu next to the search bar. | [saint-james-fr/mailspring-sort-inbox](https://github.com/saint-james-fr/mailspring-sort-inbox) |
| `mailspring-minimalist-gris.zip` | Theme (v0.3.0) | A minimalist, gray-toned theme. | Based on [hstandaert/mailspring-minimalist](https://github.com/hstandaert/mailspring-minimalist) |
| `ejbiker93ss-ms-plugin-1.0.1.zip` | Plugin (v1.0.1) | Inline PDF viewer, sticky subject and more. **Not recommended**, see [below](#not-recommended-ejbiker93ss-ms-plugin). | [ejbiker93ss/ejbiker93ss-ms-plugin](https://github.com/ejbiker93ss/ejbiker93ss-ms-plugin) |

## Installation

Each zip contains a single folder with a `package.json` at its root. Installing means putting that folder in Mailspring's `packages` directory.

1. **Quit Mailspring completely.** On Windows it can keep running in the system tray, so right-click its tray icon and choose Quit. Reloading the window may not be enough: message windows might not pick up a new plugin until Mailspring restarts.
2. Extract the zip.
3. Copy the extracted folder into the `packages` directory:

   | OS | Path |
   | --- | --- |
   | Windows | `%APPDATA%\Mailspring\packages` |
   | macOS | `~/Library/Application Support/Mailspring/packages` |
   | Linux | `~/.config/Mailspring/packages` |

   Paste `%APPDATA%\Mailspring\packages` into the Explorer address bar to get there on Windows.
4. Start Mailspring again.

Themes go in the same folder. After restarting, pick the theme under **Preferences → Appearance**.

To uninstall anything, quit Mailspring and delete its folder from `packages`.

## The plugins

### mailspring-open-in-window

With the thread list in the layout **without a reading pane**, a single click on a message opens it in a separate window, the same one a double click opens.

- Ctrl/Cmd + click and Shift + click keep their normal multi-select behavior.
- Alt + click opens the message in the main window.
- Clicks on the checkbox, the star/read icon, the importance marker and the quick-action buttons are unchanged.
- With a reading pane enabled, the plugin does nothing.

### mailspring-pdf-viewer

Click a PDF attachment and the viewer opens **inside the message**, in place of the attachment chip. It reuses the PDF.js viewer that ships with Mailspring.

- **Cerrar** (close) brings the attachment chip back; **Abrir fuera** (open externally) opens the PDF in your default app.
- Other attachment types, double click, the context menu, download and remove work as usual.
- Works in the main window and in message windows.
- It replaces Mailspring's own attachments component while active and restores it when disabled. For that reason it cannot run together with another plugin that does the same thing, such as `ejbiker93ss-ms-plugin`.

### mailspring-popout-toolbar

Message windows (the ones opened with the pop-out button) have no toolbar on Windows, so they lose the Trash, Move and Labels buttons. This plugin adds them **just below the subject line**:

- **Trash** moves the message to the trash and closes the window. It is hidden when the current view doesn't allow trashing the message (for example, when it is already in the trash).
- **Move to folder** and **Labels** open Mailspring's own pickers. Labels only appear for accounts that use them, such as Gmail.

### upcoming-events

Adds a sidebar at the right of the mail window with your calendar events for the next 14 days, grouped by day. Events in progress get a "Now" badge. A calendar button in the toolbar shows or hides the sidebar, and you can drag its left edge to resize it. It requires Mailspring 1.26 or later and at least one account whose calendars sync. See the README inside the zip for details.

### mailspring-sort-inbox

Adds a **Sort & Filter** menu to the thread list toolbar: sort by date or sender, newest or oldest first, and show only unread, read or starred threads. It ships with French, Spanish, German, Italian and Brazilian Portuguese translations.

This plugin patches Mailspring internals, so a Mailspring update can break it. Check it after upgrading.

## The theme

**mailspring-minimalist-gris** is a variation of the Minimalist theme with a gray palette. The sidebar and message list colors are set by two variables in `styles/settings/variables.less` (`@surface-lighter` and `@surface-light`). The same file includes alternative palettes (stone, sage, graphite) that you can uncomment.

## Not recommended: ejbiker93ss-ms-plugin

This package is kept here for reference only. In my setup, in the message window, any message containing a line of dashes (`------------`) was cut off after that line, and the `[...]` button to expand the rest did not appear. Removing the plugin fixed it. It also replaces the same attachments component as `mailspring-pdf-viewer`, so the two cannot be used together.

`mailspring-pdf-viewer` reimplements its inline PDF viewer on its own, without the rest of the plugin.

## Compatibility and troubleshooting

- The three plugins written for this repo were developed against the current Mailspring source (React 17, Electron 44) and use internal APIs. A Mailspring update may break them.
- Some labels in those plugins are in Spanish ("Cargando PDF…", "Abrir fuera", "Cerrar"), and their per-plugin READMEs are in Spanish too.
- **A plugin doesn't show up:** make sure you fully quit Mailspring (including the tray icon) and that the folder sits directly under `packages`, with `package.json` right inside it and not in a second nested folder.
- **Looking for errors:** open **Developer → Toggle Developer Tools** and check the console. `mailspring-popout-toolbar` logs lines starting with `[mailspring-popout-toolbar]`. Open the tools from the window where the problem happens, since message windows have their own console.
- **"Error compiling Less stylesheet" and the theme resets:** remove the plugin named in the error message. Then reselect your theme under **Preferences → Appearance**.

## License

The plugins written for this repo are MIT-licensed (see each `package.json`). Third-party packages keep their own licenses; see the files inside each zip.
