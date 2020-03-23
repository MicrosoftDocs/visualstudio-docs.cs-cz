---
title: Konfigurace emulace sítě pomocí nastavení testu
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, network emulation
ms.assetid: ff275cfb-5df9-4710-9a91-9caabaaad34f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 350640a4db6a81d19801aedb03d0d490895f97ef
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589211"
---
# <a name="how-to-configure-network-emulation-using-test-settings-in-visual-studio"></a>Postup: Konfigurace emulace sítě pomocí nastavení testu v sadě Visual Studio

Adaptér diagnostických dat můžete nakonfigurovat tak, aby otestoval aplikaci v různých síťových prostředích z aplikace Visual Studio. Může být také nakonfigurován pro testování umělé zatížení sítě nebo kritických bodů při spuštění testů.

> [!WARNING]
> Pokud spustíte testy v reálné síti, která je pomalejší typ než síť, kterou emulujete, test bude stále běžet při pomalejší rychlosti sítě. Emulace může pouze zpomalit síťové prostředí, nikoli ho urychlit.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Následující postup popisuje, jak nakonfigurovat emulaci sítě z konfiguračního editoru. Tyto kroky platí pro editor konfigurace ve Správci testů společnosti Microsoft i v sadě Visual Studio.

> [!NOTE]
> Adaptér diagnostických dat emulace sítě je použitelný pouze pro nastavení testu sady Visual Studio. Nepoužívá se pro nastavení testu ve Správci testů společnosti Microsoft.

Účet, který má oprávnění správce, musí být použit pro emulaci sítě. Pokud jste pro místní roli, která spouští ruční testy, vybrali emulaci sítě, je nutné spustit správce testů pomocí oprávnění správce. Pokud jste vybrali emulaci sítě pro jakoukoli jinou roli, je nutné ověřit, zda testovací agent v počítači pro tuto roli používá uživatelský účet, který je členem skupiny Administrators. Další informace o nastavení účtu testovacího agenta naleznete v [tématu Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).

> [!NOTE]
> Účet síťové služby, který je výchozím účtem testovacího agenta, není členem skupiny administrators.

**Skutečná emulace sítě**

Visual Studio používá softwarovou skutečnou síťovou emulaci pro všechny typy testů. To zahrnuje zátěžové testy. Skutečná emulace sítě simuluje síťové podmínky přímou manipulací se síťovými pakety. Skutečný emulátor sítě může emulovat chování kabelových i bezdrátových sítí pomocí spolehlivého fyzického propojení, například sítě Ethernet. Následující síťové atributy jsou začleněny do skutečné emulace sítě:

- Doba odezvy v síti (latence)

- Velikost dostupné šířky pásma

- Chování při řazení do fronty

- Ztráta paketů

- Změna pořadí paketů

- Šíření chyb.

Skutečná síťová emulace také poskytuje flexibilitu při filtrování síťových paketů na základě adres IP nebo protokolů, jako jsou TCP, UDP a ICMP.

Skutečná síťová emulace může být použita síťovými vývojáři a testery k emulaci požadovaného testovacího prostředí, posouzení výkonu, předvídání účinku změny nebo rozhodování o optimalizaci technologií. Ve srovnání s hardwarovými testovacími lůžky je skutečná emulace sítě mnohem levnějším a flexibilnějším řešením.

## <a name="configure-network-emulation-for-your-test-settings"></a>Konfigurace emulace sítě pro nastavení testu

Před provedením kroků v tomto postupu je nutné otevřít nastavení testu z aplikace Visual Studio a potom vybrat stránku **Data a diagnostika.**

### <a name="to-configure-network-emulation-for-your-test-settings"></a>Konfigurace emulace sítě pro nastavení testu

1. Vyberte roli, která se má použít k emulace určité sítě.

    > [!NOTE]
    > Adaptér emulace sítě je nutné nakonfigurovat pouze v roli klienta nebo v roli serveru. Není třeba používat adaptér v obou rolích. Adaptér emuluje šum sítě, který ovlivňuje komunikaci mezi oběma rolemi, takže jej není nutné použít na obou. Pokud to není nutné, měli byste vybrat roli klienta pro adaptér emulace sítě, abyste se vyhnuli dodatečné režii role serveru.

2. Vyberte **Emulace sítě** a pak zvolte **Konfigurovat**.

     Zobrazí se dialogové okno pro konfiguraci emulace sítě.

3. Vyberte šipku vedle **položky Vyberte síťový profil, který chcete použít**, a vyberte typ sítě, který chcete emulovat při spuštění testu (například **Kabel-DSL 768Kps).**

    > [!WARNING]
    > Pokud spustíte testy v reálné síti, která je pomalejší typ než síť, kterou emulujete, test bude stále běžet při pomalejší rychlosti sítě. Emulace může pouze zpomalit síťové prostředí, nikoli ho urychlit.

4. Pokud do nastavení testu zahrnete adaptér diagnostických dat emulace sítě a chcete jej použít v místním počítači, musíte také svázat ovladač emulace sítě s jedním ze síťových adaptérů počítače. Ovladač emulace sítě je vyžadován pro funkci adaptéru diagnostických dat emulace sítě. Ovladač emulace sítě je nainstalován a vázán na adaptér dvěma způsoby:

    - **Ovladač emulace sítě nainstalovaný s testovacím agentem sady Microsoft Visual Studio:** Testovací agent sady Microsoft Visual Studio lze použít ve vzdálených počítačích i v místním počítači. Při instalaci testovacího agenta sady Visual Studio zahrnuje proces instalace krok konfigurace, který váže ovladač emulace sítě na síťovou kartu. Další informace naleznete v [tématu Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).

    - **Ovladač emulace sítě nainstalovaný v aplikaci Microsoft Visual Studio Test Professional:** Při prvním použití emulace sítě budete vyzváni k vytvoření svázání ovladače emulace sítě se síťovou kartou.

    > [!TIP]
    > Ovladač emulace sítě můžete nainstalovat také z příkazového řádku v místním počítači bez instalace testovacího agenta sady Visual Studio pomocí následujícího **příkazu: VSTestConfig NETWORKEMULATION /install**

## <a name="see-also"></a>Viz také

- [Shromažďování diagnostických informací pomocí nastavení testu](../test/collect-diagnostic-information-using-test-settings.md)
- [Spuštění ručních testů (plány testů Azure)](/azure/devops/test/run-manual-tests?view=vsts)
