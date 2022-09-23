---
wts:
  title: "11 - Créer une machine virtuelle avec la CLI (10\_min)"
  module: 'Module 03: Describe core solutions and management tools'
---
# <a name="11---create-a-vm-with-the-cli-10-min"></a>11 - Créer une machine virtuelle avec la CLI (10 min)

Dans cette procédure pas à pas, nous allons configurer Cloud Shell, utiliser Azure CLI pour créer un groupe de ressources et une machine virtuelle et passer en revue les recommandations Azure Advisor. 

# <a name="task-1-configure-the-cloud-shell"></a>Tâche 1 : Configurer Cloud Shell 

Dans cette tâche, nous configurer Cloud Shell., puis nous utiliserons Azure CLI pour créer un groupe de ressources et une machine virtuelle.  

1. Connectez-vous au [portail Azure](https://portal.azure.com).

2. Dans le portail Azure, ouvrez **Azure Cloud Shell** en cliquant sur l’icône située en haut à droite du portail Azure.

    ![Capture d’écran de l’icône Azure Cloud Shell dans le portail Azure.](../images/1002.png)
   
3. Dans la boîte de dialogue Bienvenue dans Azure Cloud Shelll, lorsque vous serez invité à sélectionner **Bash** ou **PowerShell**, sélectionnez **Bash**. 

4. A new window will open stating <bpt id="p1">**</bpt>You have no storage mounted<ept id="p1">**</ept>. Select <bpt id="p1">**</bpt>advanced settings<ept id="p1">**</ept>.

5. Dans la boîte de dialogue Paramètres avancés, renseignez les champs suivants, puis cliquez sur Créer un stockage :
    - Groupe de ressources : **Créer un groupe de ressources**
    - Compte de stockage : Créez un nouveau compte et utilisez un nom unique au monde (par exemple: stockagecloudshellstockagexyz))
    - Partage de fichiers : Créez un nouveau partage et nommez-le cloudshellfileshare


# <a name="task-2-use-cli-to-create-a-virtual-machine"></a>Tâche 2 : Utilisez CLI pour créer une machine virtuelle

Dans cette tâche, nous utiliserons Azure CLI pour créer un groupe de ressources et une machine virtuelle.

1. Assurez-vous que **Bash** est sélectionné dans le menu déroulant situé dans la partie supérieur gauche du volet Cloud Shell. Si ce n’est pas le cas, sélectionnez-le.

    ![Capture d’écran d’Azure Cloud Shell dans le Portail Azure avec la liste déroulante Bash en surbrillance.](../images/1002a.png)


2. Vérifiez le groupe de ressources que vous utilisez en entrant la commande suivante.

    ```cli
    az group list --output table
    ```

4. In Cloud Shell enter the command below and make sure that each line, except for the last one, is followed by the backslash (<ph id="ph1">`\`</ph>) character. If you type the whole command on the same line, do not use any backslash characters. 

    ```cli
    az vm create \
    --name myVMCLI \
    --resource-group myRGCLI \
    --image UbuntuLTS \
    --location EastUS2 \
    --admin-username azureuser \
    --admin-password Pa$$w0rd1234
    ```

    >**Remarque** : Si vous utilisez la ligne de commande sur un ordinateur Windows, remplacez le caractère barre oblique inverse (`\`) par le caractère caret, représentant un accent circonflexe (`^`).

    <bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: The command will take 2 to 3 minutes to complete. The command will create a virtual machine and various resources associated with it such as storage, networking and security resources. Do not continue to the next step until the virtual machine deployment is complete. 

5. Une fois la commande exécutée, dans la fenêtre du navigateur, fermez le volet Cloud Shell.

6. Dans le portail Azure, recherchez **Machines virtuelles** et vérifiez si **myVMCLI** est bien en cours d’exécution.

    ![Capture d’écran de la page des machines virtuelles avec myVMPS en cours d’exécution.](../images/1101.png)


# <a name="task-3-execute-commands-in-the-cloud-shell"></a>Tâche 3 : Exécuter des commandes dans Cloud Shell

Dans cette tâche, nous nous entraînerons à exécuter des commandes CLI à partir de Cloud Shell. 

1. Dans le portail Azure, ouvrez **Azure Cloud Shell** en cliquant sur l’icône située en haut à droite du portail Azure.

2. Assurez-vous que **Bash** est sélectionné dans le menu déroulant affiché en haut à gauche du volet Cloud Shell.

3. Retrieve information about the virtual machine you provisioned, including name, resource group, location, and status. Notice the PowerState is <bpt id="p1">**</bpt>running<ept id="p1">**</ept>.

    ```cli
    az vm show --resource-group myRGCLI --name myVMCLI --show-details --output table 
    ```

4. Stop the virtual machine. Notice the message that billing continues until the virtual machine is deallocated. 

    ```cli
    az vm stop --resource-group myRGCLI --name myVMCLI
    ```

5. Verify your virtual machine status. The PowerState should now be <bpt id="p1">**</bpt>stopped<ept id="p1">**</ept>.

    ```cli
    az vm show --resource-group myRGCLI --name myVMCLI --show-details --output table 
    ```

# <a name="task-4-review-azure-advisor-recommendations"></a>Tâche 4 : Consulter les suggestions dans Azure Advisor

Dans cette tâche, nous passerons en revue les recommandations présentées dans Azure Advisor.

   **Remarque :** Si vous avez terminé le labo précédent (Créer une machine virtuelle avec PowerShell), vous avez déjà effectué cette tâche. 

1. Dans le panneau **Tous les services**, recherchez et sélectionnez **Advisor**. 

2. On the <bpt id="p1">**</bpt>Advisor<ept id="p1">**</ept> blade, select <bpt id="p2">**</bpt>Overview<ept id="p2">**</ept>. Notice recommendations are grouped by Reliability, Security, Performance, and Cost. 

    ![Capture d’écran de la page Vue d’ensemble d’Advisor ](../images/1103.png)

3. Sélectionnez **Toutes les suggestions** et prenez le temps de consulter toutes les suggestions et actions suggérées. 

    **Remarque :** Selon vos ressources, vos suggestions peuvent être différentes. 

    ![Capture d’écran de la page Toutes les suggestions Advisor. ](../images/1104.png)

4. Notez que vous pouvez télécharger les suggestions au format CSV ou PDF. 

5. Notez également que vous pouvez créer des alertes. 

6. Si vous avez le temps, continuez à expérimenter Azure CLI. 

Congratulations! You have configured Cloud Shell, created a virtual machine using Azure CLI, practiced with Azure CLI commands, and viewed Advisor recommendations.

<bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: To avoid additional costs, you can optionally remove this resource group. Search for resource groups, click your resource group, and then click <bpt id="p1">**</bpt>Delete resource group<ept id="p1">**</ept>. Verify the name of the resource group and then click <bpt id="p1">**</bpt>Delete<ept id="p1">**</ept>. Monitor the <bpt id="p1">**</bpt>Notifications<ept id="p1">**</ept> to see how the delete is proceeding.
