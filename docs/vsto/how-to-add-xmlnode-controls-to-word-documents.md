---
title: 'Postupy: Přidání ovládacích prvků XMLNode do dokumentů aplikace Word'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control, adding to documents
- controls [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: eccdeab67840873a9b40fe52986bd0d4d0b31767
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2018
ms.locfileid: "35254972"
---
# <a name="how-to-add-xmlnode-controls-to-word-documents"></a>Postupy: Přidání ovládacích prvků XMLNode do dokumentů aplikace Word
  **Důležité** informace uvedené v tomto tématu týkající se aplikace Microsoft Word je vidění výhradně pro benefit a použití jednotlivce a organizace, kteří se nacházejí mimo Spojené státy a jeho území nebo který používáte, nebo vývoj programy, které běží na, produkty Microsoft Word, které byly před leden 2010, když Microsoft odebrat implementace konkrétní funkce licencí společnosti Microsoft týkající se vlastní kód XML z aplikace Microsoft Word. Tyto informace týkající se aplikace Microsoft Word nemusí přečteny nebo používány jednotlivce nebo organizace v USA nebo v jeho území, které používáte, nebo vývoj programy, které běží na produkty Microsoft Word, které byly licencí společnosti Microsoft po 10 leden 2010 ; tyto produkty nebudou chovají stejně jako produkty licencované před tímto datem nebo zakoupených a licenci na použití mimo Spojené státy.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Pokud namapujete bez opakování element schématu XML na dokument aplikace Microsoft Office Word, Visual Studio automaticky přidá <xref:Microsoft.Office.Tools.Word.XMLNode> ovládacího prvku do dokumentu. Informace o mapování opakovaných prvků schématu XML najdete v tématu [postupy: Přidání XmlNodes – ovládací prvky do dokumentů aplikace Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md).  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Word.XMLNode> Ovládací prvek není k dispozici **sada nástrojů** nebo **zdroje dat** okna a nelze vytvořit prostřednictvím kódu programu.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-an-xmlnode-control-to-a-document"></a>Přidání ovládacího prvku XMLNode do dokumentu.  
  
1.  V dokumentu v návrháři Visual Studio na pásu karet, klepněte **vývojáře** kartě.  
  
    > [!NOTE]  
    >  Pokud **vývojáře** karta není viditelný, musíte ji nejdříve zobrazit. Další informace najdete v tématu [postupy: zobrazení karty Vývojář na pásu karet](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
2.  V **XML** klikněte na možnost **schématu**.  
  
     **Šablony a doplňky** otevře se dialogové okno.  
  
3.  Klikněte **schématu XML** kartě.  
  
4.  Klikněte na tlačítko **přidat schématu**.  
  
     **Přidat schéma** otevře se dialogové okno.  
  
5.  Vyberte schéma XML, který obsahuje bez opakování prvky schématu z **přidat schéma** dialogové okno a klikněte na tlačítko **otevřete**.  
  
     **Schéma – nastavení** zobrazí se dialogové okno.  
  
6.  Přiřadit alias nebo klikněte na tlačítko **OK** přidat schéma bez alias.  
  
     Schéma se přidá do **přidat schéma** dialogové okno.  
  
7.  V **přidat schéma** dialogové okno, klikněte na tlačítko **OK**.  
  
8.  **Struktuře XML** otevře v podokně úloh.  
  
9. Klikněte na element schema bez opakování **struktuře XML** podokna úloh přidat do dokumentu.  
  
     <xref:Microsoft.Office.Tools.Word.XMLNode> Ovládací prvek je vytvořen a přidán do projektu.  
  
## <a name="see-also"></a>Viz také:  
 [XmlNode – ovládací prvek](../vsto/xmlnode-control.md)   
 [Automatizace aplikace Word s použitím rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)   
 [Přehled ovládacích prvků hostitele a hostitelské položky](../vsto/host-items-and-host-controls-overview.md)   
 [Programová omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  