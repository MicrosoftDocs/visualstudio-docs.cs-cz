---
title: Spustit kód při nasazení nebo odvolání projektu služby SharePoint
titleSuffix: ''
description: Naučte se, jak spustit kód při nasazení nebo odvolání projektu služby SharePoint, abyste mohli zpracovávat události, které jsou vyvolány v aplikaci Visual Studio.
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4645d0b2cf1670a3834c4ac09cd66d56b48fbf27
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2021
ms.locfileid: "106214470"
---
# <a name="how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Postupy: spuštění kódu při nasazení nebo odvolání projektu služby SharePoint
  Chcete-li provést další úkoly při nasazení nebo odvolání projektu služby SharePoint, můžete zpracovávat události, které jsou vyvolány v aplikaci Visual Studio. Další informace najdete v tématu věnovaném [rozšiřování balení a nasazení služby SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

### <a name="to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Spuštění kódu při nasazení nebo odvolání projektu služby SharePoint

1. Vytvořte rozšíření položky projektu, rozšíření projektu nebo definici nového typu položky projektu. Další informace najdete v následujících tématech:

   - [Postupy: Vytvoření rozšíření položky projektu služby SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

   - [Postupy: Vytvoření rozšíření projektu služby SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

   - [Postupy: definování typu položky projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. V rozšíření přístup k <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objektu. Další informace najdete v tématu [Postup: načtení služby projektu služby SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).

3. Zpracování <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> událostí a <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> služby projektu.

4. V obslužných rutinách událostí použijte <xref:Microsoft.VisualStudio.SharePoint.DeploymentEventArgs> parametr k získání informací o aktuální relaci nasazení. Můžete například určit, který projekt je v aktuální relaci nasazení a zda je nasazen nebo odvolán.

   Následující příklad kódu ukazuje, jak zpracovat <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> události a v rozšíření projektu. Toto rozšíření zapíše další zprávu do okna **výstup** , jakmile se nasazení spustí a dokončí pro projekt služby SharePoint.

   :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handleprojectdeploymentevents.cs" id="Snippet12":::
   :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handleprojectdeploymentevents.vb" id="Snippet12":::

## <a name="compile-the-code"></a>Kompilovat kód
 Tento příklad vyžaduje odkazy na následující sestavení:

- Microsoft. VisualStudio. SharePoint

- System. ComponentModel. složení

## <a name="deploy-the-extension"></a>Nasazení rozšíření
 Chcete-li nasadit rozšíření, vytvořte [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] balíček rozšíření (VSIX) pro sestavení a všechny další soubory, které chcete distribuovat s rozšířením. Další informace naleznete v tématu [nasazení rozšíření pro nástroje služby SharePoint v aplikaci Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Viz také
- [Rozšiřování balení a nasazení služby SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Postupy: spuštění kódu při spuštění kroků nasazení](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
