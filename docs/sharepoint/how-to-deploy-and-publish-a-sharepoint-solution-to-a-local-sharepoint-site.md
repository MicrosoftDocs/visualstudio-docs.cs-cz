---
title: Nasazení & publikování řešení služby SharePoint na místní SharePointový Web
titleSuffix: ''
description: Přečtěte si, jak nasadit nebo publikovat řešení služby SharePoint na místním SharePointovém serveru na vašem vývojovém počítači.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 22fe46e2876b14551637dd97712e1728816b020e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913700"
---
# <a name="how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site"></a>Postupy: nasazení a publikování řešení služby SharePoint na místní web služby SharePoint
  Řešení služby SharePoint můžete nasadit nebo publikovat na místním SharePointovém serveru na svém vývojovém počítači. Proces nasazení zkopíruje soubor *. wsp* na server SharePoint, nainstaluje řešení a potom tyto funkce aktivuje. Proces publikování kopíruje pouze soubor *. wsp* na server SharePoint a nainstaluje jej. Pokud ho chcete povolit v SharePointu, musíte ho ručně aktivovat.

## <a name="to-deploy-a-sharepoint-solution-to-the-local-sharepoint-server"></a>Nasazení řešení služby SharePoint na místní server SharePoint

1. V **Průzkumník řešení** vyberte projekt, který chcete nasadit.

2. Na řádku nabídek klikněte na položku **sestavit**, **nasadit řešení**.

     Soubor *. wsp* se vytvoří a nainstaluje na místním sharepointovém serveru. Funkce jsou také aktivovány.

## <a name="to-publish-a-sharepoint-solution-to-a-local-sharepoint-server"></a>Publikování řešení služby SharePoint na místním serveru SharePoint

1. V **Průzkumník řešení** otevřete místní nabídku pro projekt služby SharePoint, který chcete publikovat, a pak zvolte možnost **publikovat**.

2. V dialogovém okně **publikovat** klikněte na tlačítko možnosti **publikovat do systému souborů** .

3. Do textového pole **cílové umístění** zadejte místní cestu a pak klikněte na tlačítko **publikovat** .

     Průběh publikování se zobrazí v okně **výstupu** sady Visual Studio. Po dokončení procesu se soubor řešení (*. wsp*) nainstaluje na místní sharepointový Server. Musí se ale ještě aktivovat pro použití v SharePointu. Pokud soubor řešení již existuje, dojde k chybě a zobrazí se dotaz, zda chcete přepsat existující soubor. Informace o upgradu balíčku najdete v části věnované upgradu vzdálených balíčků v tématu [Postupy: nasazení, publikování a upgrade řešení služby SharePoint na vzdáleném serveru](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

## <a name="see-also"></a>Viz také
- [Postupy: nasazení, publikování a upgrade řešení služby SharePoint na vzdáleném serveru](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)
- [Vytváření balíčků řešení služby SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)
- [Postupy: Přizpůsobení balíčku řešení služby SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Postupy: Přidání a odebrání funkcí a položek do balíčku pomocí návrháře balíčků](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
