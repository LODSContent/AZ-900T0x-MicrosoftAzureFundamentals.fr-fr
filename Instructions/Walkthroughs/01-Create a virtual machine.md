---
wts:
  title: "01 - Créez une machine virtuelle dans le portail (10\_min)"
  module: Module 02 - Core Azure Services (Workloads)
---
# <a name="01---create-a-virtual-machine-in-the-portal-10-min"></a>01 - Créez une machine virtuelle dans le portail (10 min)

Au cours de cette procédure pas à pas, nous allons créer une machine virtuelle dans le portail Azure, nous connecter à cette machine virtuelle, installer le rôle Serveur web et effectuer un test. 

**Remarque** : Au cours de cette procédure pas à pas, prenez le temps de lire les informations en cliquant sur les icônes correspondantes. 

# <a name="task-1-create-the-virtual-machine"></a>Tâche 1 : Créer la machine virtuelle 
1. Connectez-vous au portail Azure : **https://portal.azure.com**

3. Dans le panneau **Tous les services** du menu du portail, recherchez et sélectionnez **Machines virtuelles**, puis cliquez sur **+Créer** et choisissez **+Machine virtuelle Azure** dans le menu déroulant.

4. Sous l’onglet **Informations de base** renseignez les informations suivantes (conservez les valeurs par défaut pour toutes les autres options) :

    | Paramètres | Valeurs |
    |  -- | -- |
    | Abonnement | **Utilisez la valeur par défaut fournie** |
    | Resource group | **Créer un groupe de ressources** |
    | Nom de la machine virtuelle | **myVM** |
    | Région | **(États-Unis) USA Est**|
    | Options de disponibilité | Aucune option de redondance de l'infrastructure requise|
    | Image | **Windows Server 2019 Datacenter - Gen2**|
    | Taille | **Standard D2s v3**|
    | Nom d’utilisateur du compte d’administrateur | **azureuser** |
    | Mot de passe du compte d’administrateur (à taper avec prudence) | **Pa$$w0rd1234**|
    | Règles de trafic entrant pour un port - | ** Autoriser les ports sélectionnés **|
    | Sélectionner des ports d’entrée | **RDP (3389)** et **HTTP (80)**| 

5. Accédez à l’onglet Mise en réseau pour vous assurer que **HTTP (80) et RDP (3389)** sont bien sélectionnés dans la section **Sélectionner les ports d’entrée**.

6. Accédez à l’onglet Gestion. Dans la section **Surveillance**, sélectionnez le paramètre suivant :

    | Paramètres | Valeurs |
    | -- | -- |
    | Diagnostics de démarrage | **Désactiver**|

7. Conservez les autres valeurs par valeur défaut, puis cliquez sur le bouton **Examiner et créer** au bas de la page.

8. Once Validation is passed click the <bpt id="p1">**</bpt>Create<ept id="p1">**</ept> button. It can take anywhere from five to seven minutes to deploy the virtual machine.

9. Vous pouvez accéder aux mises à jour sur la page Déploiement et dans la zone **Notifications** (icône représentant une cloche en haut de la barre de menus).

# <a name="task-2-connect-to-the-virtual-machine"></a>Tâche 2 : Se connecter à la machine virtuelle

Dans cette tâche, nous nous connecterons à notre nouvelle machine virtuelle à l'aide du protocole RDP (Remote Desktop Protocol). 

1. Cliquez sur l'icône représentant une cloche dans la barre d'outils bleue supérieure, et sélectionnez « Go to resource » à la fin du déploiement. 

    **Remarque** : Vous pouvez également utiliser le lien **Go to resource** sur la page du déploiement 

2. Sur la machine virtuelle, accédez au panneau **Présentation**, cliquez sur **Connecter** et choisissez **RDP** dans la liste déroulante.

    ![Capture d’écran des propriétés de la machine virtuelle avec le bouton Se connecter activé.](../images/0101.png)

    <bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: The following directions tell you how to connect to your VM from a Windows computer. On a Mac, you need an RDP client such as this Remote Desktop Client from the Mac App Store and on a Linux computer you can use an open source RDP client.

2. On the <bpt id="p1">**</bpt>Connect to virtual machine<ept id="p1">**</ept> page, keep the default options to connect with the public IP address over port 3389 and click <bpt id="p2">**</bpt>Download RDP File<ept id="p2">**</ept>. A file will download on the bottom left of your screen.

3. **Ouvrez** le fichier RDP téléchargé (situé dans la partie inférieure gauche de votre machine de labo), puis cliquez sur **Connexion** lorsque vous y serez invité. 

    ![Capture d’écran des propriétés de la machine virtuelle avec le bouton Se connecter activé. ](../images/0102.png)

4. Dans la fenêtre **Sécurité Windows**, ouvrez une session à l'aide des identifiants d’administrateur que vous avez utilisés lors de la création de votre machine virtuelle **azureuser** et du mot de passe **Pa$$w0rd1234**. 

5. You may receive a warning certificate during the sign-in process. Click <bpt id="p1">**</bpt>Yes<ept id="p1">**</ept> or to create the connection and connect to your deployed VM. You should connect successfully.

    ![Capture d’écran de la boîte de dialogue Avertissement de certificat, signalant à l’utilisateur que le certificat n’est pas approuvé, avec le bouton Oui activé. ](../images/0104.png)

A new Virtual Machine (myVM) will launch inside your Lab. Close the Server Manager and dashboard windows that pop up (click "x" at top right). You should see the blue background of your virtual machine. <bpt id="p1">**</bpt>Congratulations!<ept id="p1">**</ept> You have deployed and connected to a Virtual Machine running Windows Server. 

# <a name="task-3-install-the-web-server-role-and-test"></a>Tâche 3 : Installez le rôle serveur web et testez-le

Dans cette tâche, installez le rôle serveur web sur la machine virtuelle que vous venez de créer et vérifiez que la page d’accueil par défaut du serveur IIS est bien affichée. 

1. Dans la machine virtuelle que vous venez d'ouvrir, lancez PowerShell en recherchant **PowerShell** dans la barre de recherche, puis cliquez avec le bouton droit sur **Windows PowerShell** pour activer l’option **Exécuter en tant qu’administrateur**.

    ![Capture d’écran du Bureau de la machine virtuelle avec le bouton Démarrer activé et PowerShell sélectionné avec l’option Exécuter en tant qu’administrateur en surbrillance.](../images/0105.png)

2. In PowerShell, install the <bpt id="p1">**</bpt>Web-Server<ept id="p1">**</ept> feature on the virtual machine by running the following command. (Paste in the command and hit ENTER for the installment to begin).

    ```PowerShell
    Install-WindowsFeature -name Web-Server -IncludeManagementTools
    ```
  
3. When completed, a prompt will state <bpt id="p1">**</bpt>Success<ept id="p1">**</ept> with a value <bpt id="p2">**</bpt>True<ept id="p2">**</ept>. You do not need to restart the virtual machine to complete the installation. Close the RDP connection to the VM by clicking the <bpt id="p1">**</bpt>x<ept id="p1">**</ept> on the blue bar at the top center of your virtual machine. You can also minimize it by clicking the <bpt id="p1">**</bpt><ph id="ph1">-</ph><ept id="p1">**</ept> on the blue bar at the top center.

    ![Capture d’écran de l’invite de commandes Windows PowerShell avec la commande Install-WindowsFeature -name Web-Server -IncludeManagementTools exécutée avec succès et le résultat correspondant.](../images/0106.png)

4. Revenez au niveau du portail, naviguez vers le panneau **Présentation** de myVM et cliquez sur le bouton **Cliquez sur le Presse-papiers** pour copier l’adresse IP publique de myVM, puis ouvrez un nouvel onglet du navigateur, collez l'adresse IP publique dans la zone de texte de l’URL et appuyez sur **Entrée** pour y accéder.

    ![Capture d’écran du volet de propriétés de la machine virtuelle du portail Azure, avec l’adresse IP copiée.](../images/0107.png)

5. La page d’accueil par défaut du serveur web IIS s'affiche.

    ![Capture d’écran de la page d’accueil par défaut du serveur web IIS accessible via l’adresse IP publique dans un navigateur web.](../images/0108.png)

<bpt id="p1">**</bpt>Congratulations!<ept id="p1">**</ept> You have created a new VM running a web server that is accessible via its public IP address. If you had a web application to host, you could deploy application files to the virtual machine and host them for public access on the deployed virtual machine.


<bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: To avoid additional costs, you can optionally remove this resource group. Search for resource groups, click your resource group, and then click <bpt id="p1">**</bpt>Delete resource group<ept id="p1">**</ept>. Verify the name of the resource group and then click <bpt id="p1">**</bpt>Delete<ept id="p1">**</ept>. Monitor the <bpt id="p1">**</bpt>Notifications<ept id="p1">**</ept> to see verify that the deletion completed successfully. 
