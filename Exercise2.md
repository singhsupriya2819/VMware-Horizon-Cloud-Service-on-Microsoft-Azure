# **Exercise 2: Creating an Image**

**About Image Creation**

Microsoft provides a variety of VM templates in the Microsoft Azure Marketplace. Upon import, Horizon Cloud Service joins the VM to the domain, enables the RDS role, automates the Horizon and DaaS installations, and performs a bootstrap process, enabling secure pairing of the DaaS agent to the Horizon Cloud Service pod. All of this is automated, although the process can be performed manually if you want to convert an existing VM to a Horizon Cloud Service image yourself.

After the imported VM is configured with the necessary applications, Horizon Cloud Service converts the VM to an image by automatically running SYSPREP and sealing the OS. You can then use the image to create RDS session host farms and assign dedicated and floating VDI desktops.

**Note:** With the March 2020 release of Horizon Cloud on Microsoft Azure, you have access to new operating system types in your drop-down menu. For more information, see [_Horizon Cloud on Microsoft Azure Support for Azure Virtual Desktop is Here](https://blogs.vmware.com/euc/2020/03/windows-virtual-desktop-support.html) and [_VMware Horizon Cloud Service Release Notes - v3 - March 2020_](https://docs.vmware.com/en/VMware-Horizon-Cloud-Service/services/rn/horizon-cloud-service-relnotes-30.html).


## **Exercise 2.1: Importing VMs from Microsoft Azure Marketplace**

In this exercise, you import a VM from the Microsoft Azure Marketplace, configure it with applications, and convert the VM to an image. With this image, you can then create new instances of the VM.

Later in this Tutorial, a set of exercises create an RDS server farm, for which you need an image with a server OS. Another set of exercises create a pool of VDI desktops, for which you need a Windows 10 desktop OS.

This exercise demonstrates deploying a new image using a desktop OS, and the process for deploying a server OS is virtually the same.

### **Task 1: Navigate to Imported VMs**

1. In the navigation panel of the Horizon Cloud Service Administration Console, click **Inventory**.

2. In the Inventory menu, click **Imported VMs**.

3. In Imported VMs page, click on **IMPORT** button.

   ![ws name.](media/us47.png)


### **Task 2: Provide Destination Desktop Details**
 
1. In the Import Desktop Marketplace window under Destination Desktop, provide the following information:

  - **Location:** Select the location we used while creating Pod in Exercise 1.

  - **Pod:** Select **<inject key="POD Name" />**

2. Scroll down to the Virtual Machine Details panel.

   ![ws name.](media/exc19.png)


### **Task 3: Provide Desktop Details**

**Note:** Please wait until the drop down against the **OS** field is loaded with a value

 
1. Under Desktop Details, provide the following information:

  - **OS:** Select **Windows 10 Enterprise milti-session, 1909 + Office 365 ProPlus** from dropdown menu.

  - **Include GPU:** Slide **disable**

  - **Domain Join:** Slide **enable**
  
  - **Domain:** Select the Active Directory domain **<inject key="Domain NETBIOS Name" />** .

  - **Enable Public IP Address:** Select **Yes** to configure a public IP address so you can access the VM through an RDP connection.

  - **Optimize Windows Image:** **Enable** it to optimize Windows on image import, which improves VM performance and capacity utilization.

2. Scroll down to the next panel.

   ![ws name.](media/updt1.png)


### **Task 4: Provide Admin Credentials for the Desktop**

1. Under Admin Credentials for the Desktop, provide the required information:

  - Username: **<inject key="Desktop Local Admin UserName" />**

  - Password: **<inject key="Desktop Local Admin Password" />**
  
  - Verify Password: **<inject key="Desktop Local Admin Password" />**

    ![ws name.](media/updt110.png)

2. Scroll to the next panel.

   
### **Task 5: Provide Properties**

1. In the Admin Credentials for the Desktop panel and the Properties panel, provide the required information.

  - **Name:** Enter **RDSHGoldenImage**

  - **Description:** You can enter an optional description.

2. Select **ADVANCED OPTIONS** to reveal the Horizon Agent Features panel.

   ![ws name.](media/exc22.png)


### **Task 6: Provide Horizon Agent Details**

1. Under Horizon Agent Features, accept the default to install all features in the golden VM:

- App Volume Agent: **ENABLE**
   - Description: Installs the App Volumes Agent on the desktop.

- Enable Flash MMR: **DISABLE**
   - Description: Redirects Flash multimedia content sent to the client system and plays in a Flash container window using the Flash Player ActiveX version.


- 3D support in Windows 10 MultiSession: **DISABLE**
   - Description: Provides support for vGPU-powered 3D RDS hosts.


- MMR for Terminal Services: **ENABLE**
   - Description: Redirects multimedia content directly to the client computer, which plays the media content, offloading the demand on the RDS desktop and improving performance optimization.


- Client Drive Redirection: **ENABLE**
   - Description: Allows you to share folders and drives on your local system with remote desktops and applications.


- Skype for Business: **ENABLE**
   - Description: Provides the ability to use the RDS desktops to make optimized audio and video calls with Skype for Business inside a virtual desktop without negatively affecting the virtual infrastructure and overloading the network.


- Webcam Support (Real Time Audio Video RTAV): **ENABLE**
   - Description: Allows you to run Skype, Webex, Google Hangouts, and other online conferencing applications on remote desktops with client local webcam and audio devices.


- VMware Print: **ENABLE**
   - Description: Allows you to print to any printer configured for your local computer from a remote desktop or application without installing printer drivers on the remote desktop.


- Scanner Redirection: **DISABLE**
   - Description: Redirects scanning and imaging devices that are connected to the client systems so those devices can be used with the desktop or remote application.

- USB Redirection: **DISABLE**
   - Description: Enables redirection of USB devices that are connected to your local client system so those devices can be used with the desktop or remote application.


- URL Redirection: **DISABLE**
   - Description: Collects performance data from monitored software and hardware objects in your Horizon environment and provides predictive analysis and real-time information about problems in your Horizon infrastructure.


- Serial Port Redirection: **DISABLE**
   - Description: Enables devices connected to serial ports on your local client system so those devices can be used with the remote desktop or application.


- Geolocation Redirection: **DISABLE**
   - Description: Allows the geolocation information of the client system to be used by Internet Explorer in remote desktops.


- Help Desk: **ENABLE**
   - Description: Installs the Help Desk.



2. In the lower right corner, click **IMPORT**.

   ![ws name.](media/upload3new.png)

**Note: This process will take approximately 10 minutes to complete.**

3. Wait for the agent status to turn **Import successful** under Imported VM section before proceeding with the lab. Once the import is successful, a **Green dot** appears under Status.

   ![ws name.](media/exc23.png)
   
   >**Note:** We may have to click on refresh icon to see the updated status.

### **Task 7: Verify the VM Imported Successfully in Microsoft Azure**

1. When the success banner verifies that the import is complete, open **Microsoft Azure portal(```portal.azure.com```)** in a new tab in your browser.

2. Enter following credentials when asked for credentials:

   - Username: Enter **<inject key="AzureAdUserEmail" />** and click on **Next**.
   
   - Password: Enter **<inject key="AzureAdUserPassword" />** and click on **Sign in**.

> **Note:**  If there is a popup entitled **Help us protect your account**, click on **Skip for now (14 days until this is required)**.

> ![ws name.](media/us51.png)
   
>  - If there's a popup entitled **Stay signed in?** with buttons for **No** and **Yes** - Choose **No**.
>  - If there's another popup entitled **Welcome to Microsoft Azure** with buttons for **Start Tour** and **Maybe Later** - Choose **Maybe Later**.


3. Open _Virtual Machines_ and verify that the VM was successfully completed.

   ![ws name.](media/vmw47.png)

### **Task 8: Explore the Details of the Imported VM**

1. Select the imported VM.

2. Explore the details.

   ![ws name.](media/vmw48.png)


For more information, see [_VMware Horizon Cloud Service on Microsoft Azure Administration Guide_](https://docs.vmware.com/en/VMware-Horizon-Cloud-Service/index.html), and search the guide for **Create a Master Virtual Machine Automatically from the Microsoft Azure Marketplace**.

**Note:** It is also recommended that you optimize the image using the [_VMware Windows Operating System Optimization Tool_](https://labs.vmware.com/flings/vmware-os-optimization-tool). This tool includes templates that you can customize to enable and disable Windows system services and features across multiple systems. Many Windows system services are enabled by default. You can disable services or features using the optimization tool, and improve performance by eliminating unnecessary services or features. For instructions, see the [_VMware Windows Operating System Optimization Tool Guide_](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/techpaper/vmware-view-virtual-desktops-windows-optimization.pdf).

When you finish importing the Windows 10 desktop OS VM, proceed to the next exercise to customize it.


## **Exercise 2.2: Customizing the Windows VM**

You can customize the Windows operating system of the new golden image VM, set wallpapers, and install applications to provide to your end users. If you enabled a public IP address for the golden image VM, you can connect to the VM by using the IP address displayed in the Imported VMs window in an RDP client like Microsoft Remote Desktop Connection.

### **Task 1: RDP to a Public IP**

1. Use the Public IP address of the golden image VM to connect to the Virtual Windows Enterprise 10 Multi-session operating system.

2. Copy the IP address.

   ![ws name.](media/us52.png)

3. In your AD Virtual Machine click on **Search** on task bar, search for _Remote Desktop Connection_ and click on it.

   ![ws name.](media/us38.png)
   
4. Paste the IP Address you copied in step 2 and click on **Connect**.

   ![ws name.](media/us39.png)

5. On Enter your Credentials popup, paste the password below and click on **OK**.

   Password: **<inject key="AD VM Admin Password" />**
   
   ![ws name.](media/us40.png)

6. On the popup click on **Yes**.

   ![ws name.](media/us41.png)

7. Once you are connected, make sure the Virtual Machine resembles the image below. 

   ![ws name.](media/us44.png)
    
    **Note:** If the VM starts shutting down automatically, please restart the VM and login to RDP.
    
8. You can add end-user applications and video GPU drivers, and any other required configurations to the VM.

9. Install the third-party applications and drivers that you want available to run in the multi-user RDS desktop environment.

  - In the Windows Server operating system, right-click the Start button and click Command Prompt (Admin) to open a command prompt as an administrator.

  - In the command prompt, use the following command to determine the install mode of the server:
  
   ```
   change user /query
   ```

  - The server is in RD-Execute mode if you receive the following response:
**Application EXECUTE mode is enabled**

  - In the command prompt, use the following command to switch the server into RD-Install mode, a special mode to install applications so they can run in a multi-user environment:
  
   ``` 
   change user /install 
   ```

  - Install the third-party user applications you want to provide to your end users in their RDS desktops or as remote applications.
  
 

10. Go to start and search for **PowerShell ISE** and launch it.

   ![ws name.](media/updt220.png)

11. In PowerShell ISE paste the script below and run it.


    ```
    Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
    choco install googlechrome -y -force
    choco install vscode -y -force
    choco install adobereader -y -force
    

![ws name.](media/updt221.png)

>**Note:** Wait for the script to complete and then close the Powershell ISE

 - Return to the command prompt, and issue the following command to switch the server back into RD-Execute mode:
    
    ``` 
    change user /execute 
    ```

12. In the operating system, install any custom drivers you want in the RDS desktops, such as GPU-backed VMs that leverage NVIDIA GPUs.

13. Make any customizations or configurations you want to the RDS desktops, such as adding custom wallpaper, setting default fonts or colors or themes, adjusting the taskbar default settings, and so on.

14. When you finish do not shut down the Windows operating system, instead **Disconnect**.

    ![ws name.](media/us43.png)    

For more information, see [_VMware Horizon Cloud Service on Microsoft Azure Administration Guide](https://docs.vmware.com/en/VMware-Horizon-Cloud-Service-on-Microsoft-Azure/index.html), and search the guide for **Customize the Guest Windows Operating System of the Master Image Virtual Machine**.

After you finish customizing the golden image VM, proceed to the next exercise to convert the golden image VM to an assignable image.


## **Exercise 2.3: Converting the Golden VM to an Image**

When the golden image VM is ready, it is made assignable. For this exercise, you can use any VM with the Agent and bootstrap process already complete.

### **Task 1: Start Creating a New Image**

1. In the Horizon Cloud Service Administration Console navigation bar on the left, select **Inventory**.

2. In the Inventory menu, select **Images**.

3. In the Images window, click **New**.

   ![ws name.](media/exc25.png)

### **Task 2: Provide Desktop-to-Image Details**

1. In the New Image window under **Convert Desktop to Image**, provide the following information:

  - **Location:** Select the location to get a list of pods available to store the desktop.

  - **Pod:** Select **<inject key="POD Name" />**

  - **Desktop:** From the list of desktops that can be converted to an image, select the desktop you want.

   ![ws name.](media/exc26.png)

### **Task 3: Provide OS Properties Details**

1. Under **OS Properties**, provide the following information:

  - **Image Name:** Provide a unique name to the image that will be used as the operating system on your virtual desktops.

  - **Company Name:** Enter an identifying name, which is used as the default in desktops that are created with this image.

  - **Timezone:** Set the time zone, to be the default time zone for all desktops created with this image.


   ![ws name.](media/exc27.png)

### **Task 4: Provide Admin Credentials**

1. Under **Admin credentials for the desktop**, provide the account credentials for a valid administrator account in the selected image VM. Make sure to follow the complexity standards and other limitations.

  - Username: **<inject key="Desktop Local Admin UserName" />**

  - Password: **<inject key="Desktop Local Admin Password" />**
  
  - Confirm Password: **<inject key="Desktop Local Admin Password" />**

  - **Note:** These credentials are the user name and password that were entered in the wizard when the golden VM was created in the Imported VMs window.

   ![ws name.](media/exc28.png)

2. In the lower right corner, click **Publish**.


### **Task 5: Wait for the Published Status**

1. Wait until the status changes to **Published** to use the assignable image for creating a farm.

   ![ws name.](media/exc29.png)

For more information, see [_VMware Horizon Cloud Service on Microsoft Azure Administration Guide_](https://docs.vmware.com/en/VMware-Horizon-Cloud-Service-on-Microsoft-Azure/index.html), and search the guide for **Convert a Configured Master Virtual Machine to an Assignable Image**.

After you finish importing and customizing a golden image VM and converting it into an assignable image, proceed to the next section to use the assignable image.
If the golden image you created has a server OS, proceed to [_Deploying a Farm_](https://techzone.vmware.com/quick-start-tutorial-vmware-horizon-cloud-service-microsoft-azure) to create an RDSH farm.


Click on the **Next** button from lower right corner of the guide to move on the next page.

