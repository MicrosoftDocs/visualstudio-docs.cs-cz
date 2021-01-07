---
title: Ladění pomocí předběžného načteného obsahu v aplikacích pro UWP | Microsoft Docs
description: Pokud chcete, aby aplikace UWP lépe reagovala, použijte ContentPrefetcher a vyžádejte si systém Windows, aby využíval webový obsah.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 33eb7aa0559fc7a6170da658ccc9f00653968bb6
ms.sourcegitcommit: c67dece5ded82a5867148e1f94396954c1ec4398
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2021
ms.locfileid: "97975027"
---
# <a name="debug-uwp-apps-using-prefetched-content-in-visual-studio"></a>Ladění aplikací pro UWP pomocí předběžného načteného obsahu v aplikaci Visual Studio

 Pokud chcete, aby aplikace pro UWP lépe reagovala, můžete požádat Windows, aby předem načetl nějaký webový obsah, například webové stránky nebo obrázky, do mezipaměti [WinInet](/windows/desktop/WinInet/about-wininet) aplikace. Tato funkce se nazývá předběžné načítání. Je to obzvláště efektivní pro obsah, který se používá při spuštění, ale můžete také předběžně vymezit i jiný často používaný obsah. Metody třídy [Windows. Networking. BackgroundTransfer. ContentPrefetcher](/uwp/api/Windows.Networking.BackgroundTransfer.ContentPrefetcher) umožňují zadat identifikátory URI obsahu, který chcete předem načíst. Příklady přidávání funkcí ContentPrefetcher do aplikace najdete v [ukázce předběžného načtení obsahu](https://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309) Windows SDK.

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
- [Blogový příspěvek: Aktivace předběžného načtení aplikací pro Windows Store ve Visual Studio 2013 Update 2](https://devblogs.microsoft.com/devops/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2/)