---
title: řešení pro aplikaci Word
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], Word
- Office projects [Office development in Visual Studio], Word
- application-level add-ins [Office development in Visual Studio], Word
- Word [Office development in Visual Studio]
- projects [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], about Word solutions
- Office solutions [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], application-level add-ins
- documents [Office development in Visual Studio], Word
- Office development in Visual Studio, Word solutions
- add-ins [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], document-level customizations
- user interfaces [Office development in Visual Studio], Word
- Office documents [Office development in Visual Studio, Word
- document-level customizations [Office development in Visual Studio], Word
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3cef71cc5f6c4e25d04e6045be7059d81c06b484
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254944"
---
# <a name="word-solutions"></a>řešení pro aplikaci Word
  Visual Studio poskytuje projektové šablony, které můžete použít k vytvoření přizpůsobení na úrovni dokumentu a doplňku VSTO pro systém Microsoft Office Word. Tato řešení můžete použít k automatizaci aplikace Word, rozšiřování funkcí aplikace Word a přizpůsobení uživatelského rozhraní (UI) aplikace Word. Další informace o rozdílech mezi přizpůsobení na úrovni dokumentu a doplňky VSTO najdete v tématu [přehled vývoje řešení pro Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Toto téma poskytuje následující informace:

- [Automatizuje Word](#automating).

- [Vývoj přizpůsobení na úrovni dokumentu pro Word](#doclevel)

- [Vývoj doplňků VSTO pro Word](#applevel)

- [Přizpůsobení uživatelského rozhraní aplikace Word](#UI).

## <a name="automating"></a>Automatizace Wordu
 Objektový model aplikace Word zpřístupňuje mnoho typů, které lze použít k automatizaci aplikace Word. Můžete například programově vytvářet tabulky, formátovat dokumenty a nastavovat text v oblastech a odstavcích. Další informace najdete v tématu [Přehled modelu objektů aplikace Word](../vsto/word-object-model-overview.md).

 Při vývoji řešení aplikace Word v aplikaci Visual Studio můžete také použít *položky hostitele* a *hostitelské ovládací prvky* ve vašich řešeních. Jedná se o <xref:Microsoft.Office.Interop.Word.Document> objekty, které rozšířily určité běžně používané objekty v objektovém modelu aplikace Word, <xref:Microsoft.Office.Interop.Word.ContentControl> například objekty a. Rozšířené objekty se chovají jako objekty aplikace Word, na kterých jsou založeny, ale přidávají do objektů další události a funkce vazby dat. Další informace najdete v tématu [Automatizace Wordu pomocí rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md).

## <a name="doclevel"></a>Vývoj přizpůsobení na úrovni dokumentu pro Word
 Přizpůsobení na úrovni dokumentu pro systém Microsoft Office Word sestává ze sestavení, které je spojeno s určitým dokumentem. Sestavení obvykle rozšiřuje dokument přizpůsobením uživatelského rozhraní a automatizací aplikace Word. Na rozdíl od doplňku VSTO, který je spojen s samotným slovem, je funkce, kterou implementujete v rámci přizpůsobení, dostupná pouze v případě, že je přidružený dokument otevřen v aplikaci Word.

 Chcete-li vytvořit projekt přizpůsobení na úrovni dokumentu pro aplikaci Word, použijte šablony projektu aplikace Word nebo šablony aplikace Word v dialogovém okně **Nový projekt** aplikace Visual Studio. Další informace najdete v tématu [jak: Vytváření projektů Office v sadě Visual](../vsto/how-to-create-office-projects-in-visual-studio.md)Studio.

 Další informace o tom, jak přizpůsobení na úrovni dokumentu fungují, je [Architektura přizpůsobení na úrovni dokumentu](../vsto/architecture-of-document-level-customizations.md).

### <a name="word-customization-programming-model"></a>Programovací model přizpůsobení aplikace Word
 Když vytvoříte projekt na úrovni dokumentu pro aplikaci Word, aplikace Visual Studio vygeneruje třídu, která `ThisDocument`je volána, což je základem vašeho řešení. Tato třída představuje dokument, který je spojen s vaším řešením, a poskytuje výchozí bod pro psaní kódu.

 Další informace o `ThisDocument` třídě a dalších funkcích, které můžete použít v projektu na úrovni dokumentu, najdete v tématu věnovaném [přizpůsobení na úrovni dokumentu programu](../vsto/programming-document-level-customizations.md).

## <a name="applevel"></a>Vývoj doplňků VSTO pro Word
 Doplněk VSTO pro systém Microsoft Office Word se skládá ze sestavení, které je načtené pomocí Wordu. Sestavení obvykle rozšiřuje Word přizpůsobením uživatelského rozhraní a automatizací aplikace Word. Na rozdíl od přizpůsobení na úrovni dokumentu, které je přidruženo k určitému dokumentu, funkce, které implementujete v doplňku VSTO, nejsou omezeny na žádný jednotlivý dokument.

 Chcete-li vytvořit projekt doplňku VSTO pro Word, použijte šablony projektu doplňku aplikace Word v dialogovém okně **Nový projekt** aplikace Visual Studio. Další informace najdete v tématu [jak: Vytváření projektů Office v sadě Visual](../vsto/how-to-create-office-projects-in-visual-studio.md)Studio.

 Obecné informace o tom, jak fungují doplňků VSTO najdete v tématu [doplňků VSTO architektura](../vsto/architecture-of-vsto-add-ins.md).

### <a name="word-add-in-programming-model"></a>Programovací model doplňku aplikace Word
 Když vytvoříte projekt doplňku VSTO pro Word, aplikace Visual Studio vygeneruje třídu, která je `ThisAddIn`volána, což je základem vašeho řešení. Tato třída poskytuje výchozí bod pro psaní kódu a také zpřístupňuje objektový model aplikace Word doplňku VSTO.

 Další informace o `ThisAddIn` třídě a dalších funkcích, které můžete použít v doplňku VSTO, najdete v tématu [Programová doplňky VSTO](../vsto/programming-vsto-add-ins.md).

## <a name="UI"></a>Přizpůsobení uživatelského rozhraní Wordu
 Existuje několik různých způsobů, jak přizpůsobit uživatelské rozhraní aplikace Word. Některé možnosti jsou dostupné pro všechny typy projektů a další možnosti jsou k dispozici pouze pro doplňky VSTO nebo přizpůsobení na úrovni dokumentu.

### <a name="options-for-all-project-types"></a>Možnosti pro všechny typy projektů
 Následující tabulka uvádí možnosti vlastního nastavení, které jsou k dispozici pro přizpůsobení na úrovni dokumentu a doplňky VSTO.

|Úloha|Další informace|
|----------|--------------------------|
|Přizpůsobení pásu karet.|[Přehled pásu karet](../vsto/ribbon-overview.md)|
|Přidejte ovládací prvky model Windows Forms nebo rozšířené aplikace Word do přizpůsobeného dokumentu (pro přizpůsobení na úrovni dokumentu) nebo do libovolného otevřeného dokumentu (pro doplněk VSTO).|[Postupy: Přidání ovládacích prvků model Windows Forms do dokumentů Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Postupy: Přidání ovládacích prvků obsahu do dokumentů aplikace Word](../vsto/how-to-add-content-controls-to-word-documents.md)<br /><br /> [Postupy: Přidání ovládacích prvků záložek do dokumentů aplikace Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)|

### <a name="options-for-document-level-customizations"></a>Možnosti pro přizpůsobení na úrovni dokumentu
 Následující tabulka uvádí možnosti vlastního nastavení, které jsou k dispozici jenom pro přizpůsobení na úrovni dokumentu.

|Úloha|Další informace|
|----------|--------------------------|
|Přidejte podokno akcí do dokumentu.|[Přehled podokna akcí](../vsto/actions-pane-overview.md)<br /><br /> [Postupy: Přidání podokna akcí do dokumentů aplikace Word nebo sešitů aplikace Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|
|Přidejte rozšířené ovládací prvky XMLNode a XMLNodes na plochu dokumentu.|[Postupy: Přidání ovládacích prvků XMLNode do dokumentů aplikace Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)<br /><br /> [Postupy: Přidání ovládacích prvků XMLNodes do dokumentů aplikace Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)|

### <a name="options-for-vsto-add-ins"></a>Možnosti pro doplňky VSTO
 Následující tabulka uvádí možnosti vlastního nastavení, které jsou k dispozici pouze pro doplňky VSTO.

|Úloha|Další informace|
|----------|--------------------------|
|Vytvoření vlastního podokna úloh.|[Vlastní podokna úloh](../vsto/custom-task-panes.md)|

### <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Přehled modelu objektů aplikace Word](../vsto/word-object-model-overview.md)|Poskytuje přehled hlavních typů poskytovaných objektovým modelem aplikace Word.|
|[Automatizace Wordu pomocí rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)|Poskytuje informace o rozšířených objektech (poskytovaných [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]), které můžete použít v řešeních aplikace Word.|
|[Ovládací prvky Windows Forms na dokumenty Office – přehled](../vsto/windows-forms-controls-on-office-documents-overview.md)|Popisuje, jak lze přidat ovládací prvky model Windows Forms do dokumentů aplikace Word.|
|[Návod: Vytvoření prvního přizpůsobení na úrovni dokumentu pro Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)|Ukazuje, jak vytvořit základní přizpůsobení na úrovni dokumentu pro aplikaci Word.|
|[Návod: Vytvoření prvního doplňku VSTO pro Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)|Ukazuje, jak vytvořit základní doplněk VSTO pro Word.|
|[Návod: Přidání ovládacích prvků do dokumentu za běhu v doplňku VSTO](../vsto/walkthrough-adding-controls-to-a-document-at-run-time-in-a-vsto-add-in.md)|Ukazuje, jak přidat model Windows Forms tlačítko a <xref:Microsoft.Office.Tools.Word.RichTextContentControl> k dokumentu v době běhu pomocí doplňku VSTO.|
|[Word 2010 ve vývoji pro Office](http://go.microsoft.com/fwlink/?LinkId=199020)|Obsahuje odkazy na články a referenční dokumentaci týkající se vývoje řešení pro aplikace Word (není specifické pro vývoj pro Office pomocí sady Visual Studio).|
