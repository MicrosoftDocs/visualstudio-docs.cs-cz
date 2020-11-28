---
title: 'Postupy: spuštění kódu při spuštění kroků nasazení | Microsoft Docs'
description: Spusťte kód pro zpracování událostí, které jsou vyvolány položkami projektu služby SharePoint před a poté, co aplikace Visual Studio spustí krok nasazení.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 00b921d8500c95ebbb771b5c0b5817db87b7c6ca
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304454"
---
# <a name="how-to-run-code-when-deployment-steps-are-executed"></a>Postupy: spuštění kódu při spuštění kroků nasazení
  Chcete-li provést další úkoly pro krok nasazení v projektu služby SharePoint, můžete zpracovávat události, které jsou vyvolány položkami projektu služby SharePoint před a poté, co aplikace Visual Studio provede jednotlivé kroky nasazení. Další informace najdete v tématu [rozšíření balení a nasazení služby SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

### <a name="to-run-code-when-deployment-steps-are-executed"></a>Spuštění kódu při provedení kroků nasazení

1. Vytvořte rozšíření položky projektu, rozšíření projektu nebo definici nového typu položky projektu. Další informace najdete v následujících tématech:

    - [Postupy: Vytvoření rozšíření položky projektu služby SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

    - [Postupy: Vytvoření rozšíření projektu služby SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

    - [Postupy: definování typu položky projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. V rozšíření zpracujte <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> události a <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> objektu (v rozšíření položky projektu nebo rozšíření projektu) nebo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> objekt (v definici nového typu položky projektu).

3. V obslužných rutinách událostí použijte <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs> <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepCompletedEventArgs> parametry a k získání informací o kroku nasazení. Můžete například určit, který krok nasazení je spuštěn a zda je řešení nasazeno nebo odvoláno.

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje, jak zpracovat <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> události a v rozšíření pro položku projektu instance seznamu. Toto rozšíření zapíše další zprávu do okna **výstup** , když aplikace Visual Studio recykluje fond aplikací během nasazování a odvolávání řešení.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handledeploymentstepevents.vb#4)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handledeploymentstepevents.cs#4)]

## <a name="compile-the-code"></a>Kompilovat kód
 Tento příklad vyžaduje odkazy na následující sestavení:

- Microsoft. VisualStudio. SharePoint

- System. ComponentModel. složení

## <a name="deploy-the-extension"></a>Nasazení rozšíření
 Chcete-li nasadit rozšíření, vytvořte [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] balíček rozšíření (VSIX) pro sestavení a všechny další soubory, které chcete distribuovat s rozšířením. Další informace naleznete v tématu [nasazení rozšíření pro nástroje služby SharePoint v aplikaci Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Viz také
- [Rozšiřování balení a nasazení služby SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Návod: Vytvoření vlastního kroku nasazení pro projekty SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)
- [Postupy: spuštění kódu při nasazení nebo odvolání projektu služby SharePoint](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)
