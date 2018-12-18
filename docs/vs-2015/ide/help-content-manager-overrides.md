---
title: Nápověda správce obsahu přepsání | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 95fe6396-276b-4ee5-b03d-faacec42765f
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 35c3d8a13ace801a06e7d1c658c9923e1432ef59
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49190252"
---
# <a name="help-content-manager-overrides"></a>Přepsání voleb aplikace Help Content Manager
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Úpravou registru můžete změnit výchozí chování aplikace Help Viewer a souvisejících s nápovědou funkcí v integrovaném vývojovém prostředí sady Visual Studio.  
  
|Úloha|Klíč registru|Hodnota a definice|  
|----------|------------------|--------------------------|  
|Definovat koncový bod služby jedinečný|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSWinExpress\14.0\Help|NewContentAndUpdateService--*HTTPValueForTheServiceEndpoint*.|  
|Definovat výchozí online i offline|HKEY_LOCAL_MACHINE\Software\Microsoft\VSWinExpress\14.0\help|UseOnlineHelp--zadejte `0` místní nápovědy, a zadejte `1` k určení online nápovědy.|  
|Definovat koncový bod jedinečný F1|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSWinExpress\14.0\Help|OnlineBaseUrl--*HTTPValueForTheServiceEndpoint*|  
|Přepsat Priorita úlohy BITS|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (na 64-bit machine)\Microsoft\Help\v2.2|BITSPriority – použijte jednu z následujících hodnot: **popředí**, **vysokou**, **normální**, nebo **nízké**.|  
|Zakázat Online (a možnost IDE Online)|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (na 64-bit machine)\Microsoft\VisualStudio\14.0\Help|OnlineHelpPreferenceDisabled – nastavte na 1 zakázat přístup k obsahu online nápovědy.|  
|Zakázat správu obsahu|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (na 64-bit machine)\Microsoft\VisualStudio\14.0\Help|ContentManagementDisabled--nastavena na hodnotu 1, chcete-li zakázat **spravovat obsah** kartě v aplikaci Help Viewer.|  
|Přejděte na místní úložiště obsahu v síťové sdílené složce|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio11|LocationPath = "*ContentStoreNetworkShare*"|  
|Zakážete instalaci obsahu při prvním spuštění funkce sady Visual Studio.|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (na 64-bit machine)\Microsoft\VisualStudio\14.0\Help|DisableFirstRunHelpSelection – nastavte na 1 zakázat funkce nápovědy, které jsou konfigurovány při prvním spuštění sady Visual Studio.|  
  
## <a name="see-also"></a>Viz také  
 [Příručka správce Help Vieweru](../ide/help-viewer-administrator-guide.md)



