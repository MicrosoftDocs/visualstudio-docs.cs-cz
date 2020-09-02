---
title: 'Převést: systémové typy projektů SharePointu na/z jiných typů'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 40ea60a8df5bc0bcd033c60a83d742ed3249cc53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "66836001"
---
# <a name="convert-between-sharepoint-project-system-types-and-other-visual-studio-project-types"></a>Převod mezi systémovými typy projektů SharePoint a jinými typy projektů Visual Studio
  V některých případech může být objekt v systému projektu služby SharePoint a chcete používat funkce odpovídajícího objektu v modelu automatizačních objektů sady Visual Studio nebo v modelu integračních objektů, nebo naopak. V těchto případech můžete použít <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> metodu služby projektu služby SharePoint k převedení objektu na jiný objektový model.

 Například můžete mít <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objekt, ale chcete použít metody, které jsou k dispozici pouze v <xref:EnvDTE.Project> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> objektu nebo. V tomto případě můžete použít <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> metodu k převedení na <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> <xref:EnvDTE.Project> nebo <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> .

 Další informace o modelu automatizačních objektů sady Visual Studio a modelu integračních objektů sady Visual Studio naleznete v tématu [Přehled programovacího modelu rozšíření nástrojů služby SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).

## <a name="types-of-conversions"></a>Typy převodů
 V následující tabulce jsou uvedeny typy, které může tato metoda převést mezi systémem projektu služby SharePoint a ostatními objektovými modely sady Visual Studio.

|Typ systému projektu služby SharePoint|Odpovídající typy v modelech automatizace a objektů integrace|
|------------------------------------|-------------------------------------------------------------------------|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>|<xref:EnvDTE.Project><br /><br /> nebo<br /><br /> Jakékoli rozhraní v modelu integračních objektů sady Visual Studio, které je implementováno pomocí základního objektu COM pro projekt. Mezi tato rozhraní patří <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> , <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> (nebo odvozené rozhraní) a <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> . Seznam hlavních rozhraní, která jsou implementována projekty, naleznete v tématu [základní komponenty modelu projektu](../extensibility/internals/project-model-core-components.md).|
|<xref:Microsoft.VisualStudio.SharePoint.IMappedFolder><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>|<xref:EnvDTE.ProjectItem><br /><br /> nebo<br /><br /> <xref:System.UInt32>Hodnota (označovaná také jako VSITEMID), která identifikuje člena projektu v <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> , který ho obsahuje. Tuto hodnotu lze předat parametru *itemid* některých <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> metod.|

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje, jak použít <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> metodu pro převod <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objektu na <xref:EnvDTE.Project> .

 [!code-csharp[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/CSharp/spprojectserviceaddin/connect.cs#2)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/VisualBasic/spprojectserviceaddin/connect.vb#2)]

 Tento příklad vyžaduje:

- Rozšíření systému projektu služby SharePoint, které obsahuje odkaz na sestavení *EnvDTE.dll* . Další informace najdete v tématu věnovaném [roztažení systému projektu služby SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

- Kód, který registruje `projectService_ProjectAdded` metodu pro zpracování <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> události <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objektu. Příklad naleznete v tématu [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

## <a name="see-also"></a>Viz také

- [Použití služby projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
- [Postupy: načtení služby projektu SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)
- [Přehled programovacího modelu rozšíření nástrojů služby SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
