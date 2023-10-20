---
title: Programming and debugging godot with Visual Studio Code
description:  UEnhance Your Godot Programming Experience with Visual Studio Code (VSCode)
summary: Visual Studio Code, often referred to as VSCode, is undeniably one of the most popular code editors. 
date: 2023-10-20
tags:
    - godot
    - gamedev
---

Visual Studio Code, often referred to as VSCode, is undeniably one of the most popular code editors. I personally rely on it for my daily work. However, when it comes to Godot, while the engine has its own editor, I don't like it much.

The good news is, you can seamlessly integrate Godot with Visual Studio Code. In this post, I'll walk you through the process of changing the default text editor to VSCode for your Godot projects. Not only that, but I'll also show you how to enable debugging and breakpoints within VSCode.

Let's get started!


# Godot 

Please note that this tutorial is intended for use with Godot 4.1.2, the latest stable version available at the time of writing.

To integrate an external code editor like Visual Studio Code (VSCode) with Godot, follow these steps:
1. Open Godot Engine and navigate to **Editor** > **Editor Settings.**
2. Under **Text Editor,** enable **Use External Editor.**
3. Specify the **Exec Path** to your VSCode installation.
4. For **Exec Flags,** input: {project} --goto {file}:{line}:{col}

{% image "screenshots/1020-godot-editor-settings.jpg", "Godot Editor Settings" %}

Still in **Editor Settings,** proceed to **Network** > **Language Server.** Locate **Remote Port** and ensure it's set to **6005.** This port value will be used in another setting within VSCode.

# VSCode

1. Begin by installing the **godot-tools** extension in Visual Studio Code.
2. Open VSCode and go to **File** > **Preferences** > **Settings**.
3. Under **User**, look for **Extensions** and click on **Godot Tools configuration**.
4. Here, you'll find 'Gdscript_lsp_server_port.' Set this to **6005**.

{% image "screenshots/1020-vscode-godot-autocompletee.jpg", "Godot VSCode Autocomplete" %}

That's it! You've successfully configured VSCode to serve as your primary editor for Godot."

# Debugging

1. Open VSCode.
2. Navigate to the 'Run and Debug' section.
3. Click on 'Create a launch.json file.'
4. Select 'GDScript Godot Debug.'

This action will generate a 'launch.json' file in the '.vscode' folder located within your project directory.

Now, copy and paste the provided code into your **launch.json** file."
```json
{
	"version": "0.2.0",
	"configurations": [
		{
			"name": "Godot",
			"type": "godot",
			"request": "launch",
			"project": "${workspaceFolder}",
			"port": 6006,
			"debugServer": 6006,
			"address": "127.0.0.1",
			"launch_game_instance": true,
			"launch_scene": false
		  }
	]
}
```

Once you've ensured everything is correctly set up, you can initiate breakpoints and debugging with a simple press of **F5**.  

{% image "screenshots/1020-godot-vscode-breakpoint.jpg", "Godot VSCode Autocomplete" %}

It's worth noting that in the future, Godot may update their extension for easier setup process. Until then, this workaround has been tried and tested, providing an effective solution.

If you have any questions or need further assistance, feel free to email me at <arifai.dev@gmail.com>