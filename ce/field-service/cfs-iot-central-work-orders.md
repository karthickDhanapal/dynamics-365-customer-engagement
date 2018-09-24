---
title: "Send work order updates to IoT Central | MicrosoftDocs"
ms.custom: "dyn365-fieldservice"
ms.date: 09/24/2018
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "field-service"
applies_to: 
  - "Dynamics 365 (online)"
  - "Dynamics 365 Version 9.x"
author: "shellyhaverkamp"
ms.author: "krbjoran"
ms.manager: "shellyhaverkamp"
search.audienceType: 
  - admin
  - customizer
  - enduser
search.app: 
  - D365CE
  - D365FS
--- 

# 3 - Send work order updates to Azure IoT Central

[!INCLUDE[cc-applies-to-update-9-0-0](../includes/cc_applies_to_update_9_0_0.md)]

When working with the sample data package, you'll see that work orders are automatically created in Connected Field Service when an IoT device triggers an alert in Azure IoT Central. In Connected Field Service, you'll see that work order associated with the IoT alert. But how do you get this information back into IoT Central?

## Goal

Make Connected Field Service send service information to Azure IoT Central when work orders are automatically generated.

## Steps

1. In Connected Field Service, navigate to the IoT Alerts list page. You can find this in the main navigation menu.

2. Select an IoT alert, and then navigate to the "Related" dropdown and select "Work orders." You should see that a work order has been automatically generated for this alert.

3. Select "Create a Flow" in the top menu bar.

> [!div class="mx-imgBorder"]
> ![alt text](media/iot-central-work-orders-1.png)

4. From the list of available templates, select "**Sample Contoso- When a work order is created in Connected Field Service, update IoT Central"**

Note: Alternatively, you can navigate directly to [the Microsoft Flow templates page](https://preview.flow.microsoft.com/templates/) and search "CFS" to find this template, as seen below.
  
> [!div class="mx-imgBorder"]
> ![alt text](media/iot-central-work-orders-2.png)

5. Sign into Flow with your Dynamics 365 organization, along with your associated IoT Central account.

> [!div class="mx-imgBorder"]
> ![alt text](media/iot-central-work-orders-4.png)

6. The template will be mostly ready to run; you only need to make the following changes (see the screenshots below for reference):

    a. In the field for "When a work order is created or updated," select your Dynamics 365 organization name.
   
    b. In the field for "Get the alert," and then select your Dynamics 365 organization name.
    
    c. Expand "Clean up the work order fields in the device," and then select your IoT Central application name and also the device template, "Refrigerated Vending Machine (1.0.0)."
    
    d. Expand "Get the incident type from work order," and then select  your Dynamics 365 organization name.
    
    e. Expand "Update the work order details for the device that raised the alert," and then select your IoT Central application name and also the device template, "Refrigerated Vending Machine (1.0.0)."
    
    f. **Note**: Running this Flow will not add work order information retroactively---only devices going forward will be updated on the device page in Azure IoT Central.
    
> [!div class="mx-imgBorder"]
> ![alt text](media/iot-central-work-orders-5.png)

> [!div class="mx-imgBorder"]
> ![alt text](media/iot-central-work-orders-6.png)

7. Save the Flow to make it run.


## See the results

After you've saved the Flow, head on back to your Azure IoT Central environment. Select the device that has triggered an alert and a work order in Connected Field Service. You should now see the work order information populated in the fields on the IoT Central device properties page.

> [!div class="mx-imgBorder"]
> ![alt text](media/iot-central-work-orders-7.png)

> [!div class="nextstepaction"]
> [Step 4: Send booking updates to Azure IoT Central](cfs-iot-central-bookings.md)