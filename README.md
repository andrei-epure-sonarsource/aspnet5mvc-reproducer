# aspnet5mvc-reproducer

Steps to reproduce:

1. Clone this repo
2. Download SonarQube Developer Edition 9.0.0.45539, setup dev license and new admin password
3. Download SonarScanner for .NET version 5.2.2 from https://github.com/SonarSource/sonar-scanner-msbuild/releases/tag/5.2.2.33595
4. run the analysis

```
C:\SonarQube\scanner-dotnet-5.2.2\SonarScanner.MSBuild.exe begin /k:"aspnetcore5-scanner522" /d:sonar.verbose=true /d:sonar.login="..."
MSBuild.exe /t:Restore,Rebuild .\AspNetCoreMvc5.sln
C:\SonarQube\scanner-dotnet-5.2.2\SonarScanner.MSBuild.exe end /d:sonar.login="..."
```

The 2 issues (AspNetCoreMvc5\Program.cs(12,18): warning S1118 and AspNetCoreMvc5\Controllers\HomeController.cs(14,50): warning S4487 ) appear on the C# files, however there are no metrics and no highlighting for the C# code - only for the JS code.

Actual: no metrics, no highlighting for C# code. 
Expected: metrics and highlighting for C# code.
