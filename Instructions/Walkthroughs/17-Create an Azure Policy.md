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

2. Dans le panneau **Tous les services**, recherchez et sélectionnez **Stratégie**, puis, dans la section **Création**, cliquez sur **Définitions**.  Prenez quelques instants pour passer en revue la liste des définitions de stratégie intégrées. Par exemple, dans la liste déroulante **Catégorie**, sélectionnez uniquement **Compute**. Notez que la définition des **références de machine virtuelle autorisées** permet de spécifier un ensemble de références de machine virtuelle que votre organisation peut déployer.

3. Revenez à la page **Stratégie**, puis, dans la section **Création**, cliquez sur **Affectations**. Une affectation est une stratégie qui a été affectée pour être appliquée dans une étendue spécifique. Par exemple, une définition peut être attribuée à l’étendue de l’abonnement. 

4. Cliquez sur **Attribuer une stratégie** en haut de la page **Stratégie - Affectations**.

5. Sur la page **Attribuer une stratégie**, conservez l’étendue par défaut.

      | Paramètre | Valeur | 
    | --- | --- |
    | Étendue| **Utilisez la valeur par défaut sélectionnée**|
    | Définition de stratégie | cliquez sur les ellipses, puis recherchez **Emplacements autorisés** puis **sélectionnez** |
    | Nom de l'attribution | **Emplacements autorisés** |
    
    ![Capture d’écran du volet Étendue avec ses champs renseignés et le bouton Sélectionner activé. ](../images/1402.png)
6. Sous l’onglet **Paramètres**, sélectionnez **Japon de l’Ouest**. Cliquez sur **Examiner et créer**, puis sur **Créer**.

    **Remarque** : Une étendue détermine les ressources ou le regroupement de ressources auquel l’attribution de stratégie s’applique. Dans notre cas, nous pourrions attribuer cette stratégie à un groupe de ressources spécifique, mais nous avons choisi de l’affecter au niveau de l’abonnement. N’oubliez pas que des ressources peuvent être exclues en fonction de la configuration de l’étendue. Les exclusions sont facultatives.

    **Remarque** : Cette définition de stratégie **Emplacements autorisés** spécifie un emplacement dans lequel toutes les ressources doivent être déployées. Si un autre emplacement est choisi, le déploiement ne sera pas autorisé. Pour plus d’informations, consultez la page [Exemples de stratégies Azure](https://docs.microsoft.com/en-us/azure/governance/policy/samples/index).

   ![Capture d’écran du volet Définitions disponibles avec différents champs mis en évidence et l’option Auditer les machines virtuelles qui n’utilisent pas de disques managés activée.](../images/1403.png)

9. L’attribution de stratégie **Emplacements autorisés** est à présent répertoriée dans le volet **Stratégie - Attributions** et applique la stratégie au niveau d’étendue spécifié (Abonnement).

# <a name="task-2-test-allowed-location-policy"></a>Tâche 2 : Tester la stratégie de localisation autorisée

Dans cette tâche, nous allons tester la stratégie de localisation autorisée. 

1. Dans le portail Azure, dans le panneau **Tous les services**, recherchez et sélectionnez **Comptes de stockage**, puis cliquez sur **+Créer**.

2. Configurez le compte de stockage (remplacez **xxxx** dans le nom du compte de stockage par des lettres et des chiffres afin que le nom soit unique au monde). Laissez les valeurs par défaut pour tous les autres éléments. 

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

    **Remarque** : La stratégie Emplacements autorisés peut afficher des ressources non conformes. Dans ce cas, il s’agit de ressources créées avant l’attribution de stratégie.
 
2. Cliquez sur **Emplacements autorisés** pour ouvrir la fenêtre Conformité à la stratégie Emplacements autorisés.

3. Cliquez sur **Supprimer l’affectation** dans le menu principal. Confirmez que vous souhaitez supprimer l'attribution de stratégie en cliquant sur **Oui**

   ![Capture d’écran de l’élément de menu Supprimer l’affectation.](../images/1407.png)

4. Essayez de créer un autre compte de stockage pour vous assurer que la stratégie n’est plus appliquée.

    **Remarque** : Voici quelques scénarios courants où la stratégie **Emplacements autorisés** peut être utile : 
    - *Suivi des coûts* : Vous pourriez avoir plusieurs abonnements pour différents emplacements régionaux. La stratégie garantit que toutes les ressources sont déployées dans la région prévue pour faciliter le suivi des coûts. 
    - *Résidence des données et conformité de la sécurité* : Vous pourriez également avoir des besoins en matière de résidence des données, créer des abonnements par client ou des charges de travail spécifiques, et déterminer que toutes les ressources doivent être déployées dans un centre de données particulier pour garantir le respect des exigences relatives à la conformité des données et de la sécurité.

Félicitations ! Vous avez créé une stratégie Azure pour limiter le déploiement des ressources Azure à un centre de données particulier.

**Remarque** : Pour éviter des coûts supplémentaires, vous pouvez supprimer ce groupe de ressources. Recherchez des groupes de ressources, cliquez sur votre groupe de ressources, puis sur **Supprimer le groupe de ressources**. Vérifiez le nom du groupe de ressources, puis cliquez sur **Supprimer**. Surveillez les **notifications** pour voir comment se déroule la suppression.
