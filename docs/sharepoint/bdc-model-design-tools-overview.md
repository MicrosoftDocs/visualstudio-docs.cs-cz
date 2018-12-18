---
title: Přehled nástroje pro návrh modelu služby BDC | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Method_Details
- VS.SharePointTools.BDC.Explorer
- VS.SharePointTools.BDC.Diagram
dev_langs:
- VB
- CSharp
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6c5a799a245d2149161809977446d0c005dbe293
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49914499"
---
# <a name="bdc-model-design-tools-overview"></a>Přehled nástroje pro navrhování modelů služby BDC
  Obchodní Data připojení (BDC) model můžete navrhnout pomocí návrháře služby BDC **podrobnosti metody služby BDC** okně a **služby BDC Explorer**.  
  
 **Služby BDC Explorer** umožňuje procházet model, vyhledávání modelu a definování popisovače typu.  
  
## <a name="bdc-designer"></a>Návrháři služby BDC
 Návrháři služby BDC umožňuje definovat entity v modelu a vizuálně uspořádat jejich vztahy mezi sebou. Návrháři služby BDC umožňuje provádění následujících úloh:  
  
- Přidání entity do modelu.  
  
- Odeberte entity z modelu.  
  
- Definování vztahů mezi entitami.  
  
  Otevřít návrháři služby BDC, poklikejte na soubor modelu ve vašem projektu, nebo otevřete místní nabídku pro soubor modelu a klikněte na tlačítko **otevřete**. Přidání entity do modelu přetažením nebo zkopírováním **Entity** z **nástrojů** do návrháře. Chcete-li vytvořit přidružení mezi dvěma entitami, zvolte **přidružení** v ovládacím prvku **nástrojů**, zvolte první entitu a pak zvolte druhou entitu.  
  
## <a name="bdc-method-details-window"></a>Okno Podrobnosti metody služby BDC
 Použití **podrobnosti metody služby BDC** okno Definovat parametry, instance, a popisovače metody filtrů.  
  
 Můžete rychle vytvořit metody Finder, Specific Finder, Creator, Updater a Deleter v **podrobnosti metody služby BDC** okna. Při generování těchto metod, Visual Studio přidá metadata, například parametry, instance a popisovače typu metody. Můžete upravit tato metadata splňovat vaše konkrétní scénář.  
  
 Chcete-li otevřít **podrobnosti metody služby BDC** okna na řádku nabídek zvolte **zobrazení** > **ostatní Windows** > **podrobnosti metody služby BDC** .  
  
 Chcete-li zobrazit metody v **podrobnosti metody služby BDC** okna, vyberte entitu v Návrháři služby BDC. Metody vybrané entity se zobrazí v **podrobnosti metody služby BDC** okna. Pokud jste nezvolili entitu v Návrháři služby BDC **podrobnosti metody služby BDC** okně zobrazí žádné informace.  
  
 Rozbalit nebo sbalit uzly v **podrobnosti metody služby BDC** okno Definovat parametry, instance, a popisovače filtrů. Použití **služby BDC Explorer** k definování popisovače typu.  
  
## <a name="bdc-explorer"></a>Průzkumník modelu BDC
 **Služby BDC Explorer** zobrazuje prvky, které tvoří modelu. Otevřete **služby BDC Explorer**, na panelu nabídek zvolte **zobrazení** > **ostatní Windows** > **služby BDC Explorer**. Procházet model, rozbalte uzly v **služby BDC Explorer**. Každý uzel reprezentuje element v XML souboru modelu.  
  
 Při výběru uzly v **služby BDC Explorer**, vlastnosti každý uzel, který zvolíte se zobrazí v **vlastnosti** okna. Mnohé z těchto vlastností odpovídají atributy v souboru modelu. Model můžete vyhledat pomocí vyhledávacího pole v horní části **služby BDC Explorer**.  
  
> [!NOTE]  
>  **Služby BDC Explorer** nezobrazuje identifikátory, vlastní vlastnosti, lokalizované řetězce, přidružení skupin, akce, deskriptory filtrů, seznamy řízení akce a výchozí hodnoty parametrů.  
  
### <a name="define-type-descriptors"></a>Definování popisovače typu
 Použití **služby BDC Explorer** k definování popisovače typu. Průzkumník modelu BDC umožňuje definovat popisovač typu jednou a pak znovu použít tento typ popisovače jinde v modelu. K tomu, popisovač typu zkopírujte a vložte ji na všechny ostatní parametry nebo zadejte popisovač.  
  
> [!NOTE]  
>  Změny v původní popisovač typu neovlivňují kopie tento typ popisovače.  
  
 Další informace najdete v tématu [postupy: definování deskriptoru typu pro parametr](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
## <a name="see-also"></a>Viz také:
 [Postupy: vytvoření modelu služby BDC](../sharepoint/how-to-create-a-bdc-model.md)   
 [Postupy: Přidání entity do modelu](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Postupy: přidání vyhledávací metody](../sharepoint/how-to-add-a-finder-method.md)   
 [Postupy: Přidání specifické vyhledávací metody](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Postupy: přidání metody vytvoření](../sharepoint/how-to-add-a-creator-method.md)   
 [Postupy: přidání metody odstranění](../sharepoint/how-to-add-a-deleter-method.md)   
 [Postupy: Přidání aktualizační metody](../sharepoint/how-to-add-an-updater-method.md)   
 [Vytvoření přidružení mezi entitami](../sharepoint/creating-an-association-between-entities.md)   
 [Návod: Vytvoření externího seznamu ve službě SharePoint s použitím obchodních dat](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)   
 [Integrace obchodních dat do služby SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)   
 [Vytvoření modelu připojení obchodních dat](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Navrhování modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
 
