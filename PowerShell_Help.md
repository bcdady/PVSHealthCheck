# Intro

The following Help information was generated by running the following command in a PowerShell console, for script version 1.20, as generated July 8, 2019.

    PS C:\> get-help PVS_Assessment.ps1 -full

## Index

- [NAME](#NAME)
- [SYNOPSIS](#SYNOPSIS)
- [SYNTAX](#SYNTAX)
- [DESCRIPTION](#DESCRIPTION)
- [PARAMETERS](#PARAMETERS)
- [INPUTS](#INPUTS)
- [OUTPUTS](#OUTPUTS)
- [NOTES](#NOTES)

### NAME

PVS_Assessment.ps1

### SYNOPSIS

Creates a basic assessment of a Citrix PVS 5.x or later farm.

### SYNTAX

    C:\Webster\PVS_Assessment.ps1 [-AdminAddress <String>] [-CSV] [-Domain <String>] [-User <String>] [-Password <String>] [-Folder <String>] [<CommonParameters>]

    C:\Webster\PVS_Assessment.ps1 [-AdminAddress <String>] [-CSV] [-Domain <String>] [-User <String>] [-Password <String>] [-Folder <String>] -SmtpServer <String> [-SmtpPort <Int32>] [-UseSSL] -From <String> -To <String> [<CommonParameters>]

### DESCRIPTION

Creates a basic assessment of a Citrix PVS 5.x or later farm.

Creates a text document named after the PVS farm.

Register the old string-based PVS Console PowerShell Snap-in.

For versions of Windows prior to Windows 8 and Server 2012, run:

For 32-bit:

    %systemroot%\Microsoft.NET\Framework\v2.0.50727\installutil.exe "%ProgramFiles%\Citrix\Provisioning Services Console\McliPSSnapIn.dll"

For 64-bit:

    %systemroot%\Microsoft.NET\Framework64\v2.0.50727\installutil.exe "%ProgramFiles%\Citrix\Provisioning Services Console\McliPSSnapIn.dll"

For Windows 8.x and later, Server 2012 and later, run:

For 32-bit:

    %systemroot%\Microsoft.NET\Framework\v4.0.30319\installutil.exe "%ProgramFiles%\Citrix\Provisioning Services Console\McliPSSnapIn.dll"

For 64-bit:

    %systemroot%\Microsoft.NET\Framework64\v4.0.30319\installutil.exe "%ProgramFiles%\Citrix\Provisioning Services Console\McliPSSnapIn.dll"

All lines are one line.

If you are running 64-bit Windows, you will need to run both commands so the snap-in is registered for both 32-bit and 64-bit PowerShell.

NOTE: The account used to run this script must have at least Read access to the SQL Server that holds the Citrix Provisioning databases.

### PARAMETERS

    -AdminAddress <String>
        Specifies the name of a PVS server that the PowerShell script will connect to.
        Using this parameter requires the script be run from an elevated PowerShell session.
        Starting with V1.11 of the script, this requirement is now checked.
        This parameter has an alias of AA

        Required?                    false
        Position?                    named
        Default value
        Accept pipeline input?       false
        Accept wildcard characters?  false

    -CSV [<SwitchParameter>]
        Will create a CSV file for each Appendix.
        The default value is False.

        Output CSV filename is in the format:

        PVSFarmName_Assessment_Appendix#_NameOfAppendix.csv

        For example:
            TNPVSFarm_Assessment_AppendixA_AdvancedServerItems1.csv
            TNPVSFarm_Assessment_AppendixB_AdvancedServerItems2.csv
            TNPVSFarm_Assessment_AppendixC_ConfigWizardItems.csv
            TNPVSFarm_Assessment_AppendixD_ServerBootstrapItems.csv
            TNPVSFarm_Assessment_AppendixE_DisableTaskOffloadSetting.csv
            TNPVSFarm_Assessment_AppendixF_PVSServices.csv
            TNPVSFarm_Assessment_AppendixG_vDiskstoMerge.csv
            TNPVSFarm_Assessment_AppendixH_EmptyDeviceCollections.csv
            TNPVSFarm_Assessment_AppendixI_UnassociatedvDisks.csv
            TNPVSFarm_Assessment_AppendixJ_BadStreamingIPAddresses.csv
            TNPVSFarm_Assessment_AppendixK_MiscRegistryItems.csv
            TNPVSFarm_Assessment_AppendixL_vDisksConfiguredforServerSideCaching.csv
            TNPVSFarm_Assessment_AppendixM_MicrosoftHotfixesandUpdates.csv
            TNPVSFarm_Assessment_AppendixN_InstalledRolesandFeatures.csv
            TNPVSFarm_Assessment_AppendixO_PVSProcesses.csv

        Required?                    false
        Position?                    named
        Default value                False
        Accept pipeline input?       false
        Accept wildcard characters?  false

    -Domain <String>
        Specifies the domain used for the AdminAddress connection.

        Required?                    false
        Position?                    named
        Default value                $env:UserDnsDomain
        Accept pipeline input?       false
        Accept wildcard characters?  false

    -User <String>
        Specifies the user used for the AdminAddress connection.

        Required?                    false
        Position?                    named
        Default value
        Accept pipeline input?       false
        Accept wildcard characters?  false

    -Password <String>
        Specifies the password used for the AdminAddress connection.

        Required?                    false
        Position?                    named
        Default value
        Accept pipeline input?       false
        Accept wildcard characters?  false

    -Folder <String>
        Specifies the optional output folder to save the output report.

        Required?                    false
        Position?                    named
        Default value
        Accept pipeline input?       false
        Accept wildcard characters?  false

    -SmtpServer <String>
        Specifies the optional email server to send the output report.

        Required?                    true
        Position?                    named
        Default value
        Accept pipeline input?       false
        Accept wildcard characters?  false

    -SmtpPort <Int32>
        Specifies the SMTP port.
        The default port is 25.

        Required?                    false
        Position?                    named
        Default value                25
        Accept pipeline input?       false
        Accept wildcard characters?  false

    -UseSSL [<SwitchParameter>]
        Specifies whether to use SSL for the SmtpServer.
        THe default is False.

        Required?                    false
        Position?                    named
        Default value                False
        Accept pipeline input?       false
        Accept wildcard characters?  false

    -From <String>
        Specifies the username for the From email address.
        If SmtpServer is used, this is a required parameter.

        Required?                    true
        Position?                    named
        Default value
        Accept pipeline input?       false
        Accept wildcard characters?  false

    -To <String>
        Specifies the username for the To email address.
        If SmtpServer is used, this is a required parameter.

        Required?                    true
        Position?                    named
        Default value
        Accept pipeline input?       false
        Accept wildcard characters?  false

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see
        about_CommonParameters (https:/go.microsoft.com/fwlink/?LinkID=113216).

### INPUTS

    None.  You cannot pipe objects to this script.

### OUTPUTS

    No objects are output from this script.  This script creates a text file.

### NOTES

    NAME: PVS_Assessment.ps1
    VERSION: 1.20
    AUTHOR: Carl Webster, Sr. Solutions Architect at Choice Solutions (with a lot of 
    help from BG a, now former, Citrix dev)
    LASTEDIT: July 8, 2019

    -------------------------- EXAMPLE 1 --------------------------

    PS C:\PSScript >.\PVS_Assessment.ps1

    Will use all Default values.
    LocalHost for AdminAddress.

    -------------------------- EXAMPLE 2 --------------------------

    PS C:\PSScript >.\PVS_Assessment.ps1 -AdminAddress PVS1 -User cwebster -Domain WebstersLab -Password Abc123!@#

    This example is usually used to run the script against a PVS Farm in another domain or forest.

    Will use:
        PVS1 for AdminAddress.
        cwebster for User.
        WebstersLab for Domain.
        Abc123!@# for Password.

    -------------------------- EXAMPLE 3 --------------------------

    PS C:\PSScript >.\PVS_Assessment.ps1 -AdminAddress PVS1 -User cwebster

    Will use:
        PVS1 for AdminAddress.
        cwebster for User.
        Script will prompt for the Domain and Password

    -------------------------- EXAMPLE 4 --------------------------

    PS C:\PSScript >.\PVS_Assessment.ps1 -Folder \\FileServer\ShareName

    Output file will be saved in the path \\FileServer\ShareName

    -------------------------- EXAMPLE 5 --------------------------

    PS C:\PSScript >.\PVS_Assessment.ps1 -SmtpServer mail.domain.tld -From XDAdmin@domain.tld -To ITGroup@domain.tld -ComputerName DHCPServer01

    Script will use the email server mail.domain.tld, sending from XDAdmin@domain.tld, sending to ITGroup@domain.tld.
    If the current user's credentials are not valid to send email, the user will be prompted to enter valid credentials.

    -------------------------- EXAMPLE 6 --------------------------

    PS C:\PSScript >.\PVS_Assessment.ps1 -SmtpServer smtp.office365.com -SmtpPort 587 -UseSSL -From Webster@CarlWebster.com -To ITGroup@CarlWebster.com

    Script will use the email server smtp.office365.com on port 587 using SSL, sending from webster@carlwebster.com, sending to ITGroup@carlwebster.com. 
    If the current user's credentials are not valid to send email, the user will be prompted to enter valid credentials.

    -------------------------- EXAMPLE 7 --------------------------

    PS C:\PSScript >.\PVS_Assessment.ps1 -CSV

    Will use all Default values.
    LocalHost for AdminAddress.
    Creates a CSV file for each Appendix.
