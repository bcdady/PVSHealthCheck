# Release Notes for PVS_Assessment.ps1

## Author

 Carl Webster, CTP and Sr. Solutions Architect at Choice Solutions

- webster@carlwebster.com
- [@carlwebster](https://twitter.com/carlwebster)
- http://www.CarlWebster.com

## Releases

- [Version 1.20 8-July-2019](#Version-120-8-July-2019)
- [Version 1.19 3-May-2019](#Version-119-3-May-2019)
- [Version 1.18 18-Apr-2019](#Version-118-18-Apr-2019)
- [Version 1.17 15-Apr-2019](#Version-117-15-Apr-2019)
- [Version 1.16 9-Apr-2019](#Version-116-9-Apr-2019)
- [Version 1.15 12-Apr-2018](#Version-115-12-Apr-2018)
- [Version 1.14 7-Apr-2018](#Version-114-7-Apr-2018)
- [Version 1.13 29-Mar-2017](#Version-113-29-Mar-2017)
- [Version 1.12 28-Feb-2017](#Version-112-28-Feb-2017)
- [Version 1.11 12-Sep-2016](#Version-111-12-Sep-2016)
- [Version 1.10 8-Sep-2016](#Version-110-8-Sep-2016)
- [Version 1.04 1-Aug-2016](#Version-104-1-Aug-2016)
- [Version 1.03 22-Feb-2016](#Version-103-22-Feb-2016)
- [Version 1.02 17-Feb-2016](#Version-102-17-Feb-2016)
- [Version 1.01 8-Feb-2016](#Version-101-8-Feb-2016)
- [Version 1.0 Released to the community on 2-Feb-2016](#Version-10-Released-to-the-community-on-2-Feb-2016)

### Version 1.20 8-July-2019

- Added to Farm properties, Citrix Provisioning license type: On-Premises or Cloud (new to 1808)
- Added to vDisk properties, Accelerated Office Activation (new to 1906)
- Added to vDisk properties, updated Write Cache types (new to 1811)
- Private Image with Asynchronous IO
- Cache on server, persistent with Asynchronous IO
- Cache in device RAM with overflow on hard disk with Asynchronous IO

### Version 1.19 3-May-2019

- Remove the following regkeys from analysis as they are for target devices, not PVS Servers
- (thanks to [Johan Parlevliet](https://github.com/parlevjo2) for pointing this out)
- HKLM:\SYSTEM\CurrentControlSet\Services\BNIStack\Parameters\SocketOpenRetryIntervalMS
- HKLM:\SYSTEM\CurrentControlSet\Services\BNIStack\ParametersSocketOpenRetryLimit

### Version 1.18 18-Apr-2019

- Fix bug reported by [Johan Parlevliet](https://github.com/parlevjo2)
- If either SQL server name has a port number, remove it before finding the IP address

### Version 1.17 15-Apr-2019

- Added Function ShowScriptOptions to show Parameters and some script values at the start of the script
- Changed the output of Appendix N to match the sort order
- Fixed bug preventing text output for Appendix L
- If no AdminAddress is entered, retrieve the local computer's name from $env:ComputerName
- If either SQL server has an instance name, remove it before finding the IP address
- Replaced all PSObject with PSCustomObject
- Updated Function line to use the optimized function from MBS from the Active Directory doc script
- Rewrote Line to use StringBuilder for speed
- Updated help text and ReadMe
- Updated the output for Appendix K for very long registry keys, data, and values and to keep the output
- the same as the XA/XD documentation script V2.23
- Went to Set-StrictMode -Version Latest, from Version 2 and cleaned up all related errors

### Version 1.16 9-Apr-2019

- Added "_Assessment" to output script report filename
- Added -CSV parameter
- Added Function GetInstalledRolesAndFeatures
- Added Function Get-IPAddress
- Added Function GetMicrosoftHotfixes
- Added Function GetPVSProcessInfo
- Added Function validObject
- Added License Server IP Address to Farm information
- Added SQL Server IP Address to Farm information
- Added Failover SQL Server IP Address to Farm information
- Changed the variable $pwdpath to $Script:pwdpath
- Changed Write-Verbose statements to Write-Host
- Fixed bug for Bad Streaming IP Addresses. The $ComputerName parameter was not passed to the OutputNicItem function
- Fixed bug when processing Service Failure Actions. It looks like I "assumed" there would always be three failure actions.
- Thanks to [Martin Therkelsen](https://github.com/mracket) for finding this logic flaw (bug)
- From Function OutputAppendixF2, remove the array sort. The same array is sorted in Function OutputAppendixF
- In Function OutputNicItem, Changed how $powerMgmt is retrieved.
- Will now show "Not Supported" instead of "N/A" if the NIC driver does not support Power Management (i.e. XenServer)
- To the DisableTaskOffload AppendixE, Added the statement "This setting is not needed if you are running PVS 6.0 or later"
- Updated each function that outputs each appendix to output a CSV file if -CSV is used
- Output CSV filename is in the format:
- PVSFarmName_Assessment_Appendix#_NameOfAppendix.csv
- For example:
- TNPVSFarm_Assessment_AppendixA_AdvancedServerItems1.csv
- TNPVSFarm_Assessment_AppendixB_AdvancedServerItems2.csv
- TNPVSFarm_Assessment_AppendixC_ConfigWizardItems.csv
- TNPVSFarm_Assessment_AppendixD_ServerBootstrapItems.csv
- TNPVSFarm_Assessment_AppendixE_DisableTaskOffloadSetting.csv
- TNPVSFarm_Assessment_AppendixF_PVSServices.csv
- TNPVSFarm_Assessment_AppendixG_vDiskstoMerge.csv
- TNPVSFarm_Assessment_AppendixH_EmptyDeviceCollections.csv
- TNPVSFarm_Assessment_AppendixI_UnassociatedvDisks.csv
- TNPVSFarm_Assessment_AppendixJ_BadStreamingIPAddresses.csv
- TNPVSFarm_Assessment_AppendixK_MiscRegistryItems.csv
- TNPVSFarm_Assessment_AppendixL_vDisksConfiguredforServerSideCaching.csv
- TNPVSFarm_Assessment_AppendixM_MicrosoftHotfixesandUpdateds.csv
- TNPVSFarm_Assessment_AppendixN_InstalledRolesandFeatures.csv
- TNPVSFarm_Assessment_AppendixO_PVSProcesses.csv
- Updated help text

### Version 1.15 12-Apr-2018

- Fixed invalid variable $Text

### Version 1.14 7-Apr-2018

- Added Operating System information to Functions GetComputerWMIInfo and OutputComputerItem
- Code cleanup from Visual Studio Code

### Version 1.13 29-Mar-2017

- Added Appendix L for vDisks configured to Cache on Server

### Version 1.12 28-Feb-2017

- Added Citrix PVS Services Failure Actions Appendix F2

### Version 1.11 12-Sep-2016

- Added an alias AA for AdminAddress to match the other scripts that use AdminAddress
- Added output to appendixes to show if nothing was found
- Added checking for $ComputerName parameter when testing PVS services
- Changed the "No unassociated vDisks found" to "<None found>" to match the changes to the other Appendixes
- Fixed an issue where Appendix I was not output
- Fixed error message in output when no PVS services were found (said No Bootstraps found)
- If remoting is used (-AdminAddress), check if the script is being run elevated. If not,
- show the script needs elevation and end the script
- Removed all references to $ErrorActionPreference since it is no longer used

### Version 1.10 8-Sep-2016

- Added Appendix K for 33 Misc Registry Keys
- Miscellaneous Registry Items That May or May Not Exist on Servers
- These items may or may not be needed
- This Appendix is strictly for server comparison only
- Added Break statements to most of the Switch statements
- Added checking the NIC's "Allow the computer to turn off this device to save power" setting
- Added function Get-RegKeyToObject contributed by Andrew Williamson @ Fujitsu Services
- Added testing for $Null �eq $DiskLocators. PoSH V2 did not like that I forgot to do that.
- Added to the console and report, lines when nothing was found for various items being checked.
- Cleaned up duplicate IP addresses appearing in Appendix J.
- Changed NICIPAddressess from array to hashtable
- Reset the StreamingIPAddresses array between servers
- Moved the initialization of arrays to the top of the script instead of inside a function.
- PoSH V2 did not like the �4>$Null�. I test for V2 now and use �2>$Null�.
- Script now works properly with PoSH V2 and PVS 5.x.x.
- Since PoSH V2 does not work with the way I forced Verbose on, I changed all the Write-Verbose statements to Write-Host.
- You should not be able to tell any difference.
- With the help and patience of Andrew Williamson and MBS, the script should now work with PVS servers that have multiple NICs

### Version 1.04 1-Aug-2016

- Added back missing AdminAddress, User and Password parameters
- Fixed several invalid output lines

### Version 1.03 22-Feb-2016

- Added validating the Store Path and Write Cache locations

### Version 1.02 17-Feb-2016

- In help text, changed the DLL registration lines to not wrap
- In help text, changed the smart quotes to regular quotes
- Added for Appendix E a link to the Citrix article on DisableTaskOffload
- Added link to PVS server sizing for server RAM calculation
- Added comparing Streaming IP addresses to the IP addresses configured for the server
- If a streaming IP address does not exist on the server, it is an invalid streaming IP address
- This is a bug in PVS that allows invalid IP addresses to be added for streaming IPs

### Version 1.01 8-Feb-2016

- Added specifying an optional output folder
- Added the option to email the output file
- Fixed several spacing and typo errors

### Version 1.0 Released to the community on 2-Feb-2016

- Generates a text file
- Supports PVS versions 5.x to 7.7
- Uses the old PVS PowerShell
