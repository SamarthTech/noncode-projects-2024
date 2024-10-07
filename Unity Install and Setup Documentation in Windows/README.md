# Unity Installation and Setup Guide for Windows

## Table of Contents
1. [System Requirements](#1-system-requirements)  
2. [Installing Unity Hub](#2-installing-unity-hub)  
3. [Installing Unity Editor](#3-installing-unity-editor)  
4. [Setting up Visual Studio](#4-setting-up-visual-studio)  
5. [Starting Your First Unity Project](#5-starting-your-first-unity-project)  
6. [Unity Editor Overview](#6-unity-editor-overview)  
7. [Building and Running First Project](#7-building-and-running-first-project)  
8. [Additional Resources](#8-additional-resources)  

## 1. System Requirements
Before installing Unity, ensure your machine meets the following requirements:  
- Operating System: Windows 10, 64-bit
- CPU: Intel Core i5 or higher
- RAM: 8 GB minimum (16 GB recommended)
- Graphics Card: DX10, DX11, or DX12 compatible GPU
- Hard Drive: SSD with at least 20 GB free space
- DirectX: Version 10 or higher
- Internet: A stable internet connection for installing and accessing online resources  

## 2. Installing Unity Hub
Unity Hub is a desktop application that lets you manage your Unity projects and installations.  
**Steps:**  
- Download Unity Hub:  
    - Visit the [Unity website](https://unity.com/download) and download the latest version of Unity Hub for Windows.  
- Install Unity Hub:  
    - Run the downloaded `UnityHubSetup.exe` file and follow the on-screen instructions.  
- Sign in or Create a Unity Account:  
    - Launch Unity Hub and sign in with your Unity account. If you don't have one, create a new account for free.  

## 3. Installing Unity Editor  
After setting up Unity Hub, you can install the Unity Editor.  
**Steps:**  
- Open Unity Hub and go to the `Installs` tab.  
- Click the Install Editor button and select the latest `LTS (Long-Term Support)` version of Unity, or choose a specific version you need.  
- Select Modules:  
    - In the installation options, select additional modules like:  
        - **Windows Build Support** (IL2CPP) (for building projects for Windows).  
        - **Android Build Support** (if targeting mobile devices).  
        - **WebGL Build Support** (for web-based games).  

- Install:  
    - Click Install and wait for Unity Editor to download and install.  

## 4. Setting up Visual Studio  
Unity uses C# as its primary programming language, and Visual Studio is the preferred code editor.

**Steps:**  
- During Unity installation, ensure you check the option to install Microsoft Visual Studio Community Edition (if not already installed).  
- If you missed this step, download Visual Studio from [here](https://visualstudio.microsoft.com/vs/community/) and install it manually.  
- During the installation process, select the Game development with Unity workload. This will install the required Unity tools.  

## 5. Starting Your First Unity Project  
Now that you have Unity installed, let's create your first project.

**Steps:**  
- Open Unity Hub.
- Click the Projects tab and click New Project.
- Select a project template:  
    - **3D:** Ideal for 3D games and applications.  
    - **2D:** For 2D games.  
    - **URP (Universal Render Pipeline)**: For optimized, high-quality visuals.
- Name your project and choose the location where you want to save it.
- Click Create.  

## 6. Unity Editor Overview  
Once your project is created, the Unity Editor will open. Here’s an overview of the main windows and features:

-  **Scene View:**  
The Scene View is where you visually design and place objects in your game. You can move around the scene using the middle mouse button and zoom in and out with the scroll wheel.
- **Game View:**  
The Game View shows what your game will look like during play mode. You can test gameplay and see how the game performs.
- **Hierarchy:**  
The Hierarchy lists all the GameObjects in the current scene. Every element in your game (characters, lights, cameras, etc.) will appear here.
- **Project Window:**  
The Project Window shows all the files in your project (assets, scripts, models, textures, etc.).
- **Inspector:**  
The Inspector displays details and properties for the selected object in the scene. For example, you can adjust a GameObject's position, scale, or rotation here.
- **Console:**
The Console shows debug information, warnings, and errors in your game.  

## 7. Building and Running First Project  
Once you’re happy with your project, you can build and run it on your target platform.

**Steps:**  
- Save your Scene:
    - Click `File` > `Save` and give your scene a name.
- Open Build Settings:  
    - Go to `File` > `Build Settings`.
- Select Platform:
    - Choose your target platform (e.g., **PC**, **Mac & Linux Standalone** for Windows builds).
    - If you selected **Android** or **WebGL** modules earlier, you will also see options for those platforms.
    - Click `Switch Platform` to change the platform.
- Build and Run:  
    - Click `Build and Run` to compile the game. Select a folder to save the build, and Unity will compile and launch the game.
    - If you want to just build the project without running it immediately, click `Build`.  

## 8. Additional Resources  
- [Unity Learn](https://learn.unity.com/)
- [Unity Documentation](https://docs.unity3d.com/Manual/index.html)  
- [Unity Asset Store](https://assetstore.unity.com/)  
---
