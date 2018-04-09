# tls-upgrade
Worldpay is providing this script for the purpose of updating registry settings to support TLS 1.2 for secured communications.  While we have tested this script in our labs, we cannot control any subsequent alteration or implementation usage.  Customers are strongly encouraged to back up their registry before running the script and understand that it is provided without warranty.

## Instructions to support TLS 1.2 in triPOS Direct on windows using the .reg file

* With the proper privileges (Admin), rename the file `windows-tls.txt` to `windows-tls.reg`
* Double click the reg file to insert the new registry key: `SchUseStrongCrypto = 1`
* Reboot the server

## Instructions to support TLS 1.2 in triPOS Direct on windows manually

1. With the proper privileges (Admin), start the registry editor by clicking on Start and Run. Type in "regedit" into the Run field (without quotations).
2. Highlight Computer at the top of the registry tree. Backup the registry first by clicking on File and then on Export. Select a file location to save the registry file.

   * Note: You will be editing the registry. This could have detrimental effects on your computer if done incorrectly, so it is strongly advised to make a backup.
3. Browse to the following registry key:

   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NetFramework\v4.0.30319
4. Right-click on the right pane and create a new DWORD (32-bit) Value with Name SchUseStrongCrypto.
5. Ensure that the Value data field is set to 1 and the Base is Hexadecimal. Click on OK.
6. Repeat steps 4 and 5 for the registry key: HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NetFramework\v4.0.30319
7. Reboot the server


## Instructions to support TLS 1.2 in triPOS Direct on linux using the bash file

* Rename the file `linux-tls.txt` to `linux-tls.sh`
* Ensure the renamed file is executable and run `.\linux-tls.sh` with the proper privileges (sudo or root)
* Reboot the server

## Instructions to support TLS 1.2 in triPOS Direct on linux manually

Run the below commands with the proper privileges (sudo or root):
```bash
yum install yum-utils
rpm --import "http://keyserver.ubuntu.com/pks/lookup?op=get&search=0x3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF"
yum-config-manager --add-repo http://download.mono-project.com/repo/centos6/

yum install mono-complete

certmgr -ssl -m https://transaction.elementexpress.com
```


Worldpay is providing this script for the purpose of updating registry settings to support TLS 1.2 for secured communications.  While we have tested this script in our labs, we cannot control any subsequent alteration or implementation usage.  Customers are strongly encouraged to back up their registry before running the script and understand that it is provided without warranty.

