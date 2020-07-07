---
title: 'Postupy: Přidání souboru prostředků | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- resource files [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, resource files
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 657eb473adcff40a62d2fc9b09518ebe8135eeb4
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015184"
---
# <a name="how-to-add-a-resource-file"></a>Postupy: Přidání souboru prostředků
  Příkazy pro přidání souborů prostředků jsou v místní nabídce uzlu řešení a uzlů funkcí v Průzkumník řešení. Další informace najdete v tématu [Lokalizace řešení služby SharePoint](../sharepoint/localizing-sharepoint-solutions.md).

### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>Přidání souboru globálních prostředků do řešení služby SharePoint

1. V aplikaci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] otevřete řešení služby SharePoint.

2. V **Průzkumník řešení**zvolte uzel projektu služby SharePoint a poté v řádku nabídek zvolte možnost **projekt**  >  **Přidat novou položku**.

3. V dialogovém okně **Přidat novou položku** zvolte šablonu **souboru globálních zdrojů** a pak klikněte na tlačítko **Přidat** .

   > [!NOTE]
   > Šablona položky projekt soubor globálních prostředků se zobrazí pouze v případě, že je vybrána položka SharePointového projektu.

4. V dialogovém okně **Přidat prostředek** vyberte jazykovou verzi pro soubor prostředků, například angličtinu (USA).

    Tento krok přidá do vašeho řešení soubor globálních prostředků ve formátu Resource_x_**.** <em>jazyková verze</em><strong>.</strong> RESX, například, *Resource1. en-US. resx*.

5. Po otevření **editoru prostředků** v nástroji [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] přidejte prostředky do souboru prostředků.

### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>Přidání souboru prostředků funkce do funkce SharePointu

1. Pokud řešení služby SharePoint ještě není v nástroji otevřené [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , otevřete řešení.

2. V **Průzkumník řešení**otevřete místní nabídku pro název funkce pod uzlem **funkce** a pak zvolte **Přidat prostředek funkce**.

     Tento krok přidá soubor prostředků do funkce ve formátu _resourceFileName_**.** _culture_**. resx**, například, *Feature1. en-US. resx*.

3. Po otevření **editoru prostředků** v nástroji [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] přidejte prostředky do souboru prostředků.

## <a name="see-also"></a>Viz také:
- [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)
