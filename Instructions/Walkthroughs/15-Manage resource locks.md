---
wts:
  title: "15 - Gérer le verrouillage des ressources (5\_minutes)\_»"
  module: 'Module 05: Describe identity, governance, privacy, and compliance features'
---
# <a name="15---manage-resource-locks-5-min"></a>15 - Gérer le verrouillage des ressources (5 minutes) »

In this walkthrough, we will add a lock to the resource group and test deleting the resource group. Locks can be applied in a subscription to resource groups, or individual resources to prevent accidental deletion or modification of critical resources.  


# <a name="task-1--add-a-lock-to-the-resource-group-and-test-deletion"></a>Tâche 1 :  Ajouter un verrou au groupe de ressources et tester la suppression

Au cours de cette tâche, nous allons ajouter un verrou de ressource au groupe de ressources et tester la suppression de ce groupe. 

1. Connectez-vous au [portail Azure](https://portal.azure.com).

2. Dans le portail Azure, accédez au groupe de ressources **myRGLocks**.

3. Vous pouvez appliquer un verrou à un abonnement, à un groupe de ressources ou à une ressource pour empêcher la suppression ou la modification accidentelle de ressources critiques. 

4. Dans la section **Paramètres**, cliquez sur **Verrous**, puis sur **+ Ajouter**. 

    ![Capture d’écran du groupe de ressources myRGLocks avec le volet Verrous affiché.](../images/1601.png)

5. Configure the new lock. When you are done click <bpt id="p1">**</bpt>OK<ept id="p1">**</ept>. 

    | Paramètre | Value |
    | -- | -- |
    | Nom du verrou | '''RGLock''' |
    | Type de verrou | **Supprimer** |
    | | |

6. Click <bpt id="p1">**</bpt>Overview<ept id="p1">**</ept> and click <bpt id="p2">**</bpt>Delete resource group<ept id="p2">**</ept>. Type the name of the resource group and click <bpt id="p1">**</bpt>OK<ept id="p1">**</ept>. You receive an error message stating the resource group is locked and can't be deleted.

    ![Capture d’écran d’échec dû à un verrou de suppression.](../images/1602.png)

# <a name="task-2-test-deleting-a-member-of-the-resource-group"></a>Tâche 2 : Tester la suppression d’un membre du groupe de ressources

Au cours de cette tâche, nous allons tester si le verrou de ressource protège un compte de stockage dans le groupe de ressources. 

1. Dans le panneau **Tous les services**, recherchez et sélectionnez **Comptes de stockage**, puis cliquez sur **+ Ajouter, + Créer ou + Nouveau**. 

2. Au cours de cette procédure pas à pas, nous allons ajouter un verrou de ressource au groupe de ressources et tester la suppression de ce groupe.

    | Paramètre | Valeur | 
    | --- | --- |
    | Abonnement | **Sélectionnez votre abonnement** |
    | Groupe de ressources | **myRGLocks** |
    | Nom du compte de stockage | **compte_stockagexxxx** |
    | Emplacement | **(États-Unis) USA Est**  |
    | Performances | **Standard** |
    | Type de compte | **StorageV2 (v2 universel)** |
    | Réplication | **Stockage localement redondant (LRS)** |
    | Niveau d’accès (par défaut) | **Chaud** |
   

3. Cliquez sur **Examiner et créer** pour réviser les paramètres de votre compte de stockage et autoriser Azure à valider la configuration. 

4. Vous pouvez appliquer un verrou dans un abonnement à un groupe de ressources ou à une ressource individuelle pour empêcher la suppression ou la modification accidentelle de ressources critiques. 

5.  Attendez la notification indiquant que le compte de stockage a bien été créé. 

6. Access your new storage account and from the <bpt id="p1">**</bpt>Overview<ept id="p1">**</ept> pane, click <bpt id="p2">**</bpt>Delete<ept id="p2">**</ept>. You receive an error message stating the resource or its parent has a delete lock. 

    ![Capture d’écran de l’erreur de suppression du compte de stockage.](../images/1603.png)

    <bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: Although we did not create a lock specifically for the storage account, we did create a lock at the resource group level, which contains the storage account. As such, this <bpt id="p1">*</bpt>parent<ept id="p1">*</ept> level lock prevents us from deleting the resource and the storage account inherits the lock from the parent.

# <a name="task-3-remove-the-resource-lock"></a>Tâche 3 : Supprimer le verrou de ressource

Au cours de cette tâche, nous allons supprimer le verrou de ressource et effectuer un test. 

1. Revenez au panneau du groupe de ressources **myRGLocks-XXXXXXXX** puis, dans la section **Paramètres**, cliquez sur **Verrous**.
    
2. Cliquez sur le lien **Supprimer** tout à droite de l’entrée **myRGLocks-XXXXXXXX**, à droite de **Modifier**.

    ![Capture d’écran du verrou avec le lien Supprimer activé.](../images/1604.png)

3. Revenez au panneau du compte de stockage et vérifiez que vous pouvez à présent supprimer la ressource.

Congratulations! You created a resource group, added a lock to resource group and tested deletion, tested deleting a resource in the resource group, and removed the resource lock. 

<bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: To avoid additional costs, you can optionally remove this resource group. Search for resource groups, click your resource group, and then click <bpt id="p1">**</bpt>Delete resource group<ept id="p1">**</ept>. Verify the name of the resource group and then click <bpt id="p1">**</bpt>Delete<ept id="p1">**</ept>. Monitor the <bpt id="p1">**</bpt>Notifications<ept id="p1">**</ept> to see how the delete is proceeding.
