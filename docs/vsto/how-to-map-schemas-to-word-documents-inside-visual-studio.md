---
title: 'Postupy: mapování schémat na dokumenty aplikace Word v rámci sady Visual Studio'
description: Přečtěte si, jak můžete mapovat schéma XML na systém Microsoft Office wordový dokument, když je dokument otevřený v aplikaci Visual Studio.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Word documents
- Word [Office development in Visual Studio], mapping XML schemas
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 082d5fe4fbcc7f66709770c16d3c9a1a2811e60d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900929"
---
# <a name="how-to-map-schemas-to-word-documents-inside-visual-studio"></a>Postupy: mapování schémat na dokumenty aplikace Word v rámci sady Visual Studio
  **Důležité** informace Informace uvedené v tomto tématu týkající se Microsoft Wordu se poskytují výhradně pro zvýhodnění a použití jednotlivců a organizací, kteří se nacházejí mimo USA a její oblasti nebo kteří používají nebo vyvíjí programy, na kterých běží, od společnosti Microsoft Word, které byly licencované od společnosti Microsoft před lednem 2010, když společnost Microsoft odebrala implementaci konkrétních funkcí souvisejících s vlastním kódem XML z aplikace Microsoft Word. Tyto informace týkající se Microsoft Wordu nemusí číst ani používat jednotlivci nebo organizace v USA nebo na jejích oblastech, kteří používají, nebo vyvíjet programy, na kterých běží, od společnosti Microsoft Word, které byly licencované od Microsoftu po 10. ledna 2010. Tyto produkty se nebudou chovat stejně jako produkty licencované před tímto datem nebo zakoupené a licencované pro použití mimo USA.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Schéma XML lze namapovat na dokument, zatímco je dokument otevřen v aplikaci Visual Studio. Použijete stejné systém Microsoft Office nástroje pro Word, které použijete, když je dokument otevřen mimo sadu Visual Studio. Projekt sady Office vytvoří stejné objekty bez ohledu na to, zda schéma namapujete do dokumentu před nebo po vytvoření řešení pro aplikace Word.

## <a name="to-map-an-xml-schema-to-a-word-document-in-visual-studio"></a>Mapování schématu XML k dokumentu aplikace Word v aplikaci Visual Studio

1. Otevřete dokument aplikace Word nebo šablonu projektu v aplikaci Visual Studio.

2. Kliknutím v dokumentu přesuňte fokus do návrháře.

3. Na pásu karet klikněte na kartu **vývojář** .

    > [!NOTE]
    > Pokud karta **vývojář** není zobrazená, musíte ji nejdřív zobrazit. Další informace najdete v tématu [Postup: zobrazení karty Vývojář na pásu karet](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. Ve skupině **XML** klikněte na **schéma**.

     Otevře se dialogové okno **šablony a doplňky** .

5. Klikněte na kartu **schéma XML** .

6. Klikněte na **Přidat schéma**.

     Otevře se dialogové okno **Přidat schéma** .

7. Vyhledejte soubor schématu, vyberte jej a klikněte na tlačítko **otevřít**.

     Otevře se dialogové okno **Nastavení schématu** .

8. Přiřaďte alias nebo kliknutím na tlačítko **OK** přidejte schéma bez aliasu.

9. Klikněte na **OK**.

     Otevře se okno **struktury XML** .

10. Přetáhněte prvky z okna **struktury XML** na místa v dokumentu, kde chcete vytvořit odpovídající ovládací prvky.

## <a name="see-also"></a>Viz také
- [Postupy: mapování schémat na listy v rámci sady Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [Schémata XML a data v přizpůsobeních na úrovni dokumentu](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
