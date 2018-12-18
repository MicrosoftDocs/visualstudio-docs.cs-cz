---
title: řešení pro aplikaci Word
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2b443cd985910cbb6e81ce79016193623bdeb2dd
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35675885"
---
# <a name="word-solutions"></a>řešení pro aplikaci Word
  Visual Studio obsahuje šablony projektů, které lze použít k vytvoření přizpůsobení na úrovni dokumentu a doplňky VSTO pro Microsoft Office Word. Tato řešení můžete použít k automatizaci aplikace Word rozšíření funkcí aplikace Word a přizpůsobení uživatelského rozhraní (UI) aplikace Word. Další informace o rozdílech mezi přizpůsobení na úrovni dokumentu a doplňky VSTO najdete v tématu [přehled vývoje řešení pro Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
> [!NOTE]  
>  Zajímá vás vývoj řešení, které rozšiřují Office prostředí napříč [více platforem](https://dev.office.com/add-in-availability)? Podívejte se na nové [Office Add-ins modelu](https://dev.office.com/docs/add-ins/overview/office-add-ins). Doplňky sady Office mají malé náklady v porovnání s doplňky VSTO a řešení a je můžete vytvořit s využitím téměř jakékoli webové programování technologie, jako je například HTML5, JavaScript, CSS3 a XML.  
  
 Toto téma poskytuje následující informace:  
  
-   [Automatizace aplikace Word](#automating).  
  
-   [Vývoj přizpůsobení na úrovni dokumentu pro Word](#doclevel).  
  
-   [Vývoj doplňků VSTO pro Word](#applevel).  
  
-   [Přizpůsobení uživatelského rozhraní aplikace Word](#UI).  
  
##  <a name="automating"></a> Automatizace aplikace Word  
 Objektový model aplikace Word poskytuje mnoho typů, které můžete použít k automatizaci aplikace Word. Například můžete můžete programově vytvářet tabulky, formátovat dokumenty a nastavit text podle oblastí a odstavců. Další informace najdete v tématu [přehled modelu objektů aplikace Word](../vsto/word-object-model-overview.md).  
  
 Při vývoji řešení aplikace Word v sadě Visual Studio, můžete použít také *hostovat položky* a *hostování ovládacích prvků* ve vašich řešeních. Jedná se o objekty, které rozšiřují některé běžně používané objekty v objektovém modelu aplikace Word, jako <xref:Microsoft.Office.Interop.Word.Document> a <xref:Microsoft.Office.Interop.Word.ContentControl> objekty. Rozšířené objekty se chovají jako objekty aplikace Word, které jsou založeny na, ale přidávají další události a možnosti vázání dat na objekty. Další informace najdete v tématu [automatizace aplikace Word s použitím rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md).  
  
##  <a name="doclevel"></a> Vývoj přizpůsobení na úrovni dokumentu pro Word  
 Přizpůsobení úrovni dokumentu pro aplikaci Microsoft Office Word obsahuje sestavení, který je spojen s určitým dokumentem. Sestavení obvykle rozšiřuje dokument přizpůsobením uživatelského rozhraní a automatizací aplikace Word. Na rozdíl od doplňku VSTO, který je spojen s aplikací Word samotnou, funkce, kterou implementujete ve vlastním nastavení je k dispozici pouze v případě, že související dokument je otevřen v aplikaci Word.  
  
 Chcete-li vytvořit projekt přizpůsobení na úrovni dokumentu pro Word, použijte šablony projektů dokument aplikace Word a šablona aplikace Word v **nový projekt** dialogové okno sady Visual Studio. Další informace najdete v tématu [postupy: vytvoření Office projekty v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Další informace o úpravách na úrovni dokumentu [architektura přizpůsobení na úrovni dokumentu](../vsto/architecture-of-document-level-customizations.md).  
  
### <a name="word-customization-programming-model"></a>Programovací model přizpůsobení Word  
 Při vytváření projektu úrovni dokumentu pro Word, aplikace Visual Studio vygeneruje třídy, nazvané `ThisDocument`, které jsou základem vašeho řešení. Tato třída reprezentuje dokument, který je přidružen k řešení, a poskytuje výchozí bod pro psaní kódu.  
  
 Další informace o `ThisDocument` třídy a další funkce můžete použít v projektu úrovni dokumentu naleznete v tématu [programování přizpůsobení na úrovni dokumentu](../vsto/programming-document-level-customizations.md).  
  
##  <a name="applevel"></a> Vývoj doplňků VSTO pro Word  
 Doplňku VSTO pro Microsoft Office Word obsahuje sestavení, který je načteno aplikací Word. Sestavení obvykle rozšiřuje aplikaci Word přizpůsobením uživatelského rozhraní a automatizací aplikace Word. Na rozdíl od přizpůsobení úrovni dokumentu, které je spojeno s určitým dokumentem, funkce, kterou implementujete v doplňku VSTO není omezeno na jeden dokument.  
  
 Chcete-li vytvořit projekt doplňku VSTO pro Word, použijte šablony projektů doplňků aplikace Word v **nový projekt** dialogové okno sady Visual Studio. Další informace najdete v tématu [postupy: vytvoření Office projekty v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Obecné informace o tom, jak fungují doplňků VSTO najdete v tématu [doplňků VSTO architektura](../vsto/architecture-of-vsto-add-ins.md).  
  
### <a name="word-add-in-programming-model"></a>Slova Add-in programovací model  
 Při vytváření projektu doplňku VSTO pro Word, aplikace Visual Studio vygeneruje třídy, nazvané `ThisAddIn`, které jsou základem vašeho řešení. Tato třída poskytuje výchozí bod pro psaní kódu a také poskytuje objektový model aplikace Word do vašeho doplňku VSTO.  
  
 Další informace o `ThisAddIn` třídy a další funkce můžete použít v VSTO Add-in, naleznete v tématu [doplňků Program VSTO](../vsto/programming-vsto-add-ins.md).  
  
##  <a name="UI"></a> Přizpůsobení uživatelského rozhraní aplikace Word  
 Existuje několik různých způsobů přizpůsobení uživatelského rozhraní aplikace Word. Některé možnosti jsou dostupné pro všechny typy projektů a další možnosti jsou k dispozici pouze pro doplňky VSTO nebo přizpůsobení na úrovni dokumentu.  
  
### <a name="options-for-all-project-types"></a>Možnosti pro všechny typy projektů  
 Následující tabulka uvádí možnosti vlastního nastavení, které jsou k dispozici pro přizpůsobení na úrovni dokumentu a doplňky VSTO.  
  
|Úloha|Další informace|  
|----------|--------------------------|  
|Přizpůsobení pásu karet.|[Přehled pásu karet](../vsto/ribbon-overview.md)|  
|Přidání ovládacích prvků Windows Forms nebo rozšířené ovládací prvky aplikace Word do přizpůsobeného dokumentu (pro přizpůsobení na úrovni dokumentu) nebo do libovolného otevřeného dokumentu (pro VSTO doplňku).|[Postupy: Přidání ovládacích prvků Windows Forms do dokumentů Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Postupy: Přidání ovládacích prvků obsahu do dokumentů aplikace Word](../vsto/how-to-add-content-controls-to-word-documents.md)<br /><br /> [Postupy: Přidání ovládacích prvků záložek do dokumentů aplikace Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)|  
  
### <a name="options-for-document-level-customizations"></a>Možnosti pro přizpůsobení na úrovni dokumentu  
 Následující tabulka uvádí možnosti vlastního nastavení, které jsou k dispozici jenom pro přizpůsobení na úrovni dokumentu.  
  
|Úloha|Další informace|  
|----------|--------------------------|  
|Přidání podokna akcí do dokumentů.|[Přehled podokna akcí](../vsto/actions-pane-overview.md)<br /><br /> [Postupy: Přidání podokna akcí do dokumentů aplikace Word nebo sešitů aplikace Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|  
|Přidejte rozšířené ovládací prvky XMLNode a XMLNodes na plochu dokumentu.|[Postupy: Přidání ovládacích prvků XMLNode do dokumentů aplikace Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)<br /><br /> [Postupy: Přidání ovládacích prvků XMLNodes do dokumentů aplikace Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)|  
  
### <a name="options-for-vsto-add-ins"></a>Možnosti pro doplňky VSTO  
 Následující tabulka uvádí možnosti vlastního nastavení, které jsou k dispozici pouze pro doplňky VSTO.  
  
|Úloha|Další informace|  
|----------|--------------------------|  
|Vytvoření vlastního podokna úloh.|[Vlastní podokna úloh](../vsto/custom-task-panes.md)|  
  
### <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Přehled modelu objektů aplikace Word](../vsto/word-object-model-overview.md)|Obsahuje přehled hlavních typů poskytnutý objektovým modelem aplikace Word.|  
|[Automatizace aplikace Word s použitím rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)|Poskytuje informace o rozšířených objektech (poskytovaných [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]), který vám pomůže v řešení aplikace Word.|  
|[Ovládací prvky Windows Forms na dokumenty Office – přehled](../vsto/windows-forms-controls-on-office-documents-overview.md)|Popisuje, jak přidat ovládací prvky Windows Forms do dokumentů aplikace Word.|  
|[Návod: Vytvoření prvního přizpůsobení na úrovni dokumentu pro Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)|Ukazuje, jak vytvořit základní přizpůsobení úrovni dokumentu pro aplikaci Word.|  
|[Návod: Vytvoření vašeho prvního doplňku VSTO pro Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)|Ukazuje, jak vytvořit základní Add-in VSTO pro Word.|  
|[Návod: Přidání ovládacích prvků do dokumentu za běhu v doplňku VSTO](../vsto/walkthrough-adding-controls-to-a-document-at-run-time-in-a-vsto-add-in.md)|Ukazuje, jak přidat Windows Forms button a <xref:Microsoft.Office.Tools.Word.RichTextContentControl> do dokumentu za běhu pomocí doplňku VSTO.|  
|[Word 2010 ve vývoji Office](http://go.microsoft.com/fwlink/?LinkId=199020)|Obsahuje odkazy na články a referenční dokumentaci o vývoji řešení aplikace Word (nezávislé na vývoj pro Office pomocí sady Visual Studio).|  
  
  