---
title: 'Postup: provedení příkazu SharePoint | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], executing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ce195dd34c7c0b509f9de4cbe2cfd14d9a477f87
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120362"
---
# <a name="how-to-execute-a-sharepoint-command"></a>Postup: provedení příkazu SharePoint
  Pokud chcete použít objektový model serveru v rozšíření nástrojů služby SharePoint, je třeba vytvořit vlastní *příkazu SharePoint* pro volání rozhraní API. Po definování příkazu a nasadit pomocí rozšíření nástrojů služby SharePoint, můžete toto rozšíření spustit příkaz provést volání do objektový model serveru SharePoint. Chcete-li spustit příkaz, použijte jednu z metod ExecuteCommand <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objektu.  
  
 Další informace o účelu SharePoint – příkazy najdete v tématu [volání do objektových modelů služby SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
### <a name="to-execute-a-sharepoint-command"></a>K provedení příkazu SharePoint  
  
1.  Ve vašem rozšíření nástrojů SharePoint získat <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objektu. Způsob, jak můžete získat <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objekt závisí na typu rozšíření vytváříte:  
  
    -   V rozšíření systému projektu služby SharePoint, použijte <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A> vlastnost.  
  
         Další informace o rozšíření systému projektu najdete v tématu [rozšíření systému projektu služby SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
    -   V rozšíření **připojení služby SharePoint** uzlu v **Průzkumníka serveru**, použijte <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A> vlastnost. Chcete-li získat <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext> objektu, použijte <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A> vlastnost.  
  
         Další informace o **Průzkumníka serveru** rozšíření, najdete v části [rozšíření uzlu připojení služby SharePoint v Průzkumníku serveru](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
    -   V kódu, který není součástí rozšíření nástrojů služby SharePoint, jako je například Průvodce šablonou projektu, použijte <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> vlastnost.  
  
         Další informace o načtení služby projektu najdete v tématu [použití služby projektu služby SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
2.  Volání jednoho z metod ExecuteCommand <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objektu. Předejte název příkazu, který chcete provést první argument ExecuteCommand metody. Pokud má váš příkaz vlastní parametr, předejte parametr druhý argument ExecuteCommand metody.  
  
     Neexistuje jiný ExecuteCommand přetížení pro každou podporovanou signaturu příkazu. Následující tabulka uvádí podporované podpisů a které přetížení použít pro každý podpis.  
  
    |Příkaz podpis|Parametr ExecuteCommand přetížení pro použití|  
    |-----------------------|------------------------------------|  
    |Příkaz má pouze výchozí <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametr a žádnou návratovou hodnotu.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |Příkaz má pouze výchozí <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametr a návratovou hodnotu.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |Příkaz má dva parametry (výchozí hodnota <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametr a vlastní parametr) a žádnou návratovou hodnotu.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |Příkaz má dva parametry a návratové hodnoty.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak používat <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> přetížení volání `Contoso.Commands.UpgradeSolution` příkaz, který je popsán v [postupy: vytvoření příkazu SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md).  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#6)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#6)]  
  
 `Execute` Uvedeno v tomto příkladu metoda je implementací <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A> metodu <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> rozhraní v vlastního kroku nasazení. Tento kód v rámci většího příkladu najdete v sekci [návod: vytvoření vlastního kroku nasazení pro projekty SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
 Poznamenejte si následující podrobnosti o volání <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> metoda:  
  
-   První parametr určuje příkaz, který chcete volat. Tento řetězec odpovídá hodnotě, který můžete předat <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> v definici příkazu.  
  
-   Druhý parametr je hodnota, kterou chcete předat vlastní druhý parametr příkazu. V takovém případě je úplná cesta *WSP* soubor, který se upgraduje na stránku služby SharePoint.  
  
-   Kód nepředává implicitní <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> do příkazu parametr. Tento parametr je předán do příkaz automaticky při volání příkazu z rozšíření systému projektu služby SharePoint nebo rozšíření **připojení služby SharePoint** uzlu v **Průzkumníka serveru**. V jiných typech řešení, jako například Průvodce šablonou projektu, který implementuje <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> rozhraní, tento parametr je **null**.  
  
## <a name="compile-the-code"></a>Kompilace kódu  
 Tento příklad vyžaduje odkaz na sestavení Microsoft.VisualStudio.SharePoint.  
  
## <a name="see-also"></a>Viz také:
 [Volání do objektových modelů služby SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Postupy: vytvoření příkazu SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [Návod: Rozšíření Průzkumníka serveru pro zobrazení webové části](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
