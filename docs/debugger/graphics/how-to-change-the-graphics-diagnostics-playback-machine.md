---
title: 'Postupy: Změna počítače pro přehrávání diagnostiky grafiky | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 143ae65b8d7db584546c250bf5d032450bf220aa
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31473868"
---
# <a name="how-to-change-the-graphics-diagnostics-playback-machine"></a>Postupy: Změna počítače pro přehrávání diagnostiky grafiky
Grafických informací můžete přehrát zpět, pomocí místního počítače nebo pomocí vzdáleného počítače nebo zařízení.  
  
## <a name="choosing-a-playback-machine"></a>Vybrat počítače pro přehrávání  
 Počítače pro přehrávání je počítač nebo zařízení, která se používá k přehrání grafiky události z protokolu grafiky. Obvykle na místním počítači je nejvhodnější možnost, ale nemusí vykreslování problém reprodukovat na počítači, který má jiný hardware nebo ovladač verze než počítač, kde byla zaznamenána; v takovém případě můžete zvolit přehrávání vzdálený počítač, který lépe se shoduje s problém a dál používat vývojovém počítači při diagnostice ho.  
  
#### <a name="to-use-the-local-machine-to-play-back-graphics-information"></a>Použití místního počítače a přehrání grafických informací  
  
1.  V okně dokument grafických protokolů, zvolte **počítače pro přehrávání** odkaz. **Připojení vzdáleného ladicího programu** zobrazí se dialogové okno.  
  
2.  V části **ruční konfigurace**v **adresu** vlastnost, zadejte `localhost`.  
  
3.  Nastavte **režim ověřování** vlastnost **žádné**.  
  
4.  Vyberte **vyberte** tlačítko.  
  
#### <a name="to-use-a-remote-machine-to-play-back-graphics-information"></a>Použití vzdáleného počítače k přehrání grafických informací  
  
1.  V okně dokument grafických protokolů, zvolte **počítače pro přehrávání** odkaz. **Připojení vzdáleného ladicího programu** zobrazí se dialogové okno.  
  
2.  V části **ruční konfigurace**v **adresu** vlastnost, zadejte název domény systému Windows nebo IP adresu počítače nebo zařízení, které chcete použít k přehrání grafických informací.  
  
3.  Zadejte typ ověřování, který chcete použít k zabezpečení připojení k počítači přehrávání.  
  
    -   Pro ověřování systému Windows, nastavte **režim ověřování** vlastnost **Windows**.  
  
    -   Bez ověřování, nastavit **režim ověřování** vlastnost **žádné**.  
  
4.  Vyberte **vyberte** tlačítko.  
  
> [!NOTE]
>  **Připojení vzdáleného ladicího programu** dialogové okno se může zobrazit také vzdáleného ladění cíle, které jsou připojeny přímo k počítači pro vývoj nebo jsou ve stejné podsíti. Jeden z těchto cílů vzdáleného ladění můžete použít jako počítače pro přehrávání diagnostiky grafiky bez ručně její konfiguraci. V **připojení vzdáleného ladicího programu** dialogové okno, vyberte cíl má a potom zvolte **vyberte** tlačítko.  
  
## <a name="see-also"></a>Viz také  
 [Dokument grafických protokolů](graphics-log-document.md)