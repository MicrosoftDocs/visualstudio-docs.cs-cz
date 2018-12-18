---
title: 'Postupy: připojení spravovaných rozšíření kódu k dokumentům'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], attaching
- documents [Office development in Visual Studio], managed code extensions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c6e39f27caf9d321bb83666d72114a9675091f03
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257036"
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>Postupy: připojení spravovaných rozšíření kódu k dokumentům
  Přizpůsobení sestavení může připojit k existující dokument aplikace Microsoft Office Word nebo sešitu aplikace Microsoft Office Excel. Tento dokument nebo sešitu může být v libovolném formátu souboru, která je podporována projektů Microsoft Office a nástroje pro vývoj v sadě Visual Studio. Další informace najdete v tématu [architektura přizpůsobení na úrovni dokumentu](../vsto/architecture-of-document-level-customizations.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Přizpůsobení připojit k dokumentu Word či Excel, použijte <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> metodu <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> třídy. Protože <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> třída slouží ke spuštění v počítači, který nemá nainstalovanou sadu Microsoft Office, můžete použít tuto metodu v řešení, které přímo nesouvisejí s vývoj aplikace Microsoft Office (například konzole nebo aplikace Windows Forms).  
  
> [!NOTE]  
>  Přizpůsobení se nepodaří načíst, pokud kód očekává ovládacích prvků, které nemá zadaný dokument.  
  
 ![odkaz na video](../vsto/media/playvideo.gif "odkaz na video") související Videoukázka, najdete v části [jak I: připojit nebo odpojit sestavení VSTO z dokumentu aplikace Word?](http://go.microsoft.com/fwlink/?LinkId=136782).  
  
### <a name="to-attach-managed-code-extensions-to-a-document"></a>Připojení rozšíření spravovaného kódu do dokumentu.  
  
1.  V projektu, který nevyžaduje Microsoft Office, jako je konzolová aplikace nebo projekt Windows Forms, přidejte odkaz na *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* a  *Microsoft.VisualStudio.Tools.Applications.Runtime.dll* sestavení.  
  
2.  Přidejte následující **importy** nebo **pomocí** příkazy na začátek souboru kódu.  
  
     [!code-csharp[Trin_VstcoreDeployment#4](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#4)]  
  
3.  Zavolejte statickou <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> metoda.  
  
     Následující příklad kódu používá <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> přetížení. Toto přetížení provede úplnou cestu dokumentu a <xref:System.Uri> , určuje umístění manifest nasazení pro přizpůsobení, které chcete připojit k dokumentu. Tento příklad předpokládá, že dokument aplikace Word s názvem **WordDocument1.docx** je na ploše a který manifest nasazení je umístěný ve složce s názvem **publikovat** , je také na ploše.  
  
     [!code-csharp[Trin_VstcoreDeployment#3](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#3)]  
  
4.  Sestavte projekt a spusťte aplikaci v počítači, ve které chcete připojit přizpůsobení. Počítač musí mít Visual Studio 2010 Tools for Office Runtime nainstalována.  
  
## <a name="see-also"></a>Viz také:  
 [Správa dokumentů na serveru s použitím třídy ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Postupy: odebrání spravovaných rozšíření kódu z dokumentů](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Manifesty aplikace a nasazení v řešeních pro systém Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  