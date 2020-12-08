---
title: 'Excel: Začněte programovat přizpůsobení na úrovni dokumentu.'
description: Zjistěte, co potřebujete vědět, abyste mohli začít vytvářet přizpůsobení na úrovni dokumentu pro systém Microsoft Office Excel pomocí sady Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel solutions in Visual Studio
- Excel projects [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1fb048fd015126e5438a007be1950cddffbac9e1
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846035"
---
# <a name="get-started-programming-document-level-customizations-for-excel"></a>Začínáme s programováním přizpůsobení na úrovni dokumentu pro Excel
  Pokud jste právě začali vytvářet přizpůsobení na úrovni dokumentu pro systém Microsoft Office Excel pomocí sady Visual Studio, je zde potřeba znát.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="understand-how-document-level-customizations-for-excel-work"></a>Vysvětlení fungování přizpůsobení na úrovni dokumentu pro aplikaci Excel
 Přizpůsobení na úrovni dokumentu v aplikaci Excel je založeno na jednom sešitu. Chcete-li začít s vlastním nastavením, koncový uživatel otevře sešit nebo vytvoří sešit ze šablony aplikace Excel. Události v sešitu, například psaní v buňkách nebo kliknutí na tlačítka a položky nabídky, mohou volat metody zpracování událostí v sestavení. Když je sešit uzavřen, funkce poskytované přizpůsobením již nejsou v aplikaci Excel k dispozici, pouze v dokumentu, který je obsahuje.

 Další informace najdete v tématu [Architektura přizpůsobení na úrovni dokumentu](../vsto/architecture-of-document-level-customizations.md).

## <a name="create-document-level-projects-for-excel"></a>Vytváření projektů na úrovni dokumentu v Excelu
 Chcete-li vytvořit přizpůsobení na úrovni dokumentu pro aplikaci Excel, použijte excelový sešit nebo šablonu projektu šablony aplikace Excel v dialogovém okně **Nový projekt** . Tyto šablony obsahují požadované odkazy na sestavení a soubory projektu.

 Další informace o tom, jak vytvořit projekt na úrovni dokumentu pro aplikaci Excel, naleznete v tématu [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Další informace o šablonách projektů naleznete v tématu [Přehled šablon projektů Office](../vsto/office-project-templates-overview.md).

## <a name="program-excel-workbooks-by-using-host-items-and-host-controls"></a>Program excelové sešity pomocí hostitelských položek a hostitelských ovládacích prvků
 *Hostitelské položky* a *hostitelské ovládací prvky* jsou třídy, které poskytují programovací model pro přizpůsobení na úrovni dokumentu vytvořené pomocí sady Visual Studio.

 Položky hostitele poskytují vstupní bod pro váš kód a mohou sloužit také jako kontejnery pro ovládací prvky hostování a model Windows Forms ovládací prvky. V projektech na úrovni dokumentu v aplikaci Excel jsou tyto hostitelské položky zastoupeny `ThisWorkbook` `Sheet1` `Sheet2` třídami,, a `Sheet3` .

 Hostitelské ovládací prvky jsou založené na nativních objektech aplikace Excel, jako jsou například objekty a rozsahy seznamu. Ovládací prvky hostitele poskytují podobnou funkci nativním objektům aplikace Excel, ale mají také nové události, podporu návrháře a schopnost datových vazeb. Zobrazují se jako objekty první třídy v kódu projektu a v technologii IntelliSense, což usnadňuje odkazování na konkrétní objekty přímo v kódu, aniž by bylo nutné procházet model objektu aplikace Excel.

 Další informace najdete v následujících tématech:

- [Přizpůsobení na úrovni dokumentu programu](../vsto/programming-document-level-customizations.md)

- [Automatizace Excelu pomocí rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)

- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)

## <a name="customize-the-user-interface-of-excel"></a>Přizpůsobení uživatelského rozhraní Excelu
 Většina řešení systém Microsoft Office upravuje uživatelské rozhraní (UI) aplikace Office, aby uživatelům poskytovala nějaký způsob, jak s řešením pracovat. Existuje mnoho způsobů, jak můžete upravit uživatelské rozhraní aplikace Excel pomocí přizpůsobení na úrovni dokumentu. Můžete například přidat ovládací prvky na pás karet nebo můžete zobrazit podokno akcí. Další informace najdete v tématu [přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md).

 Sešit, který je přidružený k projektu, můžete také otevřít přímo v aplikaci Visual Studio. Když je sešit otevřený v aplikaci Visual Studio, můžete ho upravit pomocí uživatelského rozhraní Excelu. Sešit můžete také použít jako návrhovou plochu, která umožňuje přetahovat ovládací prvky na listy. Další informace najdete v tématu [projekty Office v prostředí Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="use-data-binding"></a>Použití datové vazby
 Ovládací prvky hostitele jsou také v seznamu ovládacích prvků, které lze přetáhnout z okna **zdroje dat** . Přidání hostitelských ovládacích prvků tímto způsobem je automaticky sváže se zdrojem dat, který jste nastavili pomocí okna. Bez psaní kódu můžete zobrazit data z databází, webových služeb a obchodních objektů. Další informace najdete v tématu [vázání dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md).

## <a name="next-steps"></a>Další kroky
 Další informace o tom, jak vytvořit přizpůsobení na úrovni dokumentu pro aplikaci Excel, najdete v tématu [Návod: vytvoření prvního přizpůsobení na úrovni dokumentu pro aplikaci Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md). V tomto návodu se seznámíte s nástroji pro vývoj pro Office v sadě Visual Studio a programovacím modelem pro přizpůsobení na úrovni dokumentu v Excelu.

 Seznam témat, která vás provedou některými běžnými úkoly v projektech aplikace Excel, najdete v tématu [běžné úlohy při programování pro systém Office](../vsto/common-tasks-in-office-programming.md).

## <a name="see-also"></a>Viz také
- [Postupy: vytváření projektů Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Přizpůsobení na úrovni dokumentu programu](../vsto/programming-document-level-customizations.md)
- [Řešení pro Excel](../vsto/excel-solutions.md)
- [Návod: vytvoření prvního přizpůsobení na úrovni dokumentu pro Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)
- [Návody pomocí Excelu](../vsto/walkthroughs-using-excel.md)
- [Přehled modelu objektů aplikace Excel](../vsto/excel-object-model-overview.md)
- [Psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md)
