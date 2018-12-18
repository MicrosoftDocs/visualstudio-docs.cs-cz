---
title: 'Postupy: odebrání rozšíření se spravovaným kódem z dokumentů'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], removing
- documents [Office development in Visual Studio], managed code extensions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a57384fa22e810be27969bb5164e1951dccd1bf2
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676443"
---
# <a name="how-to-remove-managed-code-extensions-from-documents"></a>Postupy: odebrání rozšíření se spravovaným kódem z dokumentů
  Přizpůsobení sestavení můžete odebrat prostřednictvím kódu programu z dokumentu nebo sešitu, který je součástí přizpůsobení na úrovni dokumentu pro aplikaci Microsoft Office Word nebo Microsoft Office Excel. Uživatelé pak můžete otevřít dokumenty a zobrazit obsah, ale nezobrazí se žádné vlastní uživatelské rozhraní (UI) přidáte k dokumentům a kódu se nespustí.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Přizpůsobení sestavení můžete odebrat pomocí jedné z `RemoveCustomization` metody poskytované objektem [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Jakou metodu použijete, závisí na tom, jestli chcete odebrat vlastní nastavení v době běhu (spouštěním kódu v přizpůsobení při slovo dokumentu nebo Excelového sešitu je otevřený), nebo pokud chcete odebrat ze zavřeného dokumentu nebo dokumentu přizpůsobení této i s na serveru, který nemá nainstalovanou sadu Microsoft Office.  
  
 ![odkaz na video](../vsto/media/playvideo.gif "odkaz na video") související video ukázku naleznete v tématu [udělat jak mohu: připojit nebo odpojit sestavení VSTO z Wordového dokumentu?](http://go.microsoft.com/fwlink/?LinkId=136782).  
  
## <a name="to-remove-the-customization-assembly-at-runtime"></a>Chcete-li odebrat vlastní nastavení sestavení za běhu  
  
1.  Ve vlastním kódu volat <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> – metoda (pro aplikaci Word) nebo <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A> – metoda (pro aplikace Excel). Tuto metodu lze volat pouze po přizpůsobení je už je nepotřebujete.  
  
     Pokud volání této metody v kódu závisí na použití vašeho vlastního nastavení. Například pokud vaše přizpůsobení funkce zákazníkům používat, dokud jsou připravené k odeslání dokumentu jiným klientům, kteří potřebují pouze dokumentu (ne přizpůsobení), můžete zadat některé uživatelské rozhraní, která volá `RemoveCustomization` když zákazník klikne. Případně pokud vaše přizpůsobení naplní dokument s daty při prvním otevření, ale přizpůsobení neposkytuje žádné funkce, které jsou k němu přistupuje přímo zákazníkům, pak můžete volat RemoveCustomization co nejdříve vaše vlastní nastavení dokončení inicializace dokumentu.  
  
## <a name="to-remove-the-customization-assembly-from-a-closed-document-or-a-document-on-a-server"></a>Odebrat vlastní nastavení sestavení ze zavřeného dokumentu nebo dokumentu na serveru  
  
1.  V projektu, který nevyžaduje, aby aplikace Microsoft Office, jako je například projekt aplikace Windows Forms a konzolové aplikace, přidejte odkaz na *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* sestavení.  
  
2.  Přidejte následující **importy** nebo **pomocí** příkaz do horní části souboru kódu.  
  
     [!code-csharp[Trin_VstcoreDeployment#1](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#1)]
     [!code-vb[Trin_VstcoreDeployment#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#1)]  
  
3.  Zavolejte statickou <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> metodu <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> třídy a zadejte cestu k dokumentu řešení pro parametr.  
  
     Následující příklad kódu předpokládá, že odeberete vlastní nastavení z dokumentu s názvem *WordDocument1.docx* , který je na ploše.  
  
     [!code-csharp[Trin_VstcoreDeployment#2](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#2)]
     [!code-vb[Trin_VstcoreDeployment#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#2)]  
  
4.  Sestavte projekt a spusťte aplikaci v počítači, ve které chcete odebrat vlastní nastavení. Na počítači musí být Visual Studio 2010 Tools for Office runtime nainstalovaný.  
  
## <a name="see-also"></a>Viz také:  
 [Správa dokumentů na serveru s použitím třídy ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Postupy: připojení spravovaného kódu rozšíření do dokumentů](../vsto/how-to-attach-managed-code-extensions-to-documents.md)  
  
  