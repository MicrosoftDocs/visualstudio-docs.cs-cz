---
title: Získat data pro integrovaný uzel služby SharePoint v Průzkumník serveru
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7649092cc21fcc7b861f4ddf630007bde896e852
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585768"
---
# <a name="how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer"></a>Postupy: získání dat pro předdefinovaný uzel služby SharePoint v Průzkumník serveru
  Pro každý integrovaný uzel služby SharePoint v **Průzkumník serveru**můžete získat data pro základní komponentu služby SharePoint, kterou uzel představuje. Další informace najdete v tématu věnovaném [rozšiřování uzlu připojení služby SharePoint v Průzkumník serveru](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje, jak získat data pro základní SharePointový seznam, který uzel seznamu představuje v **Průzkumník serveru**. Ve výchozím nastavení mají uzly seznam uzlů **zobrazení v** kontextové nabídce prohlížeče, na které můžete kliknout a otevřít seznamy ve webovém prohlížeči. Tento příklad rozšiřuje seznam uzlů přidáním **zobrazení v místní nabídce aplikace Visual Studio** , která otevře seznamy přímo v aplikaci Visual Studio. Kód přistupuje k datům seznamu uzlu, aby získal adresu URL seznamu, který se má otevřít v aplikaci Visual Studio.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#10)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#10)]

 Tento příklad používá službu projektu SharePoint k získání <xref:EnvDTE.DTE> objektu, který se používá k otevření seznamů v aplikaci Visual Studio. Další informace o službě projektu služby SharePoint naleznete v tématu [použití služby projektu služby SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

 Další informace o základních úlohách pro vytvoření rozšíření pro uzel služby SharePoint naleznete v tématu [How to: rozšíření uzlu služby SharePoint v Průzkumník serveru](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

## <a name="compile-the-code"></a>Kompilovat kód
 Tento příklad vyžaduje odkazy na následující sestavení:

- EnvDTE

- Microsoft. VisualStudio. SharePoint

- Microsoft. VisualStudio. SharePoint. Explorer. Extensions

- System. ComponentModel. složení

## <a name="deploy-the-extension"></a>Nasazení rozšíření
 Chcete-li nasadit rozšíření **Průzkumník serveru** , vytvořte [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] balíček rozšíření (VSIX) pro sestavení a všechny další soubory, které chcete distribuovat s rozšířením. Další informace naleznete v tématu [nasazení rozšíření pro nástroje služby SharePoint v aplikaci Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Viz také
- [Rozšíří uzel připojení služby SharePoint v Průzkumník serveru](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Postupy: rozšiřování uzlu služby SharePoint v Průzkumník serveru](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [Použití služby projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
- [Nasazení rozšíření pro nástroje služby SharePoint v aplikaci Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
