---
title: Položka hostitele dokumentu
description: Přečtěte si, že položka hostitele dokumentu je typ, který rozšiřuje typ dokumentu z primárního definičního sestavení pro Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio]
- documents [Office development in Visual Studio], document host items
- document host items
- Word [Office development in Visual Studio], Word documents
- Word [Office development in Visual Studio]
- Word documents
- host items [Office development in Visual Studio], Document
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b7eb29a9cae9e43bd0372088298d2bd6b122c7a1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910582"
---
# <a name="document-host-item"></a>Položka hostitele dokumentu
  <xref:Microsoft.Office.Tools.Word.Document>Položka hostitele je typ, který rozšiřuje <xref:Microsoft.Office.Interop.Word.Document> typ z primárního definičního sestavení pro Word. <xref:Microsoft.Office.Tools.Word.Document>Položka hostitele poskytuje všechny stejné vlastnosti, metody a události jako <xref:Microsoft.Office.Interop.Word.Document> objekt, ale také zpřístupňuje další události a funguje jako kontejner pro ovládací prvky hostitele a model Windows Forms ovládací prvky.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 V projektech na úrovni dokumentu je výchozí <xref:Microsoft.Office.Tools.Word.Document> Hostitelská položka, která představuje dokument v projektu. V projektech doplňku VSTO můžete v <xref:Microsoft.Office.Tools.Word.Document> době běhu generovat položky hostitele.

## <a name="understand-the-document-host-item-in-document-level-projects"></a>Pochopení položky hostitele dokumentu v projektech na úrovni dokumentu
 Pro přístup k dokumentu v projektu použijte `ThisDocument` třídu. Když vytvoříte projekt na úrovni dokumentu, aplikace Visual Studio vygeneruje `ThisDocument` třídu, která bude sloužit jako odkaz na komunikaci mezi Wordem a kódem vlastního nastavení. `ThisDocument`Třída poskytuje přístup ke členům <xref:Microsoft.Office.Tools.Word.Document> hostitelské položky k provádění základních úloh v přizpůsobení, jako je například spuštění kódu při otevření nebo zavření dokumentu. Můžete také použít třídu pro přidání ovládacích prvků do dokumentu. Kombinací různých sad ovládacích prvků a psaní kódu můžete navazovat ovládací prvky na data, shromažďovat informace od uživatele a reagovat na akce uživatele. Další informace najdete v tématu věnovaném [přizpůsobení na úrovni dokumentu programu](../vsto/programming-document-level-customizations.md).

 `ThisDocument`Třída poskytuje umístění, ve kterém můžete začít psát kód v projektu. Vzhledem k tomu, že třída poskytuje všechny stejné vlastnosti, metody a události jako <xref:Microsoft.Office.Interop.Word.Document> objekt v primárním sestavení vzájemné spolupráce pro Word, můžete použít také `ThisDocument` pro přístup k objektovému modelu aplikace Word. Další informace najdete v tématu [Přehled modelu objektů aplikace Word](../vsto/word-object-model-overview.md).

### <a name="limitations-of-the-document-host-item-in-document-level-projects"></a>Omezení položky hostitele dokumentu v projektech na úrovni dokumentu
 Projekt na úrovni dokumentu může obsahovat pouze jednu <xref:Microsoft.Office.Tools.Word.Document> položku hostitele (tj `ThisDocument` . třídu). Nové <xref:Microsoft.Office.Tools.Word.Document> položky hostitele nelze do projektu přidat v době návrhu a v době spuštění nelze vytvořit nové <xref:Microsoft.Office.Tools.Word.Document> položky hostitele z přizpůsobení na úrovni dokumentu.

 Pokud vytvoříte nový wordový dokument v době běhu, bude to typ <xref:Microsoft.Office.Interop.Word.Document> . Protože se nejedná o hostitelskou položku, nemůže obsahovat žádné ovládací prvky hostitele ani ovládací prvky model Windows Forms. Další informace o vytváření dokumentů za běhu najdete v tématu [Postupy: vytváření nových dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-create-new-documents.md).

## <a name="understand-document-host-items-in-application-level-projects"></a>Porozumění položkám hostitele dokumentů v projektech na úrovni aplikace
 V projektech doplňku VSTO můžete vygenerovat <xref:Microsoft.Office.Tools.Word.Document> položku hostitele v době běhu pro libovolný dokument, který je otevřen v aplikaci Word. Můžete použít <xref:Microsoft.Office.Tools.Word.Document> položku hostitele k přidání ovládacích prvků do přidruženého dokumentu nebo pro zpracování událostí, které nejsou k dispozici pro <xref:Microsoft.Office.Interop.Word.Document> objekty.

 Chcete-li vygenerovat <xref:Microsoft.Office.Tools.Word.Document> položku hostitele, použijte `GetVstoObject` metodu. Další informace najdete v tématu [rozšiřování dokumentů aplikace Word a sešitů aplikace Excel v doplňkech VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="see-also"></a>Viz také
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Automatizace Wordu pomocí rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)
- [Přehled modelu objektů aplikace Word](../vsto/word-object-model-overview.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Rozšiřování dokumentů aplikace Word a excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
