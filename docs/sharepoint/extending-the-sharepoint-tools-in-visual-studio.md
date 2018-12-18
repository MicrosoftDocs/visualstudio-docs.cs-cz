---
title: Rozšíření nástrojů SharePoint v sadě Visual Studio | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- extensibility [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extending tools
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f360982f26cf2eb9ffe26678743bb514d9606ae7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49890670"
---
# <a name="extend-the-sharepoint-tools-in-visual-studio"></a>Rozšíření nástrojů SharePoint v sadě Visual Studio
  Nástroje služby SharePoint v sadě Visual Studio požadavkům mnoha scénářů vývoje aplikace. Však můžete narazit na případy, kdy neposkytují funkce, které vyžadují vy nebo ostatní vývojáři. V těchto případech můžete rozšířit nástroje služby SharePoint k vytvoření funkce, které potřebujete.

## <a name="how-to-extend-the-sharepoint-tools"></a>Rozšíření nástrojů SharePoint
 Můžete rozšířit systém projektu služby SharePoint a **připojení služby SharePoint** uzlu **Průzkumníka serveru** okna.

### <a name="extend-the-sharepoint-project-system"></a>Rozšíření systému projektu služby SharePoint
 Visual Studio obsahuje sadu šablon projektů a šablon položek, které můžete použít k vytvoření řešení služby SharePoint. Jsou například šablony pro přijímače událostí, definice seznamu, pracovních postupů a webové části. Ale můžete také definovat vlastní typy položek Sharepointového projektu pro vytváření komponent služby SharePoint, například pole nebo vlastní akce. Můžete také vytvořit rozšíření pro typů položek projektu služby SharePoint, které jsou již nainstalovány v sadě Visual Studio a můžete vytvořit rozšíření pro projekty služby SharePoint.

 Další informace najdete v tématu [rozšíření systému projektu služby SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

### <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Rozšíření uzlu připojení služby SharePoint v Průzkumníku serveru
 V sadě Visual Studio, můžete použít **připojení služby SharePoint** uzlu **Průzkumníka serveru** okně zobrazíte mnoho součástí jednoho nebo více místních webů služby SharePoint v hierarchickém stromovém zobrazení. Můžete rozšířit také **připojení služby SharePoint** uzel následujícími způsoby:

- Přidáním vlastních uzlů. To je užitečné, pokud chcete zobrazit součásti Sharepointové weby, které nejsou zobrazeny ve výchozím nastavení.

- Rozšířením existujících uzlů. Například můžete přidat nový podřízený uzel do existujícího uzlu, nebo můžete přidat položky místní nabídky k uzlu a provádět úlohy, když vývojář klikne na položku nabídky.

  Další informace najdete v tématu [rozšíření uzlu připojení služby SharePoint v Průzkumníku serveru](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

## <a name="development-computer-requirements"></a>Požadavky na vývojový počítač
 Jak vytvořit rozšíření pro nástroje služby SharePoint, vývojový počítač musí splňovat stejné požadavky na vytváření řešení služby SharePoint v sadě Visual Studio.

 Doporučujeme také nainstalovat [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Sada SDK zahrnuje šablony projektů a nástrojů, které můžete použít rozšíření sady Visual Studio. Konkrétně se sada SDK zahrnuje šablony projektu, který vám umožní snadno vytvořit balíček rozšíření aplikace Visual Studio (VSIX). Balíčky VSIX jsou preferovaným způsobem, jak nasadit rozšíření sady Visual Studio v sadě Visual Studio. Všechna rozšíření nástrojů SharePoint musí být nasazené s použitím balíčků VSIX. Některé názorné postupy v této dokumentaci předpokládají, že máte [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] nainstalované.

 Instalaci sady Visual Studio SDK naleznete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md). Další informace o rozšíření sady Visual Studio najdete v tématu [spuštění pro vývoj rozšíření sady Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).

## <a name="see-also"></a>Viz také:

- [Přehled programovacího modelu SharePoint rozšíření nástrojů](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [Rozšíření systému projektu služby SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Rozšíření uzlu připojení služby SharePoint v Průzkumníku serveru](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Programování konceptů a funkcí pro rozšíření nástrojů SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [Referenční dokumentace &#40;rozšíření nástrojů SharePoint&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)
- [Ladění rozšíření pro nástroje služby SharePoint v sadě Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
- [Nasazení rozšíření pro nástroje služby SharePoint v sadě Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)