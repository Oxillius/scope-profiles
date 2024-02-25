<img src="https://cdn.discordapp.com/attachments/1042684239163969559/1211389506603974666/image.png?ex=65ee0564&is=65db9064&hm=dcaeb7b40447c9f5e627a99be10222b78b24d50ecdc36ceab7678b04eca7cef1&" align="right" width=30%>

# Live STARS Traffic (scope)
Huge thanks to [@k2fc (Denis)](https://github.com/k2fc) for creating the [scope](https://github.com/k2fc/scope) repository that intergrates live traffic of the United States TRACONs into a STARS simulator. Thank you to [@glott (Josh Glottmann)](https://github.com/glott) and Shane Friedman for teaching others how to compile this program for personal use and how to create their own files for TRACONs. Below are the instructions on how to compile the program for yourself using Git CMD and nuget.exe. This repository has all TRACONs from the ZMA ARTCC along with the BNA TRACON from the ZME ARTCC. 

> [!WARNING]
> When you use the **CTRL + S** (save) command, the action is irreversible. Any changes made to your scope will be saved in the XML file you selected after opening the scope executable. Please make file backups of the preferences you make as there is no undo button.

### STARS Commands:
	F1: Holding toggles Beacon Readout
	CTRL + F1: Re-centers radar scope
	CTRL + F2: Video Maps Menu (popup)
	F7: MULTIFUNC
	CTRL + F8: Hides DCB
	F12: Signon (Example: 1V for MIA Approach)
	CTRL + Q: Toggles quick look (Enables FDB for all Primary targets)
### Miscellaneous Commands:
	CTRL + P: Settings Menu (popup)
	CTRL + S: Save preferences (Saves to .xml)
	CTRL + C: Exit application

## Step (1): Dependencies Installation (~5 Minutes)
1) Download [dotnet 7.0.405 x64](https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/sdk-7.0.405-windows-x64-installer) if your Windows is running x64. Download [dotnet 7.0.405 x86](https://download.visualstudio.microsoft.com/download/pr/79c973e6-7992-4b55-a175-981812c5dfb9/cd403d7bb1c56c104e148655c985fc00/dotnet-sdk-7.0.405-win-x86.exe) if your Windows is running x86. **Once you download dotnet 7.0.405 x64 or x86**, run the exe file and after running delete the dotnet-sdk-7.0.405-win-x86.exe file from your Downloads (or don't delete if you you don't want a clean Downloads folder, up to you).
2) Install [Git for Windows](https://git-scm.com/downloads) and click next for each prompt from the Installation Manager (You can delete the installer once the Installation Manager is done).
3) Download [nuget.exe](https://dist.nuget.org/win-x86-commandline/latest/nuget.exe) and leave it in your Downloads folder.

## Step (2): GitHub account setup and SSH key intilization (~7 Minutes)
1) Create a GitHub account if you don't have one already and verify your email.
2) Open Git CMD in Windows and run the ``ssh-keygen -o -t rsa -C "your@email.com"`` command.
3) To copy the new generated SSH key to your clipboard, run the  ``copy < ~/.ssh/id_ed25519.pub`` command in Git CMD. If this command doesn't work locate the hidden .ssh file found in the directory ``C:\Users\YOURNAME\.ssh\id_rsa.pub``, open this file in a Text Editor and copy its contents.
4) Navigate to <em>Settings</em> on the GitHub website then select <em>SSH and GPG keys</em> and click the green button labeled <em>New SSH key</em>.
5) Title the key anything you'd like. Keep the Key type as <em>Authentication Key</em> and Paste the new SSH key from your clipboard into the Key free-text field. After all fields are filled, click the green <em>Add SSH key</em> button.

## Step (3): Scope.exe Installation using Git CMD (~8 Minutes)
> [!IMPORTANT]
> Before you complete following the steps, ensure you have meet the requirements: (a) Running Windows 10/11, (b) Downloaded all Dependencies listed above, (c) Have a GitHub account, (d) Have Git CMD installed (Git for Windows), (e) SSH key is linked to Git CMD terminal.

1) Open Git CMD in Windows and use the CD command to select up where you want to save the scope file.
> Example: Type and run the ``CD Documents`` command (In this example, the Documents folder is where the scope folder will be copied from GitHub, replace this Directory with anywhere you want to save the file).
2) Run the ``git clone git@github.com:k2fc/scope.git`` command in Git CMD.
3) Drag the nuget.exe from your Downloads folder into the ``...\...\scope`` folder that was cloned from GHithub (If you used the example in Step 1, you would find this file in the Directory of ``C:\Users\...\Documents\scope``.
4) Navigate back to the Git CMD window and run the CD command to navigate to the scope folder, for example, ``CD C:\Users\...\Documents\scope`` and the ``nuget.exe install`` and then ``nuget.exe restore`` command.
6) Run the ``git clone git@github.com:k2fc/csharp-metar-decoder.git`` command in Git CMD.
7) Run the ``dotnet build`` command in Git CMD.

You can find the new compiled program in your scope folder under the directory of ``...\...\scope\build\Debug``