---
title: 'Postupy: Přidání nebo odebrání připojení služby SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, browsing SharePoint sites
- SharePoint development in Visual Studio, SharePoint Connections
- SharePoint Connections [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cec1389294c8baf169db055acb87619114d7d19b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "86014565"
---
# <a name="how-to-add-or-remove-sharepoint-connections"></a>Postupy: Přidání nebo odebrání připojení služby SharePoint
  Průzkumník serveru umožňuje procházet SharePointové weby i datová připojení. Než však budete moci procházet obsah webu služby SharePoint, je nutné jej přidat do uzlu **připojení služby SharePoint** .

### <a name="to-add-a-sharepoint-site-to-the-sharepoint-connections-node"></a>Přidání webu služby SharePoint do uzlu připojení služby SharePoint

1. Na panelu nabídek vyberte možnost **zobrazení**, **Průzkumník serveru**.

2. V **Průzkumník serveru**zvolte uzel **připojení služby SharePoint** a potom v řádku nabídek zvolte **nástroje**  >  **Přidat připojení k SharePointu**.

3. V poli **Přidat připojení služby SharePoint** zadejte [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] pro web služby SharePoint (například http://testserver/sites/unittests) .

### <a name="to-delete-a-sharepoint-site-from-the-sharepoint-connections-node"></a>Odstranění webu služby SharePoint z uzlu připojení služby SharePoint

1. V řádku nabídek otevřete **Průzkumník serveru**výběrem **View**možnosti zobrazení **Průzkumník serveru** .

2. Rozbalte uzel **připojení služby SharePoint** , aby bylo možné zobrazit web služby SharePoint, který chcete odstranit z **Průzkumník serveru**.

3. Zvolte lokalitu a pak na panelu nabídek zvolte **Upravit**  >  **Odstranit**.

    > [!NOTE]
    > Tento krok neodstraní příslušný web. odstraní pouze připojení z **Průzkumník serveru**.

## <a name="see-also"></a>Viz také
- [Procházení připojení služby SharePoint pomocí Průzkumník serveru](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
