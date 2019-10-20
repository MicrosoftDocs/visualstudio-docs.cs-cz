---
title: Přepsání obsahu Help Manageru | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-help-viewer
ms.topic: conceptual
ms.assetid: 95fe6396-276b-4ee5-b03d-faacec42765f
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 70c0044a0436dcf27a3b087b3f11a5f759824735
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645567"
---
# <a name="help-content-manager-overrides"></a>Přepsání voleb aplikace Help Content Manager
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Úpravou registru můžete změnit výchozí chování aplikace Help Viewer a funkcí souvisejících s nápovědy v integrovaném vývojovém prostředí sady Visual Studio.

|Úloha|Klíč registru|Hodnota a definice|
|----------|------------------|--------------------------|
|Definování jedinečného koncového bodu služby|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSWinExpress\14.0\Help|NewContentAndUpdateService--*HTTPValueForTheServiceEndpoint*.|
|Definovat výchozí nastavení online/offline|HKEY_LOCAL_MACHINE\Software\Microsoft\VSWinExpress\14.0\help|UseOnlineHelp – zadejte `0` pro zadání místní aplikace Help a zadejte `1` pro zadání online nápovědě.|
|Definování jedinečného koncového bodu F1|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSWinExpress\14.0\Help|OnlineBaseUrl –*HTTPValueForTheServiceEndpoint*|
|Přepsat prioritu úlohy služby BITS|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (na 64ovém počítači) \Microsoft\Help\v2.2|BITSPriority – použijte jednu z následujících hodnot: **popředí**, **Vysoká**, **normální**nebo **Nízká**.|
|Zakázat online (a možnost IDE online)|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (na 64ovém počítači) \Microsoft\VisualStudio\14.0\Help|OnlineHelpPreferenceDisabled – Pokud chcete zakázat přístup k obsahu online, nastavte na hodnotu 1.|
|Zakázat správu obsahu|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (na 64ovém počítači) \Microsoft\VisualStudio\14.0\Help|ContentManagementDisabled – nastavením na hodnotu 1 zakážete kartu **Spravovat obsah** v programu Help Viewer.|
|Nasměrování na místní úložiště obsahu v síťové sdílené složce|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio11|LocationPath = "*ContentStoreNetworkShare*"|
|Zakáže instalaci obsahu při prvním spuštění funkce sady Visual Studio.|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (na 64ovém počítači) \Microsoft\VisualStudio\14.0\Help|DisableFirstRunHelpSelection – nastavte na hodnotu 1, pokud chcete zakázat funkce, které jsou nakonfigurovány při prvním spuštění sady Visual Studio.|

## <a name="see-also"></a>Viz také
 [Příručka správce Help Vieweru](../ide/help-viewer-administrator-guide.md)
