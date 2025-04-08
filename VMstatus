# PowerShell Script to List Running, Stopped, and Offline VMs in Hyper-V

# Retrieve all VMs on the current Hyper-V host
$VMs = Get-VM

# Create arrays to store running, stopped, and offline VMs
$RunningVMs = @()
$StoppedVMs = @()
$OtherStateVMs = @()

# Loop through all VMs to check their state
foreach ($VM in $VMs) {
    switch ($VM.State) {
        'Running' { $RunningVMs += $VM.Name }
        'Off' { $StoppedVMs += $VM.Name }
        default { $OtherStateVMs += "$($VM.Name) (State: $($VM.State))" }
    }
}

# Output results
Write-Host "`nRunning VMs:" -ForegroundColor Green
if ($RunningVMs.Count -eq 0) {
    Write-Host "No VMs are currently running." -ForegroundColor Yellow
} else {
    $RunningVMs | ForEach-Object { Write-Host $_ -ForegroundColor Green }
}

Write-Host "`nStopped VMs:" -ForegroundColor Red
if ($StoppedVMs.Count -eq 0) {
    Write-Host "No VMs are currently stopped." -ForegroundColor Yellow
} else {
    $StoppedVMs | ForEach-Object { Write-Host $_ -ForegroundColor Red }
}

Write-Host "`nOther State VMs (e.g., Paused, Saved, Starting):" -ForegroundColor Cyan
if ($OtherStateVMs.Count -eq 0) {
    Write-Host "No VMs are in other states." -ForegroundColor Yellow
} else {
    $OtherStateVMs | ForEach-Object { Write-Host $_ -ForegroundColor Cyan }
}
