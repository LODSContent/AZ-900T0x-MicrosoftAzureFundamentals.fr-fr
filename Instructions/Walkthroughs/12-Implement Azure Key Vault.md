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

3. Configure the key vault (replace <bpt id="p1">**</bpt>xxxx<ept id="p1">**</ept> in the name of the key vault with letters and digits such that the name is globally unique). Leave the defaults for everything else.

    | Paramètre | Valeur | 
    | --- | --- |
    | Abonnement | **Utilisez la valeur par défaut fournie** |
    | Resource group | **Créer un groupe de ressources** |
    | Nom du coffre de clés | **keyvaulttestxxx** |
    | Location | **USA Est** |
    | Niveau tarifaire | **Standard** |
    
    **Remarque** remplacez **xxxx** afin de créer un nom unique.
4. Cliquez sur **Examiner et créer**, puis cliquez sur **Créer**. 

5. Once the new key vault is provisioned, click <bpt id="p1">**</bpt>Go to resource<ept id="p1">**</ept>. Or you can locate your new key vault by searching for it. 

6. Click on the key vault <bpt id="p1">**</bpt>Overview<ept id="p1">**</ept> tab and take note of the <bpt id="p2">**</bpt>Vault URI<ept id="p2">**</ept>. Applications that use your vault through the REST APIs will need this URI.

7. Take a moment to browse through some of the other key vault options. Under <bpt id="p1">**</bpt>Settings<ept id="p1">**</ept> review <bpt id="p2">**</bpt>Keys<ept id="p2">**</ept>, <bpt id="p3">**</bpt>Secrets<ept id="p3">**</ept>, <bpt id="p4">**</bpt>Certificates<ept id="p4">**</ept>, <bpt id="p5">**</bpt>Access Policies<ept id="p5">**</ept>, <bpt id="p6">**</bpt>Firewalls and virtual networks<ept id="p6">**</ept>.

    <bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: Your Azure account is the only one authorized to perform operations on this new vault. You can modify this if you wish in the <bpt id="p1">**</bpt>Settings<ept id="p1">**</ept> and then the <bpt id="p2">**</bpt>Access policies<ept id="p2">**</ept> section.

# <a name="task-2-add-a-secret-to-the-key-vault"></a>Tâche 2 : Ajouter un secret au coffre de clés
        
Dans cette tâche, nous ajouterons un mot de passe au coffre à clés. 

1. Sous **Paramètres**, cliquez sur **Secrets**, puis sur **+ Générer/Importer**.

2. Configure the secret. Leave the other values at their defaults. Notice you can set an activation and expiration date. Notice you can also disable the secret.

    | Paramètre | Valeur | 
    | --- | --- |
    | Options de chargement | **Manuel** |
    | Nom | **ExamplePassword** |
    | Value | **hVFkk96** |

3. Cliquez sur **Créer**.

4. Une fois le secret créé, cliquez sur **ExamplePassword** et notez qu’il a le statut **Activé**

5. Select the secret you just created, note the the <bpt id="p1">**</bpt>Secret Identifier<ept id="p1">**</ept>. This is the url value that you can now use with applications. It provides a centrally managed and securely stored password. 

6. Cliquez sur le bouton **Afficher la valeur du secret** pour afficher le mot de passe que vous avez spécifié précédemment.


Configurer le coffre de clés (remplacer **xxxx** dans le nom du coffre de clés par des lettres et des chiffres pour que le nom soit unique au monde).

Laissez les valeurs par défaut pour tous les autres éléments.
