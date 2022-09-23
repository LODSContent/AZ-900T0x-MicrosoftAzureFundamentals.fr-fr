---
wts:
  title: "13 - Sécuriser le trafic réseau (10\_minutes)"
  module: 'Module 04: Describe general security and network security features'
---
# <a name="13---secure-network-traffic-10-min"></a>13 - Sécuriser le trafic réseau (10 minutes)

Dans cette procédure pas à pas, nous allons configurer un groupe de sécurité réseau.

# <a name="task-1-create-a-virtual-machine"></a>Tâche 1 : Créer une machine virtuelle

Au cours de cette tâche, nous allons créer une machine virtuelle de centre de données Windows Server 2019. 

1. Connectez-vous au [portail Azure](https://portal.azure.com).

2. Dans le panneau **Tous les services**, recherchez et sélectionnez **Machines virtuelles**, puis cliquez sur **+ Ajouter, + Créer, + Nouveau**.

3. Sous l’onglet **Informations de base** renseignez les informations suivantes (conservez les valeurs par défaut pour toutes les autres options) :

    | Paramètres | Valeurs |
    |  -- | -- |
    | Abonnement | **Utiliser la valeur par défaut fournie** |
    | Resource group | **Créer un groupe de ressources** |
    | Nom de la machine virtuelle | **SimpleWinVM** |
    | Région | **(États-Unis) USA Est**|
    | Image | **Windows Server 2019 Datacenter Gen 2**|
    | Taille | **Standard D2s v3**|
    | Nom d’utilisateur du compte d’administrateur | **azureuser** |
    | Mot de passe du compte d’administrateur | **Pa$$w0rd1234**|
    | Règles des ports d’entrée | **Aucun**|

4. Accédez à l’onglet **Mise en réseau** et configurez le paramètre suivant :

    | Paramètres | Valeurs |
    | -- | -- |
    | Groupe de sécurité réseau de la carte réseau | **Aucun**|

5. Sous l’onglet **Gestion**, dans la section **Contrôle**, sélectionnez le paramètre suivant :

    | Paramètres | Valeurs |
    | -- | -- |
    | Diagnostics de démarrage | **Désactiver**|

6. Conservez les autres valeurs par défaut, puis cliquez sur le bouton **Examiner et créer** au bas de la page.

7. Once Validation is passed click the <bpt id="p1">**</bpt>Create<ept id="p1">**</ept> button. It can take about five minutes to deploy the virtual machine.

8. Monitor the deployment. It may take a few minutes for the resource group and virtual machine to be created. 

9. Dans le panneau de déploiement ou dans la zone de notification, cliquez sur **Accéder à la ressource**. 

10. Sur le panneau de la machine virtuelle **SimpleWinVM**, cliquez sur **Mise en réseau** et, sous l’onglet **Règles de port entrant** vérifiez qu’aucun groupe de sécurité réseau n’est associé à l’interface réseau de la machine virtuelle ou au sous-réseau auquel l’interface réseau est connectée.

    <bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: Identify the name of the network interface. You will need it in the next task.

# <a name="task-2-create-a-network-security-group"></a>Tâche 2 : Créer un groupe de sécurité réseau

Dans cette tâche, nous allons créer un groupe de sécurité réseau et l’associer à l’interface réseau. 

1. Dans le panneau **Tous les services**, recherchez et sélectionnez **Groupes de sécurité réseau**, puis cliquez sur **+ Ajouter, + Créer, + Nouveau**

2. Sous l’onglet **Informations de base** du panneau **Créer un groupe de sécurité réseau**, spécifiez les paramètres suivants.

    | Paramètre | Valeur |
    | -- | -- |
    | Abonnement | **Utilisez l’abonnement par défaut** |
    | Resource group | **Sélectionnez la valeur par défaut dans la liste déroulante** |
    | Nom | **myNSGSecure** |
    | Région | **(États-Unis) USA Est**  |

3. Cliquez sur **Examiner et créer** puis, après la validation, cliquez sur **Créer**.

4. Une fois le NSG créé, cliquez sur **Accéder à la ressource**.

5. En dessous de **Paramètres**, cliquez sur **Interfaces réseau** et ensuite sur ** Associer**.

6. Sélectionnez l’interface réseau que vous avez identifiée dans la tâche précédente. 

# <a name="task-3-configure-an-inbound-security-port-rule-to-allow-rdp"></a>Tâche 3 : Configurer une règle de port de sécurité entrante pour autoriser RDP

Dans cette tâche, nous autoriserons le trafic RDP vers la machine virtuelle en configurant une règle de sécurité de trafic entrant pour un port. 

1. Dans le Portail Azure, accédez au panneau de la machine virtuelle **SimpleWinVM**. 

2. Dans le panneau **Aperçu**, cliquez sur **Connecter**.

3. Attempt to connect to the virtual machine by selecting RDP and downloading an running the RDP file. By default the network security group does not allow RDP. Close the error window. 


    ![Capture d’écran du message d’erreur indiquant que la connexion de la machine virtuelle a échoué.](../images/1201.png)

4. Dans le panneau de la machine virtuelle, défilez vers le bas jusqu’à la section **Paramètres**, cliquez sur **Réseau**, puis notez les règles de trafic entrant pour **myNSGSecure (attached to network interface: myVMNic)** . Le groupe de sécurité réseau refuse tout trafic entrant, à l'exception du trafic au sein du réseau virtuel et des sondes de l'équilibreur de charge.

5. On the <bpt id="p1">**</bpt>Inbound port rules<ept id="p1">**</ept> tab, click <bpt id="p2">**</bpt>Add inbound port rule<ept id="p2">**</ept> . Click <bpt id="p1">**</bpt>Add<ept id="p1">**</ept> when you are done. 

    | Paramètre | Valeur |
    | -- | -- |
    | Source | **Any**|
    | Source port ranges | **\*** |
    | Destination | **Any** |
    | Plages de ports de destination | **3389** |
    | Protocol | **TCP** |
    | Action | **Autoriser** |
    | Priority | **300** |
    | Nom | **AllowRDP** |

6. Select <bpt id="p1">**</bpt>Add<ept id="p1">**</ept> and wait for the rule to be provisioned and then try again to RDP into the virtual machine by going back to <bpt id="p2">**</bpt>Connect<ept id="p2">**</ept> This time you should be successful. Remember the user is <bpt id="p1">**</bpt>azureuser<ept id="p1">**</ept> and the password is <bpt id="p2">**</bpt>Pa$$w0rd1234<ept id="p2">**</ept>.

# <a name="task-4-configure-an-outbound-security-port-rule-to-deny-internet-access"></a>Tâche 4 : Configurer une règle de port de sécurité sortante pour refuser l’accès à Internet

Dans cette tâche, nous allons créer une règle de port de sortie NSG qui refusera l’accès à Internet, puis vérifier que cette règle fonctionne.

1. Continuez dans votre session RDP de machine virtuelle. 

2. Après le démarrage de la machine, ouvrez un navigateur **Internet Explorer**. 

3. Verify that you can access <bpt id="p1">**</bpt><ph id="ph1">https://www.bing.com</ph><ept id="p1">**</ept> and then close Internet Explorer. You will need to work through the IE enhanced security pop-ups. 

    **Remarque** : Nous allons maintenant configurer une règle pour refuser l’accès Internet sortant. 

4. Revenez dans le Portail Azure et accédez de nouveau au panneau de la machine virtuelle **SimpleWinVM**. 

5. En dessous de **Paramètres**, cliquez sur **Mise en réseau**, puis sur **Règles de port de sortie**.

6. Notice there is a rule, <bpt id="p1">**</bpt>AllowInternetOutbound<ept id="p1">**</ept>. This a default rule and cannot be removed. 

7. Click <bpt id="p1">**</bpt>Add outbound port rule<ept id="p1">**</ept> to the right of the <bpt id="p2">**</bpt>myNSGSecure  (attached to network interface: myVMNic)<ept id="p2">**</ept> network security group and configure a new outbound security rule with a higher priority that will deny internet traffic. Click <bpt id="p1">**</bpt>Add<ept id="p1">**</ept> when you are finished. 

    | Paramètre | Valeur |
    | -- | -- |
    | Source | **Any**|
    | Source port ranges | **\*** |
    | Destination | **Étiquette du service** |
    | Identification de destination | **Internet** |
    | Plages de ports de destination | **\*** |
    | Protocol | **TCP** |
    | Action | **Deny** |
    | Priority | **4000** |
    | Nom | **DenyInternet** |

8. Cliquez sur **Ajouter** pour revenir au niveau de la machine virtuelle pour laquelle vous avez autorisé RDP. 

9. Browse to <bpt id="p1">**</bpt><ph id="ph1">https://www.microsoft.com</ph><ept id="p1">**</ept>. The page should not display. You may need to work through additional IE enhanced security pop-ups.  

<bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: To avoid additional costs, you can optionally remove this resource group. Search for resource groups, click your resource group, and then click <bpt id="p1">**</bpt>Delete resource group<ept id="p1">**</ept>. Verify the name of the resource group and then click <bpt id="p1">**</bpt>Delete<ept id="p1">**</ept>. Monitor the <bpt id="p1">**</bpt>Notifications<ept id="p1">**</ept> to see how the delete is proceeding.
