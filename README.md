# InstallZshWsl

## Install PowerLines fonts


## Check presence of WSL in Regedit
HKCU:\Console\*WSL_NAME*
If it does not appear,
* right click on the title of the console host
* change the font size from exemple from 14 to 12
* it chose add the WSL in the list `HKCU:\Console`

## Update Font pallette for specific WSL

In a powershell :

```
Get-ChildItem "HKCU:\Console\*openSUSE*" | ForEach-Object {
    Set-ItemProperty -Path Registry::$($_.Name) -Name ColorTable00 -Value 3549952
    Set-ItemProperty -Path Registry::$($_.Name) -Name ColorTable01 -Value 9868419
    Set-ItemProperty -Path Registry::$($_.Name) -Name ColorTable02 -Value 7695960
    Set-ItemProperty -Path Registry::$($_.Name) -Name ColorTable03 -Value 10592659
    Set-ItemProperty -Path Registry::$($_.Name) -Name ColorTable04 -Value 1461195
    Set-ItemProperty -Path Registry::$($_.Name) -Name ColorTable05 -Value 12874092
    Set-ItemProperty -Path Registry::$($_.Name) -Name ColorTable06 -Value 8616805
    Set-ItemProperty -Path Registry::$($_.Name) -Name ColorTable07 -Value 14018798
    Set-ItemProperty -Path Registry::$($_.Name) -Name ColorTable08 -Value 4339207
    Set-ItemProperty -Path Registry::$($_.Name) -Name ColorTable09 -Value 13798182
    Set-ItemProperty -Path Registry::$($_.Name) -Name ColorTable10 -Value 39301
    Set-ItemProperty -Path Registry::$($_.Name) -Name ColorTable11 -Value 10002730
    Set-ItemProperty -Path Registry::$($_.Name) -Name ColorTable12 -Value 3093212
    Set-ItemProperty -Path Registry::$($_.Name) -Name ColorTable13 -Value 8533715
    Set-ItemProperty -Path Registry::$($_.Name) -Name ColorTable14 -Value 35253
    Set-ItemProperty -Path Registry::$($_.Name) -Name ColorTable15 -Value 14939901
}
```

