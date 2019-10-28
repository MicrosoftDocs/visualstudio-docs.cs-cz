---
title: 'Postupy: připojení rozšíření spravovaného kódu k dokumentům'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 8fb212f9c5441d697cfa92feee7dc18fab9270d2
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985968"
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>Postupy: připojení rozšíření spravovaného kódu k dokumentům
  Sestavení vlastního nastavení můžete připojit k existujícímu systém Microsoft Office dokumentu aplikace Word nebo sešitu systém Microsoft Office aplikace Excel. Dokument nebo sešit může být ve formátu souboru, který je podporován systém Microsoft Office projekty a vývojové nástroje v aplikaci Visual Studio. Další informace najdete v tématu [Architektura přizpůsobení na úrovni dokumentu](../vsto/architecture-of-document-level-customizations.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Chcete-li připojit přizpůsobení k dokumentu aplikace Word nebo Excel, použijte metodu <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> třídy <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>. Vzhledem k tomu, že třída <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> je navržena tak, aby byla spuštěna na počítači, který nemá systém Microsoft Office nainstalován, můžete tuto metodu použít v řešeních, která přímo nesouvisejí s vývojem systém Microsoft Office (například konzolu nebo model Windows Forms aplikace).

> [!NOTE]
> Přizpůsobení se nezdaří, pokud kód očekává ovládací prvky, které zadaný dokument neobsahuje.

### <a name="to-attach-managed-code-extensions-to-a-document"></a>Připojení rozšíření spravovaného kódu k dokumentu

1. V projektu, který nevyžaduje systém Microsoft Office, jako je například Konzolová aplikace nebo projekt model Windows Forms, přidejte odkaz na soubor *Microsoft. VisualStudio. Tools. Applications. ServerDocument. dll* a  *Sestavení Microsoft. VisualStudio. Tools. Applications. Runtime. dll* .

2. Přidejte následující příkazy **Imports** nebo **using** do horní části souboru kódu.

     [!code-csharp[Trin_VstcoreDeployment#4](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#4)]

3. Zavolejte statickou metodu <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>.

     Následující příklad kódu používá přetížení <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>. Toto přetížení získá úplnou cestu k dokumentu a <xref:System.Uri>, která určuje umístění manifestu nasazení pro vlastní nastavení, které chcete připojit k dokumentu. V tomto příkladu se předpokládá, že se dokument aplikace Word s názvem **WordDocument1. docx** nachází na ploše a že manifest nasazení je umístěný ve složce s názvem **Publish** , která je také na ploše.

     [!code-csharp[Trin_VstcoreDeployment#3](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#3)]

4. Sestavte projekt a spusťte aplikaci na počítači, do kterého chcete připojovat vlastní nastavení. Počítač musí mít nainstalované sady Visual Studio 2010 Tools for Office runtime.

## <a name="see-also"></a>Viz také:
- [Správa dokumentů na serveru pomocí třídy ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Postupy: odebrání rozšíření spravovaného kódu z dokumentů](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Manifesty aplikací a nasazení v řešeních pro systém Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
