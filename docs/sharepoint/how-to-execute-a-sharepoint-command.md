---
title: 'Postupy: provedení příkazu SharePointu | Microsoft Docs'
description: Přečtěte si, jak vytvořit vlastní příkaz SharePointu pro volání rozhraní API objektového modelu serveru z rozšíření nástrojů služby SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], executing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2746704e30a61b0971db50a5083855b4a93560d4
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903532"
---
# <a name="how-to-execute-a-sharepoint-command"></a>Postupy: provedení příkazu SharePoint
  Pokud chcete použít objektový model serveru v rozšíření nástrojů služby SharePoint, je nutné vytvořit vlastní *příkaz SharePointu* pro volání rozhraní API. Po definování příkazu a jeho nasazení pomocí rozšíření nástrojů služby SharePoint může rozšíření spustit příkaz pro volání do objektového modelu serveru SharePoint. Chcete-li spustit příkaz, použijte jednu z metod ExecuteCommand <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objektu.

 Další informace o účelu příkazů služby SharePoint naleznete v tématu [volání do objektových modelů služby SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

### <a name="to-execute-a-sharepoint-command"></a>Provedení příkazu SharePoint

1. V rozšíření nástrojů služby SharePoint získejte <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objekt. Způsob, jakým získáte <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objekt, závisí na typu rozšíření, které vytváříte:

    - V rozšíření systému projektu služby SharePoint použijte <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A> vlastnost.

         Další informace o rozšířeních systému projektů naleznete v tématu [rozšíření systému projektu služby SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

    - V rozšíření uzlu **připojení služby SharePoint** v **Průzkumník serveru** použijte <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A> vlastnost. Chcete-li získat <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext> objekt, použijte <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A> vlastnost.

         Další informace o rozšířeních **Průzkumník serveru** najdete [v tématu rozšíření uzlu připojení služby SharePoint v Průzkumník serveru](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

    - V kódu, který není součástí rozšíření nástrojů služby SharePoint, jako je například Průvodce šablonou projektu, použijte <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> vlastnost.

         Další informace o načtení služby projektu naleznete v tématu [použití služby projektu služby SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

2. Zavolejte jednu z metod ExecuteCommand <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objektu. Předejte název příkazu, který chcete spustit, na první argument metody ExecuteCommand. Pokud má váš příkaz vlastní parametr, předejte tento parametr druhému argumentu metody ExecuteCommand.

     Pro každý podporovaný podpis příkazu existuje jiné přetížení ExecuteCommand. V následující tabulce jsou uvedeny podporované podpisy a které přetížení použít pro každý podpis.

    |Podpis příkazu|ExecuteCommand přetížení k použití|
    |-----------------------|------------------------------------|
    |Příkaz má pouze výchozí <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametr a žádnou návratovou hodnotu.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |Příkaz má pouze výchozí <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametr a návratovou hodnotu.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |Příkaz má dva parametry (výchozí <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametr a vlastní parametr) a žádnou návratovou hodnotu.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |Příkaz má dva parametry a návratovou hodnotu.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje, jak použít <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> přetížení k volání `Contoso.Commands.UpgradeSolution` příkazu, který je popsán v tématu [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md).

 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#6)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#6)]

 `Execute`Metoda uvedená v tomto příkladu je implementací <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A> metody <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> rozhraní ve vlastním kroku nasazení. Chcete-li zobrazit tento kód v kontextu většího příkladu, přečtěte si [Návod: Vytvoření vlastního kroku nasazení pro projekty SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

 Všimněte si následujících podrobností o volání <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> metody:

- První parametr identifikuje příkaz, který chcete volat. Tento řetězec odpovídá hodnotě, kterou předáte do <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> definice příkazu.

- Druhý parametr je hodnota, kterou chcete předat vlastnímu parametru druhého příkazu. V tomto případě je to úplná cesta k souboru *. wsp* , který je upgradován na web služby SharePoint.

- Kód nepředá implicitní <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametr příkazu. Tento parametr se předává do příkazu automaticky při volání příkazu z rozšíření systému projektu služby SharePoint nebo rozšíření uzlu **připojení služby SharePoint** v **Průzkumník serveru**. V jiných typech řešení, jako je například v Průvodci šablonou projektu, který implementuje <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> rozhraní, má tento parametr **hodnotu null**.

## <a name="compile-the-code"></a>Kompilovat kód
 Tento příklad vyžaduje odkaz na sestavení Microsoft. VisualStudio. SharePoint.

## <a name="see-also"></a>Viz také
- [Volání do objektových modelů služby SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Postupy: vytvoření příkazu SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)
- [Návod: roztažení Průzkumník serveru pro zobrazení webových částí](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
