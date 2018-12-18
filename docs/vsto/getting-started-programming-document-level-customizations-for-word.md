---
title: Začínáme s programováním přizpůsobení na úrovni dokumentu pro Word
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word solutions in Visual Studio
- Word projects [Office development in Visual Studio], getting started
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a5bed5c08e15861840a34960d186b408fb86085d
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2018
ms.locfileid: "34448851"
---
# <a name="get-started-programming-document-level-customizations-for-word"></a>Začínáme s programováním přizpůsobení na úrovni dokumentu pro Word
  Pokud jste začali vytváření úpravy na úrovni dokumentů pro Microsoft Office Word pomocí sady Visual Studio, zde je, co potřebujete vědět.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
## <a name="understand-how-document-level-customizations-for-word-work"></a>Pochopit, jak dokument úrovni přizpůsobení pro pracovní aplikace Word  
 Každý Word přizpůsobení, které vytvoříte vychází kolem jednotlivý dokument. Pokud chcete začít používat přizpůsobení, koncový uživatel otevře dokument nebo vytvoří dokument z šablony aplikace Word. Události v dokumentu, například přesun kurzoru do určitých oblastí nebo kliknutím na tlačítko tlačítka a položky nabídky, můžete volat metody zpracování událostí v sestavení. Při zavření v dokumentu, funkce poskytované službou přizpůsobení již nejsou k dispozici v aplikaci Word.  
  
 Další informace najdete v tématu [architektura přizpůsobení na úrovni dokumentu](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="create-document-level-projects-for-word"></a>Vytvoření projekty na úrovni dokumentu pro Word  
 Chcete-li vytvořit přizpůsobení na úrovni dokumentu ve Wordu, použijte šablona projektu dokumentu aplikace Word nebo šablony aplikace Word v **nový projekt** dialogové okno. Tyto šablony zahrnout požadované odkazy na sestavení a soubory projektu.  
  
 Další informace o tom, jak vytvořit projekt na úrovni dokumentu ve Wordu najdete v tématu [postupy: vytvoření Office projekty v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Další informace o šablonách projektů najdete v tématu [Přehled šablon projektů Microsoft Office](../vsto/office-project-templates-overview.md).  
  
## <a name="program-word-documents-by-using-host-items-host-controls"></a>Dokumenty aplikace Word program pomocí hostitele položky hostitelské ovládací prvky  
 *Hostování položky* a *hostování ovládacích prvků* jsou třídy, které poskytují programovací model pro úpravy na úrovni dokumentů.  
  
 Hostitelské položky vytvořit vstupní bod pro kód a mohou chovat i jako kontejnery pro hostitele a ovládacích prvků Windows Forms. V projektech na úrovni dokumentu ve Wordu, je reprezentována položka hostitele `ThisDocument` třídy.  
  
 Hostitelské ovládací prvky jsou založené na nativní aplikace Word objekty, například ovládací prvky obsahu, záložky a z uzlů XML. Hostitelské ovládací prvky poskytují podobné funkce jako nativních objektů aplikace Word, ale mají také nové události, podpora návrháře a schopností datové vazby. Zobrazí se jako první třídy objekty ve vašem projektu kódu a technologii IntelliSense, která usnadňuje odkazovat na konkrétní objekty přímo v kódu bez nutnosti přejděte model objektů aplikace Word.  
  
 Další informace naleznete v následujících tématech:  
  
-   [Úpravy na úrovni dokumentů programu](../vsto/programming-document-level-customizations.md)  
  
-   [Automatizace aplikace Word s použitím rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)  
  
-   [Přehled ovládacích prvků hostitele a hostitelské položky](../vsto/host-items-and-host-controls-overview.md)  
  
## <a name="customize-the-user-interface-of-word"></a>Přizpůsobení uživatelského rozhraní aplikace Word  
 Většina řešení Microsoft Office upravit uživatelské rozhraní (UI) aplikace Office a poskytují některé způsob uživatelům interakci s řešením. Existuje mnoho způsobů, ve kterých můžete upravit pomocí přizpůsobení na úrovni dokumentu Word uživatelského rozhraní. Například můžete přidat ovládací prvky na pásu karet, a můžete zobrazit podokna akcí. Další informace najdete v tématu [přizpůsobení uživatelského rozhraní Office](../vsto/office-ui-customization.md).  
  
 Můžete také otevřít dokument, který je přidružen projektu přímo v sadě Visual Studio. Pokud dokument otevřít v sadě Visual Studio, můžete upravit dokumentu pomocí uživatelského rozhraní aplikace Word. Můžete taky v dokumentu jako návrhovou plochu, která umožňuje přetažením ovládacích prvků. Další informace najdete v tématu [projektech pro systém Office v sadě Visual Studio prostředí](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="bind-controls-to-data"></a>Vytvoření vazby ovládacích prvků k datům  
 Ovládací prvky obsahu a <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvek se v seznamu ovládacích prvků, které můžete přetáhnout z **zdroje dat** okno. Přidání obsahu ovládací prvky a záložky v tomto způsobem automaticky je váže ke zdroji dat, které jste nastavili pomocí okna. Bez psaní kódu, můžete zobrazit data z databáze, služeb a obchodní objekty. Další informace najdete v tématu [vazby dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
## <a name="next-steps"></a>Další kroky  
 Informace o vytváření přizpůsobení na úrovni dokumentu ve Wordu, najdete v tématu [návod: vytvoření prvního přizpůsobení na úrovni dokumentu ve Wordu](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md). Tento názorný postup vás seznámí s vývojových nástrojů Office v sadě Visual Studio a programovací model pro úpravy na úrovni dokumentů aplikace Word.  
  
 Seznam témat, která vás provede procesem některé běžné úlohy v projekty aplikace Word najdete v tématu [běžné úlohy při programování pro Office](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: vytváření projektů Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Úpravy na úrovni dokumentů programu](../vsto/programming-document-level-customizations.md)   
 [Řešení aplikace Word](../vsto/word-solutions.md)   
 [Návod: Vytvoření prvního přizpůsobení na úrovni dokumentu pro Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)   
 [Návody pro aplikaci Word](../vsto/walkthroughs-using-word.md)   
 [Přehled modelu objektů aplikace Word](../vsto/word-object-model-overview.md)   
 [Psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md)  
  
  