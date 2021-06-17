---
title: 'Postupy: Vytvoření modelu služby BDC | Microsoft Docs'
description: Vytvořte model připojení obchodních dat (BDC) pomocí šablony Visual Studio pro tento druh položky a pak model přidejte do libovolného projektu SharePointu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fd5184f87cf3895e1519a91e6f7e6661702f1181
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112405"
---
# <a name="how-to-create-a-bdc-model"></a>Postupy: Vytvoření modelu služby BDC

  Model připojení obchodních dat (BDC) můžete vytvořit pomocí šablony pro tento druh položky a potom ho přidat do libovolného projektu SharePointu. Další informace najdete v tématu [Vytvoření modelu připojení obchodních dat.](../sharepoint/creating-a-business-data-connectivity-model.md) Další informace o tom, jak navrhnout model, najdete v tématu [Návrh modelu připojení obchodních dat.](../sharepoint/designing-a-business-data-connectivity-model.md)

## <a name="to-create-a-bdc-project"></a>Vytvoření projektu služby BDC

1. Na řádku nabídek zvolte File New Project **(Soubor**  >  **nový**  >  **projekt).**
::: moniker range="=vs-2017"
   > [!NOTE]
   > Pokud je vaše integrované vývojové prostředí (IDE) nastavené Visual Basic vývojového prostředí, zvolte File New Project **(Soubor**  >  **nového projektu).**

  Otevře **se dialogové okno** Nový projekt.

2. V části **Visual Basic** nebo **Visual C#** zvolte **Řešení pro Office/SharePoint** a **SharePoint.**

3. V **podokně Šablony** zvolte položku **SharePoint 2013 – Prázdný** projekt a pak zvolte tlačítko **OK.**

     Otevře **se Průvodce přizpůsobením služby SharePoint.**
::: moniker-end
::: moniker range=">=vs-2019"
2. V dialogovém **okně Vytvořit nový projekt** vyberte prázdný projekt *SharePointu** pro konkrétní verzi SharePointu, kterou jste nainstalovali. Pokud máte například instalaci SharePointu 2019, vyberte šablonu **SharePoint 2019 – prázdný** projekt.
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

3. Pokud chcete, změňte název projektu a pak zvolte **tlačítko** Vytvořit.

::: moniker-end
4. Na **stránce** Zadejte web a úroveň zabezpečení pro ladění zadejte adresu URL sharepointového  webu v místním počítači, zvolte tlačítko nasadit jako řešení farmy a pak zvolte **tlačítko** Dokončit.

     Model otestujte na webu služby SharePoint, který jste zadali.

    > [!IMPORTANT]
    > Projekt musíte nasadit jako řešení farmy, protože modely služby BDC podporují pouze řešení farmy.

     Vytvoří se prázdný projekt SharePointu.

5. V řádku nabídek zvolte Project Add New Item **(Projekt**  >  **– přidat novou položku).**

6. V **dialogovém okně Přidat** novou položku zvolte uzel **Office/SharePoint.**

7. V seznamu šablon služby SharePoint zvolte Model připojení obchodních dat **(pouze řešení farmy).**

8. Do **pole Název** zadejte název modelu služby BDC a pak zvolte **tlačítko** Přidat.

     Do **projektu se přidá položka Modelu** připojení obchodních dat. Ve výchozím nastavení se model zobrazí v návrháři služby BDC. Další informace najdete v tématu [Vytvoření modelu připojení obchodních dat.](../sharepoint/creating-a-business-data-connectivity-model.md)

## <a name="see-also"></a>Viz také

- [Vytvoření modelu připojení obchodních dat](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Postupy: Přidání existujícího souboru modelu služby BDC do projektu služby SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Postupy: Určení lokalizovaných názvů, vlastností a oprávnění pomocí souboru prostředků](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Postupy: Zahrnutí vlastního sestavení do funkce služby BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Integrace obchodních dat do SharePointu](../sharepoint/integrating-business-data-into-sharepoint.md)
