---
title: 'Postupy: zahrnutí souborů pomocí modulu | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5c5152221e5e58504ba84e0ad0f31511b4d93aa0
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120162"
---
# <a name="how-to-include-files-by-using-a-module"></a>Postupy: zahrnutí souborů pomocí modulu
  *Moduly* (Nezaměňovat s [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] moduly) jsou kontejnery, které vám umožní nasadit soubory, jako jsou hlavní stránky ASPX, textové soubory nebo bitové kopie do služby SharePoint.  
  
 Můžete nasazovat soubor do knihovny dokumentů nebo jako normální soubor (například default.aspx) mimo knihovnu dokumentů. Chcete-li přidat soubor do knihovny dokumentů, zadejte `Type="GhostableInLibrary"` jako atribut v **souboru** elementu. Toto nastavení dá pokyn služby SharePoint k vytvoření položky seznamu můžete využívat souboru při jejím přidání do knihovny. K nasazení souboru mimo knihovnu dokumentů, buď zadejte `Type="Ghostable"` nebo právě vynechejte **typ** atribut.  
  
## <a name="add-a-module-to-a-sharepoint-solution"></a>Přidat modul do řešení služby SharePoint  
  
#### <a name="to-add-a-module"></a>Chcete-li přidat modul  
  
1.  V [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], otevřete nebo vytvoření projektu služby SharePoint.  
  
     Další informace najdete v tématu [SharePoint projekt a projekt šablon položek](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  V **Průzkumníku řešení**, vyberte uzel projektu a potom na řádku nabídek zvolte **projektu** > **přidat novou položku**.  
  
     **Přidat novou položku** otevře se dialogové okno.  
  
3.  V seznamu šablon služby SharePoint, vyberte **modulu** šablony a potom zvolte **přidat** tlačítko.  
  
     Tento krok vytvoří uzel v projektu s názvem modul 1.  
  
4.  V modul 1, odstraňte *ukázka.txt* souboru.  
  
     Ukázka.txt je zahrnuta ve všech modulech nové například účely a není potřeba. (Všimněte si, že soubor odstranit také odebere jeho položku z modulu *Elements.xml* souboru.)  
  
5.  Pokud chcete, aby vaše soubory nasadit do konkrétní složky struktury ve službě SharePoint, vytvořte tyto složky pod modul 1 v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] výběrem uzlu modul 1 a potom v nabídce panelu Výběr **projektu**, **nový Složka**.  
  
6.  Vyberte složku, ve které chcete přidat soubor a potom na řádku nabídek zvolte **projektu**, **přidat existující položku**.  
  
7.  Vyberte jeden nebo více souborů, které chcete nasadit do služby SharePoint a pak vyberte **přidat** tlačítko.  
  
     Když přidáte do projektu soubor, položku pro něj se automaticky přidá do souboru Elements.xml modulu. Při nasazení projektu, soubory se zkopírují na server služby SharePoint, vzhledem k projektu kořenový adresář, který je určený **soubor** elementu **Url** atributů, jako například `Url="Module1/New Folder/SomeFile.doc`. Pokud chcete změnit umístění nasazení pro soubor, buď ji přesunout do jiné složky v **Průzkumníku řešení** nebo změnit jeho **Url** nastavení.  
  
8.  Pro všechny soubory, které se má zobrazit v knihovně dokumentů, připojte `Type="GhostableInLibrary"` atribut jejich vstupu v *Elements.xml*. Například  
  
    ```xml  
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />  
    ```  
  
9. Nasazení projektu.  
  
     Zkopírujte soubory do určitých umístění ve službě SharePoint.  
  
## <a name="see-also"></a>Viz také:
 [Zabalení a nasazení řešení služby SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
