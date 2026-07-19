# Provisioning-Azure-Virtual-Machine
Watch me provision an Azure VM from start to finish.
https://www.loom.com/share/2cad6a4ec71047a18d92747fdef39e73

## Create and Access an Azure Windows Server Virtual Machine for Remote Administration

### Objective

Provision a Windows Server virtual machine in Azure, then connect to it remotely from a Linux workstation so it can be used for server management tasks such as installing and configuring Active Directory Domain Services.

### Key Steps

**1. Create the Azure virtual machine** [0:00](https://loom.com/share/2cad6a4ec71047a18d92747fdef39e73?t=0)

![generated-image-at-00:00:00](https://loom.com/i/a29358f47b984052b62e29b155030b39?workflows_screenshot=true)

- In Azure, start the process to create a new virtual machine.
- Choose the appropriate subscription/resource group setup as needed.
- Proceed to the VM creation form and begin entering the required details.

**2. Configure the VM name, region, and OS** [0:14](https://loom.com/share/2cad6a4ec71047a18d92747fdef39e73?t=14)

![generated-image-at-00:00:14](https://loom.com/i/3c929bfc29e2401cb33adf4be3c66fb3?workflows_screenshot=true)

- Enter a clear VM name; in the video, the VM is named **HelpDesk**.
- Select the deployment region; the example uses (**US)** Central US
- Choose the operating system image: **Windows Server Datacenter**.
- Select the **least costly** option that still meets the requirement.

**3. Set administrator credentials and remote access** [1:14](https://loom.com/share/2cad6a4ec71047a18d92747fdef39e73?t=74)

![generated-image-at-00:01:14](https://loom.com/i/7089d1f8c958443cbfc3df562abfa287?workflows_screenshot=true)

- Create the administrator username; the example uses **support**.
- Set a strong, secure password.
- Ensure **RDP** access is allowed so the machine can be reached remotely.
- Review the configuration before continuing.

**4. Wait for Azure provisioning to complete** [2:11](https://loom.com/share/2cad6a4ec71047a18d92747fdef39e73?t=131)

![generated-image-at-00:02:11](https://loom.com/i/8e452fc63b014660b7fab084f3b2b3fe?workflows_screenshot=true)

- Allow Azure time to finish creating and configuring the VM.
- The VM will be used to install and configure **Windows Server Manager** and **Active Directory Domain Services**.
- Confirm the VM is fully provisioned before attempting to connect.

**5. Verify the VM is ready before connecting** [5:24](https://loom.com/share/2cad6a4ec71047a18d92747fdef39e73?t=324)

![generated-image-at-00:05:24](https://loom.com/i/39aff4b60257481cb7f555dad81c9bf5?workflows_screenshot=true)

- Check the VM status in Azure.
- If the agent status shows **not ready**, wait a few minutes and refresh.
- Do not attempt remote access until the VM is fully available.

**6. Download the RDP file and prepare to connect from Linux** [7:04](https://loom.com/share/2cad6a4ec71047a18d92747fdef39e73?t=424)

![generated-image-at-00:07:04](https://loom.com/i/3d015eb83bc147108afa71a2d14cf5a1?workflows_screenshot=true)

- From your Linux workstation, choose a local connection method.
- Download the **RDP file** from Azure.
- Open the file using an RDP client on Linux rather than assuming SSH will be used.
- In the video, the user opens the file with **Remmina**.

**7. Choose the correct RDP connection method** [10:34](https://loom.com/share/2cad6a4ec71047a18d92747fdef39e73?t=634)

![generated-image-at-00:10:34](https://loom.com/i/09f0494140a8475299db9a2b4b77cb0d?workflows_screenshot=true)

- If prompted, understand the difference between connection options: 
  - **Connect**: opens the RDP file directly for a one-time connection.
  - **Import**: lets you save and edit the connection for future use.
- For this workflow, use **Connect** to proceed quickly.

**8. Troubleshoot connection errors on the Linux client** [11:13](https://loom.com/share/2cad6a4ec71047a18d92747fdef39e73?t=673)

![generated-image-at-00:11:13](https://loom.com/i/28b2703ea55448899b0f75a72850985b?workflows_screenshot=true)

- If an internal error appears, pause and investigate the Linux system state.
- Check for package installation issues or interrupted package configuration.
- Be aware that other software installations can interfere with RDP client behavior.

**9. Repair interrupted package configuration if needed** [18:41](https://loom.com/share/2cad6a4ec71047a18d92747fdef39e73?t=1121)

![generated-image-at-00:18:41](https://loom.com/i/0b919d90b1c845ddaf1bcbb8ad225266?workflows_screenshot=true)

- If the system has interrupted package installs, run the package repair command: 
  - `sudo dpkg --configure -a`
- This can resolve issues caused by incomplete installations such as VirtualBox or related dependencies.
- After repair, retry the RDP connection.

**10. Reopen the RDP file and complete the remote connection** [20:23](https://loom.com/share/2cad6a4ec71047a18d92747fdef39e73?t=1223)

![generated-image-at-00:20:23](https://loom.com/i/95d2663cea914fc69dd8de6c1c3a0e5f?workflows_screenshot=true)

- Open the downloaded RDP file again after fixing any package issues.
- Wait for the remote desktop session to initialize.
- Confirm that the Windows Server desktop loads successfully.

**11. Confirm the VM is accessible and ready for administration** [28:16](https://loom.com/share/2cad6a4ec71047a18d92747fdef39e73?t=1696)

![generated-image-at-00:28:16](https://loom.com/i/25f601cc91384eecb04c222abca2ecbf?workflows_screenshot=true)

- Verify that the Azure VM was provisioned successfully.
- Confirm that you can RDP into the machine without errors.
- Once connected, the VM is ready for the next administrative tasks, such as installing and configuring Active Directory.

### Cautionary Notes

- Use a strong, unique password for the VM administrator account.
- Ensure RDP is enabled only as needed and follow your organization’s security policies.
- If the Linux client shows package errors, fix the local system before retrying the connection.
- Do not assume SSH is the correct access method for a Windows Server VM; use RDP.
- Wait for Azure provisioning to fully complete before attempting to connect.

### Tips for Efficiency

- Choose the lowest-cost VM size that still meets the lab or project requirements.
- Use a clear VM name so it is easy to identify later.
- If the RDP client fails, try importing or reopening the file after repairing local packages.
- Keep the Azure portal open while waiting so you can quickly verify VM status.
- If you frequently connect to the same VM, consider using the import/save option in your RDP client for future sessions.
