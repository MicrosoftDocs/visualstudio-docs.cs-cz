---
title: Bookmark – ovládací prvek
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.Bookmark
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- bookmarks, controlling
- Bookmark control, data binding
- Bookmark control, events
- Bookmark control
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 242a4692bc75715e661244dc8f513d30cc9480ed
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248189"
---
# <a name="bookmark-control"></a>Bookmark – ovládací prvek
  <xref:Microsoft.Office.Tools.Word.Bookmark> Ovládací prvek je záložku, která má jedinečný název, zpřístupní události a může být vázaný na data. Záložka může sloužit jako zástupný symbol pro označení položku nebo místo v dokumentu aplikace Microsoft Office Word. <xref:Microsoft.Office.Tools.Word.Bookmark> Ovládací prvek je kombinací identifikátoru <xref:Microsoft.Office.Interop.Word.Bookmark> objektu a <xref:Microsoft.Office.Interop.Word.Range> objektu.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Projekty na úrovni dokumentu, můžete přidat <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacích prvků do dokumentu v době návrhu nebo za běhu. Projekty doplňků VSTO, můžete přidat <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacích prvků do libovolného otevřeného dokumentu za běhu. Další informace najdete v tématu [jak: Přidání ovládacích prvků záložek do dokumentů aplikace Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md).

## <a name="bind-data-to-the-control"></a>Vytvoření vazby dat k ovládacímu prvku
 A <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvek podporuje jednoduchou datovou vazbu. Záložky by měl být vázaný na zdroji dat pomocí <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> vlastnost. Je výchozí vlastnost vazby dat záložky <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> vlastnost.

 Pokud aktualizaci dat v datové sadě vázané <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvek zobrazuje změny.

 V projektech na úrovni dokumentu, můžete také navázat data do záložek s použitím **zdroje dat** okna. Další informace najdete v tématu [jak: Naplnění dokumentů daty z objektů](../vsto/how-to-populate-documents-with-data-from-objects.md).

## <a name="formatting"></a>Formátování
 Který lze použít k formátování <xref:Microsoft.Office.Interop.Word.Bookmark> lze použít u <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacího prvku. Toto formátování zahrnuje písma, odsazení, mezeru, číslování a styly.

## <a name="assign-text-to-the-bookmark"></a>Přiřadit text na záložku
 Další rozdíl mezi <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType> objektu a <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> ovládací prvek je, jak se chová při přiřazení text na záložku. Pokud přiřadíte text nulové délky <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType>, text se připojí k pravému záložky a zůstane Záložka nulové délky. Nicméně pokud přiřadíte text nulové délky <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType>, text je vložen do záložky a délky na záložku rozšíří na celkový počet znaků, které jsou vloženy.

 <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> Ovládací prvek má také <xref:Microsoft.Office.Tools.Word.Bookmark.Text?displayProperty=nameWithType> vlastnost. Tato vlastnost se liší od <xref:Microsoft.Office.Interop.Word.Range.Text?displayProperty=nameWithType> vlastnost, která je k dispozici na <xref:Microsoft.Office.Tools.Word.Bookmark.Range?displayProperty=nameWithType> vlastnost <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> ovládacího prvku, nebo <xref:Microsoft.Office.Interop.Word.Bookmark.Range?displayProperty=nameWithType> vlastnost <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType> objektu.

|Vlastnost text|Popis|
|-------------------|-----------------|
|<xref:Microsoft.Office.Tools.Word.Bookmark.Text?displayProperty=nameWithType>|Tuto vlastnost použijte k zobrazení textu v záložce a nechat záložky v dokumentu. Přiřazení text na záložku rozšiřuje rozsah záložky a nedojde k odstranění na záložku.<br /><br /> Například `Bookmark1.Text = "Hello world"` vloží text do záložky a ponechá beze změny na záložku.|
|<xref:Microsoft.Office.Interop.Word.Range.Text?displayProperty=nameWithType>|Tuto vlastnost použijte k zobrazení textu v umístění záložku a automaticky odstranit záložky. Například `Bookmark1.Range.Text = "Hello world"` vloží text do záložky a odstraní záložky.|

## <a name="rename-the-control-at-design-time"></a>Přejmenujte ovládací prvek v době návrhu
 V projektech na úrovni dokumentu, při přetažení <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacího prvku **nástrojů** do dokumentu sady Visual Studio automaticky vygeneruje název ovládacího prvku. Můžete změnit název ovládacího prvku **vlastnosti** okna.

## <a name="overlapping-controls"></a>Překrývání ovládacích prvků
 Ovládacích prvků záložek můžete vzájemně překrývat. Stejný text může být sdílen více než jednu záložku. Když přiřadíte nový text do jednoho z překrývající se záložky, obsahuje pouze nový text a záložky už překrývat. Na další záložku nyní obsahuje pouze text, který nebyl sdílen mezi původní překrývající se záložkami.

 Následující tabulka ukazuje, jak se věta "Toto je ukázkový text". je sdílen dvěma překrývající se záložek:

|záložky|Text|
|--------------|----------|
|Překrývající se záložky|[Toto je ukázka {] text.}|
|Bookmark1|Toto je ukázka|
|Bookmark2|text v ukázce.|

 Pokud přiřadíte nové text "Toto je náhrada." Bookmark1 záložky nepřekrývají, a Bookmark2 zachová pouze text, který není součástí Bookmark1 původně.

|záložky|Text|
|--------------|----------|
|Dva samostatné záložky|[Toto je nahrazení] {text}.|
|Bookmark1|Toto je nahrazení|
|Bookmark2|Text.|

Pokud změníte text, který obsahuje další Záložka záložku, vnitřní záložky se neodstraní. Vnitřní záložku však stane prázdný záložku a přesune na konec vnější záložku.

Následující tabulka ukazuje, jak se věta "Toto je ukázkový text". sdílí záložku, která je obsažena v jiné záložku:

|záložky|Text|
|--------------|----------|
|Překrývající se záložky|[Toto je text {ukázka}].|
|Bookmark1|Toto je ukázkový text.|
|Bookmark2|ukázka|

 Pokud přiřadíte nové text "Toto je náhrada." Chcete-li Bookmark1 už překrývající se záložky a Bookmark2 stane prázdný záložku, která se nachází na konci Bookmark1.

|záložky|Text|
|--------------|----------|
|Dva samostatné záložky|[Toto je náhrada.]{}|
|Bookmark1|Toto je nahrazení.|
|Bookmark2|*\<Prázdný >*|

## <a name="events"></a>Události

Tyto události jsou k dispozici pro <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacího prvku:

-   <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeDoubleClick>

-   <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick>

-   <xref:Microsoft.Office.Tools.Word.Bookmark.BindingContextChanged>

-   <xref:Microsoft.Office.Tools.Word.Bookmark.Deselected>

-   <xref:System.ComponentModel.IComponent.Disposed>

-   <xref:Microsoft.Office.Tools.Word.Bookmark.Selected>

-   <xref:Microsoft.Office.Tools.Word.Bookmark.SelectionChange>

## <a name="see-also"></a>Viz také:

- [Automatizace aplikace Word s použitím rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)
- [Postupy: Přidání ovládacích prvků záložek do dokumentů aplikace Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Návod: Vytváření místních nabídek pro záložky](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)
- [Vytvoření vazby dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Programová omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)