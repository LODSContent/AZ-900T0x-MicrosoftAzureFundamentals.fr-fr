---
wts:
  title: "20 - Utilisation de l’outil de calcul du TCO Azure (10\_min)"
  module: 'Module 06: Describe Azure cost management and service level agreements'
---
# <a name="20---use-the-azure-tco-calculator-10-min"></a>20 - Utilisation de l’outil de calcul du TCO Azure (10 min)


Dans cette procédure pas à pas, vous allez utiliser l’outil de calcul du coût total de possession (TCO) pour générer un rapport de comparaison des coûts pour un environnement local.

<bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: This walkthrough provides example definitions of on-premises infrastructure and workloads for a typical datacenter. To create a TCO Calculator report, use the example definitions or provide details of your <bpt id="p1">*</bpt>actual<ept id="p1">*</ept> on-premises infrastructure and workloads.

# <a name="task-1-configure-the-tco-calculator"></a>Tâche 1 : Configurer la calculatrice du coût total de possession (TCO)

Dans cette tâche, nous ajouterons des informations d’infrastructure à la calculatrice. 

1. Dans un navigateur, accédez à la page [Outil de calcul du coût total de possession (TCO)](https://azure.microsoft.com/en-us/pricing/tco/calculator/).

2. Pour ajouter des détails sur votre infrastructure de serveur locale, cliquez sur **+ Ajouter une charge de travail de serveur** dans le volet **Définissez vos charges de travail**.

    | Paramètres | Valeur |
    | -- | -- |
    | Nom | **Serveurs : Machines virtuelles Windows** |
    | Charge de travail | **Serveur Windows/Linux** |
    | Environnement | **Machines virtuelles** |
    | Système d’exploitation | **Windows** |  
    | Machines virtuelles | **50** |
    | Virtualisation | **Hyper-V** |
    | Processeur(s) | **8**|
    | RAM (Go) | **16** |
    | Optimiser par | **UC** |
    | Windows Server 2008/2008 R2 | **Désactivé** |

3. Sélectionnez **+ Ajouter une charge de travail de serveur** pour créer une ligne pour une nouvelle définition de charges de travail de serveur. 

    | Paramètres | Valeur |
    | -- | -- |
    | Nom | **Serveurs : Machines virtuelles Linux** |
    | Charge de travail | **Serveur Windows/Linux** |
    | Environnement | **Machines virtuelles** |
    | Système d’exploitation | **Linux** |  
    | Machines virtuelles | **50** |
    | Virtualisation | **VMware** |
    | Processeur(s) | **8**|
    | RAM (Go) | **16** |
    | Optimiser par | **UC** |
    | Windows Server 2008/2008 R2 | **Désactivé** |

4. Dans le volet **Stockage**, cliquez sur **Ajouter du stockage**.

    | Paramètres | Valeur |
    | -- | -- |
    | Nom | **Stockage serveur** |
    | Type de stockage | **Disque local/SAN** |
    | Type de disque | **HDD** |
    | Capacité | **60 To** |  
    | Sauvegarde | **120 To** |
    | Archivage | **0 To** |

5. Dans le volet **Mise en réseau**, ajoutez de la bande passante. 

    | Paramètres | Valeur |
    | -- | -- |
    | Bande passante sortante | 15 To|

6. Cliquez sur **Suivant**.

7. Parcourez les options et effectuez les ajustements nécessaires. 

    | Paramètres | Valeur |
    | -- | -- |
    | Devise | **Euro** |

8. Cliquez sur **Suivant**.

# <a name="task-2-review-the-results-and-save-a-copy"></a>Tâche 2 : Vérifier les résultats et enregistrer une copie

Dans cette tâche, nous évaluerons les suggestions de réduction des coûts et téléchargerons un rapport. 

1. Consultez les recommandations et les exemples de réduction des coûts Azure.

    | Paramètres | Valeur |
    | -- | -- |
    | Délai d’exécution| **3 ans** |
    | Région | **Europe Nord** |

2. Pour modifier les informations que vous avez fournies, accédez au bas de la page et cliquez sur **Retour**. 

3. Pour enregistrer ou imprimer une copie PDF du rapport, cliquez sur **Télécharger**.

    ![Screenshot of the report pane of the tco calculator in Azure. The highlighted and completed input fields indicates how set the tco calculator timeframe to three years and the region to north europe. A graph shows the cost of on-premises infrastructure and workloads off-set against the reduced cost of using Azure.](../images/2001.png)

Congratulations! You have used the TCO Calculator to generate a cost comparison report for an on-premises environment.
