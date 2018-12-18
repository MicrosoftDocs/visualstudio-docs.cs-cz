---
title: 'Postupy: Přidání ovládacích prvků XMLNodes do dokumentů aplikace Word'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNodes control, adding to documents
- controls [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ff7a1966c9107fcd2a60b14c21b6a2dfbda09033
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2018
ms.locfileid: "35258067"
---
# <a name="how-to-add-xmlnodes-controls-to-word-documents"></a>Postupy: Přidání ovládacích prvků XMLNodes do dokumentů aplikace Word
  **Důležité** informace uvedené v tomto tématu týkající se aplikace Microsoft Word je vidění výhradně pro benefit a použití jednotlivce a organizace, kteří se nacházejí mimo Spojené státy a jeho území nebo který používáte, nebo vývoj programy, které běží na, produkty Microsoft Word, které byly před leden 2010, když Microsoft odebrat implementace konkrétní funkce licencí společnosti Microsoft týkající se vlastní kód XML z aplikace Microsoft Word. Tyto informace týkající se aplikace Microsoft Word nemusí přečteny nebo používány jednotlivce nebo organizace v USA nebo v jeho území, které používáte, nebo vývoj programy, které běží na produkty Microsoft Word, které byly licencí společnosti Microsoft po 10 leden 2010 ; tyto produkty nebudou chovají stejně jako produkty licencované před tímto datem nebo zakoupených a licenci na použití mimo Spojené státy.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Pokud namapujete opakující se prvek schématu XML na dokument aplikace Microsoft Office Word, Visual Studio automaticky přidá <xref:Microsoft.Office.Tools.Word.XMLNodes> ovládacího prvku do dokumentu.  
  
 Informace o mapování bez opakování prvků schématu XML najdete v tématu [postupy: Přidání XmlNode – ovládací prvky do dokumentů aplikace Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md).  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Word.XMLNodes> Ovládací prvek není k dispozici **sada nástrojů** nebo **zdroje dat** okno ani mohou být vytvořeny programově.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-an-xmlnodes-control-to-a-document"></a>Chcete-li přidat XmlNodes – ovládací prvek do dokumentu.  
  
1.  V dokumentu v návrháři Visual Studio na pásu karet, klepněte **vývojáře** kartě.  
  
    > [!NOTE]  
    >  Pokud **vývojáře** karta není viditelný, musíte ji nejdříve zobrazit. Další informace najdete v tématu [postupy: zobrazení karty Vývojář na pásu karet](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
2.  V **XML** klikněte na možnost **schématu**.  
  
     **Šablony a doplňky** otevře se dialogové okno.  
  
3.  Klikněte **schématu XML** kartě.  
  
4.  Klikněte na tlačítko **přidat schématu**.  
  
     **Přidat schéma** otevře se dialogové okno.  
  
5.  Vyberte schéma XML, který obsahuje opakující se prvky schématu a klikněte na tlačítko **otevřete**.  
  
     **Schéma – nastavení** zobrazí se dialogové okno.  
  
6.  Přiřadit alias nebo klikněte na tlačítko **OK** přidat schéma bez alias.  
  
     Schéma se přidá do **přidat schéma** dialogové okno.  
  
7.  V **přidat schéma** dialogové okno, klikněte na tlačítko **OK**.  
  
     **Struktuře XML** otevře v podokně úloh.  
  
8.  Opakující se element schema klikněte na **struktuře XML** podokna úloh přidat do dokumentu.  
  
     <xref:Microsoft.Office.Tools.Word.XMLNodes> Ovládací prvek je vytvořen a přidán do projektu.  
  
## <a name="see-also"></a>Viz také:  
 [XmlNodes – ovládací prvek](../vsto/xmlnodes-control.md)   
 [Automatizace aplikace Word s použitím rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)   
 [Přehled ovládacích prvků hostitele a hostitelské položky](../vsto/host-items-and-host-controls-overview.md)   
 [Programová omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  