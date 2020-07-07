---
title: Rozšíření nástrojů služby SharePoint v aplikaci Visual Studio | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- extensibility [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extending tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7dc0cc0d0af73d032d870629877b62c94e6b347b
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016034"
---
# <a name="extend-the-sharepoint-tools-in-visual-studio"></a>Rozšiřování nástrojů služby SharePoint v aplikaci Visual Studio
  Nástroje služby SharePoint v aplikaci Visual Studio splňují požadavky mnoha scénářů vývoje aplikací. Můžete však zjistit případy, kdy neposkytují funkce, které požadujete vy nebo ostatní vývojáři. V těchto případech můžete nástroje služby SharePoint rozšíříte tak, aby se vytvořila funkčnost, kterou potřebujete.

## <a name="how-to-extend-the-sharepoint-tools"></a>Postup rozšiřování nástrojů služby SharePoint
 Můžete roztáhnout systém projektu služby SharePoint a uzel **připojení služby SharePoint** v okně **Průzkumník serveru** .

### <a name="extend-the-sharepoint-project-system"></a>Rozšíří systém projektu služby SharePoint.
 Sada Visual Studio obsahuje sadu šablon projektů a šablon položek, které můžete použít k vytvoření řešení služby SharePoint. Existují například šablony pro přijímače událostí, definice seznamů, pracovní postupy a Webové části. Můžete však také definovat vlastní typy položek projektu služby SharePoint pro vytváření komponent služby SharePoint, jako jsou například pole nebo vlastní akce. Můžete také vytvořit rozšíření pro typy položek projektu služby SharePoint, které jsou již nainstalovány v aplikaci Visual Studio, a můžete vytvořit rozšíření pro projekty služby SharePoint.

 Další informace najdete v tématu věnovaném [roztažení systému projektu služby SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

### <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Rozšíří uzel připojení služby SharePoint v Průzkumník serveru
 V aplikaci Visual Studio můžete použít uzel **připojení služby SharePoint** v okně **Průzkumník serveru** k zobrazení mnoha součástí jednoho nebo více místních webů služby SharePoint v hierarchickém stromovém zobrazení. Uzel **připojení služby SharePoint** můžete také roztáhnout následujícími způsoby:

- Přidáním vlastních uzlů. To je užitečné, pokud chcete zobrazit součásti webů SharePointu, které se ve výchozím nastavení nezobrazují.

- Rozšířením existujících uzlů. Můžete například přidat nový podřízený uzel do existujícího uzlu nebo můžete přidat položku místní nabídky do uzlu a provádět úlohy, když vývojář klikne na položku nabídky.

  Další informace najdete v tématu věnovaném [rozšiřování uzlu připojení služby SharePoint v Průzkumník serveru](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

## <a name="development-computer-requirements"></a>Požadavky na vývojového počítače
 Chcete-li vytvořit rozšíření pro nástroje služby SharePoint, váš vývojový počítač musí splňovat stejné požadavky pro vytváření řešení služby SharePoint v aplikaci Visual Studio.

 Doporučujeme také nainstalovat [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] . Sada SDK obsahuje šablony projektů a nástroje, které můžete použít k rozšiřování sady Visual Studio. Konkrétně sada SDK obsahuje šablonu projektu, kterou můžete použít k snadnému vytvoření balíčku rozšíření sady Visual Studio (VSIX). Balíčky VSIX jsou preferovaným způsobem, jak nasadit rozšíření sady Visual Studio v aplikaci Visual Studio. Všechna rozšíření nástrojů služby SharePoint je nutné nasadit pomocí balíčků VSIX. Všechny návody v této dokumentaci předpokládají, že máte [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] nainstalovanou sadu.

 Chcete-li nainstalovat sadu Visual Studio SDK, přečtěte si téma [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md). Další informace o rozšířeních sady Visual Studio naleznete v tématu [zahájení vývoje rozšíření aplikace Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).

## <a name="see-also"></a>Viz také:

- [Přehled programovacího modelu rozšíření nástrojů služby SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [Rozšíří systém projektu služby SharePoint.](../sharepoint/extending-the-sharepoint-project-system.md)
- [Rozšíří uzel připojení služby SharePoint v Průzkumník serveru](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Programování konceptů a funkcí pro rozšíření nástrojů služby SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [Referenční informace &#40;rozšíření nástrojů služby SharePoint&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)
- [Rozšíření ladění pro nástroje služby SharePoint v aplikaci Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
- [Nasazení rozšíření pro nástroje služby SharePoint v aplikaci Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)