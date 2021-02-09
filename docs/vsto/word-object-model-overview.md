---
title: Přehled modelu objektů aplikace Word
description: Objektový model aplikace Word se skládá z tříd a rozhraní, které jsou k dispozici v primárním sestavení vzájemné spolupráce pro Word a jsou definovány v oboru názvů Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word object model
- Word [Office development in Visual Studio], object model
- object models [Office development in Visual Studio], Office
- object models [Office development in Visual Studio], Word
- objects [Office development in Visual Studio], Office object models
- Office object models
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3d593185412db23fa985f7effea6e91f9b3faa6c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847645"
---
# <a name="word-object-model-overview"></a>Přehled modelu objektů aplikace Word
  Při vývoji řešení aplikace Word v aplikaci Visual Studio budete pracovat s modelem objektu aplikace Word. Tento objektový model se skládá z tříd a rozhraní, které jsou k dispozici v primárním sestavení vzájemné spolupráce pro Word, a jsou definovány v <xref:Microsoft.Office.Interop.Word> oboru názvů.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Toto téma poskytuje stručný přehled modelu objektu aplikace Word. Prostředky, ve kterých se můžete dozvědět víc o celém objektovém modelu aplikace Word, najdete v [dokumentaci k objektovému modelu aplikace Word](#WordOMDocumentation).

 Informace o použití objektového modelu aplikace Word k provádění konkrétních úkolů naleznete v následujících tématech:

- [Práce s dokumenty](../vsto/working-with-documents.md)

- [Práce s textem v dokumentech](../vsto/working-with-text-in-documents.md)

- [Práce s tabulkami](../vsto/working-with-tables.md)

## <a name="understand-the-word-object-model"></a><a name="understanding"></a> Pochopení modelu objektu aplikace Word
 Word poskytuje stovky objektů, se kterými můžete pracovat. Tyto objekty jsou uspořádány v hierarchii, která úzce odpovídá uživatelskému rozhraní. V horní části hierarchie je <xref:Microsoft.Office.Interop.Word.Application> objekt. Tento objekt představuje aktuální instanci aplikace Word. <xref:Microsoft.Office.Interop.Word.Application>Objekt obsahuje <xref:Microsoft.Office.Interop.Word.Document> <xref:Microsoft.Office.Interop.Word.Selection> objekty,, a <xref:Microsoft.Office.Interop.Word.Bookmark> <xref:Microsoft.Office.Interop.Word.Range> . Každý z těchto objektů má mnoho metod a vlastností, které lze použít k manipulaci s objektem a práci s nimi.

 Následující ilustrace znázorňuje jeden pohled na tyto objekty v hierarchii objektového modelu aplikace Word.

 ![Grafika modelu objektu aplikace Word](../vsto/media/wrwordobjectmodel.gif "Grafika modelu objektu aplikace Word")

 Na první pohled se objekty překrývají. Například <xref:Microsoft.Office.Interop.Word.Document> <xref:Microsoft.Office.Interop.Word.Selection> objekty a jsou oba členy <xref:Microsoft.Office.Interop.Word.Application> objektu, ale <xref:Microsoft.Office.Interop.Word.Document> objekt je také členem <xref:Microsoft.Office.Interop.Word.Selection> objektu. Objekty i <xref:Microsoft.Office.Interop.Word.Document> <xref:Microsoft.Office.Interop.Word.Selection> obsahují <xref:Microsoft.Office.Interop.Word.Bookmark> a <xref:Microsoft.Office.Interop.Word.Range> . Překrytí existuje, protože existuje více způsobů, jak můžete přistupovat ke stejnému typu objektu. Například použijete formátování <xref:Microsoft.Office.Interop.Word.Range> objektu, ale můžete chtít získat přístup k rozsahu aktuálního výběru, konkrétního odstavce, oddílu nebo celého dokumentu.

 Následující části stručně popisují objekty nejvyšší úrovně a jejich vzájemné interakce. Mezi tyto objekty patří pět následujících:

- Objekt aplikace

- Objekt dokumentu

- Objekt výběru

- rozsah – objekt

- Objekt Bookmark

  Kromě objektového modelu aplikace *Word poskytují projekty* Office v sadě Visual Studio i hostitelské *ovládací prvky* , které rozšířily některé objekty v objektovém modelu aplikace Word. Hostitelské položky a hostitelské ovládací prvky se chovají stejně jako objekty aplikace Word, které rozšiřuje, ale mají také další funkce, jako jsou například funkce vazby dat a dodatečné události. Další informace najdete v tématu [Automatizace Wordu pomocí rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md) a [položek hostitele a Přehled hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).

### <a name="application-object"></a>Objekt aplikace
 <xref:Microsoft.Office.Interop.Word.Application>Objekt představuje aplikaci Word a je nadřazeným prvkem všech ostatních objektů. Její členové se obvykle vztahují na slovo jako celek. Pro řízení prostředí slov můžete použít jeho vlastnosti a metody.

 V projektech doplňku VSTO můžete k <xref:Microsoft.Office.Interop.Word.Application> objektu přistupovat pomocí `Application` pole `ThisAddIn` třídy. Další informace najdete v tématu [programové doplňky VSTO](../vsto/programming-vsto-add-ins.md).

 V projektech na úrovni dokumentu můžete k <xref:Microsoft.Office.Interop.Word.Application> objektu přistupovat pomocí <xref:Microsoft.Office.Tools.Word.Document.Application%2A> vlastnosti `ThisDocument` třídy.

### <a name="document-object"></a>Objekt dokumentu
 <xref:Microsoft.Office.Interop.Word.Document>Objekt je střední pro programování v aplikaci Word. Představuje dokument a veškerý jeho obsah. Když otevřete dokument nebo vytvoříte nový dokument, vytvoříte nový <xref:Microsoft.Office.Interop.Word.Document> objekt, který je přidán do <xref:Microsoft.Office.Interop.Word.Documents> kolekce <xref:Microsoft.Office.Interop.Word.Application> objektu. Dokument, který má fokus, se nazývá aktivní dokument. Je reprezentován <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> vlastností <xref:Microsoft.Office.Interop.Word.Application> objektu.

 Vývojové nástroje pro Office v sadě Visual Studio rozšiřuje <xref:Microsoft.Office.Interop.Word.Document> objekt zadáním <xref:Microsoft.Office.Tools.Word.Document> typu. Tento typ je *Hostitelská položka* , která poskytuje přístup ke všem funkcím <xref:Microsoft.Office.Interop.Word.Document> objektu a přidává další události a možnost Přidat spravované ovládací prvky.

 Při vytváření projektu na úrovni dokumentu můžete ke <xref:Microsoft.Office.Tools.Word.Document> členům přistupovat pomocí generované `ThisDocument` třídy v projektu. Ke členům položky hostitele můžete přistupovat <xref:Microsoft.Office.Tools.Word.Document> pomocí **mě** nebo **těchto** klíčových slov z kódu ve `ThisDocument` třídě nebo pomocí `Globals.ThisDocument` kódu z jiné `ThisDocument` třídy. Další informace najdete v tématu věnovaném [přizpůsobení na úrovni dokumentu programu](../vsto/programming-document-level-customizations.md). Chcete-li například vybrat první odstavec v dokumentu, použijte následující kód.

 [!code-vb[Trin_VstcoreWordAutomation#120](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#120)]
 [!code-csharp[Trin_VstcoreWordAutomation#120](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#120)]

 V projektech doplňku VSTO můžete v <xref:Microsoft.Office.Tools.Word.Document> době běhu generovat položky hostitele. Vygenerovanou položku hostitele můžete použít k přidání ovládacích prvků do přidruženého dokumentu. Další informace najdete v tématu [rozšiřování dokumentů aplikace Word a sešitů aplikace Excel v doplňkech VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

### <a name="selection-object"></a>Objekt výběru
 <xref:Microsoft.Office.Interop.Word.Selection>Objekt představuje aktuálně vybranou oblast. Když provedete operaci v uživatelském rozhraní aplikace Word, například tučný text, vyberete nebo zvýrazníte text a pak použijete formátování. <xref:Microsoft.Office.Interop.Word.Selection>Objekt je vždy přítomen v dokumentu. Pokud není nic vybráno, představuje bod vložení. Kromě toho může výběr zahrnovat více bloků textu, které nejsou souvislé.

### <a name="range-object"></a>rozsah – objekt
 <xref:Microsoft.Office.Interop.Word.Range>Objekt představuje souvislou oblast v dokumentu a je definován počáteční polohou znaku a koncovou pozicí znaků. Nejste omezeni pouze na jeden <xref:Microsoft.Office.Interop.Word.Range> objekt. <xref:Microsoft.Office.Interop.Word.Range>V jednom dokumentu můžete definovat více objektů. <xref:Microsoft.Office.Interop.Word.Range>Objekt má následující vlastnosti:

- Může se skládat pouze z bodu vložení, oblasti textu nebo celého dokumentu.

- Zahrnuje netiskové znaky, jako jsou mezery, znaky tabulátoru a značky odstavců.

- Může se jednat o oblast reprezentovanou aktuálním výběrem, nebo může představovat oblast odlišnou od aktuálního výběru.

- Není viditelný v dokumentu, na rozdíl od výběru, který je vždy viditelný.

- Není uložen s dokumentem a existuje pouze v případě, že kód je spuštěn.

  Když vložíte text na konci rozsahu, Word automaticky rozbalí rozsah tak, aby zahrnoval vložený text.

### <a name="content-control-objects"></a>Objekty ovládacího prvku obsahu
 A <xref:Microsoft.Office.Interop.Word.ContentControl> poskytuje způsob, jak řídit vstup a prezentaci textu a dalších typů obsahu v dokumentech aplikace Word. <xref:Microsoft.Office.Interop.Word.ContentControl>Může zobrazit několik různých typů uživatelského rozhraní, které jsou optimalizované pro použití v dokumentech aplikace Word, jako je například ovládací prvek RTF, výběr data nebo pole se seznamem. Můžete také použít <xref:Microsoft.Office.Interop.Word.ContentControl> k zabránění uživatelům v úpravách oddílů dokumentu nebo šablony.

 Visual Studio rozšiřuje <xref:Microsoft.Office.Interop.Word.ContentControl> objekt na několik různých hostitelských ovládacích prvků. Vzhledem k tomu, že <xref:Microsoft.Office.Interop.Word.ContentControl> objekt může zobrazit libovolný z různých typů uživatelského rozhraní, které jsou k dispozici pro ovládací prvky obsahu, Visual Studio poskytuje pro každý ovládací prvek obsahu jiný typ. Například můžete použít <xref:Microsoft.Office.Tools.Word.RichTextContentControl> k vytvoření ovládacího prvku formátovaného textu nebo můžete použít <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> k vytvoření výběru data. Tyto hostitelské ovládací prvky se chovají jako nativní <xref:Microsoft.Office.Interop.Word.ContentControl> , ale mají další události a funkce vazby dat. Další informace najdete v tématu [ovládací prvky obsahu](../vsto/content-controls.md).

### <a name="bookmark-object"></a>Objekt Bookmark
 <xref:Microsoft.Office.Interop.Word.Bookmark>Objekt představuje souvislou oblast v dokumentu s počáteční a koncovou pozicí. Můžete použít záložky k označení umístění v dokumentu nebo jako kontejneru pro text v dokumentu. <xref:Microsoft.Office.Interop.Word.Bookmark>Objekt se může skládat z bodu vložení nebo být stejně velký jako celý dokument. <xref:Microsoft.Office.Interop.Word.Bookmark>Má následující vlastnosti, které nastavují od <xref:Microsoft.Office.Interop.Word.Range> objektu:

- Záložku můžete pojmenovat v době návrhu.

- <xref:Microsoft.Office.Interop.Word.Bookmark> objekty jsou uloženy spolu s dokumentem, a proto nejsou odstraněny, když kód přestane běžet nebo je dokument uzavřen.

- Záložky lze skrýt nebo zobrazit, pokud nastavíte <xref:Microsoft.Office.Interop.Word.View.ShowBookmarks%2A> vlastnost <xref:Microsoft.Office.Interop.Word.View> objektu na **hodnotu false** nebo **true**.

  Visual Studio rozšiřuje <xref:Microsoft.Office.Interop.Word.Bookmark> objekt poskytnutím <xref:Microsoft.Office.Tools.Word.Bookmark> hostitelského ovládacího prvku. <xref:Microsoft.Office.Tools.Word.Bookmark>Hostitelský ovládací prvek se chová jako nativní <xref:Microsoft.Office.Interop.Word.Bookmark> , ale má další události a funkce vazby dat. Data můžete navazovat na ovládací prvek záložka v dokumentu stejným způsobem, jako svážete data s ovládacím prvkem textového pole ve formuláři Windows. Další informace naleznete v tématu [ovládací prvek Bookmark](../vsto/bookmark-control.md).

## <a name="use-the-word-object-model-documentation"></a><a name="WordOMDocumentation"></a> Použití dokumentace k objektovému modelu aplikace Word
 Úplné informace o objektovém modelu aplikace Word můžete odkazovat na odkaz na primární definiční sestavení (PIA) a odkaz na objektový model jazyk Visual Basic for Application (VBA).

### <a name="primary-interop-assembly-reference"></a>Odkaz na primární definiční sestavení
 Referenční dokumentace k aplikaci Word PIA popisuje typy v primárním sestavení vzájemné spolupráce pro Word. Tato dokumentace je k dispozici z následujícího umístění: [odkaz na primární definiční sestavení aplikace Word 2010](../vsto/office-primary-interop-assemblies.md).

 Další informace o návrhu aplikace Word PIA, jako jsou rozdíly mezi třídami a rozhraními PIA a jak jsou implementovány události v PIA, naleznete v tématu [Přehled tříd a rozhraní v primárních sestaveních vzájemné spolupráce pro systém Office](/previous-versions/office/office-12/ms247299(v=office.12)).

### <a name="vba-object-model-reference"></a>Referenční dokumentace modelu objektu VBA
 Odkaz model objektu VBA odkazuje na dokument objektový model aplikace Word, protože je vystavený pro kód VBA. Další informace najdete v tématu [referenční materiály k objektovému modelu Word 2010](/office/vba/api/overview/Word/object-model).

 Všechny objekty a členy v referenčním modelu objektu VBA odpovídají typům a členům ve slovech PIA. Například objekt dokumentu v odkazu modelu objektu VBA odpovídá <xref:Microsoft.Office.Interop.Word.Document> objektu ve slovech PIA. I když odkaz na objektový model VBA poskytuje příklady kódu pro většinu vlastností, metod a událostí, je nutné překládat kód VBA v tomto odkazu na Visual Basic nebo Visual C#, pokud je chcete použít v projektu aplikace Word, který vytvoříte pomocí sady Visual Studio.

## <a name="see-also"></a>Viz také
- [Sestavení primární spolupráce pro Office](../vsto/office-primary-interop-assemblies.md)
- [Automatizace Wordu pomocí rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)
- [Práce s dokumenty](../vsto/working-with-documents.md)
- [Práce s textem v dokumentech](../vsto/working-with-text-in-documents.md)
- [Práce s tabulkami](../vsto/working-with-tables.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
