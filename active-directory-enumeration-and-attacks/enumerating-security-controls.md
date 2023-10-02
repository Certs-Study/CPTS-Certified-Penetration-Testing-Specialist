# 🟢 Enumerating Security Controls

### Windows Defender

```powershell
Get-MpComputerStatus
```

### AppLocker

```
Get-AppLockerPolicy -Effective | select -ExpandProperty RuleCollections
```

### PowerShell Constrained Language Mode

```
$ExecutionContext.SessionState.LanguageMode
```

PowerShell [Constrained Language Mode](https://devblogs.microsoft.com/powershell/powershell-constrained-language-mode/)

### LAPS

Microsoft [Local Administrator Password Solution (LAPS)](https://www.microsoft.com/en-us/download/details.aspx?id=46899) is used to randomize and rotate local administrator passwords on Windows hosts and prevent lateral movement.

Tool: [LAPSToolkit](https://github.com/leoloobeek/LAPSToolkit)&#x20;

#### Using Find-LAPSDelegatedGroups

```
Find-LAPSDelegatedGroups
```

#### Using Find-AdmPwdExtendedRights

```
Find-AdmPwdExtendedRights
```

#### Using Get-LAPSComputers

```
Get-LAPSComputers
```
