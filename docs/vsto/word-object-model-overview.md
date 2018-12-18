---
title: Přehled modelu objektů aplikace Word
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 75a5f8e79bbd6dd34b046cbff6d59844a977efb3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49878008"
---
# <a name="word-object-model-overview"></a>Přehled modelu objektů aplikace Word
  Při vývoji řešení aplikace Word v sadě Visual Studio, budete moct používat objektovému modelu Wordu. Tento objektový model se skládá z třídy a rozhraní, které jsou k dispozici ve primárního spolupracujícího sestavení pro aplikaci Word a jsou definovány v <xref:Microsoft.Office.Interop.Word> oboru názvů.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Toto téma nabízí stručný přehled modelu objektů aplikace Word. Prostředky, kde můžete dozvědět více o celé objektovému modelu Wordu, naleznete v tématu [dokumentace modelu objektu slovo](#WordOMDocumentation).  
  
 Informace o používání objektovému modelu Wordu k provádění konkrétních úkolů naleznete v následujících tématech:  
  
-   [Práce s dokumenty](../vsto/working-with-documents.md)  
  
-   [Práce s textem v dokumentech](../vsto/working-with-text-in-documents.md)  
  
-   [Práce s tabulkami](../vsto/working-with-tables.md)  
  
##  <a name="understanding"></a> Pochopení modelu objektů aplikace Word  
 Aplikace Word poskytuje stovky objektů, se kterými můžete pracovat. Tyto objekty jsou uspořádány do hierarchie, která přesně dodržuje uživatelského rozhraní. V horní části hierarchie <xref:Microsoft.Office.Interop.Word.Application> objektu. Tento objekt představuje aktuální instanci aplikace Word. <xref:Microsoft.Office.Interop.Word.Application> Obsahuje objekt <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Word.Selection>, <xref:Microsoft.Office.Interop.Word.Bookmark>, a <xref:Microsoft.Office.Interop.Word.Range> objekty. Každý z těchto objektů má mnoho metod a vlastností, kterým můžete přistupovat k manipulaci s a interaktivně pracovat s objektem.  
  
 Následující obrázek znázorňuje jedno zobrazení těchto objektů v hierarchii objektovému modelu Wordu.  
  
 ![Objektový Model aplikace Word obrázek](../vsto/media/wrwordobjectmodel.gif "obrázek objektový Model aplikace Word")  
  
 Objekty na první pohled se překrývají. Například <xref:Microsoft.Office.Interop.Word.Document> a <xref:Microsoft.Office.Interop.Word.Selection> oba členy jsou objekty <xref:Microsoft.Office.Interop.Word.Application> objektu, ale <xref:Microsoft.Office.Interop.Word.Document> objektu je také členem skupiny <xref:Microsoft.Office.Interop.Word.Selection> objektu. Jak <xref:Microsoft.Office.Interop.Word.Document> a <xref:Microsoft.Office.Interop.Word.Selection> objekty obsahují <xref:Microsoft.Office.Interop.Word.Bookmark> a <xref:Microsoft.Office.Interop.Word.Range> objekty. Překrytí existuje, protože existuje více způsobů přistupujete stejný typ objektu. Například můžete použít formátování <xref:Microsoft.Office.Interop.Word.Range> objekt; ale může být vhodné pro přístup k rozsahu aktuálního výběru, v konkrétním odstavci, oddílu nebo celého tohoto dokumentu.  
  
 Následující části stručně popisují nejvyšší úrovně objektů a jejich vzájemné interakce mezi sebou. Mezi tyto objekty patří následujících pět:  
  
- Objekt aplikace  
  
- Objekt dokumentu  
  
- Výběr objektu  
  
- rozsah – objekt  
  
- Objekt (záložky)  
  
  Kromě objektovému modelu Wordu projektech pro systém Office v sadě Visual Studio poskytují *hostovat položky* a *hostování ovládacích prvků* , které rozšiřují některé objekty v objektovém modelu aplikace Word. Hostitelských položek a hostitelských ovládacích prvků se chovat jako objekty aplikace Word, které jejich rozšíření, ale mají také další funkce, jako jsou datové vazby funkce a další události. Další informace najdete v tématu [automatizace aplikace Word s použitím rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md) a [hostovat položky a hostujte Přehled ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).  
  
### <a name="application-object"></a>Objekt aplikace  
 <xref:Microsoft.Office.Interop.Word.Application> Objekt představuje aplikace Word a je nadřazeného člena všechny ostatní objekty. Jeho členy obvykle platí pro aplikaci Word jako celek. Jeho vlastnostem a metodám můžete použít k řízení prostředí aplikace Word.  
  
 Projekty doplňků VSTO, dostanete <xref:Microsoft.Office.Interop.Word.Application> s použitím `Application` pole `ThisAddIn` třídy. Další informace najdete v tématu [doplňků Program VSTO](../vsto/programming-vsto-add-ins.md).  
  
 V projektech na úrovni dokumentu, dostanete <xref:Microsoft.Office.Interop.Word.Application> s použitím <xref:Microsoft.Office.Tools.Word.Document.Application%2A> vlastnost `ThisDocument` třídy.  
  
### <a name="document-object"></a>Objekt dokumentu  
 <xref:Microsoft.Office.Interop.Word.Document> Objektu je zásadním programovací slova. Představuje dokument a veškerý jeho obsah. Při otevření dokumentu nebo vytvořit nový dokument, vytvoříte nový <xref:Microsoft.Office.Interop.Word.Document> objektu, který je přidán do <xref:Microsoft.Office.Interop.Word.Documents> kolekce <xref:Microsoft.Office.Interop.Word.Application> objektu. Dokument, který má fokus se nazývá aktivní dokument. Je reprezentován <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> vlastnost <xref:Microsoft.Office.Interop.Word.Application> objektu.  
  
 Vývojářské nástroje balíku Office v sadě Visual Studio rozšířit <xref:Microsoft.Office.Interop.Word.Document> objekt tím, že poskytuje <xref:Microsoft.Office.Tools.Word.Document> typu. Tento typ je *hostitelský objekt* , který poskytuje přístup ke všem funkcím <xref:Microsoft.Office.Interop.Word.Document> objektu a přidá další události a možnost přidávat spravované ovládací prvky.  
  
 Při vytváření projektu úrovni dokumentu, dostanete <xref:Microsoft.Office.Tools.Word.Document> členy s použitím vytvořeného `ThisDocument` třídu ve vašem projektu. Můžete přístup ke členům v <xref:Microsoft.Office.Tools.Word.Document> hostitelský objekt s použitím **mě** nebo **to** klíčová slova z kódu v `ThisDocument` třídy, nebo pomocí `Globals.ThisDocument` z kódu mimo `ThisDocument` Třída. Další informace najdete v tématu [programování přizpůsobení na úrovni dokumentu](../vsto/programming-document-level-customizations.md). Například vyberte první odstavec v dokumentu, použijte následující kód.  
  
 [!code-vb[Trin_VstcoreWordAutomation#120](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#120)]
 [!code-csharp[Trin_VstcoreWordAutomation#120](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#120)]  
  
 V doplňku VSTO projektů, můžete vygenerovat <xref:Microsoft.Office.Tools.Word.Document> hostovat položky v době běhu. Vygenerovaný hostitelský objekt můžete použít k přidávání ovládacích prvků přidružený dokument. Další informace najdete v tématu [rozšíření Wordových dokumentů a Excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
### <a name="selection-object"></a>Výběr objektu  
 <xref:Microsoft.Office.Interop.Word.Selection> Objekt představuje oblasti, která aktuálně není vybrán. Při provádění operace v uživatelském rozhraní aplikace Word, jako je text tučné, vyberte, nebo označte text a pak použít formátování. <xref:Microsoft.Office.Interop.Word.Selection> Objektu je vždy přítomna v dokumentu. Pokud není nic vybráno, ho reprezentuje bod vložení. Kromě toho výběr může zahrnovat více bloky textu, které nejsou souvislé.  
  
### <a name="range-object"></a>rozsah – objekt  
 <xref:Microsoft.Office.Interop.Word.Range> Objekt představuje souvislý oblast v dokumentu a je definován tak, že počáteční pozici znaku a koncové pozici znaku. Nejste omezeni do jediné <xref:Microsoft.Office.Interop.Word.Range> objektu. Můžete definovat více <xref:Microsoft.Office.Interop.Word.Range> objekty ve stejném dokumentu. A <xref:Microsoft.Office.Interop.Word.Range> objektu má následující vlastnosti:  
  
- To se může skládat z kurzor samostatně, rozsah textu nebo celý dokument.  
  
- Zahrnuje netisknutelné znaky, jako jsou mezery, tabulátory a odstavců.  
  
- Může být reprezentována aktuální výběr oblasti nebo může představovat oblasti liší od aktuální výběr.  
  
- Není viditelné v dokumentu, na rozdíl od určitého výběru, který je vždycky viditelný.  
  
- S dokumentem se neuloží a existuje pouze, když je kód spuštěn.  
  
  Při vložení textu na konci rozsahu slovo automaticky rozbalí rozsahu, který chcete zahrnout byl vložen text.  
  
### <a name="content-control-objects"></a>Ovládací prvek obsahu objektů  
 A <xref:Microsoft.Office.Interop.Word.ContentControl> poskytuje způsob, jak určovat, vstupu a prezentace textu a jiné typy obsahu do dokumentů aplikace Word. A <xref:Microsoft.Office.Interop.Word.ContentControl> může zobrazit několik různých typů uživatelského rozhraní, které jsou optimalizovány pro použití v dokumentech aplikace Word, jako je například ovládací prvek RTF, výběr data nebo pole se seznamem. Můžete také použít <xref:Microsoft.Office.Interop.Word.ContentControl> zabránit uživatelům v úpravách oddílů dokumentu nebo šablony.  
  
 Visual Studio rozšiřuje <xref:Microsoft.Office.Interop.Word.ContentControl> objektu do několika různých hostitelských ovládacích prvků. Vzhledem k tomu <xref:Microsoft.Office.Interop.Word.ContentControl> objektu lze zobrazit některé z různých typů uživatelského rozhraní, které jsou k dispozici pro ovládací prvky obsahu, Visual Studio obsahuje jiný typ pro každý ovládací prvek. Například můžete použít <xref:Microsoft.Office.Tools.Word.RichTextContentControl> můžete použít k vytvoření formátovaného textu ovládacího prvku, nebo <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> vytvoření ovládacího prvku pro výběr data. Tyto hostitelské ovládací prvky se chovat jako nativní <xref:Microsoft.Office.Interop.Word.ContentControl>, ale mají další události a datové vazby funkce. Další informace najdete v tématu [ovládací prvky obsahu](../vsto/content-controls.md).  
  
### <a name="bookmark-object"></a>Objekt (záložky)  
 <xref:Microsoft.Office.Interop.Word.Bookmark> Objekt představuje souvislý oblast v dokumentu, s počáteční pozice a koncovou pozicí. Záložky můžete použít k označení umístění v dokumentu, nebo jako kontejner pro text v dokumentu. A <xref:Microsoft.Office.Interop.Word.Bookmark> objekt může skládat z bodu vložení nebo být velké až celý dokument. A <xref:Microsoft.Office.Interop.Word.Bookmark> má následující vlastnosti, které smí z nastavit <xref:Microsoft.Office.Interop.Word.Range> objektu:  
  
- Název záložky můžete v době návrhu.  
  
- <xref:Microsoft.Office.Interop.Word.Bookmark> objekty se uloží do dokumentu a proto nebudou odstraněny při kód přestane fungovat nebo zavření dokumentu.  
  
- Záložky lze skrytý nebo zviditelnit nastavením <xref:Microsoft.Office.Interop.Word.View.ShowBookmarks%2A> vlastnost <xref:Microsoft.Office.Interop.Word.View> objektu **false** nebo **true**.  
  
  Visual Studio rozšiřuje <xref:Microsoft.Office.Interop.Word.Bookmark> objekt tím, že poskytuje <xref:Microsoft.Office.Tools.Word.Bookmark> hostování ovládacího prvku. <xref:Microsoft.Office.Tools.Word.Bookmark> Hostitelského ovládacího prvku se chová stejně jako nativní <xref:Microsoft.Office.Interop.Word.Bookmark>, ale platí další události a datové vazby funkce. Data lze svázat ovládací prvek bookmark dokumentu stejným způsobem jako svázat data s ovládacího prvku textového pole ve formuláři Windows. Další informace najdete v tématu [Bookmark – ovládací prvek](../vsto/bookmark-control.md).  
  
##  <a name="WordOMDocumentation"></a> Pomocí dokumentace modelu objektu aplikace Word  
 Podrobnější informace o objektovému modelu Wordu mohou odkazovat na referenční primární sestavení vzájemné spolupráce (PIA) aplikace Word a Visual Basic for Applications (VBA) referenční dokumentace modelu objektu.  
  
### <a name="primary-interop-assembly-reference"></a>Odkaz na primární spolupracující sestavení  
 Referenční dokumentaci slovo PIA popisují typy ve primárního spolupracujícího sestavení pro aplikaci Word. Tato dokumentace je k dispozici z následujícího umístění: [odkaz na primární spolupracující sestavení aplikace Word 2010](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
 Další informace o návrhu aplikace Word PIA, jako jsou rozdíly mezi třídami a rozhraní v PIA a jak jsou implementované událostí v PIA, naleznete v tématu [přehled třídy a rozhraní v primární spolupracující sestavení Office](http://go.microsoft.com/fwlink/?LinkId=189592).  
  
### <a name="vba-object-model-reference"></a>Referenční dokumentace objektového modelu VBA  
 Referenční dokumentace objektového modelu VBA dokumenty objektový model aplikace Word, jako je vystavená pro kód VBA. Další informace najdete v tématu [referenční dokumentace objektového modelu Wordu 2010](http://go.microsoft.com/fwlink/?LinkId=199772).  
  
 Všechny objekty a členy v referenční dokumentace objektového modelu VBA odpovídají typy a členy v aplikaci Word PIA. Například objekt dokumentu v referenční dokumentace objektového modelu VBA odpovídá <xref:Microsoft.Office.Interop.Word.Document> objektu ve Wordu PIA. I když referenční dokumentace objektového modelu VBA poskytuje příklady kódu pro většinu vlastnosti, metody a události, musí překládat kód VBA v této referenční dokumentace jazyka Visual Basic nebo Visual C# Pokud budete chtít použít v projektu aplikace Word, který vytvoříte pomocí sady Visual Studio .  
  
## <a name="see-also"></a>Viz také:  
 [Primární spolupracující sestavení Office](../vsto/office-primary-interop-assemblies.md)   
 [Automatizace aplikace Word s použitím rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)   
 [Práce s dokumenty](../vsto/working-with-documents.md)   
 [Práce s textem v dokumentech](../vsto/working-with-text-in-documents.md)   
 [Práce s tabulkami](../vsto/working-with-tables.md)   
 [Přehled ovládacích prvků hostitele a hostitelské položky](../vsto/host-items-and-host-controls-overview.md)   
 [Programová omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  