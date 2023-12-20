## Praktikum 13 
Ma ei saanud pci sedadmete draiveri infot kätte :(
```
# Masina nimi, PowerShelli versioon ja Windowsi versioon
$hostname = $env:COMPUTERNAME
$psVersion = $PSVersionTable.PSVersion.ToString()
$osVersion = (Get-CimInstance Win32_OperatingSystem).Caption

# Võrgu konfiguratsioon
$networkConfig = Get-NetIPAddress | Where-Object { $_.InterfaceAlias -eq 'Ethernet' } | Select-Object IPAddress, PrefixLength, DefaultGateway, Dhcp
$macAddress = (Get-NetAdapter | Where-Object { $_.InterfaceAlias -eq 'Ethernet' }).MacAddress

# Arvuti protsessori kirjeldus ja põhimälu RAM kogus
$processorInfo = Get-CimInstance Win32_ComputerSystem | Select-Object Description
$ramInfo = Get-CimInstance Win32_ComputerSystem | Select-Object TotalPhysicalMemory

# Graafikakaardi info
$videoInfo = Get-CimInstance Win32_VideoController | Select-Object Name, DriverVersion, DriverDate, VideoModeDescription

# Arvuti kõvaketaste info
$diskInfo = Get-CimInstance Win32_DiskDrive | Select-Object PartitionStyle, Size
$partitionInfo = Get-CimInstance Win32_LogicalDisk | Where-Object { $_.DeviceID -eq 'C:' } | Select-Object FreeSpace

# PCI-seadmete draiverite info
$pciDevices = Get-WmiObject Win32_PnPSignedDriver | Where-Object { $_.DeviceClass -eq "PCI" } | Select-Object Description, Manufacturer, DriverVersion

# Arvutis olevad kasutajad
$users = Get-CimInstance Win32_UserAccount | Select-Object Name, Description, LocalAccount, Disabled

# Käimasolevate protsesside arv
$processCount = (Get-Process).Count

# 10 viimasena käivitatud protsessi info
$recentProcesses = Get-Process | Sort-Object StartTime -Descending | Select-Object -First 10 Name, Id, StartTime

# Arvuti kuupäev ja kellaaeg
$dateTime = Get-Date

# Salvesta info faili
$outputFilePath = "arvuti_info.txt"
@"
Masina nimi: $hostname
PowerShelli versioon: $psVersion
Windowsi versioon: $osVersion

Võrgu konfiguratsioon:
  IP-aadress: $($networkConfig.IPAddress)
  Võrgumask: $($networkConfig.PrefixLength)
  Gateway: $($networkConfig.DefaultGateway)
  DHCP lubatud: $($networkConfig.Dhcp)
  MAC-aadress: $macAddress

Arvuti protsessor ja RAM:
  Protsessor: $($processorInfo.Description)
  RAM kogus: $($ramInfo.TotalPhysicalMemory / 1GB) GB

Graafikakaart:
  Nimi: $($videoInfo.Name)
  Draiveri versioon: $($videoInfo.DriverVersion)
  Draiveri kuupäev: $($videoInfo.DriverDate)
  Ekraani lahutus: $($videoInfo.VideoModeDescription)

Kõvakettad:
  Partitsioonitabel: $($diskInfo.PartitionStyle)
  Ketta mahutavus: $($diskInfo.Size / 1GB) GB
  Vaba ruum C:-kettal: $($partitionInfo.FreeSpace / 1GB) GB

PCI-seadmete draiverid:
$($pciDevices | Format-Table -AutoSize)

Kasutajad:
$($users | Format-Table -AutoSize)

Käimasolevate protsesside arv: $processCount

Viimased 10 protsessi:
$($recentProcesses | Format-Table -AutoSize)

Arvuti kuupäev ja kellaaeg: $dateTime
"@ | Out-File -FilePath $outputFilePath -Encoding UTF8

Write-Host "Skripti käivitamise tulemus on salvestatud faili: $outputFilePath"
```
