---
title: 'Postupy: Import stránky předlohy nebo motivu | Microsoft Docs'
description: Vytvořte šablony pro hlavní stránky a motivy v SharePoint designeru a pak je importujte do sady Visual Studio, aby stránky na SharePointovém webu měly konzistentní vzhled.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 331ae3964de40e6590345aadae59776fe37f467a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913669"
---
# <a name="how-to-import-a-master-page-or-theme"></a>Postupy: Import stránky předlohy nebo motivu
  Stránky na SharePointovém webu můžete poskytovat konzistentní vzhled vytvořením a použitím stránek předloh a motivů. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] neposkytuje šablony pro tyto prvky, ale můžete je vytvořit v aplikaci SharePoint Designer a pak je importovat do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Další informace naleznete v tématu [stavební blok: stránky a uživatelské rozhraní](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14)) na webu společnosti Microsoft.

### <a name="to-import-a-master-page-or-theme"></a>Import stránky předlohy nebo motivu

1. V [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] portálu vytvořte nebo otevřete projekt služby SharePoint.

     Informace o tom, jak vytvořit projekt služby SharePoint, naleznete v tématu [šablony projektů a položek projektu služby SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. Na řádku nabídek klikněte na položku **projekt**  >  **Přidat novou položku**.

3. V dialogovém okně **Přidat novou položku** rozbalte uzel **SharePoint** a pak zvolte uzel **2010** .

4. V seznamu šablon služby SharePoint zvolte šablonu **modulu** a pak zadejte název modulu.

     Modul obsahuje soubory (například stránky předlohy nebo soubory motivů) pro nasazení do umístění, které zadáte na SharePointu.

5. V modulu odstraňte výchozí soubor s názvem *Sample.txt*.

6. Vyberte uzel modul.

7. V panelu nabídek zvolte **projekt**  >  **Přidat existující položku** a pak zvolte stránku předlohy nebo soubor motivu.

     Soubory stránky předlohy mají příponu. Master a soubory motivů mají příponu. thmx.

8. Pokud jste přidali hlavní stránku, změňte nastavení **řešení konfliktů nasazení** na hodnotu **automaticky** ve vlastnostech modulu.

    > [!NOTE]
    > K chybám může dojít, pokud je název stránky předlohy stejný jako název existující stránky předlohy, která je označena jako výchozí stránka předlohy nebo vlastní stránka předlohy. Informace o tom, jak tento problém vyřešit, najdete v tématu [Návod: import vlastní stránky předlohy a stránky webu s obrázkem](../sharepoint/walkthrough-import-a-custom-master-page-and-site-page-with-an-image.md).

9. V modulu otevřete *Elements.xml*.

     Je nutné aktualizovat soubor *Elements.xml* , aby odkazoval na stránku předlohy nebo motiv, který jste přidali.

10. Pro stránku předlohy nahraďte existující značku modulu následujícím kódem.

    ```xml
    <Module Name="[Module Name]" Url="_catalogs/masterpage">
        <File Path="[Module Name]\[Master Page Name].master"
          Url="[Master Page Name].master" Type="GhostableInLibrary" />
    </Module>
    ```

     Pro motiv nahraďte existující značky modulu následujícím kódem.

    ```xml
    <Module Name="[Module Name]" Url="_catalogs/theme"
        <File Path="[Module Name]\[Theme Name].thmx" Url="[Theme
          Name].thmx" Type="GhostableInLibrary" />
    </Module>
    ```

     Nezapomeňte nahradit hodnoty zástupných znaků skutečnými názvy modulu a stránky předlohy nebo motivu.

     Atribut `Type="GhostableInLibrary"` označuje, že položka je přidána do databáze obsahu, a `Url` atribut Module určuje, kam uložit soubor v databázi obsahu služby SharePoint.

11. Chcete-li změnit rozsah nasazení pro stránku předlohy, v **Průzkumník řešení** otevřete soubor funkce v Návrháři funkcí a pak zvolte nový obor nasazení ze seznamu **Rozsah** .

     Hodnota **Web** znamená, že se stránka předlohy vztahuje pouze na web, který je aktuálně zadaný v projektu. Hodnota **webu** znamená, že se stránka předlohy vztahuje na aktuální kolekci webů, která zahrnuje všechny podřízené weby a kořenový Web. Ostatní hodnoty se nevztahují.

    > [!NOTE]
    > Vzhledem k tomu, že se motivy vztahují pouze na úroveň kolekce webů, doporučujeme nenastavit rozsah motivu na jinou hodnotu než **Web**. K chybám může dojít, pokud se motiv používá v podřízené lokalitě.

12. Na panelu nabídek vyberte **sestavení**  >  **nasadit řešení**.

13. Chcete-li ověřit, zda byly soubory správně nasazeny, otevřete web služby SharePoint, zvolte nabídku **Akce webu** , zvolte příkaz **nastavení lokality** a pak zvolte buď odkaz **hlavní stránky** nebo odkaz **motivy** .

     Zobrazí se seznam stránek předlohy nebo motivů, které obsahují buď vzorovou stránku, nebo motiv, který jste naimportovali.

## <a name="see-also"></a>Viz také
- [Stránky předlohy](/previous-versions/office/developer/sharepoint-2010/ms443795(v=office.14))
- [Import položek z existujícího webu služby SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Vytváření stránek pro SharePoint](../sharepoint/creating-pages-for-sharepoint.md)
- [Zahrnutí souborů do řešení pomocí modulů](../sharepoint/using-modules-to-include-files-in-the-solution.md)
