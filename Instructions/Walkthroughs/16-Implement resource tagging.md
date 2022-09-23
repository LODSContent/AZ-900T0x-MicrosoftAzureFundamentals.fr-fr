---
wts:
  title: "16 - Implémenter le balisage des ressources (5\_minutes)"
  module: 'Module 05: Describe identity, governance, privacy, and compliance features'
---
# <a name="16---implement-resource-tagging-5-min"></a>16 - Implémenter le balisage des ressources (5 minutes)

Au cours de cette procédure pas à pas, nous allons créer une affectation de stratégie qui exige un balisage, créer un compte de stockage et tester le balisage, afficher les ressources avec une balise spécifique et supprimer la stratégie de balisage.

# <a name="task-1-create-a-policy-assignment"></a>Tâche 1 : Créer une affectation de stratégie 

Au cours de cette tâche, nous allons configurer la stratégie **Exiger une balise pour les ressources** et l’assigner à notre abonnement. 

1. Connectez-vous au [portail Azure](https://portal.azure.com).

2. Dans le panneau **Tous les services**, recherchez et sélectionnez **Stratégie**.

3. Faites défiler vers le bas jusqu’à la section **Création**, cliquez sur **Affectations**, puis sur **Attribuer une stratégie** en haut de la page.

4. Notez que la **Portée** de notre stratégie sera valable au niveau de l’abonnement. 

5. Under <bpt id="p1">**</bpt>Basics<ept id="p1">**</ept> Select the <bpt id="p2">**</bpt>Policy definition<ept id="p2">**</ept> ellipsis button (right side of textbox). In the <bpt id="p1">**</bpt>Search<ept id="p1">**</ept> box, enter the value <bpt id="p2">**</bpt>tag<ept id="p2">**</ept>. A list of related Policies with the word <bpt id="p1">**</bpt>tag<ept id="p1">**</ept> will appear. Scroll down till you find the <bpt id="p1">**</bpt>Require a tag and its value on resources<ept id="p1">**</ept> definition, click on it and click <bpt id="p2">**</bpt>Select<ept id="p2">**</ept>.

   ![image](https://user-images.githubusercontent.com/89808319/155607579-d564a43e-a9cd-443d-8482-f47879eff2e9.png)
   
6.  On the <bpt id="p1">**</bpt>Parameters<ept id="p1">**</ept> tab, type in **Company : Contoso ** for the tag key/value pair name. Click <bpt id="p1">**</bpt>Review + create<ept id="p1">**</ept>, and then <bpt id="p2">**</bpt>Create<ept id="p2">**</ept>.

  

7. The <bpt id="p1">**</bpt>Require a tag amd its value on resources<ept id="p1">**</ept> policy assignment is now in place. When a resource is created, it must include a tag with the Company : Contoso key.
   <bpt id="p1">**</bpt>Note - you need to wait up to 30 minutes for the Policy to be applied.<ept id="p1">**</ept> 

  ![image](https://user-images.githubusercontent.com/89808319/155607357-556646b6-9ca7-4817-a02e-643869b2c4dd.png)

# <a name="task-2-create-a-storage-account-to-test-the-required-tagging"></a>Tâche 2 : Créer un compte de stockage pour tester le balisage requis

Au cours de cette tâche, nous allons créer des comptes de stockage pour tester le balisage requis. 

1. Dans le portail Azure, dans le panneau **Tous les services**, recherchez et sélectionnez **Comptes de stockage**, puis cliquez sur **+Ajouter +Nouveau +Créer**.

2. On the <bpt id="p1">**</bpt>Basics<ept id="p1">**</ept> tab of the <bpt id="p2">**</bpt>Create storage account<ept id="p2">**</ept> blade, fill in the following information (replace <bpt id="p3">**</bpt>xxxx<ept id="p3">**</ept> in the name of the storage account with letters and digits such that the name is globally unique). Leave the defaults for everything else.

    | Paramètre | Valeur | 
    | --- | --- |
    | Abonnement | **Utiliser la valeur par défaut fournie** |
    | Resource group | **Créer un groupe de ressources** |
    | Nom du compte de stockage | **compte_stockagexxxx** |
    | Emplacement | **(États-Unis) USA Est** |

3. Cliquez sur **Vérifier + créer**. 

    <bpt id="p1">**</bpt>Note:<ept id="p1">**</ept> We are testing to see what happens when the tag is not supplied. Please note, it can take up to 30 minutes for Policies to take effect.

4. You will receive a Validation failed message. Click the <bpt id="p1">**</bpt>Click here to view details<ept id="p1">**</ept> message. On the <bpt id="p1">**</bpt>Errors<ept id="p1">**</ept> blade, on the <bpt id="p2">**</bpt>Summary<ept id="p2">**</ept> tab note the error message stating that resource was disallowed by Policy.

    **Remarque :** Si vous affichez l’onglet Erreur brute, vous verrez le nom de balise spécifique requis. 

    ![Capture d’écran de refus en raison d’une erreur de stratégie.](../images/1704.png)


5. Close the <bpt id="p1">**</bpt>Error<ept id="p1">**</ept> pane and click <bpt id="p2">**</bpt>Previous<ept id="p2">**</ept> (bottom of the screen). Provide the tagging information. 

    | Paramètre | Valeur | 
    | --- | --- |
    | Nom de la balise | **Company:Contoso** (peut ne pas se trouver dans la liste déroulante) |

6. Click <bpt id="p1">**</bpt>Review + create<ept id="p1">**</ept> and verify that the validation was successful. Click <bpt id="p1">**</bpt>Create<ept id="p1">**</ept> to deploy the storage account. 

# <a name="task-3-view-all-resources-with-a-specific-tag"></a>Tâche 3 : Afficher toutes les ressources avec une balise spécifique

1. Dans le portail Azure, dans le panneau **Tous les services**, recherchez et sélectionnez **Balises**.

2. Note all tags and their values. Click the <bpt id="p1">**</bpt>Company : Contoso<ept id="p1">**</ept> key/value pair. This will display a blade showing the newly created storage account, as long as you included the tag during its deployment. 

   ![Capture d’écran des balises avec les options Entreprise et Contoso sélectionnées.](../images/1705.png)

3. Dans le portail, affichez le panneau **Toutes les ressources**.

4. Click <bpt id="p1">**</bpt>Add filter<ept id="p1">**</ept> and add the <bpt id="p2">**</bpt>Company<ept id="p2">**</ept> tag key as the filter category. With the filter applied, only your storage account will be listed.

    ![Capture d’écran du filtre Toutes les ressources avec l’option Entreprise activée.](../images/1706.png)

# <a name="task-4-delete-the-policy-assignment"></a>Tâche 4 : Supprimer l’attribution de stratégie

Au cours de cette tâche, nous allons supprimer la stratégie **Exiger une balise pour les ressources** afin de ne pas affecter nos travaux suivants. 

1. Dans le portail, depuis le panneau **Tous les services**, recherchez et sélectionnez **Stratégie**.

2. Cliquez sur l’entrée de stratégie **Exiger une balise sur les ressources**.

3. Cliquez sur **Supprimer l’affectation** dans le menu principal.

4. Confirmez la suppression de l’affectation de stratégie dans la boîte de dialogue **Supprimer l’affectation** en cliquant sur **Oui**.

5. Si vous avez le temps, créez une autre ressource sans balise pour vous assurer que la stratégie n’est plus en vigueur.

Sous **Informations de base**, sélectionnez les points de suspension affichés en regard de la zone **Définition de la stratégie** (côté droit de la zone de texte).


Dans la zone de **Recherche**, entrez la valeur **balise**.
