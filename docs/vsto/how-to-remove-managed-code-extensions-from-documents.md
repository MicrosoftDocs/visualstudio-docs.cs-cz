---
title: 'Postupy: Odebrat rozšíření spravovaného kódu z dokumentů'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], removing
- documents [Office development in Visual Studio], managed code extensions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 83bd57c8ffdcb268a560431c74806ddb6544d4e8
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252159"
---
# <a name="how-to-remove-managed-code-extensions-from-documents"></a>Postupy: Odebrat rozšíření spravovaného kódu z dokumentů
  Můžete programově odebrat sestavení přizpůsobení z dokumentu nebo sešitu, který je součástí přizpůsobení na úrovni dokumentu pro systém Microsoft Office Word nebo systém Microsoft Office Excel. Uživatelé pak můžou otevřít dokumenty a zobrazit obsah, ale jakékoli vlastní uživatelské rozhraní (UI), které přidáte do dokumentů, se nezobrazí a váš kód se nespustí.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Můžete odebrat sestavení vlastního nastavení pomocí jedné z `RemoveCustomization` metod, které poskytuje. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] To, kterou metodu použijete, závisí na tom, zda chcete odebrat vlastní nastavení v době běhu (to znamená spuštěním kódu v přizpůsobení během otevřeného dokumentu nebo sešitu aplikace Word), nebo pokud chcete odebrat vlastní nastavení z zavřeného dokumentu nebo dokumentu, který jsem s na serveru, na kterém není nainstalovaná systém Microsoft Office.

 ![odkaz na video](../vsto/media/playvideo.gif "odkaz na video") Související video ukázku naleznete v tématu [How to: Připojení nebo odpojení sestavení VSTO z wordového dokumentu? ](http://go.microsoft.com/fwlink/?LinkId=136782).

## <a name="to-remove-the-customization-assembly-at-run-time"></a>Odebrání sestavení vlastního nastavení v době běhu

1. V kódu vlastního nastavení zavolejte <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> metodu (pro Word) <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A> nebo metodu (pro Excel). Tato metoda by se měla volat až po tom, co už nepotřebujete vlastní nastavení.

     Místo volání této metody v kódu závisí na způsobu použití vlastního nastavení. Pokud například zákazníci použijí funkce vlastního nastavení, dokud nebudou připraveni k odeslání dokumentu do jiných klientů, kteří potřebují pouze samotný dokument (nikoli přizpůsobení), můžete poskytnout nějaké uživatelské rozhraní, které volá `RemoveCustomization` , když na něj zákazník klikne. Případně, pokud vaše přizpůsobení naplní dokument daty při prvním otevření, ale přizpůsobení neposkytuje žádné jiné funkce, ke kterým přistupovali přímo zákazníci, pak můžete volat RemoveCustomization hned po přizpůsobení dokončí inicializaci dokumentu.

## <a name="to-remove-the-customization-assembly-from-a-closed-document-or-a-document-on-a-server"></a>Odebrání sestavení vlastního nastavení z zavřeného dokumentu nebo dokumentu na serveru

1. V projektu, který nevyžaduje systém Microsoft Office, jako je například Konzolová aplikace nebo projekt model Windows Forms, přidejte odkaz na sestavení *Microsoft. VisualStudio. Tools. Applications. ServerDocument. dll* .

2. Přidejte následující příkaz **Imports** nebo **using** do horní části souboru kódu.

     [!code-csharp[Trin_VstcoreDeployment#1](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#1)]
     [!code-vb[Trin_VstcoreDeployment#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#1)]

3. Zavolejte statickou <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> metodu <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> třídy a určete cestu k dokumentu řešení pro parametr.

     Následující příklad kódu předpokládá, že odebíráte vlastní nastavení z dokumentu s názvem *WordDocument1. docx* , který je na ploše.

     [!code-csharp[Trin_VstcoreDeployment#2](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#2)]
     [!code-vb[Trin_VstcoreDeployment#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#2)]

4. Sestavte projekt a spusťte aplikaci na počítači, na kterém chcete odebrat vlastní nastavení. Počítač musí mít nainstalované sady Visual Studio 2010 Tools for Office runtime.

## <a name="see-also"></a>Viz také:
- [Správa dokumentů na serveru pomocí třídy ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Postupy: Připojit rozšíření spravovaného kódu k dokumentům](../vsto/how-to-attach-managed-code-extensions-to-documents.md)
