# Visual Studio Workarounds

## `.editorconfig` spelling path is set relative to the location of the editor config file rather than to the solution folder.

### Observations

Using a global `.editorconfig` (e.g., c:\my\.editorconfig), the `spelling_exclusion_path` is resolved relative to the folder of the `.editorconfig` file rather than relative to the location of the the `.sln` file. This requires adding an '.editorconfig' in the same folder as the `.sln` folder. 

Specifically, using Visual Studio 17.5.3:

(a) Setting `spelling_exclusion_path = .\exclusion.dic` the file `c:\my\exclusion.dic` is created or updated.
	
(b) Commenting out `spelling_exclusion_path`, e.g., `# spelling_exclusion_path = .\exclusion.dic` the file <user>\AppData\Local\Microsoft\VisualStudio\17.0_b1161621\exclusion.dic` is updated or created.

(c) Adding an `editorconfig` file to the solution folder, e.g., `c:\my\vs\solution\src\MySolution.sln`, with `spelling_exclusion_path = .\exclusion.dic` the file `c:\my\vs\solution\src\exclusion.dic` is updated or created.
	
### Workaround

Add an editor config file in the same folder as the `.sln` file.

## The reference to the `Microsoft.Testing.Extensions.CodeCoverage` Package Can Be Removed

The `Microsoft.Testing.Extensions.CodeCoverage` package can be removed when using the `global.JSson` to specify the test `MSTest.SDX` as follows

### Search and Replace script

* Search: `<PackageReference Update="Microsoft.Testing.Extensions.CodeCoverage" Version="17.14.2" />`
* Binary Replace
```
    <!-- Already included with the default profile of the MSTest.SDK
      <PackageReference Update="Microsoft.Testing.Extensions.CodeCoverage" />
    -->
```

## `Windows Desktop Package warning

Warnings related to the Windows Desktop Package can be removed by adding the following Item to the project file.

```
<ItemGroup>
    <FrameworkReference Include="Microsoft.WindowsDesktop.App" />
</ItemGroup>
```

## MS Test Project Fails to Build After Running a Test

The following errors appears when attempting to compile a modified test project after running a test either a failed to successful test. 

```
1>------ Build started: Project: cc.isr.Json.AppSettings.ViewModels.MSTest, Configuration: Debug Any CPU ------
1>C:\Program Files\Microsoft Visual Studio\2022\Community\MSBuild\Current\Bin\amd64\Microsoft.Common.CurrentVersion.targets(4886,5): warning MSB3026: Could not copy "obj\Debug\net48\cc.isr.Json.AppSettings.ViewModels.MSTest.exe" to "bin\Debug\net48\cc.isr.Json.AppSettings.ViewModels.MSTest.exe". Beginning retry 1 in 1000ms. The process cannot access the file 'bin\Debug\net48\cc.isr.Json.AppSettings.ViewModels.MSTest.exe' because it is being used by another process. The file is locked by: "cc.isr.Json.AppSettings.ViewModels.MSTest (2352)"
1>C:\Program Files\Microsoft Visual Studio\2022\Community\MSBuild\Current\Bin\amd64\Microsoft.Common.CurrentVersion.targets(5364,5): warning MSB3026: Could not copy "C:\my\lib\vs\core\json\src\app.settings\app.settings.view.models.mstest\obj\Debug\net9.0\apphost.exe" to "bin\Debug\net9.0\cc.isr.Json.AppSettings.ViewModels.MSTest.exe". Beginning retry 1 in 1000ms. The process cannot access the file 'bin\Debug\net9.0\cc.isr.Json.AppSettings.ViewModels.MSTest.exe' because it is being used by another process. The file is locked by: "cc.isr.Json.AppSettings.ViewModels.MSTest (9460)"
1>C:\Program Files\Microsoft Visual Studio\2022\Community\MSBuild\Current\Bin\amd64\Microsoft.Common.CurrentVersion.targets(4886,5): warning MSB3026: Could not copy "obj\Debug\net472\cc.isr.Json.AppSettings.ViewModels.MSTest.exe" to "bin\Debug\net472\cc.isr.Json.AppSettings.ViewModels.MSTest.exe". Beginning retry 1 in 1000ms. The process cannot access the file 'bin\Debug\net472\cc.isr.Json.AppSettings.ViewModels.MSTest.exe' because it is being used by another process. The file is locked by: "cc.isr.Json.AppSettings.ViewModels.MSTest (9744)"
1>C:\Program Files\Microsoft Visual Studio\2022\Community\MSBuild\Current\Bin\amd64\Microsoft.Common.CurrentVersion.targets(4886,5): warning MSB3026: Could not copy "obj\Debug\net48\cc.isr.Json.AppSettings.ViewModels.MSTest.exe" to "bin\Debug\net48\cc.isr.Json.AppSettings.ViewModels.MSTest.exe". Beginning retry 2 in 1000ms. The process cannot access the file 'bin\Debug\net48\cc.isr.Json.AppSettings.ViewModels.MSTest.exe' because it is being used by another process. The file is locked by: "cc.isr.Json.AppSettings.ViewModels.MSTest (2352)"
1>C:\Program Files\Microsoft Visual Studio\2022\Community\MSBuild\Current\Bin\amd64\Microsoft.Common.CurrentVersion.targets(5364,5): warning MSB3026: Could not copy "C:\my\lib\vs\core\json\src\app.settings\app.settings.view.models.mstest\obj\Debug\net9.0\apphost.exe" to "bin\Debug\net9.0\cc.isr.Json.AppSettings.ViewModels.MSTest.exe". Beginning retry 2 in 1000ms. The process cannot access the file 'bin\Debug\net9.0\cc.isr.Json.AppSettings.ViewModels.MSTest.exe' because it is being used by another process. The file is locked by: "cc.isr.Json.AppSettings.ViewModels.MSTest (9460)"
1>C:\Program Files\Microsoft Visual Studio\2022\Community\MSBuild\Current\Bin\amd64\Microsoft.Common.CurrentVersion.targets(4886,5): warning MSB3026: Could not copy "obj\Debug\net472\cc.isr.Json.AppSettings.ViewModels.MSTest.exe" to "bin\Debug\net472\cc.isr.Json.AppSettings.ViewModels.MSTest.exe". Beginning retry 2 in 1000ms. The process cannot access the file 'bin\Debug\net472\cc.isr.Json.AppSettings.ViewModels.MSTest.exe' because it is being used by another process. The file is locked by: "cc.isr.Json.AppSettings.ViewModels.MSTest (9744)"
1>C:\Program Files\Microsoft Visual Studio\2022\Community\MSBuild\Current\Bin\amd64\Microsoft.Common.CurrentVersion.targets(4886,5): warning MSB3026: Could not copy "obj\Debug\net48\cc.isr.Json.AppSettings.ViewModels.MSTest.exe" to "bin\Debug\net48\cc.isr.Json.AppSettings.ViewModels.MSTest.exe". Beginning retry 3 in 1000ms. The process cannot access the file 'bin\Debug\net48\cc.isr.Json.AppSettings.ViewModels.MSTest.exe' because it is being used by another process. The file is locked by: "cc.isr.Json.AppSettings.ViewModels.MSTest (2352)"
1>C:\Program Files\Microsoft Visual Studio\2022\Community\MSBuild\Current\Bin\amd64\Microsoft.Common.CurrentVersion.targets(4886,5): warning MSB3026: Could not copy "obj\Debug\net472\cc.isr.Json.AppSettings.ViewModels.MSTest.exe" to "bin\Debug\net472\cc.isr.Json.AppSettings.ViewModels.MSTest.exe". Beginning retry 3 in 1000ms. The process cannot access the file 'bin\Debug\net472\cc.isr.Json.AppSettings.ViewModels.MSTest.exe' because it is being used by another process. The file is locked by: "cc.isr.Json.AppSettings.ViewModels.MSTest (9744)"
1>C:\Program Files\Microsoft Visual Studio\2022\Community\MSBuild\Current\Bin\amd64\Microsoft.Common.CurrentVersion.targets(5364,5): warning MSB3026: Could not copy "C:\my\lib\vs\core\json\src\app.settings\app.settings.view.models.mstest\obj\Debug\net9.0\apphost.exe" to "bin\Debug\net9.0\cc.isr.Json.AppSettings.ViewModels.MSTest.exe". Beginning retry 3 in 1000ms. The process cannot access the file 'bin\Debug\net9.0\cc.isr.Json.AppSettings.ViewModels.MSTest.exe' because it is being used by another process. The file is locked by: "cc.isr.Json.AppSettings.ViewModels.MSTest (9460)"
1>C:\Program Files\Microsoft Visual Studio\2022\Community\MSBuild\Current\Bin\amd64\Microsoft.Common.CurrentVersion.targets(4886,5): warning MSB3026: Could not copy "obj\Debug\net48\cc.isr.Json.AppSettings.ViewModels.MSTest.exe" to "bin\Debug\net48\cc.isr.Json.AppSettings.ViewModels.MSTest.exe". Beginning retry 4 in 1000ms. The process cannot access the file 'bin\Debug\net48\cc.isr.Json.AppSettings.ViewModels.MSTest.exe' because it is being used by another process. The file is locked by: "cc.isr.Json.AppSettings.ViewModels.MSTest (2352)"
1>C:\Program Files\Microsoft Visual Studio\2022\Community\MSBuild\Current\Bin\amd64\Microsoft.Common.CurrentVersion.targets(5364,5): warning MSB3026: Could not copy "C:\my\lib\vs\core\json\src\app.settings\app.settings.view.models.mstest\obj\Debug\net9.0\apphost.exe" to "bin\Debug\net9.0\cc.isr.Json.AppSettings.ViewModels.MSTest.exe". Beginning retry 4 in 1000ms. The process cannot access the file 'bin\Debug\net9.0\cc.isr.Json.AppSettings.ViewModels.MSTest.exe' because it is being used by another process. The file is locked by: "cc.isr.Json.AppSettings.ViewModels.MSTest (9460)"
1>C:\Program Files\Microsoft Visual Studio\2022\Community\MSBuild\Current\Bin\amd64\Microsoft.Common.CurrentVersion.targets(4886,5): warning MSB3026: Could not copy "obj\Debug\net472\cc.isr.Json.AppSettings.ViewModels.MSTest.exe" to "bin\Debug\net472\cc.isr.Json.AppSettings.ViewModels.MSTest.exe". Beginning retry 4 in 1000ms. The process cannot access the file 'bin\Debug\net472\cc.isr.Json.AppSettings.ViewModels.MSTest.exe' because it is being used by another process. The file is locked by: "cc.isr.Json.AppSettings.ViewModels.MSTest (9744)"
1>C:\Program Files\Microsoft Visual Studio\2022\Community\MSBuild\Current\Bin\amd64\Microsoft.Common.CurrentVersion.targets(4886,5): warning MSB3026: Could not copy "obj\Debug\net48\cc.isr.Json.AppSettings.ViewModels.MSTest.exe" to "bin\Debug\net48\cc.isr.Json.AppSettings.ViewModels.MSTest.exe". Beginning retry 5 in 1000ms. The process cannot access the file 'bin\Debug\net48\cc.isr.Json.AppSettings.ViewModels.MSTest.exe' because it is being used by another process. The file is locked by: "cc.isr.Json.AppSettings.ViewModels.MSTest (2352)"
1>C:\Program Files\Microsoft Visual Studio\2022\Community\MSBuild\Current\Bin\amd64\Microsoft.Common.CurrentVersion.targets(4886,5): warning MSB3026: Could not copy "obj\Debug\net472\cc.isr.Json.AppSettings.ViewModels.MSTest.exe" to "bin\Debug\net472\cc.isr.Json.AppSettings.ViewModels.MSTest.exe". Beginning retry 5 in 1000ms. The process cannot access the file 'bin\Debug\net472\cc.isr.Json.AppSettings.ViewModels.MSTest.exe' because it is being used by another process. The file is locked by: "cc.isr.Json.AppSettings.ViewModels.MSTest (9744)"
1>C:\Program Files\Microsoft Visual Studio\2022\Community\MSBuild\Current\Bin\amd64\Microsoft.Common.CurrentVersion.targets(5364,5): warning MSB3026: Could not copy "C:\my\lib\vs\core\json\src\app.settings\app.settings.view.models.mstest\obj\Debug\net9.0\apphost.exe" to "bin\Debug\net9.0\cc.isr.Json.AppSettings.ViewModels.MSTest.exe". Beginning retry 5 in 1000ms. The process cannot access the file 'bin\Debug\net9.0\cc.isr.Json.AppSettings.ViewModels.MSTest.exe' because it is being used by another process. The file is locked by: "cc.isr.Json.AppSettings.ViewModels.MSTest (9460)"
1>C:\Program Files\Microsoft Visual Studio\2022\Community\MSBuild\Current\Bin\amd64\Microsoft.Common.CurrentVersion.targets(4886,5): warning MSB3026: Could not copy "obj\Debug\net48\cc.isr.Json.AppSettings.ViewModels.MSTest.exe" to "bin\Debug\net48\cc.isr.Json.AppSettings.ViewModels.MSTest.exe". Beginning retry 6 in 1000ms. The process cannot access the file 'bin\Debug\net48\cc.isr.Json.AppSettings.ViewModels.MSTest.exe' because it is being used by another process. The file is locked by: "cc.isr.Json.AppSettings.ViewModels.MSTest (2352)"
1>C:\Program Files\Microsoft Visual Studio\2022\Community\MSBuild\Current\Bin\amd64\Microsoft.Common.CurrentVersion.targets(4886,5): warning MSB3026: Could not copy "obj\Debug\net472\cc.isr.Json.AppSettings.ViewModels.MSTest.exe" to "bin\Debug\net472\cc.isr.Json.AppSettings.ViewModels.MSTest.exe". Beginning retry 6 in 1000ms. The process cannot access the file 'bin\Debug\net472\cc.isr.Json.AppSettings.ViewModels.MSTest.exe' because it is being used by another process. The file is locked by: "cc.isr.Json.AppSettings.ViewModels.MSTest (9744)"
1>C:\Program Files\Microsoft Visual Studio\2022\Community\MSBuild\Current\Bin\amd64\Microsoft.Common.CurrentVersion.targets(5364,5): warning MSB3026: Could not copy "C:\my\lib\vs\core\json\src\app.settings\app.settings.view.models.mstest\obj\Debug\net9.0\apphost.exe" to "bin\Debug\net9.0\cc.isr.Json.AppSettings.ViewModels.MSTest.exe". Beginning retry 6 in 1000ms. The process cannot access the file 'bin\Debug\net9.0\cc.isr.Json.AppSettings.ViewModels.MSTest.exe' because it is being used by another process. The file is locked by: "cc.isr.Json.AppSettings.ViewModels.MSTest (9460)"
1>C:\Program Files\Microsoft Visual Studio\2022\Community\MSBuild\Current\Bin\amd64\Microsoft.Common.CurrentVersion.targets(4886,5): warning MSB3026: Could not copy "obj\Debug\net48\cc.isr.Json.AppSettings.ViewModels.MSTest.exe" to "bin\Debug\net48\cc.isr.Json.AppSettings.ViewModels.MSTest.exe". Beginning retry 7 in 1000ms. The process cannot access the file 'bin\Debug\net48\cc.isr.Json.AppSettings.ViewModels.MSTest.exe' because it is being used by another process. The file is locked by: "cc.isr.Json.AppSettings.ViewModels.MSTest (2352)"
1>C:\Program Files\Microsoft Visual Studio\2022\Community\MSBuild\Current\Bin\amd64\Microsoft.Common.CurrentVersion.targets(4886,5): warning MSB3026: Could not copy "obj\Debug\net472\cc.isr.Json.AppSettings.ViewModels.MSTest.exe" to "bin\Debug\net472\cc.isr.Json.AppSettings.ViewModels.MSTest.exe". Beginning retry 7 in 1000ms. The process cannot access the file 'bin\Debug\net472\cc.isr.Json.AppSettings.ViewModels.MSTest.exe' because it is being used by another process. The file is locked by: "cc.isr.Json.AppSettings.ViewModels.MSTest (9744)"
1>C:\Program Files\Microsoft Visual Studio\2022\Community\MSBuild\Current\Bin\amd64\Microsoft.Common.CurrentVersion.targets(5364,5): warning MSB3026: Could not copy "C:\my\lib\vs\core\json\src\app.settings\app.settings.view.models.mstest\obj\Debug\net9.0\apphost.exe" to "bin\Debug\net9.0\cc.isr.Json.AppSettings.ViewModels.MSTest.exe". Beginning retry 7 in 1000ms. The process cannot access the file 'bin\Debug\net9.0\cc.isr.Json.AppSettings.ViewModels.MSTest.exe' because it is being used by another process. The file is locked by: "cc.isr.Json.AppSettings.ViewModels.MSTest (9460)"
Build has been canceled.
```

The last line indicate that the build was canceled by hitting `CTRL+BREAK`.

The errors seems to appear at random on different projects.

Apparently, the test executive seems to still be _holding_ the test executable file. 

The files are released after Visual Studio is restarted.

### Workaround: Close instances of MSTest.EXE from the Windows Task Manager

Solved by closing all instances of MSTest.exe in the windows task manager as suggested in [stackoverflow_workaround].

[stackoverflow_workaround]: https://stackoverflow.com/questions/5134137/build-error-the-process-cannot-access-the-file-because-it-is-being-used-by-ano
	