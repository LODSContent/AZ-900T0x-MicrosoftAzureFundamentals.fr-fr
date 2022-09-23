---
wts:
  title: "«\_02\_-\_Créer une application web\_(10\_minutes)\_»"
  module: Module 02 - Core Azure Services (Workloads)
---
# <a name="02---create-a-web-app-10-min"></a>« 02 - Créer une application web (10 minutes) »

In this walkthrough, we will create a web app that runs a Docker container. The Docker container contains a Welcome message. 

Azure App Service are actually a collection of four services, all of which are built to help you host and run web applications. The four services (Web Apps, Mobile Apps, API Apps, and Logic Apps) look different, but in the end they all operate in very similar ways. Web Apps are the most commonly used of the four services, and this is the service that we will be using in this lab.

# <a name="task-1-create-a-web-app"></a>Tâche 1 : Créer une application web 

Dans cette tâche, vous allez créer une application web Azure App Service. 

1. Connectez-vous au [portail Azure](http://portal.azure.com/). 

2. Dans le panneau **Tous les services**, recherchez et sélectionnez **App Services**, puis cliquez sur **+ Ajouter, + Créer, + Nouveau**

3. On the <bpt id="p1">**</bpt>Basics<ept id="p1">**</ept> tab of the <bpt id="p2">**</bpt>Web App<ept id="p2">**</ept> blade, specify the following settings (replace <bpt id="p3">**</bpt>xxxx<ept id="p3">**</ept> in the name of the web app with letters and digits such that the name is globally unique). Leave the defaults for everything else, including the App Service Plan. 

    | Paramètre | Valeur |
    | -- | -- |
    | Abonnement | **Utilisez la valeur par défaut fournie** |
    | Groupe de ressources | **Créer un groupe de ressources**|
    | Nom | **myDockerWebAppxxxx** |
    | Publier | **Conteneur Docker** |
    | Système d’exploitation | **Linux** |
    | Région | **USA Est** |
    
    **Remarque :** N’oubliez pas de remplacer la valeur de **xxxx** pour que le nom de l’application web soit unique.

4. Cliquez sur **Suivant > Docker** et configurez les informations sur le conteneur.  

    | Paramètre | Valeur |
    | -- | -- |
    | Options | **Conteneur unique** |
    | Source d’image | **Docker Hub** |
    | Type d’accès | **Public** |
    | Image et étiquette | **mcr.microsoft.com/azuredocs/aci-helloworld** |
    
 **Remarque :** La commande start-up est facultative et n’est pas nécessaire dans cet exercice.

5. Cliquez sur **Examiner et créer**, puis cliquez sur **Créer**. 

# <a name="task-2-test-the-web-app"></a>Tâche 2 : Tester l’application Web

Dans cette tâche, nous allons tester l’application web.

1. Attendez que le déploiement de l’application web soit terminé.

2. Dans la zone **Notifications**, cliquez sur **Accéder à la ressource**. 

3. Dans cette procédure pas à pas, nous allons créer une application web exécutant un conteneur Docker.

    ![Le conteneur Docker comporte un message de bienvenue.](../images/0801.png)

4. In a new browser window, paste the URl and press enter. The Welcome to Azure Container Instances! welcome message will be displayed.

    ![Capture d’écran de la page Bienvenue dans le service Azure Container Instances.](../images/0802.png)

5. Azure App Service est constitué d’une série de quatre services, chacun d’entre eux étant conçu pour vous aider à héberger et à exécuter des applications web. 

Les quatre services (Web Apps, Mobile Apps, API Apps et Logic Apps) sont différents, mais au final, ils fonctionnent tous de manière très similaire.

Félicitations, vous venez de créer une application Azure App Service.
