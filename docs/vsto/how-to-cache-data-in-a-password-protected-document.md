---
title: 'Postupy: ukládání dat do mezipaměti v dokumentu chráněném heslem'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], protected documents
- datasets [Office development in Visual Studio], caching
- data [Office development in Visual Studio], caching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 12b04b985d54161343d26cdd32178b67bd6e6b91
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547235"
---
# <a name="how-to-cache-data-in-a-password-protected-document"></a>Postupy: ukládání dat do mezipaměti v dokumentu chráněném heslem
  Pokud přidáte data do mezipaměti dat v dokumentu nebo sešitu chráněném heslem, změny v uložených datech se neukládají automaticky. Změny dat uložených v mezipaměti můžete uložit přepsáním dvou metod v projektu.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="caching-in-word-documents"></a>Ukládání do mezipaměti v dokumentech aplikace Word

### <a name="to-cache-data-in-a-word-document-that-is-protected-with-a-password"></a>Ukládání dat do mezipaměti v dokumentu aplikace Word chráněném heslem

1. Ve `ThisDocument` třídě označte veřejné pole nebo vlastnost, které mají být uloženy do mezipaměti. Další informace najdete v tématu [cache data](../vsto/caching-data.md).

2. Přepsat <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> metodu ve `ThisDocument` třídě a odebrat ochranu z dokumentu.

     Po uložení dokumentu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] voláním této metody poskytnete možnost zrušit ochranu dokumentu. To umožňuje uložení změn dat v mezipaměti.

3. Přepsat <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> metodu ve `ThisDocument` třídě a znovu použít ochranu pro dokument.

     Po uložení dokumentu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] voláním této metody poskytnete možnost znovu použít ochranu k dokumentu.

### <a name="example"></a>Příklad
 Následující příklad kódu ukazuje, jak ukládat data do mezipaměti v dokumentu aplikace Word, který je chráněn heslem. Před tím, než kód odstraní ochranu v <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> metodě, uloží aktuální <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A> hodnotu, aby bylo možné v metodě znovu použít stejný typ ochrany <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> .

 [!code-csharp[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedDocument/ThisDocument.cs#1)]
 [!code-vb[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedDocument/ThisDocument.vb#1)]

### <a name="compile-the-code"></a>Kompilovat kód
 Přidejte tento kód do `ThisDocument` třídy v projektu. Tento kód předpokládá, že heslo je uloženo v poli s názvem `securelyStoredPassword` .

## <a name="cache-in-excel-workbooks"></a>Mezipaměť v sešitech aplikace Excel
 V projektech aplikace Excel je tento postup nutný pouze v případě, že chráníte celý sešit pomocí hesla pomocí <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> metody. Tento postup není nutný, Pokud chráníte pouze konkrétní list s heslem pomocí <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> metody.

### <a name="to-cache-data-in-an-excel-workbook-that-is-protected-with-a-password"></a>Ukládání dat do mezipaměti v excelovém sešitu, který je chráněný heslem

1. Ve `ThisWorkbook` třídě nebo jedné z `Sheet` tříd *n* označte veřejné pole nebo vlastnost, která má být uložena do mezipaměti. Další informace najdete v tématu [cache data](../vsto/caching-data.md).

2. Přepsat <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> metodu ve `ThisWorkbook` třídě a odebrat ochranu sešitu.

     Když je sešit uložený, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] voláním této metody vám poskytneme možnost zrušit ochranu sešitu. To umožňuje uložení změn dat v mezipaměti.

3. Přepsat <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> metodu ve `ThisWorkbook` třídě a znovu použít ochranu pro dokument.

     Po uložení sešitu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] voláním této metody poskytnete možnost znovu použít ochranu pro sešit.

### <a name="example"></a>Příklad
 Následující příklad kódu ukazuje, jak ukládat data do mezipaměti v excelovém sešitu, který je chráněn heslem. Před tím, než kód odstraní ochranu v <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> metodě, uloží aktuální <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A> <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A> hodnoty a hodnoty, aby bylo možné v metodě znovu použít stejný typ ochrany <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> .

 [!code-vb[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedWorkbook/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedWorkbook/ThisWorkbook.cs#1)]

### <a name="compile-the-code"></a>Kompilovat kód
 Přidejte tento kód do `ThisWorkbook` třídy v projektu. Tento kód předpokládá, že heslo je uloženo v poli s názvem `securelyStoredPassword` .

## <a name="see-also"></a>Viz také
- [Data mezipaměti](../vsto/caching-data.md)
- [Postupy: ukládání dat do mezipaměti pro použití v režimu offline nebo na serveru](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Postupy: ukládání zdroje dat v dokumentu Office do mezipaměti prostřednictvím kódu programu](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
