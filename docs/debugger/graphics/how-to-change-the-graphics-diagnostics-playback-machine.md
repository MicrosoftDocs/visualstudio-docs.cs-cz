---
title: 'Postupy: Změna Diagnostika grafiky počítač pro přehrávání | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4f057e2e4f9d39fd3c5d985b3f0d19751d508614
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85769384"
---
# <a name="how-to-change-the-graphics-diagnostics-playback-machine"></a>Postupy: Změna počítače pro přehrávání diagnostiky grafiky
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

## <a name="see-also"></a>Viz také:
- [Dokument grafických protokolů](graphics-log-document.md)