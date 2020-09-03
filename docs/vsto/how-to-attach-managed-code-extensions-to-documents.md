---
title: 'Postupy: připojení rozšíření spravovaného kódu k dokumentům'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], attaching
- documents [Office development in Visual Studio], managed code extensions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f44b153ac7d55704ba649a7dc09860518a5e76b7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547521"
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>Postupy: připojení rozšíření spravovaného kódu k dokumentům
  Sestavení vlastního nastavení můžete připojit k existujícímu systém Microsoft Office dokumentu aplikace Word nebo sešitu systém Microsoft Office aplikace Excel. Dokument nebo sešit může být ve formátu souboru, který je podporován systém Microsoft Office projekty a vývojové nástroje v aplikaci Visual Studio. Další informace najdete v tématu [Architektura přizpůsobení na úrovni dokumentu](../vsto/architecture-of-document-level-customizations.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Chcete-li připojit přizpůsobení k dokumentu aplikace Word nebo Excel, použijte <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> metodu <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> třídy. Vzhledem k tomu, že <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> je třída navržena tak, aby byla spuštěna na počítači, který nemá nainstalované systém Microsoft Office, můžete použít tuto metodu v řešeních, která přímo nesouvisí s vývojem systém Microsoft Office (jako je konzola nebo model Windows Forms aplikace).

> [!NOTE]
> Přizpůsobení se nezdaří, pokud kód očekává ovládací prvky, které zadaný dokument neobsahuje.

### <a name="to-attach-managed-code-extensions-to-a-document"></a>Připojení rozšíření spravovaného kódu k dokumentu

1. V projektu, který nevyžaduje systém Microsoft Office, jako je například Konzolová aplikace nebo projekt model Windows Forms, přidejte odkaz na *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* a *Microsoft.VisualStudio.Tools.Applications.Runtime.dll* sestavení.

2. Přidejte následující příkazy **Imports** nebo **using** do horní části souboru kódu.

     [!code-csharp[Trin_VstcoreDeployment#4](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#4)]

3. Zavolejte statickou <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> metodu.

     Následující příklad kódu používá <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> přetížení. Toto přetížení získá úplnou cestu k dokumentu a <xref:System.Uri> , který určuje umístění manifestu nasazení pro vlastní nastavení, které chcete připojit k dokumentu. V tomto příkladu se předpokládá, že se dokument aplikace Word s názvem **WordDocument1.docx** nachází na ploše a že manifest nasazení je umístěný ve složce s názvem **publikovat** , která je také na ploše.

     [!code-csharp[Trin_VstcoreDeployment#3](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#3)]

4. Sestavte projekt a spusťte aplikaci na počítači, do kterého chcete připojovat vlastní nastavení. Počítač musí mít nainstalované sady Visual Studio 2010 Tools for Office runtime.

## <a name="see-also"></a>Viz také
- [Správa dokumentů na serveru pomocí třídy ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Postupy: odebrání rozšíření spravovaného kódu z dokumentů](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Manifesty aplikací a nasazení v řešeních pro systém Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
