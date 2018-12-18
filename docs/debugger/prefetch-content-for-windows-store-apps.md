---
title: Ladění pomocí předem načteného obsahu v aplikacích pro UWP | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 72c4b305152694e8d3664b54aef3477d2f8b1fec
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49854582"
---
# <a name="debug-uwp-apps-using-prefetched-content-in-visual-studio"></a>Ladění aplikací pro UWP pomocí předem načteného obsahu v sadě Visual Studio
  
 Aby vaše aplikace pro UPW odezvu, můžete požádat o přednačtení některé webového obsahu, jako je například Image, nebo webové stránky do aplikace Windows [WinINet](/windows/desktop/WinInet/about-wininet) mezipaměti. Tato funkce je volána předběžné načítání. To je zvláště efektivní pro obsah, který se používá při spuštění, ale předběžné další často používané obsah může načtení příliš. Metody [Windows.Networking.BackgroundTransfer.ContentPrefetcher](/uwp/api/Windows.Networking.BackgroundTransfer.ContentPrefetcher) umožňují zadat identifikátory URI, který chcete předběžné načtení obsahu. Sada Windows SDK [předběžné načtení obsahu ukázka](https://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309) příklady toho, jak přidat ContentPrefetcher funkce do vaší aplikace.  
  
 Windows používá heuristiky určit, kdy a pokud se předběžné načítání by mělo dojít k a které prostředky se stáhne. Heuristické metody brát v síti účet systému a podmínky napájení, historie využití aplikace uživatele a výsledky předběžného načtení předchozí pokusy. V sadě Visual Studio, můžete použít **předběžné načítání aplikací pro aktivační událost Windows Store** příkaz přinutit Windows ignorovat ContentPrefetcher heuristik a předběžné načtení veškerý obsah, zadaný web. To může být užitečné, pokud chcete otestovat výkon s obsahem pro předběžné načtení do známého stavu (načtení nebo není načtený) nebo chování aplikace.  
  
## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>Chcete-li vynutit předběžné načtení z ContentPrefetcher zadané prostředky  
 Tento postup předpokládá, že jste už nastavení funkce ContentPrefetcher a zadat identifikátory URI obsahu přednačtení v projektu aplikace. Chcete-li vynutit předběžné načtení obsahu, pokud zadané prostředky jsou nové nebo upravené, budete muset spuštění a zastavení aplikace, než se rozhodnete **předběžné načítání aplikací pro aktivační událost Windows Store** příkazu. Je-li spustit aplikaci nejprve zaregistrovat identifikátory URI. **Aktivovat předběžné načítání aplikací pro Windows Store** příkaz pak vynutí ContentPrefetcher ke stažení obsahu a přidat ho do mezipaměti. Při dalším spuštění aplikace můžete předpokládat, že obsah se předem načtou.  
  
1. Spustí aplikaci pro registraci předběžné načtení obsahu identifikátory URI v aplikaci. Na **ladění** nabídce zvolte **spustit ladění** (Klávesová zkratka: F5).  
  
2. Na **ladění** nabídce zvolte **Zastavit ladění** (Klávesová zkratka: Shift + F5).  
  
3. Na **ladění** nabídce zvolte **jiné cíle ladění** a klikněte na tlačítko **předběžné načítání aplikací pro aktivační událost Windows Store**.  
  
   Teď můžete ladit, testování nebo analyzovat aplikace s využitím předem načteného webových prostředků.  
  
> [!NOTE]
>  Tento postup opakujte, pokaždé, když přidáváte nebo odebíráte Zadaný webový obsah.  
  
## <a name="see-also"></a>Viz také  
 [Blogový příspěvek: Aktivace předběžné načtení pro Windows Store aplikace ve Visual Studio 2013 Update 2](https://blogs.msdn.microsoft.com/devops/2014/02/06/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2/)