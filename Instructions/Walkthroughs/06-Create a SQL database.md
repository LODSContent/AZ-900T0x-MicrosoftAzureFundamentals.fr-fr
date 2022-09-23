---
wts:
  title: "06 - Créer une base de données SQL (5\_minutes)"
  module: Module 02 - Core Azure Services (Workloads)
---

# <a name="06---create-a-sql-database-5-min"></a>06 - Créer une base de données SQL (5 minutes)

Dans cette procédure pas à pas, nous allons créer une base de données SQL dans Azure, puis interroger les données de cette base de données.

# <a name="task-1-create-the-database"></a>Tâche 1 : Créer la base de données 

Dans cette tâche, nous créons une base de données SQL à partir de l’exemple de base de données AdventureWorksLT. 

1. Connectez-vous au portail Azure à l’adresse [ **https://portal.azure.com** ](https://portal.azure.com).

2. Dans le panneau **Tous les services**, recherchez et sélectionnez **Bases de données SQL**, puis cliquez sur **+ Ajouter, + Créer, + Nouveau**. 

3. Sous l’onglet **Général**, renseignez ces informations.  

    | Paramètre | Valeur | 
    | --- | --- |
    | Abonnement | **Utilisez la valeur par défaut fournie** |
    | Resource group | **Créer un groupe de ressources** |
    | Nom de la base de données| **db1** | 
    | Serveur | Sélectionnez **Créer** (une nouvelle barre latérale s’ouvre sur la droite)|
    | Nom du serveur | **sqlserverxxxx** (doit être unique) | 
    | Emplacement | **(États-Unis) USA Est** |
    | Méthode d'authentification | **Utilisez l’authentification SQL** |
    | Connexion d’administrateur du serveur | **sqluser** |
    | Mot de passe | **Pa$$w0rd1234** |
    | Cliquez sur  | **OK** |

   ![Capture d’écran du volet Serveur et du volet Nouveau serveur, avec les champs renseignés conformément au tableau et avec les boutons Vérifier + créer et OK mis en surbrillance.](../images/0501.png)

4. Sous l’onglet **Réseaux**, configurez les paramètres suivants (et conservez les valeurs par défaut des autres) 

    | Paramètre | Valeur | 
    | --- | --- |
    | Méthode de connexion | **Point de terminaison public** |    
    | Autoriser les services et les ressources Azure à accéder à ce serveur | **Oui** |
    | Ajouter l’adresse IP actuelle du client | **Non** |
    
   ![Capture d’écran de l’onglet Mise en réseau du panneau Créer une base de données SQL avec les paramètres sélectionnés conformément au tableau et le bouton Examiner et créer activé.](../images/0501b.png)

5. Sous l’onglet **Sécurité**. 

    | Paramètre | Valeur | 
    | --- | --- |
    | Microsoft Defender pour SQL| **Pas maintenant** |
    
6. Sélectionnez l’onglet **Paramètres supplémentaires**. Nous allons utiliser la base de données test AdventureWorksLT.

    | Paramètre | Value | 
    | --- | --- |
    | Données existantes | **Exemple** |

    ![Capture d’écran de l’onglet Paramètres supplémentaires du panneau Créer une base de données SQL avec les paramètres sélectionnés conformément au tableau et le bouton Examiner et créer mis en surbrillance.](../images/0501c.png)

7. Click <bpt id="p1">**</bpt>Review + create<ept id="p1">**</ept> and then click <bpt id="p2">**</bpt>Create<ept id="p2">**</ept> to deploy and provision the resource group, server, and database. It can take approx. 2 to 5 minutes to deploy.


# <a name="task-2-test-the-database"></a>Tâche 2 : Tester la base de données.

Dans cette tâche, nous configurons le serveur SQL Server et nous exécutons une requête SQL. 

1. When the deployment has completed, click Go to resource from the deployment blade. Alternatively, from the <bpt id="p1">**</bpt>All Resources<ept id="p1">**</ept> blade, search and select <bpt id="p2">**</bpt>Databases<ept id="p2">**</ept>, then <bpt id="p3">**</bpt>SQL databases<ept id="p3">**</ept> ensure your new database was created. You may need to <bpt id="p1">**</bpt>Refresh<ept id="p1">**</ept> the page.

    ![Capture d’écran du serveur et de la base de données SQL qui viennent d’être déployés.](../images/0502.png)

2. Click the <bpt id="p1">**</bpt>db1<ept id="p1">**</ept> entry representing the SQL database you created. On the db1 blade click <bpt id="p1">**</bpt>Query editor (preview)<ept id="p1">**</ept>.

3. Connectez-vous en tant que **sqluser** avec le mot de passe **Pa$$w0rd1234**.

4. You will not be able to login. Read the error closely and make note of the IP address that needs to be allowed through the firewall. 

    ![Capture d’écran de la page de connexion de l’Éditeur de requêtes avec une erreur d’adresse IP.](../images/0503.png)

5. Revenez dans le panneau **db1** et cliquez sur **Présentation**. 

    ![Capture d’écran de la page du serveur SQL.](../images/0504.png)

6. Dans le panneau **Présentation** de db1, cliquez sur l’option **Définir le pare-feu du serveur** située dans la partie centrale supérieure de l’écran de présentation.

7. Click <bpt id="p1">**</bpt>+ Add client IP<ept id="p1">**</ept> (top menu bar) to add the IP address referenced in the error. (it may have autofilled for you - if not paste it into the IP address fields). Be sure to <bpt id="p1">**</bpt>Save<ept id="p1">**</ept> your changes. 

    ![Capture d’écran de la page de paramètres du pare-feu du serveur SQL, avec la nouvelle règle d’adresse IP mise en surbrillance.](../images/0506.png)

8. Return to your SQL database (slide the bottom toggle bar to the left) and click on <bpt id="p1">**</bpt>Query Editor (Preview)<ept id="p1">**</ept>. Try to login again as <bpt id="p1">**</bpt>sqluser<ept id="p1">**</ept> with the password <bpt id="p2">**</bpt>Pa$$w0rd1234<ept id="p2">**</ept>. This time you should succeed. Note that it may take a couple of minutes for the new firewall rule to be deployed. 

9. Once you log in successfully, the query pane appears. Enter the following query into the editor pane. 

    ```SQL
    SELECT TOP 20 pc.Name as CategoryName, p.name as ProductName
    FROM SalesLT.ProductCategory pc
    JOIN SalesLT.Product p
    ON pc.productcategoryid = p.productcategoryid;
    ```

    ![Capture d’écran de l’Éditeur de requêtes, avec le volet Requête affiché et les commandes exécutées avec succès.](../images/0507.png)

10. Click <bpt id="p1">**</bpt>Run<ept id="p1">**</ept>, and then review the query results in the <bpt id="p2">**</bpt>Results<ept id="p2">**</ept> pane. The query should run successfully.

    ![Capture d’écran du volet Éditeur de requêtes de la base de données, avec le code SQL exécuté avec succès et la sortie affichée dans le volet Résultats.](../images/0508.png)

Congratulations! You have created a SQL database in Azure and successfully queried the data in that database.

<bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: To avoid additional costs, you can optionally remove this resource group. Search for resource groups, click your resource group, and then click <bpt id="p1">**</bpt>Delete resource group<ept id="p1">**</ept>. Verify the name of the resource group and then click <bpt id="p1">**</bpt>Delete<ept id="p1">**</ept>. Monitor the <bpt id="p1">**</bpt>Notifications<ept id="p1">**</ept> to see how the delete is proceeding.
