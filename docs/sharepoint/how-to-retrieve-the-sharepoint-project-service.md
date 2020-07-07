---
title: 'Postupy: načtení služby projektu SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: f49883337c5748c0f8bcab5d0a88e02612e51b4c
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015558"
---
# <a name="how-to-retrieve-the-sharepoint-project-service"></a>Postupy: načtení služby projektu SharePoint
  Ke službě projektu služby SharePoint máte přístup v následujících typech řešení:

- Rozšíření systému projektu služby SharePoint, jako je například rozšíření projektu, rozšíření položky projektu nebo definice typu položky projektu. Další informace o těchto typech rozšíření naleznete v tématu [rozšíření systému projektu služby SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

- Rozšíření uzlu **připojení služby SharePoint** v **Průzkumník serveru**. Další informace o těchto typech rozšíření najdete v tématu [rozšíření uzlu připojení služby SharePoint v Průzkumník serveru](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

- Jiný typ rozšíření sady Visual Studio, jako je například VSPackage.

## <a name="retrieve-the-service-in-project-system-extensions"></a>Načtení služby v rozšířeních systému projektu
 V jakémkoli rozšíření systému projektu služby SharePoint můžete ke službě projektu přistupovat pomocí <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A> vlastnosti <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objektu.

 Můžete také načíst službu projektu pomocí následujících postupů.

#### <a name="to-retrieve-the-service-in-a-project-extension"></a>Načtení služby v rozšíření projektu

1. V implementaci <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> rozhraní vyhledejte <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> metodu.

2. K přístupu ke službě použijte parametr *ProjectService* .

     Následující příklad kódu ukazuje, jak použít službu projektu k zápisu zprávy do okna **výstupu** a **Seznam chyb** okno v jednoduchém rozšíření projektu.

     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#1)]

     Další informace o vytváření rozšíření projektu naleznete v tématu [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

#### <a name="to-retrieve-the-service-in-a-project-item-extension"></a>Načtení služby v rozšíření položky projektu

1. V implementaci <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> rozhraní vyhledejte <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> metodu.

2. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A>K načtení služby použijte vlastnost parametru *projectItemType* .

     Následující příklad kódu ukazuje, jak použít službu projektu k zápisu zprávy do okna **výstupu** a **Seznam chyb** okno v jednoduchém rozšíření položky projektu **definice seznamu** .

     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#2)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#2)]

     Další informace o vytváření rozšíření položek projektu naleznete v tématu [How to: Create a SharePoint Item](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)Extension.

#### <a name="to-retrieve-the-service-in-a-project-item-type-definition"></a>Načtení služby v definici typu položky projektu

1. V implementaci <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> rozhraní vyhledejte <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metodu.

2. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A>K načtení služby použijte vlastnost parametru *typeDefinition* .

     Následující příklad kódu ukazuje, jak použít službu projektu k zápisu zprávy do okna **výstupu** a **Seznam chyb** okno v jednoduché definici typu položky projektu.

     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#3)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#3)]

     Další informace o definování typů položek projektu naleznete v tématu [How to: define a Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

## <a name="retrieve-the-service-in-server-explorer-extensions"></a>Načtení služby v rozšířeních Průzkumník serveru
 V rozšíření uzlu **připojení služby SharePoint** v **Průzkumník serveru**můžete ke službě projektu přistupovat pomocí <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> vlastnosti <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> objektu.

#### <a name="to-retrieve-the-service-in-a-server-explorer-extension"></a>Načtení služby v rozšíření Průzkumník serveru

1. Získá <xref:System.IServiceProvider> objekt z <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> vlastnosti <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> objektu ve vaší příponě.

2. Použijte <xref:System.IServiceProvider.GetService%2A> metodu pro vyžádání <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objektu.

     Následující příklad kódu ukazuje, jak použít službu projektu k zápisu zprávy do okna **výstupu** a **Seznam chyb** okno z místní nabídky, kterou rozšíření přidá do seznamu uzlů v **Průzkumník serveru**.

     [!code-vb[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.cs#1)]

     Další informace o rozšíření uzlu **připojení služby SharePoint** v **Průzkumník serveru**naleznete v tématu [How to: Extend and SharePoint Node in Průzkumník serveru](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

## <a name="retrieve-the-service-in-other-visual-studio-extensions"></a>Načtení služby v jiných rozšířeních sady Visual Studio
 Můžete načíst službu projektu ve VSPackage nebo v jakémkoli rozšíření sady Visual Studio, které má přístup k <xref:EnvDTE80.DTE2> objektu v modelu automatizačních objektů, jako je například Průvodce šablonou projektu, který implementuje <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> rozhraní.

 V VSPackage můžete požádat o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objekt pomocí jedné z následujících metod:

- <xref:System.IServiceProvider.GetService%2A>Metoda spravovaného VSPackage, která je odvozena od <xref:Microsoft.VisualStudio.Shell.Package> třídy. Další informace najdete v tématu [Postupy: získání služby](../extensibility/how-to-get-a-service.md).

- Statická <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> metoda. Další informace najdete v tématu [použití GetGlobalService](../extensibility/internals/service-essentials.md#how-to-use-getglobalservice).

  V rozšíření sady Visual Studio, které má přístup k <xref:EnvDTE80.DTE2> objektu, můžete požádat o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objekt pomocí <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> metody <xref:Microsoft.VisualStudio.Shell.ServiceProvider> objektu. Další informace najdete v tématu [získání služby z objektu DTE](../extensibility/how-to-get-a-service.md#getting-a-service-from-the-dte-object).

## <a name="see-also"></a>Viz také:
- [Použití služby projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
- [Postupy: získání služby](../extensibility/how-to-get-a-service.md)
- [Postupy: použití průvodců se šablonami projektů](../extensibility/how-to-use-wizards-with-project-templates.md)
