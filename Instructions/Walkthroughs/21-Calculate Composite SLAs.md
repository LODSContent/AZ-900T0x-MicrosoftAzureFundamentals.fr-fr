---
wts:
  title: "21 - Calculer des SLA composites (5\_min)"
  module: 'Module 06: Describe Azure cost management and service level agreements'
---
# <a name="21---calculate-composite-slas-5-min"></a>21 - Calculer des SLA composites (5 min)

Dans cette procédure pas à pas, nous allons déterminer le contrat de niveau de service de disponibilité des services Azure, puis calculer la disponibilité attendue basée sur le contrat de niveau de service composite de l’application.

Our example application consists of these Azure services. We will not go in to deep architectural configuration and considerations, the intention here is to give an high level example.

+ **App Service** : Pour héberger l’application.
+ **Azure AD B2C** : Pour authentifier les connexions utilisateur et gérer les profils.
+ **Application Gateway** : Pour gérer l’accès aux applications et leur mise à l’échelle. 
+ **Azure SQL Database** : Pour stocker les données d’application. 

# <a name="task-1-determine-the-sla-uptime-percentage-values-for-our-application"></a>Tâche 1 : Déterminer les valeurs de pourcentage de la durée active du contrat de niveau de service pour notre application

1. Dans un navigateur, accédez à la page [Résumé SLA pour les services Azure](https://azure.microsoft.com/en-us/support/legal/sla/summary/).

2. Locate the <bpt id="p1">**</bpt>App Service<ept id="p1">**</ept> SLA uptime value, <bpt id="p2">**</bpt>99.95%<ept id="p2">**</ept>. Click <bpt id="p1">**</bpt>View full details<ept id="p1">**</ept>, and then expand <bpt id="p2">**</bpt>SLA details<ept id="p2">**</ept>. Notice the <bpt id="p1">**</bpt>Monthly uptime percentages<ept id="p1">**</ept> and <bpt id="p2">**</bpt>Service Credits<ept id="p2">**</ept>.

3. Revenez à la page Web SLA et localisez le service **Azure Active Directory B2C** puis déterminez la valeur de durée active du contrat SLA, **99,9 %** . 

4. Localisez la valeur de durée active du contrat de niveau de service de l’**Application Gateway**, **99,95 %** . 

5. The Azure SQL database uses Premium tiers but is not configured for Zone Redundant Deployments. Locate the <bpt id="p1">**</bpt>Azure SQL Database<ept id="p1">**</ept> SLA uptime value, <bpt id="p2">**</bpt>99.99%<ept id="p2">**</ept>. 

    <bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: There are different uptime values for different configurations and deployments of Azure SQL Database. It is important you are clear on your required uptime values, when planning and costing your deployment and configuration. Small changes in uptime can have impact on service costs as well as potentially increase complexity in configuration. Some other services that may be of interest on the Azure SLA summary web page would include <bpt id="p1">**</bpt>Virtual Machines<ept id="p1">**</ept>, <bpt id="p2">**</bpt>Storage Accounts<ept id="p2">**</ept> and <bpt id="p3">**</bpt>Cosmos DB<ept id="p3">**</ept>.

# <a name="task-2-calculate-the-application-composite-sla-percentage-uptime"></a>Tâche 2 : Calculer le pourcentage de temps de fonctionnement du contrat SLA composite de l’application

1. Notre exemple d’application se compose de ces services Azure.

    **% de temps de fonctionnement d’App Service** X **% de temps de fonctionnement d’Azure AD B2C** X **% de temps de fonctionnement d’Application Gateway Azure** X **% de temps de fonctionnement de la base de données SQL Azure** =  **% de temps de fonctionnement**

    qui, en pourcentage, se définit comme suit :

    **99,95 %** X **99,9 %** X **99,95 %** X **99,99 %**  = **99,79 %**

    Il s’agit de la disponibilité attendue, telle que définie dans le contrat SLA de notre application, avec les services et l’architecture actuels.

Nous n’entrerons pas dans une configuration et des considérations architecturales profondes. L’intention ici est de donner un exemple de haut niveau.
