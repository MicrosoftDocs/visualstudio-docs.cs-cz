---
title: 'Postupy: Přidání ovládacích prvků XMLNode do dokumentů aplikace Word'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control, adding to documents
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bd0429374b175da3260c3605f39c90cf2dffb841
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544895"
---
# <a name="how-to-add-xmlnode-controls-to-word-documents"></a>Postupy: Přidání ovládacích prvků XMLNode do dokumentů aplikace Word
  **Důležité** informace Informace uvedené v tomto tématu týkající se Microsoft Wordu se poskytují výhradně pro zvýhodnění a použití jednotlivců a organizací, kteří se nacházejí mimo USA a její oblasti nebo kteří používají nebo vyvíjí programy, na kterých běží, od společnosti Microsoft Word, které byly licencované od společnosti Microsoft před lednem 2010, když společnost Microsoft odebrala implementaci konkrétních funkcí souvisejících s vlastním kódem XML z aplikace Microsoft Word. Tyto informace týkající se Microsoft Wordu nemusí číst ani používat jednotlivci nebo organizace v USA nebo na jejích oblastech, kteří používají, nebo vyvíjet programy, na kterých běží, od společnosti Microsoft Word, které byly licencované od Microsoftu po 10. ledna 2010. Tyto produkty se nebudou chovat stejně jako produkty licencované před tímto datem nebo zakoupené a licencované pro použití mimo USA.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Pokud namapujete neopakující se prvek schématu XML na systém Microsoft Office wordový dokument, Visual Studio automaticky přidá <xref:Microsoft.Office.Tools.Word.XMLNode> ovládací prvek do dokumentu. Informace o mapování opakujících se prvků schématu XML naleznete v tématu [How to: Add XMLNodes Controls to a Word Documents](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md).

> [!NOTE]
> <xref:Microsoft.Office.Tools.Word.XMLNode>Ovládací prvek není k dispozici v **panelu nástrojů** nebo v okně **zdroje dat** a nelze jej vytvořit programově.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-an-xmlnode-control-to-a-document"></a>Přidání ovládacího prvku XMLNode do dokumentu

1. V dokumentu v návrháři aplikace Visual Studio klikněte na pásu karet na kartu **vývojář** .

    > [!NOTE]
    > Pokud karta **vývojář** není zobrazená, musíte ji nejdřív zobrazit. Další informace najdete v tématu [Postup: zobrazení karty Vývojář na pásu karet](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

2. Ve skupině **XML** klikněte na **schéma**.

     Otevře se dialogové okno **šablony a doplňky** .

3. Klikněte na kartu **schéma XML** .

4. Klikněte na **Přidat schéma**.

     Otevře se dialogové okno **Přidat schéma** .

5. Vyberte schéma XML, které obsahuje neopakující prvky schématu v dialogovém okně **Přidat schéma** a klikněte na tlačítko **otevřít**.

     Zobrazí se dialogové okno **Nastavení schématu** .

6. Přiřaďte alias nebo kliknutím na tlačítko **OK** přidejte schéma bez aliasu.

     Schéma je přidáno do dialogového okna **Přidat schéma** .

7. V dialogovém okně **Přidat schéma** klikněte na tlačítko **OK**.

8. Otevře se podokno úloh **Struktura XML** .

9. Klikněte na neopakovaný prvek schématu v podokně úloh **Struktura XML** a přidejte ho do dokumentu.

     <xref:Microsoft.Office.Tools.Word.XMLNode>Ovládací prvek je vytvořen a přidán do projektu.

## <a name="see-also"></a>Viz také
- [XMLNode – ovládací prvek](../vsto/xmlnode-control.md)
- [Automatizace Wordu pomocí rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
