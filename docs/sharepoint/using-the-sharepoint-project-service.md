---
title: Použití služby projektu SharePoint | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
- SharePoint development in Visual Studio, extensibility features
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a5d4c2950754ebbef2920720cf784084b2968a82
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295056"
---
# <a name="use-the-sharepoint-project-service"></a>Použití služby projektu SharePoint
  Systém projektu služby SharePoint obsahuje projekt služby, který vám pomůže provádět úlohy související s systém projektu. Služba projektu není <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objektu.  
  
 Můžete přistupovat k projektu služby SharePoint v rozšíření nástrojů služby SharePoint. Můžete také přistupovat ji v jiných typech rozšíření sady Visual Studio, jako jsou doplňky a rozšíření VSPackages. Další informace najdete v tématu [postupy: načtení služby projektu služby SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).  
  
## <a name="project-service-features"></a>Funkce služba projektu
 V následující tabulce jsou uvedeny úlohy, které můžete provést pomocí projektu služby SharePoint a <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> metodu nebo vlastnost použít k provádění jednotlivých úkolů.  
  
|Úloha|Člen použití|  
|----------|-------------------|  
|Přístup k jakéhokoli projektu SharePoint, který je otevřený v sadě Visual Studio.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Projects%2A> Vlastnost.|  
|Přístup ke všem typů položek projektu služby SharePoint, které jsou k dispozici (včetně typů položek projektu předdefinované a vlastní).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ProjectItemTypes%2A> Vlastnost.|  
|Přístup ke všem jednotlivé kroky nasazení, které jsou k dispozici do projektů služby SharePoint (včetně postupu nasazení předdefinované a vlastní).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.DeploymentSteps%2A> Vlastnost.|  
|Přístup k události, které jsou vyvolány při vývojář refactors kód v projektu služby SharePoint.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.CodeRefactoringEvents%2A> Vlastnost.|  
|Spuštění vlastní *příkaz serveru SharePoint* , která volá do objektového modelu serveru SharePoint. Další informace o příkazech SharePoint, naleznete v tématu [volání do objektových modelů služby SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> Vlastnost.|  
|Převod typu v systému projektu služby SharePoint na typ v modelu objektu automatizace sady Visual Studio nebo integrace objektový model a naopak. Další informace najdete v tématu [převod mezi systémovými typy projektů SharePoint a jinými typy projektů Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> Metoda.|  
|Zápis zpráv do **výstup** okno nebo **seznam chyb** okna v sadě Visual Studio.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Logger%2A> Vlastnost.|  
|Přístup k dalším službám, které jsou k dispozici v sadě Visual Studio.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ServiceProvider%2A> Vlastnost.|  
|Načtěte cestu ke složce instalace místního webu služby SharePoint, který se používá pro řešení ladění.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointInstallPath%2A> Vlastnost.|  
|Určení, zda [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] nebo [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] je nainstalován v počítači.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.IsSharePointInstalled%2A> Vlastnost.|  
|Ověření funkcí nebo balíčku v řešení služby SharePoint.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.PackageValidationProvider%2A> Vlastnost.|  
  
## <a name="see-also"></a>Viz také:
 [Převod mezi systémovými typy projektů SharePoint a jinými typy projektů Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Postupy: načtení služby projektu SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)   
 [Rozšíření nástrojů SharePoint v sadě Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Přehled programovacího modelu SharePoint rozšíření nástrojů](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)   
 [Postupy: načtení služby z objektu DTE](https://msdn.microsoft.com/library/bb166401.aspx)  
  
