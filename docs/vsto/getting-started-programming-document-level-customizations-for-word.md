---
title: Začínáme programovat přizpůsobení na úrovni dokumentu pro Word
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word solutions in Visual Studio
- Word projects [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f4cf54dcdd08e7c44e8318973a3653dbe9c5ea1b
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585664"
---
# <a name="get-started-programming-document-level-customizations-for-word"></a>Začínáme programovat přizpůsobení na úrovni dokumentu pro Word
  Pokud jste právě začali vytvářet přizpůsobení na úrovni dokumentu pro systém Microsoft Office Word pomocí sady Visual Studio, je zde potřeba znát.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

## <a name="understand-how-document-level-customizations-for-word-work"></a>Vysvětlení způsobu, jakým přizpůsobení aplikace Word na úrovni dokumentu funguje
 Každé vlastní přizpůsobení aplikace Word je založeno na jednom dokumentu. Chcete-li začít s vlastním nastavením, koncový uživatel otevře dokument nebo vytvoří dokument ze šablony aplikace Word. Události v dokumentu, například přesunutí kurzoru do konkrétních oblastí nebo kliknutí na tlačítka a položky nabídky, mohou volat metody zpracování událostí v sestavení. Když je dokument uzavřený, funkce poskytované přizpůsobením už nebudou ve Wordu dostupné.

 Další informace najdete v tématu [Architektura přizpůsobení na úrovni dokumentu](../vsto/architecture-of-document-level-customizations.md).

## <a name="create-document-level-projects-for-word"></a>Vytváření projektů na úrovni dokumentu pro Word
 Chcete-li vytvořit přizpůsobení na úrovni dokumentu pro aplikaci Word, použijte šablonu dokumentu aplikace Word nebo šablony projektu aplikace Word v dialogovém okně **Nový projekt** . Tyto šablony obsahují požadované odkazy na sestavení a soubory projektu.

 Další informace o tom, jak vytvořit projekt na úrovni dokumentu pro aplikaci Word, naleznete v tématu [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Další informace o šablonách projektů naleznete v tématu [Přehled šablon projektů Office](../vsto/office-project-templates-overview.md).

## <a name="program-word-documents-by-using-host-items-host-controls"></a>Programové dokumenty aplikace Word pomocí hostitelských položek hostitelských ovládacích prvků
 *Hostitelské položky* a *hostitelské ovládací prvky* jsou třídy, které poskytují programovací model pro přizpůsobení na úrovni dokumentu.

 Položky hostitele poskytují vstupní bod pro váš kód a mohou sloužit také jako kontejnery pro ovládací prvky hostování a model Windows Forms ovládací prvky. V projektech na úrovni dokumentu pro aplikaci Word je položka hostitele reprezentována `ThisDocument` třídou.

 Hostitelské ovládací prvky jsou založeny na nativních objektech aplikace Word, jako jsou ovládací prvky obsahu, záložky a uzly XML. Ovládací prvky hostitele poskytují podobnou funkci nativním objektům aplikace Word, ale mají také nové události, podporu návrháře a schopnost datové vazby. Zobrazují se jako objekty první třídy v kódu projektu a v technologii IntelliSense, což usnadňuje odkazování na konkrétní objekty přímo v kódu bez nutnosti procházení objektového modelu aplikace Word.

 Další informace najdete v následujících tématech:

- [Přizpůsobení na úrovni dokumentu programu](../vsto/programming-document-level-customizations.md)

- [Automatizace Wordu pomocí rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)

- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)

## <a name="customize-the-user-interface-of-word"></a>Přizpůsobení uživatelského rozhraní Wordu
 Většina řešení systém Microsoft Office upravuje uživatelské rozhraní (UI) aplikace Office, aby uživatelům poskytovala nějaký způsob, jak s řešením pracovat. Existuje mnoho způsobů, jak můžete upravit uživatelské rozhraní aplikace Word pomocí přizpůsobení na úrovni dokumentu. Na pás karet můžete například přidat ovládací prvky a můžete zobrazit podokno akcí. Další informace najdete v tématu [přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md).

 Dokument, který je přidružen k projektu, můžete také otevřít přímo v aplikaci Visual Studio. Když je dokument otevřen v aplikaci Visual Studio, můžete upravit dokument pomocí uživatelského rozhraní aplikace Word. Dokument můžete také použít jako návrhovou plochu, která umožňuje přetáhnout ovládací prvky na ni. Další informace najdete v tématu [projekty Office v prostředí Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="bind-controls-to-data"></a>Svázání ovládacích prvků s daty
 Ovládací prvky obsahu a <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvek jsou v seznamu ovládacích prvků, které lze přetáhnout z okna **zdroje dat** . Přidávání ovládacích prvků obsahu a záložek tímto způsobem je automaticky váže ke zdroji dat, který jste nastavili pomocí okna. Bez psaní kódu můžete zobrazit data z databází, služeb a obchodních objektů. Další informace najdete v tématu [vázání dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md).

## <a name="next-steps"></a>Další kroky
 Další informace o tom, jak vytvořit přizpůsobení na úrovni dokumentu pro Word, najdete v tématu [Návod: vytvoření prvního přizpůsobení na úrovni dokumentu pro aplikaci Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md). Tento návod vás seznámí s nástroji pro vývoj pro Office v sadě Visual Studio a programovacím modelem pro přizpůsobení na úrovni dokumentu aplikace Word.

 Seznam témat, která vás provedou některými běžnými úkoly v projektech aplikace Word, najdete v tématu [běžné úlohy při programování pro systém Office](../vsto/common-tasks-in-office-programming.md).

## <a name="see-also"></a>Viz také
- [Postupy: vytváření projektů Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Přizpůsobení na úrovni dokumentu programu](../vsto/programming-document-level-customizations.md)
- [Řešení pro Word](../vsto/word-solutions.md)
- [Návod: vytvoření prvního přizpůsobení na úrovni dokumentu pro Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)
- [Návody pomocí aplikace Word](../vsto/walkthroughs-using-word.md)
- [Přehled modelu objektů aplikace Word](../vsto/word-object-model-overview.md)
- [Psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md)
