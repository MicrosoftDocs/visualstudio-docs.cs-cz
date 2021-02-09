---
title: Přehled nástrojů pro návrh modelu služby BDC | Microsoft Docs
description: Přečtěte si přehled návrhových nástrojů pro použití s modelem připojení obchodních dat (BDC). Seznamte se s návrhářem služby BDC, oknem podrobnosti metody služby BDC a průzkumníkem služby BDC.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Method_Details
- VS.SharePointTools.BDC.Explorer
- VS.SharePointTools.BDC.Diagram
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], method details
- Business Data Connectivity service [SharePoint development in Visual Studio], designer
- Business Data Connectivity service [SharePoint development in Visual Studio], method details
- BDC [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], designer
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b398d9c00caf3a4fa2ca58bafa3273673a305859
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851683"
---
# <a name="bdc-model-design-tools-overview"></a>Přehled nástrojů pro návrh modelu služby BDC
  Model služby připojení obchodních dat (BDC) můžete navrhovat pomocí návrháře služby BDC, okna **Podrobnosti metody služby BDC** a **Průzkumníka služby BDC**.

 **Průzkumník služby BDC** umožňuje procházet model, Hledat v něm model a definovat deskriptory typů.

## <a name="bdc-designer"></a>Návrhář služby BDC
 Návrhář služby BDC umožňuje definovat entity v modelu a vizuálně uspořádat jejich vztahy mezi sebou. Pomocí návrháře služby BDC můžete provádět následující úlohy:

- Přidejte do modelu entity.

- Odeberte entity z modelu.

- Definujte vztahy mezi entitami.

  Chcete-li otevřít návrháře služby BDC, dvakrát klikněte na soubor modelu v projektu nebo otevřete místní nabídku pro soubor modelu a pak zvolte možnost **otevřít**. Přidejte entitu do modelu přetažením nebo zkopírováním **entity** z **panelu nástrojů** do návrháře. Chcete-li vytvořit přidružení mezi dvěma entitami, zvolte ovládací prvek **přidružení** v **sadě nástrojů**, zvolte první entitu a pak zvolte druhou entitu.

## <a name="bdc-method-details-window"></a>Okno Podrobnosti metody služby BDC
 K definování parametrů, instancí a filtru popisovačů metody použijte okno **Podrobnosti metody služby BDC** .

 V okně **Podrobnosti metody služby BDC** můžete rychle vygenerovat metody Finder, konkrétního vyhledávače, autora, aktualizačního programu a odstranění. Když vygenerujete tyto metody, Visual Studio přidá do metody metadata, jako jsou parametry, instance a popisovače typů. Tato metadata můžete upravit tak, aby vyhovovala vašemu konkrétnímu scénáři.

 Chcete-li otevřít okno **Podrobnosti metody služby BDC** , vyberte v řádku nabídek možnost **Zobrazit**  >  **Další**  >  **Podrobnosti o metodě služby Windows BDC**.

 Pokud chcete zobrazit metody v okně **Podrobnosti metody služby BDC** , vyberte entitu v Návrháři služby BDC. Metody vybrané entity se zobrazí v okně **Podrobnosti metody služby BDC** . Pokud nevyberete entitu v Návrháři BDC, nezobrazí se v okně **Podrobnosti metody služby BDC** žádné informace.

 Rozbalení nebo sbalení uzlů v okně **Podrobnosti metody služby BDC** k definování parametrů, instancí a popisovačů filtru. K definování popisovačů typů použijte **Průzkumníka služby BDC** .

## <a name="bdc-explorer"></a>Průzkumník modelu BDC
 **Průzkumník služby BDC** zobrazuje prvky, které tvoří model. **Průzkumníka služby BDC** otevřete tak, že na řádku nabídek kliknete na **Zobrazit**  >  **ostatní Windows** v  >  **Průzkumníkovi služby** Windows. Pokud chcete model Procházet, rozbalte uzly v **Průzkumníkovi služby BDC**. Každý uzel představuje prvek v XML souboru modelu.

 Při výběru uzlů v **Průzkumníkovi služby BDC** se v okně **vlastnosti** zobrazí vlastnosti každého uzlu, který vyberete. Mnohé z těchto vlastností odpovídají atributům v souboru modelu. Model můžete vyhledat pomocí vyhledávacího pole v horní části **Průzkumníka služby BDC**.

> [!NOTE]
> **Průzkumník služby BDC** nezobrazuje identifikátory, vlastní vlastnosti, lokalizované řetězce, skupiny přidružení, akce, popisovače filtrů, seznamy řízení akcí a výchozí hodnoty parametrů.

### <a name="define-type-descriptors"></a>Definovat popisovače typů
 K definování popisovačů typů použijte **Průzkumníka služby BDC** . Průzkumník služby BDC umožňuje definovat jeden popisovač typu jednou a potom ho znovu použít jinde v modelu. Chcete-li to provést, zkopírujte popisovač typu a vložte jej na jiný parametr nebo popisovač typu.

> [!NOTE]
> Změny v původním deskriptoru typu neovlivňují kopie tohoto deskriptoru typu.

 Další informace naleznete v tématu [How to: define a Type deskriptor parametru](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

## <a name="see-also"></a>Viz také
- [Postupy: vytvoření modelu služby BDC](../sharepoint/how-to-create-a-bdc-model.md)
- [Postupy: Přidání entity do modelu](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Postupy: Přidání vyhledávací metody](../sharepoint/how-to-add-a-finder-method.md)
- [Postupy: Přidání konkrétní vyhledávací metody](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Postupy: Přidání metody autora](../sharepoint/how-to-add-a-creator-method.md)
- [Postupy: Přidání metody odstranění](../sharepoint/how-to-add-a-deleter-method.md)
- [Postupy: Přidání aktualizační metody](../sharepoint/how-to-add-an-updater-method.md)
- [Vytvoření přidružení mezi entitami](../sharepoint/creating-an-association-between-entities.md)
- [Návod: Vytvoření externího seznamu ve službě SharePoint s použitím obchodních dat](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)
- [Integrace obchodních dat do služby SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
- [Vytvoření modelu připojení obchodních dat](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Navrhování modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md)
