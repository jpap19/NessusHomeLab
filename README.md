<h1>Nessus Essential Home Lab</h1>

<h2>Description</h2>
Vulnerability management basically consists of continually assessing assets, discovering vulnerabilities and remediate them in order to reduce those Weaknesses to an acceptable level.
In this lab, we will cover vulnerability scanning and vulnerability remediation. These are two of the main steps in the Vulnerability Management Lifecycle. Nessus is a proprietary vulnerability scanner developed by Tenable. 
We will be using Nessus Essentials to scan local VMs hosted on VMWare Workstation in order run credentialed scans to discover vulnerabilities, remediate some of the vulnerabilities, then perform a rescan to verify remediation..
<br />

<h2>Resources And Links To Download Required Softwares:</h2>

- <b>VMware SandBox</b>   https://www.vmware.com/products/workstation-player/workstation-player-evaluation.html
- <b>Windows 10 ISO</b>    https://www.microsoft.com/en-us/software-download/windows10
- <b>Nessus Essentials</b> https://www.tenable.com/products/nessus/nessus-essentials
- <b>Nessus User Guide</b> https://docs.tenable.com/Nessus.htm

<h2>Program walk-through:</h2>

<p align="center">
 
 The links provided here above can be used to download required softwares. The implementation will be in done in 4 Steps:

STEP 1: Install VMware SANDBOX, CREATE A VIRTUAL MACHINE FOR VULNERABILITY ASSESSMENT AND INSTALL WINDOWS 10 ON IT.

STEP 2: INSTALL and CONFIGURE NESSUS SCANNER

STEP 3: IDENTIFY VULNERABILITY ON WINDOWS HOST

STEP 4: PATCH AND REMEDIATE VULNERABILITIES


STEP 1: Install VMware SANDBOX, CREATE A VIRTUAL MACHINE FOR VULNERABILITY ASSESSMENT AND INSTALL WINDOWS 10 ON IT:
Go to the link provided here above, download and install VMware SANDBOX, then download windows 10 ISO and save in a folder on the computer. VMware  will be used to setup and run virtual machine, Windows 10 ISO  will be installed on the virtual machine.
 
1.1 VMware SANDBOX installed: <br/>

<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/VmwareInstalled.png" height="80%" width="80%" alt="Nessus Essential Home Lab"/>
<br />
<br />
1.2 VIRTUAL MACHINE CREATED FOR VULNERABILITY ASSESSMENT AND WINDOWS 10 INSTALLED ON IT: <br/>

<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/WindowsInstalledOnVM.png" height="80%" width="80%" alt="Nessus Essential Home Lab"/>
<br />
<br />

STEP 2: INSTALL and CONFIGURE NESSUS SCANNER: Follow the link above to Nessus, register on the first page and get the activation code in the email, Then use the download button in the email to get to Nessus download pages.

2.1 NESSUS ESSENTIAL Pages: <br/>

2.1.1 NESSUS ESSENTIAL Registration Page

<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/NessusDownloadPage.png" alt="Nessus Essential Home Lab"/>
<br />
<br />

2.1.2 NESSUS ESSENTIAL Download page: <br/>

<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/NessusDownloadPage2.png" alt="Nessus Essential Home Lab"/>
<br />
<br />

2.1.3 NESSUS ESSENTIAL installed on the local computer (Not the virtual machine) and localhost page: <br/>

<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/NessusLocalHost.png" alt="Nessus Essential Home Lab"/>
<br />
<br />

2.1.4 NESSUS ESSENTIAL localhost logged in : <br/>

<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/NessusLocalHost2.png" alt="Nessus Essential Home Lab"/>
<br />
<br />

STEP 3: IDENTIFY VULNERABILITY ON WINDOWS HOST

3.1 Windows Host Basic Scan

3.1.1 Virtual Machine Connectivity Test : From wf.msc, disable all public and private firewall profiles on the Windows Host VM. <br/>
Get the IP address of the windows 10 host installed on the virtual machine, verified it can be reached from our home network (Ping Test is successfull)  <br/>

<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/WindowsHostPing.png" alt="Nessus Essential Home Lab"/>
<br />
<br />

3.1.2 Copy the IP address (here 192.168.137.128) of the windows host in the Virtual machine and used it create a new scan in Nessus Essential (Choose Basic Network Scan)<br/>

<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/NewScanBasicScan.png" alt="Nessus Essential Home Lab"/>
<br />
<br />

3.1.3 Nessus Basic Scan creation (paste the IP address in the target area)<br/>

<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/NewScanBasicScan2.png" alt="Nessus Essential Home Lab"/>
<br />
<br />

3.1.4 Nessus Basic Scan running(Click on the play button to start scanning)<br/>

<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/NewScanBasicScan3.png" alt="Nessus Essential Home Lab"/>
<br />
<br />

3.1.5 Nessus Basic Scan Continuing<br/>

<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/scan1.png" alt="Nessus Essential Home Lab"/>
<br />
<br />

3.1.6 Nessus Basic Scan Complete<br/>

<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/scan3.png" alt="Nessus Essential Home Lab"/>
<br />
<br />

3.2 Indentifying vulnerabilities after basic scan completion. No Critical or high vulnerabilities discovered  <br/>

3.2.1 Example 1 of vulnerability identify: SMB signing not required. 17 vulnerabilities discovered <br/>

<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/scan5.png" alt="Nessus Essential Home Lab"/>
<br />
<br />

3.2.2 Example 2 of vulnerability identify: Microsoft Windows (Multiple Issues) 5 vulnerabilities discovered. <br/>

<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/scan4.png" alt="Nessus Essential Home Lab"/>
<br />
<br />

3.3 Credentials Scan Pre-configurations on the windows host virtual machine <br/>

We need to do Windows  Host Virtual machine configurations to accept credentials scan (As recommended by Nessus for credentials scanning against windows host that are not on their domain).
On the virtual host, first go to service.msc, Enable remote registry and turn it on. Secondly, go Network and Sharing center, Advanced sharing settings then, Enable firewall and printer sharing, Thirdly, Disable user account sharing
and finally add a key to the register editor to allow remote connection to the windows virtual machine, <br/>

3.3.1 Remote registry Enable: set startup type to Automatic and click start buton <br/>
<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/RemoteRegist.png" alt="Nessus Essential Home Lab"/>
<br />
<br />

3.3.1 Enable firewall and printer sharing <br/>
<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/FileAndPrintSharing.png" alt="Nessus Essential Home Lab"/>
<br />
<br />

3.3.2 Disable user account sharing <br/>
<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/UserAccoutSharing.png" alt="Nessus Essential Home Lab"/>
<br />
<br />

3.3.4 Registry key adding: Open register editor, browse to local machine, software, microsoft, windows, current version, policies, system. and then create the DWORD called "LocalAccountTokenFilterPolicy" hit enter and set value data to 1 and retart the virtual machine  <br/>
<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/registryeditor.png" alt="Nessus Essential Home Lab"/>
<br />
<br />

3.4 Nessus Essential Credentials Scan <br/>
On the my Scans page, click on the windows host, choose more, click on credentials, filled up using the VmWare username and password, and hit save buton.<br/>

3.4.1 Nessus Essential Credentials Scan configurations <br/>
<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/CredentialScan1.png" alt="Nessus Essential Home Lab"/>
<br />
<br />

3.4.2 Nessus Essential Credentials Scan running (Go back to My Scans page, select windows host and hit the play buton to start the credentials scanning.  Nessus Essential Credentials Scan Complete<br/>

<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/IdentfyVul1.png" alt="Nessus Essential Home Lab"/>
<br />
<br />

3.5 Identifying More vulnerabilities after Credentials Scan. Critical or high vulnerabilities discovered  <br/>

3.5.1 Example 1 of vulnerability identify: SMB signing not required. 33 vulnerabilities discovered compared to only 17 earlier with the bacic scan. <br/>

<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/IdentfyVul2.png" alt="Nessus Essential Home Lab"/>
<br />
<br />

3.5.2 Example 2 of vulnerability identify: Microsoft Windows (Multiple Issues). 33 vulnerabilities discovered with 7 critical compared to 17 earlier with no critical in the bacic scan <br/>

<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/IdentfyVul3.png" alt="Nessus Essential Home Lab"/>
<br />
<br />

3.6 More Scaning on a less secure host<br/>

We are going to install a deprecated software (old version of firefox for example) on the windows virtual machine and then run another scans. This will allow us to see more vulnerabilties on this very less secure virtual computer.

3.6.1 Old version of firefox (3.6.12 ) downloading on the windows host <br/>

<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/OldFirefox.png" alt="Nessus Essential Home Lab"/>
<br />
<br />

3.6.2 Old version of firefox (3.5.2 ) installed on the windows host <br/>

<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/OldFirefox2.png" alt="Nessus Essential Home Lab"/>
<br />
<br />

3.6.3 Identifying More vulnerabilities after a deprecated software installed on the windows host.  <br/>

3.6.3.1 Move vulnerabilities after scaning with the old versions of firefox installed. many more Critical or high vulnerabilities discovered <br/>

<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/FirefoxScan1.png" alt="Nessus Essential Home Lab"/>
<br />
<br />

3.6.3.1 Many vulnerabilities (35) discovered in the old version of firefox installed. <br/>

<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/FirefoxScan3.png" alt="Nessus Essential Home Lab"/>
<br />
<br />

3.6.3.3 Example 1 of vulnerability identify: SMB signing not required. 35 vulnerabilities discovered compared to only 33 earlier with the previous scan. <br/>

<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/FirefoxScan2.png" alt="Nessus Essential Home Lab"/>
<br />
<br />

3.6.3.4 Example 2 of vulnerability identify: Microsoft Windows (Multiple Issues).  35 vulnerabilities discovered with 7 critical compared to 33 earlier in the previous scan <br/>

<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/FirefoxScan4.png" alt="Nessus Essential Home Lab"/>
<br />
<br />

STEP 4: PATCH AND REMEDIATE VULNERABILITIES
In this section, We will uninstall old version of firefox and perform windows updates, then run Nessus scaning again to see the remediations achieved.

4.1 Old version of Firefox uninstalled<br/>

<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/RemediateScan1.png" alt="Nessus Essential Home Lab"/>
<br />
<br />

4.2 Windows Remediation <br/>

4.2.1 Windows not up to date <br/>

<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/RemediateScan2.png" alt="Nessus Essential Home Lab"/>
<br />
<br />

4.2.2 Windows update performed<br/>

<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/RemediateScan3.png" alt="Nessus Essential Home Lab"/>
<br />
<br />

4.3 Very less Vulnerabbilities discovered after remediations applied.  <br/>

4.3.1 Less Vulnerabbilities discovered after remediations applied.  <br/>

<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/RemediateScan4.png" alt="Nessus Essential Home Lab"/>
<br />
<br />

4.3.2 Less Vulnerabbilities discovered after remediations applied.  <br/>

<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/RemediateScan6.png" alt="Nessus Essential Home Lab"/>
<br />
<br />


<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
