---
wts:
  title: "«\_07 - Implémenter Azure IoT Hub (10\_minutes)\_»"
  module: 'Module 03: Describe core solutions and management tools'
---
# <a name="07---implement-an-azure-iot-hub-10-min"></a>« 07 - Implémenter Azure IoT Hub (10 minutes) »

In this walkthrough, we will configure a new Azure IoT Hub in Azure Portal, and then authenticate a connection to an IoT device using the online Raspberry Pi device simulator. Sensor data and messages are passed from the Raspberry Pi simulator to your Azure IoT Hub, and you view metrics for the messaging activity in Azure Portal.

# <a name="task-1-create-an-iot-hub"></a>Tâche 1 : Créer un hub IoT 

Dans cette tâche, nous allons créer un hub IoT. 

1. Connectez-vous au [portail Azure](https://portal.azure.com).

2. Dans le panneau **Tous les services**, recherchez et sélectionnez **IoT Hub**, puis cliquez sur **+ Ajouter, + Créer, + Nouveau**.

3. Sous l’onglet **Général** du panneau **Hub IoT**, remplissez les champs avec les détails suivants (remplacez **xxxx** dans le nom du compte de stockage par des lettres et des chiffres, de façon à ce que le nom soit unique au monde) :

    | Paramètres | Valeur |
    |--|--|
    | Abonnement | **Utilisez la valeur par défaut fournie** |
    | Groupe de ressources | **Créer un groupe de ressources** |
    | Nom du hub IoT | **my-hub-groupxxxxx** |
    | Région | **USA Est** |

    **Remarque** - Veillez à modifier la valeur **xxxxx** pour créer un **Nom de Hub IoT** unique.

4. Sous l’onglet **Gestion** recherchez **Prix et niveau d’échelle** dans la liste déroulante et définissez sa valeur sur **S1 : Niveau Standard**.

5. Cliquez sur le bouton **Vérifier + créer**.

6. Cliquez sur le bouton **Créer** pour commencer à créer votre nouvelle instance hub IoT Azure.

7. Attendez que l’instance hub IoT Azure soit déployée. 

# <a name="task-2-add-an-iot-device"></a>Tâche 2 : Ajouter un appareil IoT

Dans cette tâche, nous allons ajouter un appareil IoT au hub IoT. 

1. When the deployment has completed, click <bpt id="p1">**</bpt>Go to resource<ept id="p1">**</ept> from the deployment blade. Alternatively, from the <bpt id="p1">**</bpt>All services<ept id="p1">**</ept> blade, search for and select <bpt id="p2">**</bpt>IoT Hub<ept id="p2">**</ept> and locate your new IoT Hub instance

    ![Capture d’écran des notifications de déploiement en cours et de déploiement réussi dans le portail Azure.](../images/0601.png)

2. To add a new IoT device, scroll down to the <bpt id="p1">**</bpt>Device management<ept id="p1">**</ept> section and click <bpt id="p2">**</bpt>Devices<ept id="p2">**</ept>. Then, click <bpt id="p1">**</bpt>+ Add Device<ept id="p1">**</ept>.

    ![Dans cette procédure pas à pas, nous allons configurer un nouveau hub IoT Azure dans le portail Azure, puis authentifier une connexion à un appareil IoT à l’aide du simulateur d’appareil Raspberry Pi en ligne.](../images/0602.png)

3. Les données et les messages des capteurs sont transmis du simulateur Raspberry Pi à votre hub IoT Azure. Vous pouvez afficher des mesures pour l’activité de messagerie dans le portail Azure.

4. Si vous ne voyez pas votre nouvel appareil, **actualisez** la page Appareils IoT. 

5. Select <bpt id="p1">**</bpt>myRaspberryPi<ept id="p1">**</ept> and copy the <bpt id="p2">**</bpt>Primary Connection String<ept id="p2">**</ept> value. You will use this key in the next task to authenticate a connection to the Raspberry Pi simulator.

    ![Capture d’écran de la page Chaîne de connexion principale avec icône de copie en surbrillance.](../images/0603.png)

# <a name="task-3-test-the-device-using-a-raspberry-pi-simulator"></a>Tâche 3 : Tester l'appareil à l’aide d’un simulateur Raspberry Pi

Dans cette tâche, nous allons tester notre appareil à l’aide du simulateur Raspberry Pi. 

1. Open a new tab in the web browser and type this shortcut link <ph id="ph1">https://aka.ms/RaspPi</ph>. It will take you to a Raspberry Pi Simulator site. If you have time, read about the Raspberry Pi simulator. When done select "<bpt id="p1">**</bpt>X<ept id="p1">**</ept>" to close the pop-up window.

2. In the code area on the right side, locate the line with 'const connectionString ='. Replace it with the connection string you copied from the Azure portal. Note that the connection sting includes the DeviceId (<bpt id="p1">**</bpt>myRaspberryPi<ept id="p1">**</ept>) and SharedAccessKey entries.

    ![Capture d’écran de la zone de codage dans le simulateur Raspberry Pi.](../images/0604.png)

3. Click <bpt id="p1">**</bpt>Run<ept id="p1">**</ept> (below the code area) to run the application. The console output should show the sensor data and messages that are sent from the Raspberry Pi simulator to your Azure IoT Hub. Data and messages are sent each time the Raspberry Pi simulator LED flashes. 

    ![Screenshot of the Raspberry Pi simulator console.  The console output shows sensor data and messages sent from the Raspberry Pi simulator to Azure IoT Hub.](../images/0605.png)

5. Cliquez sur **Arrêter** pour interrompre l’envoi de données.

6. Revenez au Portail Azure.

7. Switch the IoT Hub <bpt id="p1">**</bpt>Overview<ept id="p1">**</ept> blade and scroll down to the <bpt id="p2">**</bpt>IoT Hub Usage<ept id="p2">**</ept> information to view usage. Change your timeframe in the <bpt id="p1">**</bpt>show data for last<ept id="p1">**</ept> to see data in the last hour.

    ![Capture d’écran des mesures dans la zone d’utilisation du hub IoT du portail Azure.](../images/0606.png)


Congratulations! You have set up Azure IoT Hub to collect sensor data from an IoT device.

<bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: To avoid additional costs, you can optionally remove this resource group. Search for resource groups, click your resource group, and then click <bpt id="p1">**</bpt>Delete resource group<ept id="p1">**</ept>. Verify the name of the resource group and then click <bpt id="p1">**</bpt>Delete<ept id="p1">**</ept>. Monitor the <bpt id="p1">**</bpt>Notifications<ept id="p1">**</ept> to see how the delete is proceeding.
