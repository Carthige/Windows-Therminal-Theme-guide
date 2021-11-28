# Windows terminal themes

This is a guide to help you install the Windows Terminal and setup themes to customize your therminal.

## Step 1: Install the Windows Terminal

To install the windows terminal go to the Microsoft Store app and search for the [Windows Terminal](https://www.microsoft.com/store/productId/9N0DX20HK701) App. 



## Step 2: Install Oh-my-posh themes

Open the Windows Terminal app with administrator privaleges and run the following line to install Oh-my-posh.

```powershell
Install-Module oh-my-posh -Scope CurrentUser
```

To enable Oh-my-posh in the current session run the following command.

```powershell
Import-Module oh-my-posh
```

To list the available themes go to [this link](https://ohmyposh.dev/docs/themes) or run:

```powershell
Get-PoshThemes
```

To enable your chosen prompt run.

```powershell
Set-PoshPrompt -Theme tonybaloney
```

The theme should be applied now. Problems with the font will be solved in a later step. 

## Step 3: Set Oh-my-posh theme to launch at startup

In the previous step the theme was enabled for only the session you are working in. To set the theme every time you launch the terminal we will have to adjust the powershell profile settings. 

```powershell
notepad $profile
```

This command will launch notepad with your powershell profile. If no profile was found you will be prompted to make a new one. 

In this profile add the following lines at the top of the file. 

```powershell
Import-Module oh-my-posh 
Set-PoshPrompt -Theme tonybaloney
```

This should start the app with your favorite Oh-my-posh theme. 

If you get prompted with a error message that says that scripts cannot be run on this machine, the Execution scope needs to be changed. 

To see what your current execution policy is run:

```powershell
Get-ExecutionPolicy -List
```

In a fresh Windows install all the execution policies are set to `Undefinded` . In order to be able to have our nice themes we have to set the CurrentUser policy to RemoteSigned. To do this run:

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

The following links provide documentation on the the shown commands:

+ [Set-ExecutionPolicy](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-7.2) 

+ [Get-ExecutionPolicy]([Get-ExecutionPolicy (Microsoft.PowerShell.Security) - PowerShell | Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-executionpolicy?view=powershell-7.2))



## Step 4: Install Fond with embedded icons

The Nerdfonts webpage has taken popular fonts and embedded icons into these. In some of these icons are used by oh-my-posh. Go to the [downloads page](https://www.nerdfonts.com/font-downloads) of the Nerdfont website and download your favourate fonts. 

If you like the Windows default search for `Caskaydia Cove Nerd Font` . Download the Fonts, unzip them, and install the fonts. You can do this by typing `Font settings` in the windows search bar and drag and drop the new fonts in there. 

Now the fonts are installed goto the Windows Terminal settings. Goto Profiles, Defaults, Appearance, Font face and set it to `CaskaydiaCove Nerd Font Mono` or the font you just installed. 

All the icons used in your oh-my-posh theme should be working. 



## Optional

### Option 1: Add Git-bash to the Windows Terminal

1. Go the Settings of the Windows Terminal.

2. Open the JSON settings file. 

3. Find `profiles`  and ind profiles find `list` 

4. Add the following code to it:
   
   ```json
   "guid": "{0affa2d1-a8d4-4b80-8eaa-dc5c1b8b58b1}",
   "closeOnExit": "always",
   "commandline": "\"D:\\Program Files\\Git\\usr\\bin\\bash.exe\" -i -l",
   "icon": "D:\\Program Files\\Git\\mingw64\\share\\git\\git-for-windows.ico",
   "name": "Git Bash",
   "acrylicOpacity": 0.8,
   "useAcrylic": true
   ```

Make sure that the guid is unique, and the commandline and icon paths are correct. 



### Update terminal inside VS Code

If you completed step 1-4 you might want to update the font of your VS Code terminal as well so all the themes show up nicely. 

1. Open VS Code and go to settings

2. Search for font and under Features>Terminal you will the intergrated font family used for your terminal

3. Copy the name of the font you setup in step for or write `"CaskaydiaCove Nerd Font Mono"` . The quotes are needed because the font has spaces in its name. 
