---
title: "Clip web pages"
type: research
source: "https://obsidian.md/help/web-clipper/capture"
author:
  - "[[Obsidian Help]]"
published:
created: 2026-03-22
status: archived
source_role: moushi
topic: Clip web pages
validation_status: 已归档（Web Clipper 官方采集样本）
archive_mode: evidence
description: "Clip web pages - Obsidian Help"
tags:
  - "web-clipper"
---
Once you install the [Web Clipper](https://obsidian.md/help/web-clipper) browser extension, you can access it in several ways, depending on your browser:

1. The Obsidian icon in your browser toolbar.
2. Hotkeys, to activate the extension from your keyboard.
3. Context menu, by right-clicking the web page you are visiting.

To save a page to Obsidian click the **Add to Obsidian** button.

## Capture a page

When you open the extension, Web Clipper extracts data from the current web page following the settings in your [template](https://obsidian.md/help/web-clipper/templates). You can create your own templates, and customize the output using [variables](https://obsidian.md/help/web-clipper/variables) and [filters](https://obsidian.md/help/web-clipper/filters).

By default Web Clipper attempts to intelligently extract only the main article content, excluding other elements on the page. However, you can override this behavior in the following ways:

- If a custom template is present it uses your template.
- If a selection is present, it uses the selection. You can use `Ctrl/Cmd+A` to select the entire page.
- If any [highlights](https://obsidian.md/help/web-clipper/highlight) are present, it uses the highlights.

## Download images

Images are not automatically downloaded when you use Web Clipper. Instead, images link to their web-based URL. This saves space in your vault but it means the images will not be accessible offline, or if the URL stops working.

You can download images for any file in Obsidian using the [command](https://obsidian.md/help/plugins/command-palette) named **Download attachments for current file**. This command can also be mapped to a hotkey in Obsidian.

## Hotkeys

Web Clipper includes keyboard shortcuts you can use to speed up your workflow. To change key mappings go to **Web Clipper Settings** → **General** and follow the instructions for your browser. Mappings can be changed for all browsers except Safari which does not support editing hotkeys.

| Action | macOS | Windows/Linux |
| --- | --- | --- |
| Open clipper | `Cmd+Shift+O` | `Ctrl+Shift+O` |
| Quick clip | `Opt+Shift+O` | `Alt+Shift+O` |
| Toggle highlighter mode | `Opt+Shift+H` | `Alt+Shift+H` |

## Interface functionality

The Web Clipper interface is divided into four sections:

1. **Header** where you can switch templates, turn on [highlighting](https://obsidian.md/help/web-clipper/highlight), [read mode](https://obsidian.md/help/web-clipper/reader), and access settings.
2. **Properties** shows the [metadata](https://obsidian.md/help/properties) extracted from the page that will be saved as [Properties](https://obsidian.md/help/properties) in Obsidian.
3. **Note content** that will be saved to Obsidian.
4. **Footer** allows you select the vault and folder, and add to Obsidian.

- **Template** dropdown to switch between your saved [templates](https://obsidian.md/help/web-clipper/templates) added in Web Clipper settings.
- **More (...)** button to display page variables you can use in templates.
- **Highlighter** button to turn on [highlighting](https://obsidian.md/help/web-clipper/highlight).
- **Cog** button to open Web Clipper settings.

- **Add to Obsidian** button to save data to Obsidian.
- **Vault** dropdown to switch between saved vaults added in Web Clipper settings.
- **Folder** field to define which folder to save to.
- **Interpreter** to run [natural language prompts](https://obsidian.md/help/web-clipper/interpreter) on the page.
