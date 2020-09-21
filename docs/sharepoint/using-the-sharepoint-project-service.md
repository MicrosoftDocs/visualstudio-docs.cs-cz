---
title: Použití služby projektu SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
- SharePoint development in Visual Studio, extensibility features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7b3aeee895810eed8e434fda93328e4e179c9d39
ms.sourcegitcommit: 7a46232242783ebe23f2527f91eac8eb84b3ae05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2020
ms.locfileid: "90740107"
---
# <a name="use-the-sharepoint-project-service"></a>Použití služby projektu SharePoint
  Systém projektu služby SharePoint zahrnuje službu projektu, kterou lze použít k provádění úloh souvisejících se systémem projektu. Služba projektu je <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objekt.

 Ke službě projektu služby SharePoint můžete přistupovat v jakémkoli rozšíření nástrojů služby SharePoint. Můžete k němu také přistupovat v jiných typech rozšíření aplikace Visual Studio, jako jsou doplňky a sady VSPackage. Další informace najdete v tématu [Postup: načtení služby projektu služby SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).

## <a name="project-service-features"></a>Funkce služby projektu
 V následující tabulce jsou uvedeny úlohy, které lze provést pomocí služby projektu služby SharePoint a <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> metody nebo vlastnosti, které mají být použity k provedení jednotlivých úkolů.

|Úloha|Člen, který se má použít|
|----------|-------------------|
|Přístup k libovolnému projektu služby SharePoint, který je otevřen v aplikaci Visual Studio.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Projects%2A> majetek.|
|Přístup ke všem typům položek projektu služby SharePoint, které jsou k dispozici (včetně předdefinovaných a vlastních typů položek projektu).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ProjectItemTypes%2A> majetek.|
|Přístup ke všem krokům nasazení, které jsou k dispozici pro projekty služby SharePoint (včetně předdefinovaných a vlastních kroků nasazení).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.DeploymentSteps%2A> majetek.|
|Přístup k událostem, které jsou vyvolány, když se v projektu služby SharePoint refaktoruje kód vývojáře.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.CodeRefactoringEvents%2A> majetek.|
|Spusťte vlastní *příkaz SharePointu* , který volá do objektového modelu serveru SharePoint. Další informace o příkazech služby SharePoint naleznete v tématu [volání do objektových modelů služby SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> majetek.|
|Převod typu v systému projektu služby SharePoint na typ v modelu automatizačních objektů sady Visual Studio nebo modelu objektu integrace a naopak. Další informace naleznete v tématu [Převod mezi systémovými typy projektů SharePoint a jinými typy projektů aplikace Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> Metoda.|
|Umožňuje psát zprávy do okna **výstupu** nebo okna **Seznam chyb** v aplikaci Visual Studio.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Logger%2A> majetek.|
|Přístup k dalším službám, které jsou k dispozici v aplikaci Visual Studio.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ServiceProvider%2A> majetek.|
|Načtěte cestu k instalační složce místního webu služby SharePoint, která se používá pro ladění řešení.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointInstallPath%2A> majetek.|
|Určete, [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] zda [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] je v počítači nainstalována nebo.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.IsSharePointInstalled%2A> majetek.|
|Ověření funkce nebo balíčku v řešení služby SharePoint.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.PackageValidationProvider%2A> majetek.|

## <a name="see-also"></a>Viz také
- [Převod mezi systémovými typy projektů SharePoint a jinými typy projektů Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [Postupy: načtení služby projektu SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)
- [Rozšiřování nástrojů služby SharePoint v aplikaci Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Přehled programovacího modelu rozšíření nástrojů služby SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [Postupy: získání služby z objektu DTE](/previous-versions/bb166401(v=vs.140))