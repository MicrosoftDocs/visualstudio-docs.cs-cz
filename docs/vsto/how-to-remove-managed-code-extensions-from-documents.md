---
title: 'Postupy: odebrání rozšíření spravovaného kódu z dokumentů'
description: Programové odebrání sestavení vlastního nastavení z dokumentu nebo sešitu, který je součástí přizpůsobení na úrovni dokumentu pro aplikaci Microsoft Word nebo Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], removing
- documents [Office development in Visual Studio], managed code extensions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 129b1bda44abf7283efe1996f1898491025ee9d9
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825443"
---
# <a name="how-to-remove-managed-code-extensions-from-documents"></a>Postupy: odebrání rozšíření spravovaného kódu z dokumentů
  Můžete programově odebrat sestavení přizpůsobení z dokumentu nebo sešitu, který je součástí přizpůsobení na úrovni dokumentu pro systém Microsoft Office Word nebo systém Microsoft Office Excel. Uživatelé pak můžou otevřít dokumenty a zobrazit obsah, ale jakékoli vlastní uživatelské rozhraní (UI), které přidáte do dokumentů, se nezobrazí a váš kód se nespustí.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Můžete odebrat sestavení vlastního nastavení pomocí jedné z metod, které `RemoveCustomization` poskytuje [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . To, kterou metodu použijete, závisí na tom, zda chcete odebrat vlastní nastavení za běhu (to znamená spuštěním kódu v přizpůsobení během otevřeného dokumentu nebo sešitu aplikace Word), nebo pokud chcete odebrat vlastní nastavení z uzavřeného dokumentu nebo dokumentu, který je na serveru, na kterém není systém Microsoft Office nainstalován.

## <a name="to-remove-the-customization-assembly-at-run-time"></a>Odebrání sestavení vlastního nastavení v době běhu

1. V kódu vlastního nastavení zavolejte <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> metodu (pro Word) nebo <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A> metodu (pro Excel). Tato metoda by se měla volat až po tom, co už nepotřebujete vlastní nastavení.

     Místo volání této metody v kódu závisí na způsobu použití vlastního nastavení. Pokud například zákazníci použijí funkce vlastního nastavení, dokud nebudou připraveni k odeslání dokumentu do jiných klientů, kteří potřebují pouze samotný dokument (nikoli přizpůsobení), můžete poskytnout nějaké uživatelské rozhraní, které volá, `RemoveCustomization` když na něj zákazník klikne. Případně, pokud vaše přizpůsobení naplní dokument daty při prvním otevření, ale přizpůsobení neposkytuje žádné jiné funkce, ke kterým přistupovali přímo zákazníci, pak můžete volat RemoveCustomization, jakmile vaše přizpůsobení dokončí inicializaci dokumentu.

## <a name="to-remove-the-customization-assembly-from-a-closed-document-or-a-document-on-a-server"></a>Odebrání sestavení vlastního nastavení z zavřeného dokumentu nebo dokumentu na serveru

1. V projektu, který nevyžaduje systém Microsoft Office, jako je například Konzolová aplikace nebo projekt model Windows Forms, přidejte odkaz na *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* sestavení.

2. Přidejte následující příkaz **Imports** nebo **using** do horní části souboru kódu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb" id="Snippet1":::

3. Zavolejte statickou <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> metodu <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> třídy a určete cestu k dokumentu řešení pro parametr.

     Následující příklad kódu předpokládá, že odebíráte vlastní nastavení z dokumentu s názvem *WordDocument1.docx* , který je na ploše.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb" id="Snippet2":::

4. Sestavte projekt a spusťte aplikaci na počítači, na kterém chcete odebrat vlastní nastavení. Počítač musí mít nainstalované sady Visual Studio 2010 Tools for Office runtime.

## <a name="see-also"></a>Viz také
- [Správa dokumentů na serveru pomocí třídy ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Postupy: připojení rozšíření spravovaného kódu k dokumentům](../vsto/how-to-attach-managed-code-extensions-to-documents.md)
