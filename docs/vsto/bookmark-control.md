---
title: Bookmark – ovládací prvek
description: Zjistěte, jak je ovládací prvek záložky záložka, která má jedinečný název, zpřístupňuje události a může být svázána s daty.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1da30943eff228aad3c5413c5d8faea337634e9b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905261"
---
# <a name="bookmark-control"></a>Bookmark – ovládací prvek
  <xref:Microsoft.Office.Tools.Word.Bookmark>Ovládací prvek je záložka, která má jedinečný název, zpřístupňuje události a může být vázána na data. Záložka se dá použít jako zástupný symbol k označení položky nebo umístění v dokumentu aplikace Wordu systém Microsoft Office. <xref:Microsoft.Office.Tools.Word.Bookmark>Ovládací prvek je kombinací <xref:Microsoft.Office.Interop.Word.Bookmark> objektu a <xref:Microsoft.Office.Interop.Word.Range> objektu.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 V projektech na úrovni dokumentu můžete přidat <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvky do dokumentu v době návrhu nebo v době běhu. V projektech doplňku VSTO můžete přidat <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvky do libovolného otevřeného dokumentu v době běhu. Další informace najdete v tématu [Postup: Přidání ovládacích prvků záložek do dokumentů aplikace Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md).

## <a name="bind-data-to-the-control"></a>Vázání dat k ovládacímu prvku
 <xref:Microsoft.Office.Tools.Word.Bookmark>Ovládací prvek podporuje jednoduchou datovou vazbu. Záložka by měla být vázána na zdroj dat pomocí <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> Vlastnosti. Výchozí vlastnost datové vazby záložky je <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> vlastnost.

 Pokud jsou data v vázané sadě dat aktualizována, <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvek zobrazí změny.

 V projektech na úrovni dokumentu můžete také vytvořit vazby mezi daty a záložkami pomocí okna **zdroje dat** . Další informace naleznete v tématu [How to: naplnit dokumenty daty z objektů](../vsto/how-to-populate-documents-with-data-from-objects.md).

## <a name="formatting"></a>Formátování
 Formátování, které lze použít na objekt, <xref:Microsoft.Office.Interop.Word.Bookmark> lze použít pro <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvek. Toto formátování zahrnuje písma, odsazení, mezery, číslování a styly.

## <a name="assign-text-to-the-bookmark"></a>Přiřadit text k záložce
 Dalším rozdílem mezi <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType> objektem a <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> ovládacím prvkem je způsob, jakým se chová při přiřazení textu k záložce. Pokud přiřadíte text nulové délce <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType> , text se připojí napravo od záložky a Záložka zůstane s nulovou délkou. Pokud ale přiřadíte text nulové délce <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> , text se vloží do záložky a délka záložky se rozšíří na celkový počet vložených znaků.

 <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType>Ovládací prvek má také <xref:Microsoft.Office.Tools.Word.Bookmark.Text?displayProperty=nameWithType> vlastnost. Tato vlastnost je odlišná od <xref:Microsoft.Office.Interop.Word.Range.Text?displayProperty=nameWithType> vlastnosti, která je k dispozici ve <xref:Microsoft.Office.Tools.Word.Bookmark.Range?displayProperty=nameWithType> vlastnosti <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> ovládacího prvku, nebo <xref:Microsoft.Office.Interop.Word.Bookmark.Range?displayProperty=nameWithType> vlastnosti <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType> objektu.

|Vlastnost text|Description|
|-------------------|-----------------|
|<xref:Microsoft.Office.Tools.Word.Bookmark.Text?displayProperty=nameWithType>|Tato vlastnost slouží k zobrazení textu v rámci záložky a ponechání záložky v dokumentu. Přiřazení textu k záložce rozbalí rozsah záložky a neodstraní záložku.<br /><br /> Například `Bookmark1.Text = "Hello world"` vloží text do záložky a nechá záložku beze změny.|
|<xref:Microsoft.Office.Interop.Word.Range.Text?displayProperty=nameWithType>|Tato vlastnost slouží k zobrazení textu v umístění záložky a k automatickému odstranění záložky. Například `Bookmark1.Range.Text = "Hello world"` vloží text do záložky a odstraní záložku.|

## <a name="rename-the-control-at-design-time"></a>Přejmenování ovládacího prvku v době návrhu
 Pokud v projektech na úrovni dokumentu přetáhnete <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvek z **panelu nástrojů** do dokumentu, sada Visual Studio automaticky vygeneruje název ovládacího prvku. Můžete změnit název ovládacího prvku v okně **vlastnosti** .

## <a name="overlapping-controls"></a>Překrývající se ovládací prvky
 Ovládací prvky záložek se můžou vzájemně překrývat. Stejný text může být sdílen více než jednou záložkou. Když přiřadíte nový text k jedné z překrývajících se záložek, bude obsahovat pouze nový text a záložky již nebudou překrývat. Druhá záložka teď obsahuje jenom text, který se nesdílel mezi původními překrývajícími se záložkami.

 Následující tabulka ukazuje, jak se jedná o větu "This je ukázkový text." sdílí se dvěma překrývajícími se záložkami:

|Záložka|Text|
|--------------|----------|
|Překrývající se záložky|[this je {Sample] text.}|
|Bookmark1|Toto je ukázka|
|Bookmark2|Vzorový text.|

 Pokud přiřadíte nový text "Toto je náhrada". bookmark1 záložky se nepřekrývají a Bookmark2 uchová pouze text, který nebyl původně součástí bookmark1.

|Záložka|Text|
|--------------|----------|
|Dvě samostatné záložky|[Toto je náhrada] {text.}|
|Bookmark1|Toto je náhrada|
|Bookmark2|textové.|

Pokud změníte text záložky, která obsahuje jinou záložku, vnitřní záložka se neodstraní. Nicméně vnitřní záložka se stane prázdnou záložkou a přejde na konec vnější záložky.

Následující tabulka ukazuje, jak se jedná o větu "This je ukázkový text." je sdílen záložkou, která je obsažena v jiné záložce:

|Záložka|Text|
|--------------|----------|
|Překrývající se záložky|[tohle je {Sample} text.]|
|Bookmark1|Toto je ukázkový text.|
|Bookmark2|ukázka|

 Pokud přiřadíte nový text "Toto je náhrada". bookmark1 záložky již nejsou překrývající a Bookmark2 se stane prázdnou záložkou, která je umístěna na konci bookmark1.

|Záložka|Text|
|--------------|----------|
|Dvě samostatné záložky|[Toto je náhrada.]{}|
|Bookmark1|Toto je náhrada.|
|Bookmark2|*\<empty>*|

## <a name="events"></a>Události

Pro ovládací prvek jsou k dispozici následující události <xref:Microsoft.Office.Tools.Word.Bookmark> :

- <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Word.Bookmark.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Word.Bookmark.Deselected>

- <xref:System.ComponentModel.IComponent.Disposed>

- <xref:Microsoft.Office.Tools.Word.Bookmark.Selected>

- <xref:Microsoft.Office.Tools.Word.Bookmark.SelectionChange>

## <a name="see-also"></a>Viz také

- [Automatizace Wordu pomocí rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)
- [Postupy: Přidání ovládacích prvků záložek do dokumentů aplikace Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Návod: Vytvoření místních nabídek pro záložky](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)
- [Vázání dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)