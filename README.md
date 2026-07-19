# Provisioning-Azure-Virtual-Machine
Watch me provision an Azure VM from start to finish.
https://www.loom.com/share/2cad6a4ec71047a18d92747fdef39e73

## Create and Access an Azure Windows Server Virtual Machine for Remote Administration

### Objective

Provision a Windows Server virtual machine in Azure, then connect to it remotely from a Linux workstation so it can be used for server management tasks such as installing and configuring Active Directory Domain Services.

### Key Steps

**1. Create the Azure virtual machine** [0:00](https://loom.com/share/2cad6a4ec71047a18d92747fdef39e73?t=0)
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/064bd6dc-510f-4e75-b9ae-b7294dd3898d" />


- In Azure, start the process to create a new virtual machine.
- Choose the appropriate subscription/resource group setup as needed.
- Proceed to the VM creation form and begin entering the required details.

**2. Configure the VM name, region, and OS** [0:14](https://loom.com/share/2cad6a4ec71047a18d92747fdef39e73?t=14)

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/41652833-8217-49a8-9445-7bcb4723181f" />


- Enter a clear VM name; in the video, the VM is named **HelpDesk**.
- Select the deployment region; the example uses (**US)** Central US
- Choose the operating system image: **Windows Server Datacenter**.
- Select the **least costly** option that still meets the requirement.

**3. Set administrator credentials and remote access** [1:14](https://loom.com/share/2cad6a4ec71047a18d92747fdef39e73?t=74)

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/9dbfea4e-2587-4869-8f31-d49090e6bca1" />


- Create the administrator username; the example uses **support**.
- Set a strong, secure password.
- Ensure **RDP** access is allowed so the machine can be reached remotely.
- Review the configuration before continuing.

**4. Wait for Azure provisioning to complete** [2:11](https://loom.com/share/2cad6a4ec71047a18d92747fdef39e73?t=131)

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/bb95bb9c-ead5-467d-8965-6fee41e81055" />


- Allow Azure time to finish creating and configuring the VM.
- The VM will be used to install and configure **Windows Server Manager** and **Active Directory Domain Services**.
- Confirm the VM is fully provisioned before attempting to connect.

**5. Verify the VM is ready before connecting** [5:24](https://loom.com/share/2cad6a4ec71047a18d92747fdef39e73?t=324)
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/a3750350-a449-4231-87cf-f5d78417ea5b" />


- Check the VM status in Azure.
- If the agent status shows **not ready**, wait a few minutes and refresh.
- Do not attempt remote access until the VM is fully available.

**6. Download the RDP file and prepare to connect from Linux** [7:04](https://loom.com/share/2cad6a4ec71047a18d92747fdef39e73?t=424)

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6fc45211-6c26-4b91-ae2b-271753333e70" />

- From your Linux workstation, choose a local connection method.
- Download the **RDP file** from Azure.
- Open the file using an RDP client on Linux rather than assuming SSH will be used.
- In the video, the user opens the file with **Remmina**.

**7. Choose the correct RDP connection method** [10:34](https://loom.com/share/2cad6a4ec71047a18d92747fdef39e73?t=634)

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/34b173d7-9210-4cb3-9aaa-011010ccba1c" />


- If prompted, understand the difference between connection options: 
  - **Connect**: opens the RDP file directly for a one-time connection.
  - **Import**: lets you save and edit the connection for future use.
- For this workflow, use **Connect** to proceed quickly.

**8. Troubleshoot connection errors on the Linux client** [11:13](https://loom.com/share/2cad6a4ec71047a18d92747fdef39e73?t=673)

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/cdd64e10-99de-41d5-a66e-303bde9572b1" />


- If an internal error appears, pause and investigate the Linux system state.
- Check for package installation issues or interrupted package configuration.
- Be aware that other software installations can interfere with RDP client behavior.

**9. Repair interrupted package configuration if needed** [18:41](https://loom.com/share/2cad6a4ec71047a18d92747fdef39e73?t=1121)

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/9354d695-81f3-4727-a89c-51afdd575e92" />


- If the system has interrupted package installs, run the package repair command: 
  - `sudo dpkg --configure -a`
- This can resolve issues caused by incomplete installations such as VirtualBox or related dependencies.
- After repair, retry the RDP connection.

**10. Reopen the RDP file and complete the remote connection** [20:23](https://loom.com/share/2cad6a4ec71047a18d92747fdef39e73?t=1223)

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/9c26a429-221e-485f-9129-2df9fd4e287b" />


- Open the downloaded RDP file again after fixing any package issues.
- Wait for the remote desktop session to initialize.
- Confirm that the Windows Server desktop loads successfully.

**11. Confirm the VM is accessible and ready for administration** [28:16](https://loom.com/share/2cad6a4ec71047a18d92747fdef39e73?t=1696)

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/d0f7372f-a46e-48cf-ba14-24f866bce6d8" />


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
