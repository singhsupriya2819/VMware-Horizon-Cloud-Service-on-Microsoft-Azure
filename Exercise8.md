# **Exercise 8: Dynamic Environment Manager in Horizon Cloud on Azure**

## **Exercise 8.1: Explore the VMware Dynamic Environment Manager console**

### **Task 1: Validate the deployment of the Dynamic Environment Manager**

1. In AdVM open the explorer and navigate to `F:\` drive and validate the deployment of the DEM is successful. There are three folders created for DEM named **DEMConfig**, **DEMProfile** and **UserData**. These folders are shared as per DEM prerequisite.
  
  ![ws name.](media/updt77.png)

2. Open Start Menu and open **Management Console* under recently added application or **VMware DEM** folder as shown below.

   ![ws name.](media/updt78.png)

3. Explore the **VMware Dynamic Environment Manager console**.

   ![ws name.](media/updt79.png)

4. Navigate to **User Environment** > **Drive Mapping** > **HomeDrive**. Click on **Edit** and review that HomeDrive is mapped to user with Frienldy name as Home.

   ![ws name.](media/updt80.png)
   >**Note:** Click on **X** icon on Drive Mapping window to close it.

5. Navigate to **User Environment** > **Folder Redirection** > **Profile** and click on **Edit** and review that user’s windows profile foders are redirected to home drive.

   ![ws name.](media/updt81.png)

6.	Navigate to **User Environment** > **Windows Settings** > **Hide Drives** > **Hide some drives**  and click on **Edit**. Now you can see that A, B, C drive are hidden.


   ![ws name.](media/updt103.png)


### **Task 2: Explore Policies configured for Dynamic Environment Manager**

1. In your ADVM virtual machine, Open **Run** promt and launch **gpmc.msc**.

   ![ws name.](media/updt83.png)
   
2. Navigate the **mydomain.local** > **Horizon OU** and click on **Flex GPO**. Click on **Settings** on the right hand side and see all the policies configured for DEM.

   ![ws name.](media/updt84.png)


## **Exercise 8.2: Experience Dynamic Environment Manager**

### **Task 1: Login into your Session Desktop**

1. In AdVM, open VMHorizon Client given on the desktop.

   ![ws name.](media/updt28.png)

2. Now on the Horizon Client double click on **vdi.mydomain.local**.

   ![ws name.](media/updt29.png)

3. Enter the password for **vdiuser1** and click on **Login**.

   - Password: **<inject key="all Account Password" props="{\&quot;enableCopy\&quot;:true,\&quot;style\&quot;:{\&quot;fontWeight\&quot;:\&quot;bold\&quot;}}" />**


   ![ws name.](media/updt30.png)
   

4. Double click on the **DesktopAssignment** to launch the SessionDesktop.

   ![ws name.](media/updt98.png)


5. Launch the **README** text file on the Desktop and note down the machine name on which you are logged into.

   ![ws name.](media/updt104.png)

6. Navigate to **Format** > **Fonts**. Change the font of the notepad and click **OK**.

   ![ws name.](media/updt86.png)
   
7.	Close the Notepad.

8. Launch Explorer and validate that **Home drive** is available to user and C drive is not visible.

   ![ws name.](media/updt87.png)

9. Open the **Home** drive `(H:)` and see user’s profile folders are created inside home drive. Create a **.txt** test file in Home Drive.

   ![ws name.](media/updt105.png)

10. **Right click** on the desktop and click on **Personalize**.

   ![ws name.](media/updt88.png)

11. Select a different background and close the settings window.

   ![ws name.](media/updt89.png)

12. The new background should be applied.

   ![ws name.](media/updt90.png)

13. Sign Out from the DesktopSession by going to **Start Menu**, then clicking on **User** icon and selecting **Sign Out**.

   ![ws name.](media/updt111.png)
    

14. Login to Horizon cloud console if not already and navigate to **Inventory** > **Farms** > **SecondFarm** *(Desktop Farm)*. 

   ![ws name.](media/updt106.png)


15. Navigate to the **Session Hosts** tab and select the Name of the machine we noted in *Step 5* and click on **USER LOGIN MODE** and click on **Prevent New Logins and Reconnections (Disabled)**
   
   ![ws name.](media/updt107.png)
   
15. On a prompt asking *Prevent New Logins and Reconnections (Disabled)*, Click on **Continue**.

   ![ws name.](media/updt91.png) 
   
16. Wait till you see the agent status as Disabled.

   ![ws name.](media/updt108.png)

17. In AdVM, open VMHorizon Client given on the desktop.

   ![ws name.](media/updt28.png)

18. Now on the Horizon Client double click on **vdi.mydomain.local**.

   ![ws name.](media/updt29.png)

19. Enter the password for **vdiuser1** and click on **Login**.

   - Password: <inject key="all Account Password" props="{\&quot;enableCopy\&quot;:true,\&quot;style\&quot;:{\&quot;fontWeight\&quot;:\&quot;bold\&quot;}}" />

   ![ws name.](media/updt30.png)

20. While logging into Session Desktop, you see that *VMware Dynamic Enviroment manager policy* getting applied.

   ![ws name.](media/updt92.png)
   
21. We can see that the desktop wallpaper is retained from our last change as done in *Step 11*. 

    ![ws name.](media/updt113.png)
    
22. Open the **README** file on desktop and validate you are logged into new Session Desktop and the font in notepad is also retained.

   ![ws name.](media/updt112.png)

23. Open the **File explorer** and go to **Home** drive, verify if the file is still retained. 

   ![ws name.](media/updt105.png)
   
