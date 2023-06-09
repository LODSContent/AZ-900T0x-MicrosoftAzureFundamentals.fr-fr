---
wts:
  title: "12 - Implémenter Azure Key Vault (5\_minutes)"
  module: 'Module 04: Describe general security and network security features'
---
# <a name="12---implement-azure-key-vault-5-min"></a>12 - Implémenter Azure Key Vault (5 minutes)

Dans cette procédure pas à pas, nous allons créer un coffre de clés Azure (Key vault), puis créer un mot de passe secret dans ce coffre de clés, fournissant un mot de passe stocké en toute sécurité et géré de manière centralisée en vue d’une utilisation dans les applications.

# <a name="task-1-create-an-azure-key-vault"></a>Tâche 1 : Créer un Azure Key Vault 

1. Connectez-vous au [portail Azure](https://portal.azure.com).

2. Dans le panneau **Tous les services**, recherchez et sélectionnez **Key vaults**, puis sélectionnez **+Ajouter +Nouveau +Créer **.

3. Configurer le coffre de clés (remplacer **xxxx** dans le nom du coffre de clés par des lettres et des chiffres pour que le nom soit unique au monde). Laissez les valeurs par défaut pour tous les autres éléments.

    | Paramètre | Valeur | 
    | --- | --- |
    | Abonnement | **Utilisez la valeur par défaut fournie** |
    | Resource group | **Créer un groupe de ressources** |
    | Nom du coffre de clés | **keyvaulttestxxx** |
    | Location | **USA Est** |
    | Niveau tarifaire | **Standard** |
    
    **Remarque** remplacez **xxxx** afin de créer un nom unique.
4. Cliquez sur **Examiner et créer**, puis cliquez sur **Créer**. 

5. Une fois le nouveau coffre de clés configuré, cliquez sur **Accéder à la ressource**. Vous pouvez également localiser votre nouveau coffre de clés en le recherchant. 

6. Cliquez sur le coffre de clés dans le panneau **Présentation** et prenez note de l’**URI Vault**. Les applications qui utilisent votre coffre via les API REST doivent utiliser cet URI.

7. Prenez un moment pour parcourir certaines des autres options du coffre de clés. Sous **Paramètres**, vérifiez **Clés**, **Secrets**, **Certificats**, **Stratégies d’accès**, **Pare-feu et réseaux virtuels**.

    **Remarque** : Votre compte Azure est le seul autorisé à effectuer des opérations sur ce nouveau coffre. Vous pouvez le modifier si vous le souhaitez dans les **Paramètres** puis dans la section **Stratégies d’accès**.

# <a name="task-2-add-a-secret-to-the-key-vault"></a>Tâche 2 : Ajouter un secret au coffre de clés
        
Dans cette tâche, nous ajouterons un mot de passe au coffre à clés. 

1. Sous **Paramètres**, cliquez sur **Secrets**, puis sur **+ Générer/Importer**.

2. Configurez le secret. Conservez les valeurs par défaut pour tous les autres éléments. Notez que vous pouvez définir une date d’activation et une date d’expiration. Notez que vous pouvez également désactiver le secret.

    | Paramètre | Valeur | 
    | --- | --- |
    | Options de chargement | **Manuel** |
    | Nom | **ExamplePassword** |
    | Value | **hVFkk96** |

3. Cliquez sur **Créer**.

4. Une fois le secret créé, cliquez sur **ExamplePassword** et notez qu’il a le statut **Activé**

5. Sélectionnez le secret que vous venez de créer et notez le **Identificateur de secret**. Il s’agit de la valeur de l’URL que vous pouvez désormais utiliser avec les applications. Il fournit un mot de passe géré de manière centralisée et stocké en toute sécurité. 

6. Cliquez sur le bouton **Afficher la valeur du secret** pour afficher le mot de passe que vous avez spécifié précédemment.


Félicitations ! Vous avez créé un coffre de clés Azure, puis créé un mot de passe secret dans ce coffre de clés. Vous disposez donc d’un mot de passe sécurisé et géré de manière centralisée, qui peut être utilisé dans les applications.

**Remarque** : Pour éviter des coûts supplémentaires, vous pouvez supprimer ce groupe de ressources. Recherchez des groupes de ressources, cliquez sur votre groupe de ressources, puis sur **Supprimer le groupe de ressources**. Vérifiez le nom du groupe de ressources, puis cliquez sur **Supprimer**. Surveillez les **notifications** pour voir comment se déroule la suppression.
