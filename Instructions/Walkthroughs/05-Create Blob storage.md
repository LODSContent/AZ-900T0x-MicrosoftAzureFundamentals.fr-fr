---
wts:
  title: "05\_-\_Créer un stockage d’objets Blob (5\_minutes)"
  module: Module 02 - Core Azure Services (Workloads)
---
# <a name="05---create-blob-storage-5-min"></a>05 - Créer un stockage d’objets Blob (5 minutes)

Dans cette procédure pas à pas, nous allons créer un compte de stockage, puis travailler avec des fichiers de stockage d’objets Blob.

# <a name="task-1-create-a-storage-account"></a>Tâche 1 : Créer un compte de stockage 

Dans cette tâche, vous allez créer un nouveau compte de stockage. 

1. Connectez-vous au portail Azure à l’adresse <a href="https://portal.azure.com" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://portal.azure.com</span></a>

2. Dans le panneau **Tous les services**, recherchez et sélectionnez **Comptes de stockage :** , puis cliquez sur **+ Ajouter, + Créer, + Nouveau**. 

3. On the <bpt id="p1">**</bpt>Basics<ept id="p1">**</ept> tab of the <bpt id="p2">**</bpt>Create storage account<ept id="p2">**</ept> blade, fill in the following information (replace <bpt id="p3">**</bpt>xxxx<ept id="p3">**</ept> in the name of the storage account with letters and digits such that the name is globally unique). Leave the defaults for everything else.

    | Paramètre | Valeur | 
    | --- | --- |
    | Abonnement | **Conservez les valeurs par défaut** |
    | Resource group | **Créer un groupe de ressources** |
    | Nom du compte de stockage | **storageaccountxxxxx** |
    | Emplacement | **(États-Unis) USA Est**  |
    | Performances | **Standard** |
    | Redondance | **Stockage localement redondant (LRS)** |
    
    **Remarque** - Veillez à modifier la valeur **xxxxx** pour créer un **Nom de compte de stockage** unique

5. Cliquez sur **Examiner et créer** pour réviser les paramètres de votre compte de stockage et autoriser Azure à valider la configuration. 

6. Once validated, click <bpt id="p1">**</bpt>Create<ept id="p1">**</ept>. Wait for the notification that the account was successfully created. 

7. Sur la page d’accueil, recherchez et sélectionnez **Comptes de stockage** et vérifiez que votre nouveau compte de stockage est répertorié.

    ![Capture d’écran du compte de stockage nouvellement créé dans le portail Azure.](../images/0401.png)

# <a name="task-2-work-with-blob-storage"></a>Tâche 2 : Travailler avec le Stockage Blob

Dans cette tâche, nous allons créer un conteneur blob et charger un fichier d’objets blob. 

1. Cliquez sur le nom du nouveau compte de stockage, faites défiler jusqu’à la section **Stockage de données** dans le menu de gauche, puis cliquez sur **Conteneurs**.

2. Click <bpt id="p1">**</bpt>+ Container<ept id="p1">**</ept> and complete the information. Use the Information icons to learn more. When done click <bpt id="p1">**</bpt>Create<ept id="p1">**</ept>.


    | Paramètre | Valeur |
    | --- | --- |
    | Nom | **conteneur1**  |
    | Niveau d'accès public| **Privé (aucun accès anonyme)** |
  

    ![Capture d’écran du conteneur d’objets blob nouvellement créé dans le compte de stockage du portail Azure.](../images/0402.png)

4. Open a new browser window and search <bpt id="p1">**</bpt>Bing<ept id="p1">**</ept> for an image of a flower. Right click on the image and save it to your VM. 

6. Revenez dans le portail, cliquez sur **conteneur1**, puis sélectionnez **Télécharger**.

5. Browse for the image file you just saved on your local computer. Select it and then select upload.

   
6. Cliquez sur la flèche **Avancée**, laissez les valeurs par défaut mais passez en revue les options disponibles, puis cliquez sur **Charger**.

    <bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: You can upload as many blobs as you like in this way. New blobs will be listed within the container.

7. Une fois le fichier chargé, cliquez avec le bouton droit sur le fichier et notez les options comprenant Afficher/modifier, Télécharger, Propriétés et Supprimer. 

8. Si vous avez le temps, vérifiez les options Fichiers, Tables et Files d'attente.

# <a name="task-3-monitor-the-storage-account"></a>Tâche 3 : Surveiller le compte de stockage

1. Revenez dans le panneau Compte de stockage et cliquez sur **Diagnostiquer et résoudre les problèmes**. 

2. Explore some of the most common storage problems. Notice there are multiple troubleshooters here.

3. On the storage account blade, scroll down to the <bpt id="p1">**</bpt>Monitoring<ept id="p1">**</ept> section and click <bpt id="p2">**</bpt>Insights<ept id="p2">**</ept>. Notice there is information on Failures, Performance, Availability, and Capacity. Your information will be different.

    ![Capture d’écran de la page Informations du compte de stockage.](../images/0403.PNG)

Sous l’onglet **Informations de base** du panneau **Créer un compte de stockage**, remplissez les informations suivantes (remplacez **xxxx** dans le nom du compte de stockage par des lettres et des chiffres de sorte que le nom soit unique au monde).

Laissez les valeurs par défaut pour tous les autres éléments.
