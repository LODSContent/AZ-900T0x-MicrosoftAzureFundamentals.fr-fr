---
wts:
  title: "17\_-\_Créer une stratégie Azure\_(10\_minutes)"
  module: 'Module 05: Describe identity, governance, privacy, and compliance features'
---
# <a name="17---create-an-azure-policy-10-min"></a>17 - Créer une stratégie Azure (10 minutes)

Dans cette procédure pas à pas, nous allons créer une stratégie Azure pour limiter le déploiement des ressources Azure à un emplacement spécifique.

# <a name="task-1-create-a-policy-assignment"></a>Tâche 1 : Créer une affectation de stratégie 

Au cours de cette tâche, nous allons configurer la stratégie d’emplacements autorisés et l’affecter à notre abonnement. 

1. Connectez-vous au [portail Azure](https://portal.azure.com).

2. From the <bpt id="p1">**</bpt>All services<ept id="p1">**</ept> blade, search for and select <bpt id="p2">**</bpt>Policy<ept id="p2">**</ept>, under the <bpt id="p3">**</bpt>Authoring<ept id="p3">**</ept> section click <bpt id="p4">**</bpt>Definitions<ept id="p4">**</ept>.  Take a moment to review the list of built-in policy definitions. For example, in the <bpt id="p1">**</bpt>Category<ept id="p1">**</ept> drop-down select only <bpt id="p2">**</bpt>Compute<ept id="p2">**</ept>. Notice the <bpt id="p1">**</bpt>Allowed virtual machine size SKUs<ept id="p1">**</ept> definition enables you to specify a set of virtual machine SKUs that your organization can deploy.

3. Return to the <bpt id="p1">**</bpt>Policy<ept id="p1">**</ept> page, under the <bpt id="p2">**</bpt>Authoring<ept id="p2">**</ept> section click <bpt id="p3">**</bpt>Assignments<ept id="p3">**</ept>. An assignment is a policy that has been assigned to take place within a specific scope. For example, a definition could be assigned to the subscription scope. 

4. Cliquez sur **Attribuer une stratégie** en haut de la page **Stratégie - Affectations**.

5. Sur la page **Attribuer une stratégie**, conservez l’étendue par défaut.

      | Paramètre | Valeur | 
    | --- | --- |
    | Étendue| **Utilisez la valeur par défaut sélectionnée**|
    | Définition de stratégie | cliquez sur les ellipses, puis recherchez **Emplacements autorisés** puis **sélectionnez** |
    | Nom de l'attribution | **Emplacements autorisés** |
    
    ![Capture d’écran du volet Étendue avec ses champs renseignés et le bouton Sélectionner activé. ](../images/1402.png)
6. On the <bpt id="p1">**</bpt>Parameters<ept id="p1">**</ept> tab, select <bpt id="p2">**</bpt>Japan West<ept id="p2">**</ept>. Click <bpt id="p1">**</bpt>Review + create<ept id="p1">**</ept>, and then <bpt id="p2">**</bpt>Create<ept id="p2">**</ept>.

    <bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: A scope determines what resources or grouping of resources the policy assignment applies to. In our case we could assign this policy to a specific resource group, however we chose to assign the policy at subscription level. Be aware that resources can be excluded based on the scope configuration. Exclusions are optional.

    <bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: This <bpt id="p2">**</bpt>Allowed Locations<ept id="p2">**</ept> policy definition will specify a location into which all resources must be deployed. If a different location is chosen, deployment will not be allowed. For more information view the <bpt id="p1">[</bpt>Azure Policy Samples<ept id="p1">](https://docs.microsoft.com/en-us/azure/governance/policy/samples/index)</ept> page.

   ![Capture d’écran du volet Définitions disponibles avec différents champs mis en évidence et l’option Auditer les machines virtuelles qui n’utilisent pas de disques managés activée.](../images/1403.png)

9. L’attribution de stratégie **Emplacements autorisés** est à présent répertoriée dans le volet **Stratégie - Attributions** et applique la stratégie au niveau d’étendue spécifié (Abonnement).

# <a name="task-2-test-allowed-location-policy"></a>Tâche 2 : Tester la stratégie de localisation autorisée

Dans cette tâche, nous allons tester la stratégie de localisation autorisée. 

1. Dans le portail Azure, dans le panneau **Tous les services**, recherchez et sélectionnez **Comptes de stockage**, puis cliquez sur **+Créer**.

2. Configure the storage account (replace <bpt id="p1">**</bpt>xxxx<ept id="p1">**</ept> in the name of the storage account with letters and digits such that the name is globally unique). Leave the defaults for everything else. 

    | Paramètre | Valeur | 
    | --- | --- |
    | Abonnement | **Utilisez les valeurs par défaut fournies** |
    | Groupe de ressources | **myRGPolicy** (création) |
    | Nom du compte de stockage | **compte_stockagexxxx** |
    | Emplacement | **(États-Unis) USA Est** |

3. Cliquez sur **Vérifier + créer**, puis sur **Créer**. 

4. Vous recevrez le message d’erreur **Échec du déploiement** spécifiant que la ressource a été désallouée par une stratégie, par exemple la stratégie **Emplacements autorisés**.

# <a name="task-3-delete-the-policy-assignment"></a>Tâche 3 : Supprimer l’attribution de stratégie

Dans cette tâche, nous allons supprimer l’attribution et le test de la stratégie de localisation autorisée. 

Nous allons supprimer l’attribution de stratégie pour ne pas risquer d’être bloqués lors d’une tâche ultérieure.

1. Dans le panneau **Tous les services**, recherchez et sélectionnez **Stratégie**, puis cliquez sur votre stratégie **Emplacements autorisés**.

    **Remarque** : Dans le panneau **Stratégie**, vous pouvez consulter l’état de conformité des différentes stratégies que vous avez attribuées.

    <bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: The Allowed location policy may show non-compliant resources. If so, these are resources created prior to the policy assignment.
 
2. Cliquez sur **Emplacements autorisés** pour ouvrir la fenêtre Conformité à la stratégie Emplacements autorisés.

3. Dans le panneau **Tous les services**, recherchez et sélectionnez **Stratégie**, puis, dans la section **Création**, cliquez sur **Définitions**.

   ![Capture d’écran de l’élément de menu Supprimer l’affectation.](../images/1407.png)

4. Essayez de créer un autre compte de stockage pour vous assurer que la stratégie n’est plus appliquée.

    **Remarque** : Voici quelques scénarios courants où la stratégie **Emplacements autorisés** peut être utile : 
    - Prenez quelques instants pour passer en revue la liste des définitions de stratégie intégrées. 
    - *Résidence des données et conformité de la sécurité* : Vous pourriez également avoir des besoins en matière de résidence des données, créer des abonnements par client ou des charges de travail spécifiques, et déterminer que toutes les ressources doivent être déployées dans un centre de données particulier pour garantir le respect des exigences relatives à la conformité des données et de la sécurité.

Par exemple, dans la liste déroulante **Catégorie**, sélectionnez uniquement **Compute**.

Notez que la définition des **références de machine virtuelle autorisées** permet de spécifier un ensemble de références de machine virtuelle que votre organisation peut déployer.
