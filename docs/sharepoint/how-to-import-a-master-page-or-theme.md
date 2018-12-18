---
title: 'Postupy: Import stránky předlohy nebo motivu | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 116ab878d8591fb15bfbb319b2c1d79952fbd0e7
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120360"
---
# <a name="how-to-import-a-master-page-or-theme"></a>Postupy: Import stránky předlohy nebo motivu
  Můžete udělit stránky na webu služby SharePoint konzistentní vzhled vytvořením a použitím hlavní stránky a motivů. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] neposkytuje šablon pro tyto elementy, ale můžete je vytvořit v seznamu služby SharePoint a pak je importovat do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Další informace najdete v tématu [stavebním blokem: stránek a uživatelské rozhraní](http://go.microsoft.com/fwlink/?LinkID=182095) na webu společnosti Microsoft.  
  
### <a name="to-import-a-master-page-or-theme"></a>Import stránky předlohy nebo motivu  
  
1.  V [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], vytvoření nebo otevření projektu služby SharePoint.  
  
     Informace o tom, jak vytvořit projektu služby SharePoint, najdete v článku [SharePoint projekt a projekt šablon položek](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Na řádku nabídek zvolte **projektu** > **přidat novou položku**.  
  
3.  V **přidat novou položku** dialogové okno, rozbalte seznam **SharePoint** uzel a potom zvolte **2010** uzlu.  
  
4.  V seznamu šablon služby SharePoint, vyberte **modulu** šablony a pak zadejte název pro modul.  
  
     Modul obsahuje soubory (například stránky předlohy nebo motivu soubory) pro nasazení do umístění, které zadáte ve službě SharePoint.  
  
5.  V modulu, odstraňte výchozí soubor, který se nazývá *ukázka.txt*.  
  
6.  Vyberte uzel modulu.  
  
7.  Na řádku nabídek zvolte **projektu** > **přidat existující položku**a potom zvolte soubor předlohové stránky nebo motivu.  
  
     Hlavní stránkovací soubory .master rozšíření a soubory motivů .thmx rozšíření.  
  
8.  Pokud jste přidali stránku předlohy, změnit jeho **řešení konfliktů při nasazení** nastavení **automatické** ve vlastnostech modulu.  
  
    > [!NOTE]  
    >  Název hlavní stránky je stejný jako název existující stránky předlohy, která je označena jako výchozí stránky předlohy nebo vlastní stránky předlohy může dojít k chybám. Informace o řešení tohoto problému najdete v tématu [návod: Import vlastní stránky předlohy a stránka s bitovou kopií](../sharepoint/walkthrough-import-a-custom-master-page-and-site-page-with-an-image.md).  
  
9. V modulu, otevřete *Elements.xml*.  
  
     Je nutné aktualizovat *Elements.xml* souboru tak, aby odkazovaly na stránky předlohy nebo motivu, který jste přidali.  
  
10. Stránky předlohy nahradí existující značky modulu následující kód.  
  
    ```xml  
    <Module Name="[Module Name]" Url="_catalogs/masterpage">  
        <File Path="[Module Name]\[Master Page Name].master"   
          Url="[Master Page Name].master" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     Pro motiv nahradí existující značky modulu následující kód.  
  
    ```xml  
    <Module Name="[Module Name]" Url="_catalogs/theme"   
        <File Path="[Module Name]\[Theme Name].thmx" Url="[Theme     
          Name].thmx" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     Nezapomeňte nahradit zástupné hodnoty skutečné názvy modul a stránky předlohy nebo motivu.  
  
     Atribut `Type="GhostableInLibrary"` označuje, zda je položka přidána k databázi obsahu a `Url` atribut modulu určuje, kam chcete soubor uložit v databázi obsahu služby SharePoint.  
  
11. Chcete-li změnit rozsah nasazení pro stránku předlohy v **Průzkumníku řešení**, otevřete soubor funkce v Návrháři funkce a potom vyberte nový obor nasazení z **oboru** seznamu.  
  
     Hodnota **webové** znamená, že hlavní stránka se vztahuje pouze na web, který je aktuálně zadaný v projektu. Hodnota **lokality** znamená, že hlavní stránka se vztahuje na aktuální kolekci webů, která zahrnuje všechny podřízené lokality a webových. Nemusíte použít jiné hodnoty.  
  
    > [!NOTE]  
    >  Protože motivy použít pouze na úrovni kolekce webů, doporučujeme nemáte nastavit rozsah motiv na nic jiné než **lokality**. Pokud motiv se používá v podřízeném webu, může dojít k chybám.  
  
12. Na řádku nabídek zvolte **sestavení** > **nasadit řešení**.  
  
13. Pokud chcete ověřit, zda soubory byly nasazeny správně, otevřete web služby SharePoint, zvolte **Akce webu** nabídce zvolte **nastavení lokality** příkaz a potom vyberte buď **stránky předlohy**  odkaz nebo **motivy** odkaz.  
  
     Seznam stránky předlohy nebo motivy se zobrazí a obsahuje stránky předlohy nebo motivu, který jste importovali.  
  
## <a name="see-also"></a>Viz také:
 [Stránky předlohy](http://go.microsoft.com/fwlink/?LinkId=184955)   
 [Import položek z existující stránky SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Vytváření stránek pro službu SharePoint](../sharepoint/creating-pages-for-sharepoint.md)   
 [Vložené soubory v řešení pomocí modulů](../sharepoint/using-modules-to-include-files-in-the-solution.md)  
  
