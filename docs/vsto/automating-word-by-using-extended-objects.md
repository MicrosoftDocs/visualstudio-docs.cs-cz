---
title: Automatizace aplikace Word s použitím rozšířených objektů
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], automating
- extended objects [Office development in Visual Studio], Word
- automation [Office development in Visual Studio], Word
- host items [Office development in Visual Studio], Word
- automating Word
- controls [Office development in Visual Studio], Word host controls
- host controls, Word
- host controls [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], host controls
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 85d3adc2ff156f6967d7590788c749d0343c7c0f
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248147"
---
# <a name="automate-word-by-using-extended-objects"></a>Automatizace aplikace Word s použitím rozšířených objektů
  Při vývoji řešení aplikace Word v sadě Visual Studio, můžete použít *hostovat položky* a *hostování ovládacího prvku*s ve vašich řešeních. Jedná se o objekty, které rozšiřují některé běžně používané objekty v objektovém modelu aplikace Word (to znamená, objektový model, který je zveřejněný prostřednictvím primárních sestavení vzájemné spolupráce pro aplikaci Word), například <xref:Microsoft.Office.Interop.Word.Document> a <xref:Microsoft.Office.Interop.Word.ContentControl> objekty. Rozšířené objekty se chovají jako objekty aplikace Word, které jsou založeny na, ale přidávají další události a možnosti vázání dat na objekty.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Hostitelských položek a hostitelských ovládacích prvků jsou k dispozici v doplňcích VSTO a přizpůsobení na úrovni dokumentu, i když se liší pro každý typ řešení kontext, ve kterém ty je možné použít. Další informace najdete v tématu [hostovat položky a hostujte Přehled ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).  
  
## <a name="document-host-item"></a>Hostitelská položka Document  
 Projekty vám poskytnou přístup k aplikaci Word <xref:Microsoft.Office.Tools.Word.Document> hostitelský objekt. <xref:Microsoft.Office.Tools.Word.Document> Hostitelský objekt funguje jako kontejner pro ostatní ovládací prvky, včetně hostitelské ovládací prvky a ovládací prvky Windows Forms, a udržuje informace o ovládacích prvcích na svém povrchu. <xref:Microsoft.Office.Tools.Word.Document> Hostitelský objekt také poskytuje většinu stejné členy jako <xref:Microsoft.Office.Interop.Word.Document> třídy, která je odpovídající třídou v objektovém modelu aplikace Word.  
  
 Další informace najdete v tématu [hostitelská položka Document](../vsto/document-host-item.md).  
  
## <a name="word-host-controls"></a>hostitelské ovládací prvky aplikace Word  
 Existuje několik hostitelů ovládací prvky pro aplikaci Word, které vám pomůžou vytvořit, uspořádání a automatizovat dokumenty. Většina jejich funkce zahrnuje import, prezentování a chrání data. Tyto ovládací prvky hostitele poskytnout události a datové vazby, které nemají jejich protějšky v nativní objektovému modelu Wordu.  
  
 V projektech na úrovni dokumentu můžete přidat libovolný ovládací prvek hostitele do dokumentu v době návrhu nebo za běhu můžete přidat ovládací prvky obsahu a ovládacích prvků záložek. V doplňku VSTO projektů můžete přidat ovládací prvky obsahu a ovládacích prvků záložek do libovolného otevřeného dokumentu za běhu.  
  
 Další informace o hostitelské ovládací prvky, které můžete použít v projektech aplikace Word naleznete v následujících tématech:  
  
-   [Ovládací prvky obsahu](../vsto/content-controls.md)  
  
-   [BOOKMARK – ovládací prvek](../vsto/bookmark-control.md)  
  
-   [XmlNode – ovládací prvek](../vsto/xmlnode-control.md)  
  
-   [XmlNodes – ovládací prvek](../vsto/xmlnodes-control.md)  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: Přidání ovládacích prvků obsahu do dokumentů aplikace Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Postupy: Přidání ovládacích prvků záložek do dokumentů aplikace Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Postupy: Přidání ovládacích prvků XMLNode do dokumentů aplikace Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [Postupy: Přidání ovládacích prvků XMLNodes do dokumentů aplikace Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [Postupy: Změna velikosti ovládacích prvků záložek](../vsto/how-to-resize-bookmark-controls.md)   
 [Návod: Vytvoření šablony s použitím ovládacích prvků obsahu](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)   
 [Návod: Vytvoření vazby ovládacích prvků obsahu do vlastní části XML](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)   
 [Návod: Vytváření místních nabídek pro záložky](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Řešení aplikace Word](../vsto/word-solutions.md)   
 [Přehled ovládacích prvků hostitele a hostitelské položky](../vsto/host-items-and-host-controls-overview.md)   
 [Programová omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Rozšíření dokumentů aplikace Word a sešitů aplikace Excel v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
  
  