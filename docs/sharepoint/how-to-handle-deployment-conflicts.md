---
title: 'Postupy: zpracování konfliktů nasazení | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5df9677fd349825983cc33c5a8ed2648f34b8c9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015308"
---
# <a name="how-to-handle-deployment-conflicts"></a>Postupy: zpracování konfliktů nasazení
  Můžete zadat vlastní kód pro zpracování konfliktů nasazení pro položku projektu služby SharePoint. Například můžete určit, zda některé soubory v aktuální položce projektu již existují v umístění nasazení, a poté odstranit nasazené soubory před nasazením aktuální položky projektu. Další informace o konfliktech nasazení najdete v tématu [rozšíření balení a nasazení služby SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

### <a name="to-handle-a-deployment-conflict"></a>Postup při zpracování konfliktu nasazení

1. Vytvořte rozšíření položky projektu, rozšíření projektu nebo definici nového typu položky projektu. Další informace najdete v následujících tématech:

    - [Postupy: Vytvoření rozšíření položky projektu služby SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

    - [Postupy: Vytvoření rozšíření projektu služby SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

    - [Postupy: definování typu položky projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. V rozšíření zpracujte <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> událost <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> objektu (v rozšíření položky projektu nebo rozšíření projektu) nebo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> objektu (v definici nového typu položky projektu).

3. V obslužné rutině události určete, zda došlo ke konfliktu mezi nasazenou položkou projektu a nasazeným řešením na webu služby SharePoint, a to na základě kritérií, která platí pro váš scénář. Můžete použít <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A> vlastnost parametru argumenty události pro analýzu položky projektu, který se nasazuje, a analyzovat soubory v umístění nasazení voláním příkazu SharePoint, který definujete pro tento účel.

     U mnoha typů konfliktů můžete nejdřív chtít určit, který krok nasazení se provádí. Můžete to provést pomocí <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A> Vlastnosti parametru argumenty události. I když má obvykle smysl detekovat konflikty v rámci integrovaného <xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution> kroku nasazení, můžete vyhledat konflikty v jakémkoli kroku nasazení.

4. Pokud existuje konflikt, použijte <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> metodu <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A> vlastnosti argumentů události pro vytvoření nového <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> objektu. Tento objekt představuje konflikt nasazení. Ve volání <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> metody zadejte také metodu, která je volána k vyřešení konfliktu.

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje základní proces pro zpracování konfliktu nasazení v rozšíření položky projektu pro položky projektu definice seznamu. Chcete-li zpracovat konflikt nasazení pro jiný typ položky projektu, předejte jinému řetězci <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> . Další informace najdete v tématu věnovaném [rozšiřování položek projektu služby SharePoint](../sharepoint/extending-sharepoint-project-items.md).

 Pro jednoduchost, <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> obslužná rutina události v tomto příkladu předpokládá, že existuje konflikt nasazení (to znamená, že vždy přidá nový <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> objekt) a `Resolve` Metoda jednoduše vrátí **hodnotu true** , aby označovala, že konflikt byl vyřešen. V reálném scénáři <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> by obslužná rutina události nejprve určila, zda konflikt existuje mezi souborem v aktuální položce projektu a souborem v umístění nasazení, a pak přidat <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> objekt pouze v případě, že existuje konflikt. Například můžete použít `e.ProjectItem.Files` vlastnost v obslužné rutině události k analýze souborů v položce projektu a můžete zavolat příkaz SharePointu k analýze souborů v umístění nasazení. Podobně v reálném scénáři `Resolve` může metoda volat příkaz SharePoint pro vyřešení konfliktu na webu služby SharePoint. Další informace o vytváření příkazů služby SharePoint naleznete v tématu [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md).

 [!code-vb[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/VisualBasic/deploymentconflict/extension/deploymentconflictextension.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/CSharp/deploymentconflict/extension/deploymentconflictextension.cs#1)]

## <a name="compile-the-code"></a>Kompilovat kód
 Tento příklad vyžaduje odkazy na následující sestavení:

- Microsoft. VisualStudio. SharePoint

- System. ComponentModel. složení

## <a name="deploy-the-extension"></a>Nasazení rozšíření
 Chcete-li nasadit rozšíření, vytvořte [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] balíček rozšíření (VSIX) pro sestavení a všechny další soubory, které chcete distribuovat s rozšířením. Další informace naleznete v tématu [nasazení rozšíření pro nástroje služby SharePoint v aplikaci Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Viz také
- [Rozšiřování balení a nasazení služby SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Rozšiřování položek projektu služby SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Postupy: spuštění kódu při spuštění kroků nasazení](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
- [Postupy: vytvoření příkazu SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)
