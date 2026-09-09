name: Windows Teste

on:
  workflow_dispatch:

jobs:
  windows:
    runs-on: windows-latest

    steps:
      - name: Informações do Windows
        shell: powershell
        run: |
          Write-Host "===== WINDOWS TESTE ====="
          Get-ComputerInfo |
            Select-Object WindowsProductName, WindowsVersion, OsArchitecture

      - name: Informações da máquina
        shell: powershell
        run: |
          Write-Host "===== CPU ====="
          Get-CimInstance Win32_Processor |
            Select-Object Name, NumberOfLogicalProcessors

          Write-Host "===== RAM ====="
          $ram = Get-CimInstance Win32_ComputerSystem
          "{0:N2} GB" -f ($ram.TotalPhysicalMemory / 1GB)

          Write-Host "===== DISCO ====="
          Get-PSDrive -PSProvider FileSystem |
            Select-Object Name,
              @{N="UsedGB";E={[math]::Round($_.Used/1GB,2)}},
              @{N="FreeGB";E={[math]::Round($_.Free/1GB,2)}}

      - name: Teste final
        shell: powershell
        run: |
          Write-Host "Windows Runner funcionando!"
          Write-Host "Teste concluído com sucesso."
