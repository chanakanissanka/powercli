# powercli
#When your vmotion is failing with the "A virtual machine failed to migrate due to incompatibilities with target resource pool"
$spec = New-Object -TypeName VMware.Vim.VirtualMachineConfigSpec
$spec.ScheduledHardwareUpgradeInfo = New-Object -TypeName VMware.Vim.ScheduledHardwareUpgradeInfo
$spec.ScheduledHardwareUpgradeInfo.UpgradePolicy = "never"
$spec.ScheduledHardwareUpgradeInfo.VersionKey = 'vmx-11'
$vm = Get-VM [VM name]
$vm.ExtensionData.ReconfigVM_task($spec)

