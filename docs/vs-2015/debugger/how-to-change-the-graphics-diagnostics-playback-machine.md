---
title: 'Postupy: Změna Diagnostika grafiky počítač pro přehrávání | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cb14fb4017ea1df6659b9a1a0ac093cd7cf7e0b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64811175"
---
# <a name="how-to-change-the-graphics-diagnostics-playback-machine"></a>Postupy: Změna počítače pro přehrávání diagnostiky grafiky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí místního počítače nebo vzdáleného počítače nebo zařízení můžete přehrát informace o grafice.  
  
## <a name="choosing-a-playback-machine"></a>Výběr počítače pro přehrávání  
 Počítač pro přehrávání je počítač nebo zařízení, které se používá k přehrávání grafických událostí z protokolu grafiky. Obvykle je místní počítač nejvhodnější možností, ale problém vykreslování nemusí reprodukován na počítači, který má jiné verze hardwaru nebo ovladače než počítač, ve kterém byl zachycen. Pokud k tomu dojde, můžete zvolit vzdálený počítač pro přehrávání, který lépe reprodukuje problém a stále používá váš vývojový počítač k jeho diagnostice.  
  
#### <a name="to-use-the-local-machine-to-play-back-graphics-information"></a>Použití místního počítače k přehrání grafické informace  
  
1. V okně dokument protokolu grafiky klikněte na odkaz pro **přehrání počítače** . Zobrazí se dialogové okno **připojení vzdáleného ladicího programu** .  
  
2. V části **Ruční konfigurace**do vlastnosti **adresa** zadejte `localhost` .  
  
3. Nastavte vlastnost **režim ověřování** na **žádný**.  
  
4. Klikněte na tlačítko **Vybrat** .  
  
#### <a name="to-use-a-remote-machine-to-play-back-graphics-information"></a>Použití vzdáleného počítače k přehrání grafické informace  
  
1. V okně dokument protokolu grafiky klikněte na odkaz pro **přehrání počítače** . Zobrazí se dialogové okno **připojení vzdáleného ladicího programu** .  
  
2. V části **Ruční konfigurace**do vlastnosti **adresa** zadejte název domény nebo IP adresu počítače nebo zařízení, které chcete použít k přehrávání informací o grafice.  
  
3. Zadejte druh autorizace, který chcete použít k zabezpečení připojení k počítači pro přehrávání.  
  
    - Pro ověřování systému Windows nastavte vlastnost **režim ověřování** na hodnotu **Windows**.  
  
    - Pro možnost bez ověřování nastavte vlastnost **režim ověřování** na **žádný**.  
  
4. Klikněte na tlačítko **Vybrat** .  
  
> [!NOTE]
> Dialogové okno **připojení vzdáleného ladicího programu** může také zobrazit cíle pro vzdálené ladění, které jsou přímo připojeny k vývojovému počítači nebo jsou ve stejné podsíti. Jeden z těchto cílů vzdáleného ladění můžete použít jako počítač pro přehrávání Diagnostika grafiky bez ruční konfigurace. V dialogovém okně **připojení vzdáleného ladicího programu** vyberte požadovaný cíl a pak klikněte na tlačítko **Vybrat** .  
  
## <a name="see-also"></a>Viz také  
 [Dokument grafických protokolů](../debugger/graphics-log-document.md)
