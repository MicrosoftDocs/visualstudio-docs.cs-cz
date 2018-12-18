---
title: Začínáme s programováním přizpůsobení na úrovni dokumentu pro Excel
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel solutions in Visual Studio
- Excel projects [Office development in Visual Studio], getting started
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 50c18564604a15265b61b17f74484f959b18b131
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2018
ms.locfileid: "34448425"
---
# <a name="get-started-programming-document-level-customizations-for-excel"></a>Začínáme s programováním přizpůsobení na úrovni dokumentu pro Excel
  Pokud jste začali vytváření přizpůsobení na úrovni dokumentu pro aplikaci Microsoft Office Excel pomocí sady Visual Studio, zde je, co potřebujete vědět.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
## <a name="understand-how-document-level-customizations-for-excel-work"></a>Pochopení přizpůsobení pro aplikaci Excel pracovní jak dokument úrovni  
 Přizpůsobení na úrovni dokumentu pro Excel je založena kolem jednoho sešitu. Pokud chcete začít používat přizpůsobení, koncový uživatel otevře sešit nebo vytvoří sešit z šablony aplikace Excel. Události v sešitu, například zadáním v buňkách nebo kliknutím na tlačítka a položky nabídky, můžete volat metody zpracování událostí v sestavení. Když se sešit zavře, funkce poskytované službou přizpůsobení již nejsou k dispozici v aplikaci Excel, pouze v dokumentu, který je obsažen.  
  
 Další informace najdete v tématu [architektura přizpůsobení na úrovni dokumentu](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="create-document-level-projects-for-excel"></a>Vytvořit projekty na úrovni dokumentu pro Excel  
 K vytvoření přizpůsobení na úrovni dokumentu pro Excel, použijte sešitu aplikace Excel nebo Excel šablona projektu šablony **nový projekt** dialogové okno. Tyto šablony zahrnout požadované odkazy na sestavení a soubory projektu.  
  
 Další informace o tom, jak vytvořit projekt na úrovni dokumentu pro Excel najdete v tématu [postupy: vytvoření Office projekty v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Další informace o šablonách projektů najdete v tématu [Přehled šablon projektů Microsoft Office](../vsto/office-project-templates-overview.md).  
  
## <a name="program-excel-workbooks-by-using-host-items-and-host-controls"></a>Program sešitů aplikace Excel pomocí hostitelských položek a hostitelských ovládacích prvků  
 *Hostování položky* a *hostování ovládacích prvků* jsou třídy, které poskytují programovací model pro úpravy na úrovni dokumentů vytvořené pomocí sady Visual Studio.  
  
 Hostitelské položky vytvořit vstupní bod pro kód a mohou chovat i jako kontejnery pro hostitele a ovládacích prvků Windows Forms. V projekty na úrovni dokumentu pro Excel, jsou reprezentovány tyto položky hostitele `ThisWorkbook`, `Sheet1`, `Sheet2`, a `Sheet3` třídy.  
  
 Hostitelské ovládací prvky jsou založené na nativní objekty aplikace Excel, například seznam objektů a rozsahy adres. Hostitelské ovládací prvky poskytují podobné funkce jako nativních objektů aplikace Excel, ale mají také nové události, podpora návrháře a funkce vazby dat. Zobrazí se jako první třídy objekty ve vašem projektu kódu a technologii IntelliSense, která usnadňuje odkazovat na konkrétní objekty přímo v kódu bez nutnosti přejděte model objektů aplikace Excel.  
  
 Další informace naleznete v následujících tématech:  
  
-   [Úpravy na úrovni dokumentů programu](../vsto/programming-document-level-customizations.md)  
  
-   [Automatizace aplikace Excel s použitím rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)  
  
-   [Přehled ovládacích prvků hostitele a hostitelské položky](../vsto/host-items-and-host-controls-overview.md)  
  
## <a name="customize-the-user-interface-of-excel"></a>Přizpůsobení uživatelského rozhraní aplikace Excel  
 Většina řešení Microsoft Office upravit uživatelské rozhraní (UI) aplikace Office a poskytují některé způsob uživatelům interakci s řešením. Existuje mnoho způsobů, ve kterých můžete upravit uživatelského rozhraní aplikace Excel pomocí přizpůsobení na úrovni dokumentu. Například můžete přidat ovládací prvky na pásu karet, nebo můžete zobrazit podokna akcí. Další informace najdete v tématu [přizpůsobení uživatelského rozhraní Office](../vsto/office-ui-customization.md).  
  
 Můžete také otevřít sešit, který je přidružen projektu přímo v sadě Visual Studio. Když je sešit otevřít v sadě Visual Studio, můžete upravit sešit pomocí uživatelského rozhraní aplikace Excel. Sešit můžete také použít jako návrhovou plochu, která umožňuje přetažením ovládacích prvků na listech. Další informace najdete v tématu [projektech pro systém Office v sadě Visual Studio prostředí](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="use-data-binding"></a>Použít datovou vazbu  
 Hostitelské ovládací prvky jsou také v seznamu ovládacích prvků, které můžete přetáhnout z **zdroje dat** okno. Přidání ovládacích prvků hostitele v tomto způsobem automaticky je váže ke zdroji dat, které jste nastavili pomocí okna. Bez psaní kódu, můžete zobrazit data z databáze, webové služby a obchodní objekty. Další informace najdete v tématu [vazby dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
## <a name="next-steps"></a>Další kroky  
 Informace o vytváření přizpůsobení na úrovni dokumentu pro Excel, najdete v tématu [návod: vytvoření prvního přizpůsobení na úrovni dokumentu pro Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md). Tento názorný postup vás seznámí s vývojových nástrojů Office v sadě Visual Studio a programovací model pro přizpůsobení na úrovni dokumentu aplikace Excel.  
  
 Seznam témat, která vás provede procesem některé běžné úlohy v projekty aplikace Excel najdete v tématu [běžné úlohy při programování pro Office](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: vytváření projektů Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Úpravy na úrovni dokumentů programu](../vsto/programming-document-level-customizations.md)   
 [Řešení pro aplikaci Excel](../vsto/excel-solutions.md)   
 [Návod: Vytvoření prvního přizpůsobení na úrovni dokumentu pro Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [Návody pomocí aplikace Excel](../vsto/walkthroughs-using-excel.md)   
 [Přehled modelu objektů aplikace Excel](../vsto/excel-object-model-overview.md)   
 [Psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md)  
  
  