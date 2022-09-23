---
wts:
  title: "19 - Utiliser la calculatrice de prix Azure (10\_minutes)"
  module: 'Module 06: Describe Azure cost management and service level agreements'
---
# <a name="19---use-the-pricing-calculator-10-min"></a>19 - Utiliser la calculatrice de prix (10 minutes)

Dans cette procédure pas à pas, nous utiliserons la calculatrice de prix Azure pour générer une estimation des coûts pour une machine virtuelle Azure et les ressources réseau associées.

# <a name="task-1-configure-the-pricing-calculator"></a>Tâche 1 : Configurer la calculatrice de prix

Dans cette tâche, nous allons estimer le coût d’un échantillon d’infrastructure à l’aide de la calculatrice de prix Azure. 

<bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: To create an Azure Pricing Calculator estimate, this walkthrough provides example configurations for the VM and related resources. Use this example configurations or provide the Azure Pricing Calculator with details of your <bpt id="p1">*</bpt>actual<ept id="p1">*</ept> resource requirements instead.

1. Dans un navigateur, accédez à la page Web [Calculateur de prix appliqués Azure](https://azure.microsoft.com/en-us/pricing/calculator/).

2. Pour ajouter des détails sur votre configuration de machine virtuelle, cliquez sur **Machines virtuelles**, sous l’onglet **Produits**. Faites défiler vers le bas pour afficher les détails de la machine virtuelle. 

3. Replace <bpt id="p1">**</bpt>Your Estimate<ept id="p1">**</ept> and <bpt id="p2">**</bpt>Virtual Machines<ept id="p2">**</ept> text with more descriptive names for your Azure Pricing Calculator estimate and your VM configuration. This walkthrough example uses <bpt id="p1">**</bpt>My Pricing Calculator Estimate<ept id="p1">**</ept> for the estimate, and <bpt id="p2">**</bpt>Windows VM<ept id="p2">**</ept> for the VM configuration.

   ![Screenshot of the vm configuration area within the Azure pricing calculator estimate webpage. The highlighted estimate name and vm configuration name indicate how to add an estimate name and a vm configuration name to an Azure pricing calculator estimate.](../images/1901.png)

4. Modifiez la configuration de la machine virtuelle par défaut.

    | Paramètres | Valeur |
    | -- | -- |
    | Région | **Europe Nord** |
    | Système d’exploitation | **Windows** |
    | Type | **(Système d’exploitation uniquement)** |
    | Niveau | **Standard** |  
    | Instance | **R2 : 2 cœurs, 3,5 Go de RAM, 135 Go de stockage temporaire** |

   ![Screenshot of the vm configuration area within the Azure pricing calculator estimate webpage. The highlighted examples of user inputted vm configuration property values indicate how to specify a vm configuration within an Azure pricing calculator estimate.](../images/1902.png)

    <bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: The VM instance specifications and pricing may differ from those in this example. Follow this walkthrough by choosing an instance that matches the example as closely as possible. To view details about the different VM product options, choose <bpt id="p1">**</bpt>Product details<ept id="p1">**</ept> from the <bpt id="p2">**</bpt>More info<ept id="p2">**</ept> menu on the right.

5. Définissez la valeur de l’option **Facturation** sur **Paiement à l’utilisation**.

   ![Screenshot of the vm billing options area within the Azure pricing calculator estimate webpage. The highlighted pay as you go billing option indicates how to specify a billing option for a vm within an Azure pricing calculator estimate.](../images/1903.png)

6. **Remarque** : Pour créer une estimation de la calculatrice de prix Azure, cette procédure pas à pas donne des exemples de configurations pour la machine virtuelle et les ressources associées.

    Laissez le nombre de machines virtuelles défini sur `1` et modifiez la valeur des heures par mois sur `365`.

   ![Utilisez cet exemple de configurations ou fournissez au calculateur de prix appliqués Azure des détails sur vos besoins *réels* en ressources.](../images/1904.png)

7. Dans le volet **Disques de système d'exploitation gérés**, modifiez la configuration de stockage de la machine virtuelle par défaut.

    | Niveau | Taille du disque | Nombre de disques | Instantané | Transactions de stockage |
    | ---- | --------- | --------------- | -------- | -------------------- |
    | HDD Standard | S30 : 1 024 Gio | 1 | Désactivé | 10 000 |

   ![Screenshot of the managed OS Disks options area within the Azure pricing calculator estimate webpage. The highlighted tier type, disk size, number of disks, and number of storage transactions, options indicate how to specify a storage configuration for a vm within an Azure pricing calculator estimate.](../images/1905.png)

8. To add networking bandwidth to your estimate, go to the top of the Azure Pricing Calculator webpage. Click <bpt id="p1">**</bpt>Networking<ept id="p1">**</ept> in the product menu on the left, then click the <bpt id="p2">**</bpt>Bandwidth<ept id="p2">**</ept> tile. In the <bpt id="p1">**</bpt>Bandwidth added<ept id="p1">**</ept> message dialog, click <bpt id="p2">**</bpt>View<ept id="p2">**</ept>.

   ![Screenshot of the networking products area within the Azure pricing calculator webpage. The highlighted networking, add bandwidth, and view bandwidth, tiles indicate how to add and view details of a networking bandwidth configuration in an Azure pricing calculator estimate.](../images/1906.png)

9. Remplacez le texte **Votre estimation** et **Machines virtuelles** avec des noms plus descriptifs pour votre estimation du calculateur de prix appliqués Azure et votre configuration de machine virtuelle.

    | Région | Montant du transfert de données sortantes de la zone 1 |
    | ------ | -------------------------------------- |
    | Europe Nord | 50 Go |

   ![Cet exemple pas à pas utilise **Mon estimation de la calculatrice de prix** pour l’estimation, et **Machine virtuelle Windows** pour la configuration de la machine virtuelle.](../images/1907.png)

10. To add an Application Gateway, return to the top of the Azure Pricing Calculator webpage. In the <bpt id="p1">**</bpt>Networking<ept id="p1">**</ept> product menu, click the <bpt id="p2">**</bpt>Application Gateway<ept id="p2">**</ept> tile. In the <bpt id="p1">**</bpt>Application Gateway<ept id="p1">**</ept> message dialog, click <bpt id="p2">**</bpt>View<ept id="p2">**</ept>.

    ![Capture d’écran de la zone de configuration de la machine virtuelle dans la page Web d’estimation de la calculatrice de prix Azure.](../images/1908.png)

11. Le nom d’estimation et le nom de configuration de la machine virtuelle en surbrillance indiquent comment ajouter un nom d’estimation et un nom de configuration de la machine virtuelle à une estimation du calculateur de prix appliqués Azure.

    | Paramètres | Valeur |
    | -- | -- |
    | Région | **Europe Nord** |
    | Niveau | **De base** |
    | Taille | **Petite** |
    | Instances | **1** |  
    | Heures | **365** |
    | Données traitées | **50 Go** |
    | Zone 1 : Amérique du Nord, Europe | **50 Go**|

    ![Capture d’écran de la zone de configuration de l’Application Gateway dans la page Web d’estimation de la calculatrice de prix appliqués Azure.](../images/1909.png)


# <a name="task-2-review-the-pricing-estimate"></a>Tâche 2 : Revoir l’estimation des prix appliqués

Dans cette tâche, nous allons examiner les résultats de la calculatrice de prix appliqués Azure. 

1. Faites défiler vers le bas de la page Web de la calculatrice de prix appliqués Azure pour afficher le total du **Coût mensuel estimé**.

    <bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: Explore the various options available within the Azure Pricing Calculator. For example, this walkthrough requires you to update the currency to Euro.

2. Modifiez la devise en Euro, puis sélectionnez **Exporter** pour télécharger une copie de l’estimation pour une consultation hors ligne au format Microsoft Excel (`.xlsx`).

    ![Screenshot of the total estimated monthly costs within the Azure pricing calculator estimate webpage. The highlighted euro currency option indicates how to modify the currency used in an Azure pricing calculator estimate. The highlighted export option illustrates how to download a copy of an estimate for offline viewing.](../images/1910.png)

    ![Capture d’écran d’un exemple d’estimation de la calculatrice de prix Azure dans Microsoft Excel.](../images/1911.png)

Congratulations! You downloaded an estimate from the Azure Pricing Calculator.
