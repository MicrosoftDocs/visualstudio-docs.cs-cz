---
title: Přehled modelu objektů aplikace Word
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 71e66d6cda802b2b1243911e1927af751e2cdbe9
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985395"
---
# <a name="word-object-model-overview"></a>Přehled modelu objektů aplikace Word
  Při vývoji řešení aplikace Word v aplikaci Visual Studio budete pracovat s modelem objektu aplikace Word. Tento objektový model se skládá z tříd a rozhraní, které jsou k dispozici v primárním sestavení vzájemné spolupráce pro Word, a jsou definovány v oboru názvů <xref:Microsoft.Office.Interop.Word>.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Toto téma poskytuje stručný přehled modelu objektu aplikace Word. Prostředky, ve kterých se můžete dozvědět víc o celém objektovém modelu aplikace Word, najdete v [dokumentaci k objektovému modelu aplikace Word](#WordOMDocumentation).

 Informace o použití objektového modelu aplikace Word k provádění konkrétních úkolů naleznete v následujících tématech:

- [Práce s dokumenty](../vsto/working-with-documents.md)

- [Práce s textem v dokumentech](../vsto/working-with-text-in-documents.md)

- [Práce s tabulkami](../vsto/working-with-tables.md)

## <a name="understanding"></a>Pochopení modelu objektu aplikace Word
 Word poskytuje stovky objektů, se kterými můžete pracovat. Tyto objekty jsou uspořádány v hierarchii, která úzce odpovídá uživatelskému rozhraní. V horní části hierarchie je objekt <xref:Microsoft.Office.Interop.Word.Application>. Tento objekt představuje aktuální instanci aplikace Word. Objekt <xref:Microsoft.Office.Interop.Word.Application> obsahuje objekty <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Word.Selection>, <xref:Microsoft.Office.Interop.Word.Bookmark>a <xref:Microsoft.Office.Interop.Word.Range>. Každý z těchto objektů má mnoho metod a vlastností, které lze použít k manipulaci s objektem a práci s nimi.

 Následující ilustrace znázorňuje jeden pohled na tyto objekty v hierarchii objektového modelu aplikace Word.

 ![Grafika modelu objektu aplikace Word](../vsto/media/wrwordobjectmodel.gif "Grafika modelu objektu aplikace Word")

 Na první pohled se objekty překrývají. Například objekty <xref:Microsoft.Office.Interop.Word.Document> a <xref:Microsoft.Office.Interop.Word.Selection> jsou členy objektu <xref:Microsoft.Office.Interop.Word.Application>, ale objekt <xref:Microsoft.Office.Interop.Word.Document> je také členem objektu <xref:Microsoft.Office.Interop.Word.Selection>. Objekty <xref:Microsoft.Office.Interop.Word.Document> i <xref:Microsoft.Office.Interop.Word.Selection> obsahují objekty <xref:Microsoft.Office.Interop.Word.Bookmark> a <xref:Microsoft.Office.Interop.Word.Range>. Překrytí existuje, protože existuje více způsobů, jak můžete přistupovat ke stejnému typu objektu. Například aplikujete formátování na objekt <xref:Microsoft.Office.Interop.Word.Range>; Můžete ale chtít získat přístup k rozsahu aktuálního výběru, konkrétního odstavce, oddílu nebo celého dokumentu.

 Následující části stručně popisují objekty nejvyšší úrovně a jejich vzájemné interakce. Mezi tyto objekty patří pět následujících:

- Objekt aplikace

- Objekt dokumentu

- Objekt výběru

- rozsah – objekt

- Objekt Bookmark

  Kromě objektového modelu aplikace *Word poskytují projekty* Office v sadě Visual Studio i hostitelské *ovládací prvky* , které rozšířily některé objekty v objektovém modelu aplikace Word. Hostitelské položky a hostitelské ovládací prvky se chovají stejně jako objekty aplikace Word, které rozšiřuje, ale mají také další funkce, jako jsou například funkce vazby dat a dodatečné události. Další informace najdete v tématu [Automatizace Wordu pomocí rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md) a [položek hostitele a Přehled hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).

### <a name="application-object"></a>Objekt aplikace
 Objekt <xref:Microsoft.Office.Interop.Word.Application> představuje aplikaci Word a je nadřazeným prvkem všech ostatních objektů. Její členové se obvykle vztahují na slovo jako celek. Pro řízení prostředí slov můžete použít jeho vlastnosti a metody.

 V projektech doplňku VSTO máte přístup k objektu <xref:Microsoft.Office.Interop.Word.Application> pomocí pole `Application` třídy `ThisAddIn`. Další informace najdete v tématu [programové doplňky VSTO](../vsto/programming-vsto-add-ins.md).

 V projektech na úrovni dokumentu můžete k objektu <xref:Microsoft.Office.Interop.Word.Application> přistupovat pomocí vlastnosti <xref:Microsoft.Office.Tools.Word.Document.Application%2A> třídy `ThisDocument`.

### <a name="document-object"></a>Objekt dokumentu
 Objekt <xref:Microsoft.Office.Interop.Word.Document> je od střední po programování v aplikaci Word. Představuje dokument a veškerý jeho obsah. Když otevřete dokument nebo vytvoříte nový dokument, vytvoříte nový objekt <xref:Microsoft.Office.Interop.Word.Document>, který je přidán do kolekce <xref:Microsoft.Office.Interop.Word.Documents> objektu <xref:Microsoft.Office.Interop.Word.Application>. Dokument, který má fokus, se nazývá aktivní dokument. Je reprezentován vlastností <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> objektu <xref:Microsoft.Office.Interop.Word.Application>.

 Vývojové nástroje pro Office v sadě Visual Studio rozšíří objekt <xref:Microsoft.Office.Interop.Word.Document> tím, že poskytují typ <xref:Microsoft.Office.Tools.Word.Document>. Tento typ je *Hostitelská položka* , která poskytuje přístup ke všem funkcím objektu <xref:Microsoft.Office.Interop.Word.Document> a přidává další události a možnost Přidat spravované ovládací prvky.

 Když vytvoříte projekt na úrovni dokumentu, můžete získat přístup k <xref:Microsoft.Office.Tools.Word.Document> členů pomocí generované `ThisDocument` třídy v projektu. Ke členům položky <xref:Microsoft.Office.Tools.Word.Document> hostitele můžete přistupovat pomocí **mě** nebo **těchto** klíčových slov z kódu ve třídě `ThisDocument` nebo pomocí `Globals.ThisDocument` z kódu mimo `ThisDocument` třídu. Další informace najdete v tématu věnovaném [přizpůsobení na úrovni dokumentu programu](../vsto/programming-document-level-customizations.md). Chcete-li například vybrat první odstavec v dokumentu, použijte následující kód.

 [!code-vb[Trin_VstcoreWordAutomation#120](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#120)]
 [!code-csharp[Trin_VstcoreWordAutomation#120](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#120)]

 V projektech doplňku VSTO můžete v době běhu vygenerovat položky <xref:Microsoft.Office.Tools.Word.Document> hostitele. Vygenerovanou položku hostitele můžete použít k přidání ovládacích prvků do přidruženého dokumentu. Další informace najdete v tématu [rozšiřování dokumentů aplikace Word a sešitů aplikace Excel v doplňkech VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

### <a name="selection-object"></a>Objekt výběru
 Objekt <xref:Microsoft.Office.Interop.Word.Selection> představuje aktuálně vybranou oblast. Když provedete operaci v uživatelském rozhraní aplikace Word, například tučný text, vyberete nebo zvýrazníte text a pak použijete formátování. Objekt <xref:Microsoft.Office.Interop.Word.Selection> je vždy přítomen v dokumentu. Pokud není nic vybráno, představuje bod vložení. Kromě toho může výběr zahrnovat více bloků textu, které nejsou souvislé.

### <a name="range-object"></a>rozsah – objekt
 Objekt <xref:Microsoft.Office.Interop.Word.Range> představuje souvislou oblast v dokumentu a je definován počáteční polohou znaku a koncovou pozicí znaků. Nejste omezeni na jeden objekt <xref:Microsoft.Office.Interop.Word.Range>. V jednom dokumentu můžete definovat více objektů <xref:Microsoft.Office.Interop.Word.Range>. Objekt <xref:Microsoft.Office.Interop.Word.Range> má následující vlastnosti:

- Může se skládat pouze z bodu vložení, oblasti textu nebo celého dokumentu.

- Zahrnuje netiskové znaky, jako jsou mezery, znaky tabulátoru a značky odstavců.

- Může se jednat o oblast reprezentovanou aktuálním výběrem, nebo může představovat oblast odlišnou od aktuálního výběru.

- Není viditelný v dokumentu, na rozdíl od výběru, který je vždy viditelný.

- Není uložen s dokumentem a existuje pouze v případě, že kód je spuštěn.

  Když vložíte text na konci rozsahu, Word automaticky rozbalí rozsah tak, aby zahrnoval vložený text.

### <a name="content-control-objects"></a>Objekty ovládacího prvku obsahu
 <xref:Microsoft.Office.Interop.Word.ContentControl> poskytuje způsob, jak řídit vstup a prezentaci textu a dalších typů obsahu v dokumentech aplikace Word. <xref:Microsoft.Office.Interop.Word.ContentControl> může zobrazit několik různých typů uživatelského rozhraní, které jsou optimalizované pro použití v dokumentech aplikace Word, jako je například ovládací prvek formátovaného textu, výběr data nebo pole se seznamem. Můžete také použít <xref:Microsoft.Office.Interop.Word.ContentControl> a zabránit tak uživatelům v úpravách oddílů dokumentu nebo šablony.

 Visual Studio rozšiřuje objekt <xref:Microsoft.Office.Interop.Word.ContentControl> do několika různých hostitelských ovládacích prvků. Vzhledem k tomu, že objekt <xref:Microsoft.Office.Interop.Word.ContentControl> může zobrazit libovolný z různých typů uživatelského rozhraní, které jsou k dispozici pro ovládací prvky obsahu, Visual Studio poskytuje pro každý ovládací prvek obsahu jiný typ. Můžete například použít <xref:Microsoft.Office.Tools.Word.RichTextContentControl> k vytvoření ovládacího prvku s bohatou textem nebo můžete použít <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> k vytvoření výběru data. Tyto hostitelské ovládací prvky se chovají jako nativní <xref:Microsoft.Office.Interop.Word.ContentControl>, ale mají další události a funkce vazby dat. Další informace najdete v tématu [ovládací prvky obsahu](../vsto/content-controls.md).

### <a name="bookmark-object"></a>Objekt Bookmark
 Objekt <xref:Microsoft.Office.Interop.Word.Bookmark> představuje souvislou oblast v dokumentu s počáteční a koncovou pozicí. Můžete použít záložky k označení umístění v dokumentu nebo jako kontejneru pro text v dokumentu. Objekt <xref:Microsoft.Office.Interop.Word.Bookmark> může sestávat z bodu vložení nebo být stejně velký jako celý dokument. <xref:Microsoft.Office.Interop.Word.Bookmark> má následující vlastnosti, které se nastavují od objektu <xref:Microsoft.Office.Interop.Word.Range>:

- Záložku můžete pojmenovat v době návrhu.

- objekty <xref:Microsoft.Office.Interop.Word.Bookmark> jsou uloženy spolu s dokumentem, a proto nejsou odstraněny, když kód přestane běžet nebo je dokument uzavřený.

- Záložky lze skrýt nebo zviditelnit nastavením vlastnosti <xref:Microsoft.Office.Interop.Word.View.ShowBookmarks%2A> objektu <xref:Microsoft.Office.Interop.Word.View> na **hodnotu false** nebo **true**.

  Visual Studio rozšiřuje objekt <xref:Microsoft.Office.Interop.Word.Bookmark> tím, že poskytuje <xref:Microsoft.Office.Tools.Word.Bookmark> hostitelský ovládací prvek. <xref:Microsoft.Office.Tools.Word.Bookmark> hostitelský ovládací prvek se chová jako nativní <xref:Microsoft.Office.Interop.Word.Bookmark>, ale obsahuje další události a funkce vazby dat. Data můžete navazovat na ovládací prvek záložka v dokumentu stejným způsobem, jako svážete data s ovládacím prvkem textového pole ve formuláři Windows. Další informace naleznete v tématu [ovládací prvek Bookmark](../vsto/bookmark-control.md).

## <a name="WordOMDocumentation"></a>Použití dokumentace k objektovému modelu aplikace Word
 Úplné informace o objektovém modelu aplikace Word můžete odkazovat na odkaz na primární definiční sestavení (PIA) a odkaz na objektový model jazyk Visual Basic for Application (VBA).

### <a name="primary-interop-assembly-reference"></a>Odkaz na primární definiční sestavení
 Referenční dokumentace k aplikaci Word PIA popisuje typy v primárním sestavení vzájemné spolupráce pro Word. Tato dokumentace je k dispozici z následujícího umístění: [odkaz na primární definiční sestavení aplikace Word 2010](../vsto/office-primary-interop-assemblies.md).

 Další informace o návrhu aplikace Word PIA, jako jsou rozdíly mezi třídami a rozhraními PIA a jak jsou implementovány události v PIA, naleznete v tématu [Přehled tříd a rozhraní v primárních sestaveních vzájemné spolupráce pro systém Office](/previous-versions/office/office-12/ms247299(v=office.12)).

### <a name="vba-object-model-reference"></a>Referenční dokumentace modelu objektu VBA
 Odkaz model objektu VBA odkazuje na dokument objektový model aplikace Word, protože je vystavený pro kód VBA. Další informace najdete v tématu [referenční materiály k objektovému modelu Word 2010](/office/vba/api/overview/Word/object-model).

 Všechny objekty a členy v referenčním modelu objektu VBA odpovídají typům a členům ve slovech PIA. Například objekt dokumentu v odkazu modelu objektu VBA odpovídá objektu <xref:Microsoft.Office.Interop.Word.Document> ve slově PIA. I když odkaz na objektový model VBA poskytuje příklady kódu pro většinu vlastností, metod a událostí, je nutné překládat kód VBA v tomto odkazu na Visual Basic nebo vizuál C# , pokud je chcete použít v projektu aplikace Word, který vytvoříte pomocí sady Visual Studio. .

## <a name="see-also"></a>Viz také:
- [Sestavení primární spolupráce pro Office](../vsto/office-primary-interop-assemblies.md)
- [Automatizace Wordu pomocí rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)
- [Práce s dokumenty](../vsto/working-with-documents.md)
- [Práce s textem v dokumentech](../vsto/working-with-text-in-documents.md)
- [Práce s tabulkami](../vsto/working-with-tables.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
