---
wts:
  title: "04 - Créer un réseau virtuel (20\_min)"
  module: Module 02 - Core Azure Services (Workloads)
---
# <a name="04---create-a-virtual-network-20-min"></a>04 - Créer un réseau virtuel (20 min)

Dans cette procédure pas à pas, nous allons créer un réseau virtuel, déployer deux machines virtuelles sur ce réseau virtuel, puis les configurer pour permettre à une machine virtuelle d’envoyer une requête ping à l’autre au sein de ce réseau virtuel.

# <a name="task-1-create-a-virtual-network"></a>Tâche 1 : Créer un réseau virtuel 

Dans cette tâche, nous allons créer un réseau virtuel. 

Remarque : Avant de commencer le labo, désactivez le pare-feu public et privé dans votre machine virtuelle en ouvrant le menu Démarrer > Paramètres > Réseau et Internet > Localiser le pare-feu Windows

1. Connectez-vous au portail Azure à l’adresse <a href="https://portal.azure.com" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://portal.azure.com</span></a>

2. Dans le panneau **Tous les services**, recherchez et sélectionnez **Réseaux virtuels**, puis cliquez sur **+ Ajouter, + Créer, + Nouveau**. 

3. Sous l’onglet **Informations de base** renseignez les informations suivantes (conservez les valeurs par défaut pour toutes les autres options) :

    | Paramètre | Valeur | 
    | --- | --- |
    | Abonnement | **Conserver la valeur par défaut fournie** |
    | Groupe de ressources | **Créer un groupe de ressources** |
    | Nom | **vnet1** |
    | Région | **(États-Unis) USA Est** |
    
   
4. Click the <bpt id="p1">**</bpt>Review + create<ept id="p1">**</ept> button. Ensure the validation passes. Then hit create to deploy the resource.


# <a name="task-2-create-two-virtual-machines"></a>Tâche 2 : Créer deux machines virtuelles

Dans cette tâche, nous allons créer deux machines virtuelles dans le réseau virtuel. 

1. Dans le panneau **Tous les services**, recherchez **Machines virtuelles**, puis cliquez sur **+ Ajouter, + Créer, + Nouveau**, puis, dans la liste déroulante, sélectionnez **Machine virtuelle**. 

2. Sous l’onglet **Informations de base** renseignez les informations suivantes (conservez les valeurs par défaut pour toutes les autres options) :

   | Paramètre | Valeur | 
   | --- | --- |
   | Abonnement | **Utilisez la valeur par défaut fournie** |
   | Resource group |  **Sélectionnez la valeur par défaut dans la liste déroulante** |
   | Nom de la machine virtuelle | **vm1**|
   | Région | **(États-Unis) USA Est** |
   | Image | **Windows Server 2019 Datacenter - Gen2** |
   | Nom d’utilisateur| **azureuser** |
   | Mot de passe| **Pa$$w0rd1234** |
   | Aucun port d’entrée public| Sélectionnez **Autoriser les ports sélectionnés**  |
   | Ports d’entrée sélectionnés| **RDP (3389)** |
   

3. Select the <bpt id="p1">**</bpt>Networking<ept id="p1">**</ept> tab. Make sure the virtual machine is placed in the <bpt id="p2">**</bpt>vnet1<ept id="p2">**</ept> virtual network. Review the default settings, but do not make any other changes. 

4. Click <bpt id="p1">**</bpt>Review + create<ept id="p1">**</ept>. After the Validation passes, click <bpt id="p1">**</bpt>Create<ept id="p1">**</ept>. Deployment times can vary but it can generally take between three to six minutes to deploy.

5. Surveillez votre déploiement, mais passez à l’étape suivante. 

6. Create a second virtual machine by repeating steps <bpt id="p1">**</bpt>2 to 4<ept id="p1">**</ept> above. Make sure you use a different virtual machine name, that the virtual machine is in the same virtual network, and is using a new public IP address:

    | Paramètre | Valeur |
    | --- | --- |
    | Groupe de ressources | **Sélectionnez Par défaut dans la liste déroulante (identique aux tâches 1-3 et 2-2)** |
    | Nom de la machine virtuelle |  **vm2** |
    | Réseau virtuel | **vnet1** |
    | Adresse IP publique | **vm2-ip** |

7. Attendez la fin du déploiement des deux machines virtuelles et le message d'avertissement du statut *running* (en cours d'exécution).

# <a name="task-3-test-the-connection"></a>Tâche 3 : Tester la connexion 

In this task, we will try to test whether the virtual machines can communicate (ping) each other. If not we will install a rule to allow an ICMP connection. Usually ICMP connections are automatically blocked.

1. From the <bpt id="p1">**</bpt>All resources<ept id="p1">**</ept> blade, search for <bpt id="p2">**</bpt>vm1<ept id="p2">**</ept>, open its <bpt id="p3">**</bpt>Overview<ept id="p3">**</ept> blade, and make sure its <bpt id="p4">**</bpt>Status<ept id="p4">**</ept> is <bpt id="p5">**</bpt>Running<ept id="p5">**</ept>. You may need to <bpt id="p1">**</bpt>Refresh<ept id="p1">**</ept> the page.

2. Dans le panneau **Présentation**, cliquez sur **Connecter** puis sélectionnez **RDP** dans la liste déroulante.

    **Remarque** : Les instructions suivantes indiquent comment vous connecter à votre machine virtuelle à partir d’un ordinateur Windows. 

3. Dans le panneau **Connexion avec RDP**, conservez les options par défaut pour vous connecter par adresse IP sur le port 3389 et cliquez sur **Télécharger le fichier RDP**.

4. Ouvrez le fichier RDP téléchargé (situé dans la partie inférieure gauche de votre machine virtuelle), puis cliquez sur **Connexion** lorsque vous y serez invité. 

5. Dans la fenêtre **Sécurité de Windows**, tapez le nom d’utilisateur **azureuser** et le mot de passe **Pa$$w0rd1234**, puis cliquez sur **OK**.

6. You may receive a certificate warning during the sign-in process. Click <bpt id="p1">**</bpt>Yes<ept id="p1">**</ept> to create the connection and connect to your deployed VM. You should connect successfully. Close the Windows Server and Dashboard windows that pop up. You should see a Blue Windows background. You are now in your virtual machine.

7. Dans **les deux** machines virtuelles nouvellement créées, connectez-vous via RDP et désactivez le pare-feu public et privé en ouvrant le menu Démarrer > Paramètres > Réseau et Internet > Localiser le pare-feu Windows.

8. Ouvrez PowerShell dans la machine virtuelle en cliquant sur le bouton **Démarrer** puis, dans la zone de recherche, tapez **PowerShell**, cliquez avec le bouton droit sur **Windows PowerShell** pour **Exécuter en tant qu’administrateur**

9. Dans Powershell, tentez de communiquer (ping) avec vm2 en tapant :

   ```PowerShell
   ping vm2
   ```

 10. You should be successful. You have pinged VM2 from VM1.


<bpt id="p1">**</bpt>Congratulations!<ept id="p1">**</ept> You have configured and deployed two virtual machines in a virtual network, and then you were able to connect them.

<bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: To avoid additional costs, you can optionally remove this resource group. Search for resource groups, click your resource group, and then click <bpt id="p1">**</bpt>Delete resource group<ept id="p1">**</ept>. Verify the name of the resource group and then click <bpt id="p1">**</bpt>Delete<ept id="p1">**</ept>. Monitor the <bpt id="p1">**</bpt>Notifications<ept id="p1">**</ept> to see how the delete is proceeding.
