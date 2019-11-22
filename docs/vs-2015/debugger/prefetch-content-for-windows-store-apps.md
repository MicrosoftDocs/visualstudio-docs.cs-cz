---
title: Předběžné načtení obsahu pro aplikace pro Windows Store | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: b4481fef-3ebf-4f7d-9748-d43821a0ebac
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4ac6479b4dbb0815374174140deb0d660636ac9e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300518"
---
# <a name="prefetch-content-for-windows-store-apps"></a>Předběžné načtení obsahu pro aplikace pro Windows Store
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí pouze pro Windows] (.. /Image/windows_only_content.png "windows_only_content")  
  
 Pokud chcete, aby vaše aplikace pro Windows Store lépe reagovala, můžete požádat systém Windows, aby předem načetl nějaký webový obsah, jako jsou webové stránky nebo obrázky,[do mezipaměti WinInet](https://msdn.microsoft.com/library/aa383630.aspx)aplikace [WinInet](https://msdn.microsoft.com/0a06f2af-957a-4dff-a8cc-187370181b5c). Tato funkce se nazývá předběžné načítání. Je to obzvláště efektivní pro obsah, který se používá při spuštění, ale můžete také předběžně vymezit i jiný často používaný obsah. Metody třídy [Windows. Networking. BackgroundTransfer. ContentPrefetcher](https://msdn.microsoft.com/library/windows/apps/windows.networking.backgroundtransfer.contentprefetcher.aspx) umožňují zadat identifikátory URI obsahu, který chcete předem načíst.  
  
 Systém Windows používá heuristiky k určení, kdy a kde se mají vyskytnout předběžné načtení a které prostředky budou staženy. Heuristika bere v úvahu systémové sítě a podmínky napájení, historii využití uživatelských aplikací a výsledky předchozích pokusů o předběžné načtení. V aplikaci Visual Studio můžete použít příkaz **Spustit předběžné načtení aplikace pro Windows Store** , který vynutí, aby systém Windows ignoroval heuristické ContentPrefetcher a předem načetly veškerý zadaný webový obsah. To může být užitečné, pokud chcete otestovat chování nebo výkon aplikace pomocí obsahu, který se má předběžně načíst do známého stavu (buď načteno nebo není načteno).  
  
## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>Vynucení přednačtení ContentPrefetcher určených prostředků  
 Tento postup předpokládá, že jste již nastavili funkci ContentPrefetcher a zadali jste identifikátory URI obsahu pro předběžné načtení do projektu aplikace. Pokud chcete vynutit, aby se předem načetly obsah, když jsou zadané prostředky nové nebo upravené, musíte aplikaci spustit a zastavit předtím, než se rozhodnete aktivovat příkaz pro **předběžné načtení aplikace pro Windows Store** . Nejdřív aplikaci spustíte pro registraci identifikátorů URI. Aktivovat příkaz pro vygenerování **aplikace pro Windows Store** : vynutí ContentPrefetcher stažení obsahu a jeho přidání do mezipaměti. V následných spuštěních aplikace můžete předpokládat, že je obsah předem načten.  
  
1. Spusťte aplikaci pro registraci identifikátorů URI obsahu předběžného načtení do aplikace. V nabídce **ladění** klikněte na příkaz **Spustit ladění** (Klávesová zkratka: F5).  
  
2. V nabídce **ladění** vyberte možnost **Zastavit ladění** (Klávesová zkratka: Shift + F5).  
  
3. V nabídce **ladění** zvolte možnost **Další cíle ladění** a pak zvolte možnost **Spustit předběžné načtení aplikace pro Windows Store**.  
  
   Nyní můžete aplikaci ladit, testovat nebo analyzovat pomocí přednačtených webových prostředků.  
  
> [!NOTE]
> Tyto kroky opakujte, kdykoli přidáte nebo upravíte zadaný webový obsah.  
  
## <a name="see-also"></a>Viz také  
 [Blogový příspěvek: Aktivace předběžného načtení aplikací pro Windows Store ve Visual Studio 2013 Update 2](https://devblogs.microsoft.com/devops/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2/)
