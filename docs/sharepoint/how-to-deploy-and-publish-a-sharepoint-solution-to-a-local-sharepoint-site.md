---
title: 'Postupy: nasazení a publikování řešení služby SharePoint na místní web služby SharePoint | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e288b5a284ca4155cf70f4458b5b490ca4289cbe
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120271"
---
# <a name="how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site"></a>Postupy: nasazení a publikování řešení služby SharePoint na místní web služby SharePoint
  Můžete nasadit nebo publikování řešení služby SharePoint na místním serveru SharePoint na vývojovém počítači. Kopie procesu nasazení *WSP* soubor na server služby SharePoint, nainstaluje řešení a potom aktivuje funkce. Publikování zpracovat pouze kopie *WSP* soubor na server služby SharePoint a ho nainstaluje. Je nutné ručně aktivovat jej a povolte ve službě SharePoint.  
  
## <a name="to-deploy-a-sharepoint-solution-to-the-local-sharepoint-server"></a>K nasazení řešení služby SharePoint na místním serveru SharePoint  
  
1.  V **Průzkumníku**, zvolte projekt, který chcete nasadit.  
  
2.  Na řádku nabídek zvolte **sestavení**, **nasadit řešení**.  
  
     *WSP* soubor je vytvořen a nainstalované na místním serveru SharePoint. Kromě toho jsou aktivované funkce.  
  
## <a name="to-publish-a-sharepoint-solution-to-a-local-sharepoint-server"></a>K publikování řešení služby SharePoint na místním serveru SharePoint  
  
1.  V **Průzkumníku řešení**, otevřete místní nabídky projektu služby SharePoint, kterou chcete publikovat a potom zvolte **publikovat**.  
  
2.  V **publikovat** dialogovém okně vyberte **publikovat do systému souborů** tlačítko.  
  
3.  V **cílové umístění** textového pole zadejte místní cestu a potom zvolte **publikovat** tlačítko.  
  
     V sadě Visual Studio se zobrazí průběh publikování **výstup** okno. Po dokončení tohoto procesu je řešení (*WSP*) soubor se nainstaluje na místní server SharePoint. Nicméně je nutné stále ho aktivovat pro použití ve službě SharePoint. Pokud již existuje soubor řešení, chybě dojde a zobrazí dotaz, zda chcete přepsat existující soubor. Informace o upgrade balíčku, najdete v části týkající se upgradu vzdálené balíčky v [postupy: nasazení, publikování a upgradování řešení služby SharePoint na vzdáleném serveru](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
## <a name="see-also"></a>Viz také:
 [Postupy: nasazení, publikování a upgradování řešení služby SharePoint na vzdáleném serveru](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)   
 [Vytváření balíčků řešení služby SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)   
 [Postupy: přizpůsobení balíčku řešení služby SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [Postupy: Přidání nebo odebrání funkcí a položek z balíčku pomocí návrháře balíčků](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
