# Global files for Visual Studio

This repository holds the current version of the global files that are used by Visual Studio.

$# Global Editor Configuration

ISR libraries use global editor configuration and test run settings. The files are stored under a folder structure that mirrors their actual folder statutre. For example, the editor configuration files, which is located under c:\my\ is located under .\src\my where as the run settings file, which islocated under c:\users\username is located under src\users\me.

Thus this command restores the editor configuration:
```
Copy .\src\my\.editorconfig c:\my\.editorconfig
```
When run frol the root folder of this repository. 

The this command restores the run settings:
```
Copy .\src\users\me\.runsettings c:\users\myusername\.runsettings
```

<a name="Repository-Owner"></a>
# Repository Owner
[ATE Coder]

<a name="Authors"></a>
## Authors
* [ATE Coder]  

<a name="legal-notices"></a>
## Legal Notices

Integrated Scientific Resources, Inc., and any contributors grant you a license to the documentation and other content in this repository under the [Creative Commons Attribution 4.0 International Public License] and grant you a license to any code in the repository under the [MIT License].

Integrated Scientific Resources, Inc., and/or other Integrated Scientific Resources, Inc., products and services referenced in the documentation may be either trademarks or registered trademarks of Integrated Scientific Resources, Inc., in the United States and/or other countries. The licenses for this project do not grant you rights to use any Integrated Scientific Resources, Inc., names, logos, or trademarks.

Integrated Scientific Resources, Inc., and any contributors reserve all other rights, whether under their respective copyrights, patents, or trademarks, whether by implication, estoppel or otherwise.

[Creative Commons Attribution 4.0 International Public License]: https://github.com/ATECoder/dn.vi.ivi/blob/main/license
[MIT License]: https://github.com/ATECoder/dn.vi.ivi/blob/main/license-code
[ATE Coder]: https://www.IntegratedScientificResources.com

[IVI Foundation]: https://www.ivifoundation.org
[Keysight I/O Suite]: https://www.keysight.com/en/pd-1985909/io-libraries-suite
[NI VISA]: https://www.ni.com/en-us/support/downloads/drivers/download.ni-visa.html#346210
[Microsoft .NET Framework]: https://dotnet.microsoft.com/download
