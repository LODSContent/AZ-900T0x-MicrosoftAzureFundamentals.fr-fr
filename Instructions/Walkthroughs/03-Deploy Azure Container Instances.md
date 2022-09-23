---
wts:
  title: "03 - Déployer Azure Container Instances (10\_minutes)"
  module: Module 02 - Core Azure Services (Workloads)
---

# <a name="03---deploy-azure-container-instances-10-min"></a>03 - Déployer Azure Container Instances (10 minutes)

In this walkthrough we create, configure, and deploy a container by using Azure Container Instances (ACI) in the Azure Portal. The container is a Welcome to ACI web application that displays a static HTML page. 

# <a name="task-1-create-a-container-instance"></a>Tâche 1 : Créer une instance de conteneur 

Dans cette tâche, nous allons créer une nouvelle instance de conteneur pour l’application web.  

1. Connectez-vous au [portail Azure](https://portal.azure.com).

2. Dans le panneau **Tous les services**, recherchez et sélectionnez **Container instances** puis cliquez sur **+ Ajouter, + Créer, + Nouveau**. 

3. Fournissez les détails de base suivants pour la nouvelle instance de conteneur (laissez les valeurs par défaut pour tous les autres éléments) : 

    | Paramètre| Valeur|
    |----|----|
    | Abonnement | ***Utilisez la valeur par défaut fournie*** |
    | Resource group | **Créer un groupe de ressources** |
    | Nom du conteneur| **mycontainer**|
    | Région | **(États-Unis) USA Est** |
    | Source d’image| **Docker Hub ou autre registre**|
    | Type d’image| **Public**|
    | Image| **mcr.microsoft.com/azuredocs/aci-helloworld**|
    | Type de système d’exploitation| **Linux** |
    | Taille| ***Laissez la valeur par défaut***|


4. Configure the Networking tab (replace <bpt id="p1">**</bpt>xxxxx<ept id="p1">**</ept> with letters and digits such that the name is globally unique). Leave all other settings at their default values.

    | Paramètre| Valeur|
    |--|--|
    | Étiquette du nom DNS| **mycontainerdnsxxxxx** |

    
    <bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: Your container will be publicly reachable at dns-name-label.region.azurecontainer.io. If you receive a <bpt id="p1">**</bpt>DNS name label not available<ept id="p1">**</ept> error message following the deployment, specify a different DNS name label (replacing the xxxxx) and re-deploy. 

5. Cliquez sur **Examiner et créer** pour lancer le processus de validation automatique.

6. Cliquez sur **Créer** pour créer l’instance de conteneur. 

7. Surveillez la page Déploiement et la page **Notifications**. 


# <a name="task-2-verify-deployment-of-the-container-instance"></a>Tâche 2 : Vérifier le déploiement de l’instance de conteneur

Dans cette tâche, nous vérifierons que l’instance de conteneur est en cours d’exécution, en nous assurant que la page d’accueil s’affiche.

1. Une fois le déploiement terminé, cliquez sur le lien **Accéder à la ressource** sur le panneau de déploiement ou sur le lien vers la ressource dans la zone de notification.

2. Dans le panneau **Aperçu** de **mycontainer**, assurez-vous que le **Statut** de votre conteneur est bien **En cours d’exécution**. 

3. Recherchez le nom de domaine complet (FQDN, Fully Qualified Domain Name).

    ![Capture d’écran du volet de vue d’ensemble du conteneur nouvellement créé dans le portail Azure, avec le nom de domaine complet en surbrillance. ](../images/0202.png)

2. Dans cette procédure pas à pas, nous allons créer, configurer et déployer un container à l’aide d’ ACI (Azure Container Instances) dans le portail Azure. 

    ![Capture d’écran du message de bienvenue ACI affiché dans un navigateur web.](../images/0203.png)


Le conteneur est une application web Welcome to ACI qui affiche une page HTML statique.

<bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: To avoid additional costs, you can optionally remove this resource group. Search for resource groups, click your resource group, and then click <bpt id="p1">**</bpt>Delete resource group<ept id="p1">**</ept>. Verify the name of the resource group and then click <bpt id="p1">**</bpt>Delete<ept id="p1">**</ept>. Monitor the <bpt id="p1">**</bpt>Notifications<ept id="p1">**</ept> to see how the delete is proceeding.
