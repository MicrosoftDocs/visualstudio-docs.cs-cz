---
title: 'Postupy: ukládání dokumentů prostřednictvím kódu programu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving
- Word [Office development in Visual Studio], saving documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e794a995d1e978cf5aae8d1b6ec9c1711436af73
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49883470"
---
# <a name="how-to-programmatically-save-documents"></a>Postupy: ukládání dokumentů prostřednictvím kódu programu
  Existuje několik způsobů k uložení dokumentů Microsoft Office Word. Dokument lze uložit beze změny název dokumentu nebo ukládáte dokument s novým názvem.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="save-a-document-without-changing-the-name"></a>Uložení dokumentu beze změny názvu  
  
### <a name="to-save-the-document-associated-with-a-document-level-customization"></a>Chcete-li uložit dokument přidružený k přizpůsobení úrovni dokumentu  
  
1.  Volání <xref:Microsoft.Office.Tools.Word.Document.Save%2A> metodu <xref:Microsoft.Office.Tools.Word.Document> třídy. Pokud chcete použít tento příklad kódu, spusťte jej z `ThisDocument` třídu ve vašem projektu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#7)]  
  
### <a name="to-save-the-active-document"></a>Uložení aktivního dokumentu  
  
1. Volání <xref:Microsoft.Office.Interop.Word._Document.Save%2A> metodu pro aktivní dokument. Pokud chcete použít tento příklad kódu, spusťte jej z `ThisDocument` nebo `ThisAddIn` třídu ve vašem projektu.  
  
    [!code-vb[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#8)]
    [!code-csharp[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#8)]  
  
   Pokud si nejste jisti, zda je dokument, který chcete uložit aktivní dokument, je můžete na něj odkazovat pomocí jeho názvu.  
  
### <a name="to-save-a-document-specified-by-name"></a>Chcete-li uložit dokument určený název  
  
1.  Použít jako argument název dokumentu <xref:Microsoft.Office.Interop.Word.Documents> kolekce. Pokud chcete použít tento příklad kódu, spusťte jej z `ThisDocument` nebo `ThisAddIn` třídu ve vašem projektu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#9)]
     [!code-csharp[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#9)]  
  
## <a name="save-a-document-with-a-new-name"></a>Uložit dokument s novým názvem.  
 Pomocí této metody SaveAs uložit dokument s novým názvem. Tuto metodu lze použít <xref:Microsoft.Office.Tools.Word.Document> hostitelský objekt v úrovni dokumentu projektu aplikace Word nebo nativní <xref:Microsoft.Office.Interop.Word.Document> objektu v každém projektu aplikace Word. Tato metoda vyžaduje, zadejte nový název souboru, ale další argumenty jsou volitelné.  
  
> [!NOTE]  
>  Pokud se zobrazuje **SaveAs** dialogovému oknu uvnitř <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> obslužná rutina události `ThisDocument` a nastavte *zrušit* parametr **false**, může aplikace neočekávané ukončení. Pokud jste nastavili *zrušit* parametr **true**, se zobrazí chybová zpráva označující, že automatické ukládání je zakázané.  
  
### <a name="to-save-the-document-associated-with-a-document-level-customization-with-a-new-name"></a>Chcete-li uložit dokument přidružený k přizpůsobení úrovni dokumentu s novým názvem.  
  
1.  Volání <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> metodu `ThisDocument` třídu ve vašem projektu, pomocí plně kvalifikovaný název a cesta k souboru. Pokud soubor s tímto názvem již existuje v této složce, je tiše přepsána. Pokud chcete použít tento příklad kódu, spusťte jej z `ThisDocument` třídy.  
  
    > [!NOTE]  
    >  <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> Metoda vyvolá výjimku, pokud cílový adresář neexistuje, nebo jestli neexistují nějaké jiné problémy uložení souboru. Je vhodné použít **try... catch** blokovat kolem <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> metoda nebo uvnitř volání metody.  
  
     [!code-vb[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#10)]  
  
### <a name="to-save-a-native-document-with-a-new-name"></a>Uložení nativní dokumentu s novým názvem.  
  
1.  Volání <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> metodu <xref:Microsoft.Office.Interop.Word.Document> , který chcete uložit, pomocí plně kvalifikovaný název a cesta k souboru. Pokud soubor s tímto názvem již existuje v této složce, je tiše přepsána.  
  
     Následující příklad kódu uloží aktivní dokument s novým názvem. Pokud chcete použít tento příklad kódu, spusťte jej z `ThisDocument` nebo `ThisAddIn` třídu ve vašem projektu.  
  
    > [!NOTE]  
    >  <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> Metoda vyvolá výjimku, pokud cílový adresář neexistuje, nebo jestli neexistují nějaké jiné problémy uložení souboru. Je vhodné použít **try... catch** blokovat kolem <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> metoda nebo uvnitř volání metody.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#10)]  
  
## <a name="compile-the-code"></a>Kompilace kódu  
 Tento příklad kódu vyžaduje následující:  
  
-   Uložení dokumentu podle názvu, dokumentu s názvem *NewDocument.doc* musí existovat v adresáři s názvem *Test* na jednotce C.  
  
-   Chcete-li uložit dokument s novým názvem, adresář s názvem *Test* , musí existovat v jednotce C.  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: zavírání dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-close-documents.md)   
 [Postupy: otevírání stávajících dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Hostitelská položka Document](../vsto/document-host-item.md)   
 [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  