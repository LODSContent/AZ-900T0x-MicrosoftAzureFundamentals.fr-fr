---
wts:
  title: "09 - Créer une machine virtuelle avec un modèle (10\_minutes)"
  module: 'Module 03: Describe core solutions and management tools'
---
# <a name="09---create-a-vm-with-a-template-10-min"></a>09 - Créer une machine virtuelle avec un modèle (10 minutes)

Dans cette procédure pas à pas, nous allons déployer une machine virtuelle avec un modèle de démarrage rapide et examiner ses capacités de surveillance.

# <a name="task-1-explore-the-quickstart-gallery-and-locate-a-template"></a>Tâche 1 : Explorer la galerie QuickStart (Démarrage rapide) et localiser un modèle 

Dans cette tâche, nous allons parcourir la galerie de démarrage rapide Azure et déployer un modèle qui crée une machine virtuelle. 

1. Within the lab environment, open a new browser window, and enter T <ph id="ph1">https://azure.microsoft.com/en-us/resources/templates/?azure-portal=true</ph>. In the gallery you will find a number of popular and recently updated templates. These templates automate deployment of Azure resources, including installation of popular software packages. Browse through the many different types of templates that are available.

3. Sélectionnez l’option **Déployer une simple machine virtuelle Windows**

4. Click the <bpt id="p1">**</bpt>Deploy to Azure<ept id="p1">**</ept> button. Your browser session will be automatically redirected to the <bpt id="p1">[</bpt>Azure portal<ept id="p1">](http://portal.azure.com/)</ept>.

  <bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: The <bpt id="p2">**</bpt>Deploy to Azure<ept id="p2">**</ept> button enables you to deploy the template via the Azure portal. During such deployment, you will be prompted only for small set of configuration parameters. 

5. Lorsque vous y êtes invité, connectez-vous à votre abonnement Azure à l’aide des informations d’identification fournies précédemment dans les instructions.

6. Click <bpt id="p1">**</bpt>Edit template<ept id="p1">**</ept>. The Resource Manager template format uses the JSON format. Review the parameters and variables.  Then locate the parameter for virtual machine name. Change the name to <bpt id="p1">**</bpt>myVMTemplate<ept id="p1">**</ept>. <bpt id="p1">**</bpt>Save<ept id="p1">**</ept> your changes. 

    ![Capture d’écran du modèle avec le changement de nom de la machine virtuelle en surbrillance.](../images/0901.png)

7. Now configure the parameters required by the template (replace <bpt id="p1">***</bpt>xxxx<ept id="p1">***</ept> in the DNS label prefix with letters and digits such that the label is globally unique). Leave the defaults for everything else. 

    | Paramètre| Valeur|
    |----|----|
    | Abonnement | **Utilisez la valeur par défaut fournie**|
    | Resource group | **Créer un groupe de ressources** |
    | Région | conservez l’URL par défaut . |
    | Nom d’utilisateur administrateur | **azureuser** |
    | Mot de passe de l'administrateur | **Pa$$w0rd1234** |
    | Préfixe d’étiquette DNS | **myvmtemplatexxxx** |
    | Version du SE | **2019-Datacenter** |


9. Cliquez sur **Vérifier + créer**.

10. Surveillez votre déploiement. 

# <a name="task-2-verify-and-monitor-your-virtual-machine-deployment"></a>Tâche 2 : Vérifier et contrôler le déploiement de votre machine virtuelle

Dans cette tâche, nous allons vérifier si la machine virtuelle s’est correctement déployée. 

1. Dans le panneau **Tous les services**, recherchez et sélectionnez **Machines virtuelles**.

2. Assurez-vous que votre nouvelle machine virtuelle a été créée. 

    ![Screenshot of the virtual machines page. The new VM is shown and running.](../images/0902.png)

3. Sélectionnez votre machine virtuelle puis, dans le panneau **Présentation**, accédez à l’onglet **Surveillance** et faites défiler vers le bas pour afficher les données de surveillance.

    **Remarque** : Le délai de surveillance peut être ajusté, de une heure à 30 jours.

4. Passez en revue les différents graphiques fournis, y compris **UC (moyenne)** , **Réseau (total)** , et **Octets de disque (total)** . 

    ![Capture d’écran des graphiques de surveillance des machines virtuelles.](../images/0903.png)

5. Dans l’environnement lab, ouvrez une nouvelle fenêtre de navigateur et entrez T https://azure.microsoft.com/en-us/resources/templates/?azure-portal=true.

6. Dans la galerie, vous trouverez un certain nombre de modèles courants et récemment mis à jour.
7. Ces modèles automatisent le déploiement des ressources Azure, y compris l’installation de packages logiciels courants. 

8. Cliquez sur **Ajouter un filtre** et recherchez différents types d’événements et d’opérations afin de vous familiariser avec cette option. 

    ![Capture d’écran de la page Ajouter des filtres avec le type d’événement sélectionné.](../images/0904.png)

Parcourez les différents types de modèles disponibles.

<bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: To avoid additional costs, you can optionally remove this resource group. Search for resource groups, click your resource group, and then click <bpt id="p1">**</bpt>Delete resource group<ept id="p1">**</ept>. Verify the name of the resource group and then click <bpt id="p1">**</bpt>Delete<ept id="p1">**</ept>. Monitor the <bpt id="p1">**</bpt>Notifications<ept id="p1">**</ept> to see how the delete is proceeding.
