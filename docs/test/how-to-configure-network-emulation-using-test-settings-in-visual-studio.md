---
title: Konfigurace emulace sítě pomocí nastavení testu
ms.date: 10/03/2016
ms.topic: how-to
helpviewer_keywords:
- test settings, network emulation
ms.assetid: ff275cfb-5df9-4710-9a91-9caabaaad34f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 27de590cc40808eb3bebf18857c0ba4b254c39d1
ms.sourcegitcommit: 754133c68ad841f7d7962e0b7a575e133289d8a8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2020
ms.locfileid: "91928655"
---
# <a name="how-to-configure-network-emulation-using-test-settings-in-visual-studio"></a>Postupy: Konfigurace emulace sítě pomocí nastavení testu v aplikaci Visual Studio

Adaptér diagnostických dat můžete nakonfigurovat tak, aby otestoval svou aplikaci v různých síťových prostředích ze sady Visual Studio. Dá se taky nakonfigurovat k otestování umělé zátěže sítě nebo při spuštění testů.

> [!WARNING]
> Spustíte-li testy v reálné síti, která je pomalejšího typu než síť, kterou emulujete, test bude stále spuštěn při pomalejší rychlosti sítě. Emulace může zpomalit jenom síťové prostředí, a ne zrychlit.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

::: moniker range="vs-2017"
Následující postup popisuje, jak nakonfigurovat emulaci sítě z editoru konfigurace. Tento postup platí pro editor konfigurace v Microsoft Test Manager i v aplikaci Visual Studio.
::: moniker-end
::: moniker range=">=vs-2019"
Následující postup popisuje, jak nakonfigurovat emulaci sítě z editoru konfigurace. Tento postup platí pro editor konfigurace v aplikaci Visual Studio.
::: moniker-end

> [!NOTE]
> Adaptér diagnostických dat emulace sítě se vztahuje pouze na nastavení testu sady Visual Studio. Nepoužívá se pro nastavení testu v Microsoft Test Manager (zastaralé v aplikaci Visual Studio 2017).

::: moniker range="vs-2017"
Pro emulaci sítě se musí použít účet, který má oprávnění správce. Pokud jste vybrali emulaci sítě pro místní roli, která spouští Manuální testy, je nutné spustit Microsoft Test Manager pomocí oprávnění správce. Pokud jste vybrali emulaci sítě pro jakékoli jiné role, je nutné ověřit, zda testovací agent na počítači pro tuto roli používá uživatelský účet, který je členem skupiny Administrators. Další informace o tom, jak nastavit účet pro testovacího agenta, najdete v tématu [instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).
::: moniker-end

> [!NOTE]
> Účet síťové služby, který je výchozím účtem pro testovacího agenta, není členem skupiny Administrators.

**Skutečná emulace sítě**

Visual Studio používá pro všechny typy testů skutečnou emulaci sítě založenou na softwaru. To zahrnuje zátěžové testy. Skutečná emulace sítě simuluje stavy sítě pomocí přímé manipulace se síťovými pakety. Skutečný emulátor sítě může emulovat chování drátové i bezdrátové sítě pomocí spolehlivého fyzického propojení, jako je Ethernet. Následující atributy sítě jsou začleněny do skutečné emulace sítě:

- Doba odezvy v síti (latence)

- Množství dostupné šířky pásma

- Chování fronty

- Ztráta paketů

- Změna pořadí paketů

- Šíření chyb.

Skutečná emulace sítě také poskytuje flexibilitu při filtrování síťových paketů na základě IP adres nebo protokolů, jako jsou TCP, UDP a ICMP.

Skutečná emulace sítě může používat vývojáři a testeri sítě k emulaci požadovaného testovacího prostředí, vyhodnocení výkonu, předpovědi účinku změn nebo rozhodování o optimalizaci technologie. Ve srovnání s vrstvami testovacího hardwaru je skutečná emulace sítě mnohem levnější a pružnější řešení.

## <a name="configure-network-emulation-for-your-test-settings"></a>Konfigurace emulace sítě pro nastavení testu

Před provedením kroků v tomto postupu je nutné otevřít nastavení testu ze sady Visual Studio a poté vybrat stránku **data a diagnostika** .

### <a name="to-configure-network-emulation-for-your-test-settings"></a>Konfigurace emulace sítě pro nastavení testu

1. Vyberte roli, která se má použít k emulaci určité sítě.

    > [!NOTE]
    > Adaptér emulace sítě je třeba nakonfigurovat pouze v roli klienta nebo serveru. Nemusíte používat adaptér na obou rolích. Adaptér emuluje šum v síti, který má vliv na komunikaci mezi oběma rolemi, takže je nemusíte používat v obou. Pokud to není nutné, měli byste vybrat roli klienta pro adaptér emulace sítě, abyste se vyhnuli mimořádným nárokům na roli serveru.

2. Vyberte **emulace sítě** a pak zvolte **Konfigurovat**.

     Zobrazí se dialogové okno pro konfiguraci emulace sítě.

3. Vyberte šipku vedle rozevíracího **seznamu vyberte profil sítě, který se má použít**, a vyberte typ sítě, který chcete emulovat při spuštění testu (například **kabel-DSL 768Kps**).

    > [!WARNING]
    > Spustíte-li testy v reálné síti, která je pomalejšího typu než síť, kterou emulujete, test bude stále spuštěn při pomalejší rychlosti sítě. Emulace může zpomalit jenom síťové prostředí, a ne zrychlit.

4. Pokud zahrnete adaptér diagnostických dat emulace sítě do nastavení testu a máte v úmyslu ho použít na místním počítači, je nutné také připojit ovladač emulace sítě k jednomu z síťových adaptérů vašeho počítače. Ovladač emulace sítě je vyžadován pro fungování adaptéru diagnostických dat síťové emulace. Ovladač emulace sítě je nainstalovaný a vázaný na adaptér dvěma způsoby:

    - **Ovladač pro emulaci sítě nainstalovaný s Microsoft Visual Studio testovacího agenta:** Testovacího agenta Microsoft Visual Studio lze použít na vzdálených počítačích i na místním počítači. Když nainstalujete testovacího agenta sady Visual Studio, proces instalace zahrnuje konfigurační krok, který váže ovladač emulace sítě k vaší síťové kartě. Další informace najdete v tématu [instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).

    - **Ovladač pro emulaci sítě nainstalovaný s Microsoft Visual Studio Test Professional:** Při prvním použití emulace sítě budete vyzváni k navázání ovladače emulace sítě na síťovou kartu.

    > [!TIP]
    > Ovladač emulace sítě můžete také nainstalovat z příkazového řádku na místním počítači bez instalace testovacího agenta sady Visual Studio pomocí následujícího příkazu: **VSTESTCONFIG NETWORKEMULATION/Install**

## <a name="see-also"></a>Viz také

- [Shromažďování diagnostických informací pomocí nastavení testu](../test/collect-diagnostic-information-using-test-settings.md)
- [Spustit Manuální testy (Azure Test Plans)](/azure/devops/test/run-manual-tests?view=vsts&preserve-view=true)
