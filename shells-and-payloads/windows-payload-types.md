# Windows Payload Types

**Payload Types to Consider**

* [DLLs](https://docs.microsoft.com/en-us/troubleshoot/windows-client/deployment/dynamic-link-library) A Dynamic Linking Library (DLL) is a library file used in Microsoft operating systems to provide shared code and data that can be used by many different programs at once. These files are modular and allow us to have applications that are more dynamic and easier to update. As a pentester, injecting a malicious DLL or hijacking a vulnerable library on the host can elevate our privileges to SYSTEM and/or bypass User Account Controls.
* [Batch](https://commandwindows.com/batch.htm) Batch files are text-based DOS scripts utilized by system administrators to complete multiple tasks through the command-line interpreter. These files end with an extension of `.bat`. We can use batch files to run commands on the host in an automated fashion. For example, we can have a batch file open a port on the host, or connect back to our attacking box. Once that is done, it can then perform basic enumeration steps and feed us info back over the open port.
* [VBS](https://www.guru99.com/introduction-to-vbscript.html) VBScript is a lightweight scripting language based on Microsoft's Visual Basic. It is typically used as a client-side scripting language in webservers to enable dynamic web pages. VBS is dated and disabled by most modern web browsers but lives on in the context of Phishing and other attacks aimed at having users perform an action such as enabling the loading of Macros in an excel document or clicking on a cell to have the Windows scripting engine execute a piece of code.
* [MSI](https://docs.microsoft.com/en-us/windows/win32/msi/windows-installer-file-extensions) `.MSI` files serve as an installation database for the Windows Installer. When attempting to install a new application, the installer will look for the .msi file to understand all of the components required and how to find them. We can use the Windows Installer by crafting a payload as an .msi file. Once we have it on the host, we can run `msiexec` to execute our file, which will provide us with further access, such as an elevated reverse shell.
* [Powershell](https://docs.microsoft.com/en-us/powershell/scripting/overview?view=powershell-7.1) Powershell is both a shell environment and scripting language. It serves as Microsoft's modern shell environment in their operating systems. As a scripting language, it is a dynamic language based on the .NET Common Language Runtime that, like its shell component, takes input and output as .NET objects. PowerShell can provide us with a plethora of options when it comes to gaining a shell and execution on a host, among many other steps in our penetration testing process.

### **Payload Generation**

| **Resource**                      | **Description**                                                                                                                                                                                                                                                                                                   |
| --------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `MSFVenom & Metasploit-Framework` | [Source](https://github.com/rapid7/metasploit-framework) MSF is an extremely versatile tool for any pentester's toolkit. It serves as a way to enumerate hosts, generate payloads, utilize public and custom exploits, and perform post-exploitation actions once on the host. Think of it as a swiss-army knife. |
| `Payloads All The Things`         | [Source](https://github.com/swisskyrepo/PayloadsAllTheThings) Here, you can find many different resources and cheat sheets for payload generation and general methodology.                                                                                                                                        |
| `Mythic C2 Framework`             | [Source](https://github.com/its-a-feature/Mythic) The Mythic C2 framework is an alternative option to Metasploit as a Command and Control Framework and toolbox for unique payload generation.                                                                                                                    |
| `Nishang`                         | [Source](https://github.com/samratashok/nishang) Nishang is a framework collection of Offensive PowerShell implants and scripts. It includes many utilities that can be useful to any pentester.                                                                                                                  |
| `Darkarmour`                      | [Source](https://github.com/bats3c/darkarmour) Darkarmour is a tool to generate and utilize obfuscated binaries for use against Windows hosts.                                                                                                                                                                    |