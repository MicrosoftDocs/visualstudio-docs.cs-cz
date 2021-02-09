---
title: Automatizace Wordu pomocí rozšířených objektů
description: Přečtěte si, jak můžete pomocí hostitelských položek a hostitelských ovládacích prvků ve svých řešeních při vývoji řešení pro Word v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 42784e27c26d729a87d5363ca41b6d2c70a364d7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882502"
---
# <a name="automate-word-by-using-extended-objects"></a>Automatizace Wordu pomocí rozšířených objektů
  Při vývoji řešení aplikace Word v aplikaci Visual Studio můžete použít *hostitelské položky* a *hostitelské řízení* s ve vašich řešeních. Jedná se o objekty, které rozšířily určité běžně používané objekty v objektovém modelu aplikace Word (tj. objektový model, který je zveřejněn v rámci primárního definičního sestavení pro Word), jako jsou například <xref:Microsoft.Office.Interop.Word.Document> <xref:Microsoft.Office.Interop.Word.ContentControl> objekty a. Rozšířené objekty se chovají jako objekty aplikace Word, na kterých jsou založeny, ale přidávají do objektů další události a funkce vazby dat.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Hostitelské položky a hostitelské ovládací prvky jsou k dispozici v doplňcích VSTO i v přizpůsobení na úrovni dokumentu, i když kontext, ve kterém je lze použít, je pro každý typ řešení odlišný. Další informace naleznete v tématu [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).

## <a name="document-host-item"></a>Položka hostitele dokumentu
 Projekty aplikace Word poskytují přístup k <xref:Microsoft.Office.Tools.Word.Document> položce hostitele. <xref:Microsoft.Office.Tools.Word.Document>Hostitelská položka funguje jako kontejner pro jiné ovládací prvky, včetně hostitelských ovládacích prvků a model Windows Formsch ovládacích prvků, a udržuje informace o ovládacích prvcích na jeho povrchu. <xref:Microsoft.Office.Tools.Word.Document>Položka hostitele také poskytuje většinu stejných členů jako <xref:Microsoft.Office.Interop.Word.Document> třídu, která je odpovídající třídou v objektovém modelu aplikace Word.

 Další informace najdete v tématu [položka hostitele dokumentu](../vsto/document-host-item.md).

## <a name="word-host-controls"></a>hostitelské ovládací prvky aplikace Word
 Existuje několik ovládacích prvků pro hostování aplikace Word, které vám pomohou vytvořit, uspořádat a automatizovat dokumenty. Většina jejich funkcí zahrnuje import, prezentaci a ochranu dat. Tyto hostitelské ovládací prvky poskytují události a funkce vazby dat, které jejich protějšky v nativním objektovém modelu aplikace Word nemají.

 V projektech na úrovni dokumentu můžete do dokumentu přidat libovolný hostitelský ovládací prvek v době návrhu nebo můžete přidat ovládací prvky obsahu a ovládací prvky záložky za běhu. V projektech doplňku VSTO můžete přidat ovládací prvky obsahu a ovládací prvky záložek do libovolného otevřeného dokumentu v době běhu.

 Další informace o hostitelských ovládacích prvcích, které lze použít v projektech aplikace Word, naleznete v následujících tématech:

- [Ovládací prvky obsahu](../vsto/content-controls.md)

- [Ovládací prvek záložek](../vsto/bookmark-control.md)

- [XMLNode – ovládací prvek](../vsto/xmlnode-control.md)

- [Ovládací prvek XMLNodes](../vsto/xmlnodes-control.md)

## <a name="see-also"></a>Viz také
- [Postupy: Přidání ovládacích prvků obsahu do dokumentů aplikace Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Postupy: Přidání ovládacích prvků záložek do dokumentů aplikace Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Postupy: Přidání ovládacích prvků XMLNode do dokumentů aplikace Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)
- [Postupy: Přidání ovládacích prvků XMLNodes do dokumentů aplikace Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)
- [Postupy: Změna velikosti ovládacích prvků záložek](../vsto/how-to-resize-bookmark-controls.md)
- [Návod: Vytvoření šablony s použitím ovládacích prvků obsahu](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)
- [Návod: Svázání ovládacích prvků obsahu s vlastními částmi XML](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)
- [Návod: Vytvoření místních nabídek pro záložky](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)
- [Řešení pro Word](../vsto/word-solutions.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Rozšiřování dokumentů aplikace Word a excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
