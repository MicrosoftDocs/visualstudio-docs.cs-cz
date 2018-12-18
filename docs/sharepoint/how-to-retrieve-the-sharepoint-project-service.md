---
title: 'Postupy: načtení služby projektu služby SharePoint | Dokumentace Microsoftu'
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e8f9faa0ca539c3b5381aca4159cc4653543087a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49880595"
---
# <a name="how-to-retrieve-the-sharepoint-project-service"></a>Postupy: načtení služby projektu SharePoint
  Můžete přistupovat k projektu služby SharePoint v následujících typů řešení:  
  
-   Rozšíření systému projektu služby SharePoint, jako je například rozšíření projektu, rozšíření položky projektu nebo definice typu položky projektu. Další informace o těchto typech rozšíření najdete v tématu [rozšíření systému projektu služby SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
-   Rozšíření **připojení služby SharePoint** uzel v **Průzkumníka serveru**. Další informace o těchto typech rozšíření najdete v tématu [rozšíření uzlu připojení služby SharePoint v Průzkumníku serveru](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
-   Jiný typ rozšíření sady Visual Studio, jako je například VSPackage.  
  
## <a name="retrieve-the-service-in-project-system-extensions"></a>Načtení služby v rozšíření systému projektu  
 V rozšíření systému projektu služby SharePoint, dostanete služba projektu s použitím <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A> vlastnost <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objektu.  
  
 Pomocí následujících postupů můžete také načtení služby projektu.  
  
#### <a name="to-retrieve-the-service-in-a-project-extension"></a>Načtení služby projektu rozšíření  
  
1.  Ve vaší implementaci <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> rozhraní, vyhledejte <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> metody.  
  
2.  Použití *projectService* parametr přístup k této službě.  
  
     Následující příklad kódu ukazuje, jak použít službu projekt k zápisu zprávy do **výstup** okno a **seznam chyb** okna Jednoduchý projekt rozšíření.  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#1)]  
  
     Další informace o vytváření rozšíření projektu naleznete v tématu [postupy: vytváření rozšíření projektu služby SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
#### <a name="to-retrieve-the-service-in-a-project-item-extension"></a>Načtení služby v rozšíření položky projektu  
  
1.  Ve vaší implementaci <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> rozhraní, vyhledejte <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> metody.  
  
2.  Použití <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A> vlastnost *projectItemType* parametr načtení služby.  
  
     Následující příklad kódu ukazuje, jak použít službu projekt k zápisu zprávy do **výstup** okno a **seznam chyb** okna jednoduché rozšíření **definice seznamu** položky projektu.  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#2)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#2)]  
  
     Další informace o vytváření rozšíření položky projektu naleznete v tématu [postupy: vytváření rozšíření položky projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
#### <a name="to-retrieve-the-service-in-a-project-item-type-definition"></a>Načtení služby v definici typu položky projektu  
  
1.  Ve vaší implementaci <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> rozhraní, vyhledejte <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metody.  
  
2.  Použití <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A> vlastnost *typeDefinition* parametr načtení služby.  
  
     Následující příklad kódu ukazuje, jak použít službu projekt k zápisu zprávy do **výstup** okno a **seznam chyb** okna v definici typu položky Jednoduchý projekt.  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#3)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#3)]  
  
     Další informace o definování typů položek projektu, naleznete v tématu [postupy: definování typu položky projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
## <a name="retrieve-the-service-in-server-explorer-extensions"></a>Načtení služby v rozšíření Průzkumníka serveru  
 V rozšíření **připojení služby SharePoint** uzel v **Průzkumníka serveru**, můžete přístup ke službě projektu s použitím <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> vlastnost <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> objektu.  
  
#### <a name="to-retrieve-the-service-in-a-server-explorer-extension"></a>Načtení služby v rozšíření Průzkumníka serveru  
  
1.  Získat <xref:System.IServiceProvider> objektu z <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> vlastnost <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> objektu v rozšíření.  
  
2.  Použití <xref:System.IServiceProvider.GetService%2A> metodu pro žádost o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objektu.  
  
     Následující příklad kódu ukazuje, jak použít službu projekt k zápisu zprávy do **výstup** okno a **seznam chyb** okna z místní nabídky, která toto rozšíření přidá do seznamu uzlů v **Průzkumníka serveru**.  
  
     [!code-vb[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.cs#1)]  
  
     Další informace o rozšíření **připojení služby SharePoint** uzel v **Průzkumníka serveru**, naleznete v tématu [postupy: rozšíření uzlu služby SharePoint v Průzkumníku serveru](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## <a name="retrieve-the-service-in-other-visual-studio-extensions"></a>Načtení služby v jiné rozšíření sady Visual Studio  
 Možné načtení služby projektu v sadě VSPackage nebo v rozšíření sady Visual Studio, který má přístup k <xref:EnvDTE80.DTE2> objektu v objektovém modelu automatizace, jako je například Průvodce pro šablony projektu, který implementuje <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> rozhraní.  
  
 V sadě VSPackage, můžete požádat <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objektu pomocí jedné z následujících metod:  
  
- <xref:System.IServiceProvider.GetService%2A> Metoda spravované VSPackage, která je odvozena z <xref:Microsoft.VisualStudio.Shell.Package> třídy. Další informace najdete v tématu [postupy: získání služby](../extensibility/how-to-get-a-service.md).  
  
- Statické <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> metody. Další informace najdete v tématu [použití GetGlobalService](../extensibility/internals/service-essentials.md#how-to-use-getglobalservice).  
  
  V rozšíření sady Visual Studio, který má přístup k <xref:EnvDTE80.DTE2> objektu, můžete požádat o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> s použitím <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> metodu <xref:Microsoft.VisualStudio.Shell.ServiceProvider> objektu. Další informace najdete v tématu [získávání služby z objektu DTE](../extensibility/how-to-get-a-service.md#getting-a-service-from-the-dte-object).  
  
## <a name="see-also"></a>Viz také:
 [Použití služby projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md)   
 [Postupy: získání služby](../extensibility/how-to-get-a-service.md)   
 [Postupy: použití průvodců se šablonami projektů](../extensibility/how-to-use-wizards-with-project-templates.md)  
  
