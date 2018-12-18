---
title: Konfigurace emulace sítě s využitím testovacích nastavení
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, network emulation
ms.assetid: ff275cfb-5df9-4710-9a91-9caabaaad34f
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 032eff41f0e6b6366e5eb56dad591a02ebde4984
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065892"
---
# <a name="how-to-configure-network-emulation-using-test-settings-in-visual-studio"></a>Postupy: Konfigurace emulace sítě s využitím testovacích nastavení v sadě Visual Studio

Můžete nakonfigurovat adaptér diagnostických dat a otestujte aplikaci v různých síťových prostředích ze sady Visual Studio. Můžete také možné nakonfigurovat, aby testovací umělé zatížení sítě nebo problémového místa při spuštění testů.

> [!WARNING]
> Pokud spustíte testy na skutečné síti, která je pomalejšího typu než síť, kterou emulujete, test bude stále spuštěn pomocí pomalejší rychlosti sítě. Emulace můžete pouze zpomalit síťové prostředí, ne zrychlit.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Následující postup popisuje konfiguraci emulace sítě z editoru konfigurace. Tento postup platí pro editor konfigurace v nástroji Microsoft Test Manager a sady Visual Studio.

> [!NOTE]
> Adaptér diagnostických dat síťové emulace platí pouze pro nastavení testu Visual Studio. Pro nastavení testu v nástroji Microsoft Test Manager se nepoužívá.

Pro emulaci sítě musíte použít účet, který má oprávnění správce. Pokud jste vybrali emulaci sítě pro roli místního spuštění ručních testů, je nutné spustit Microsoft Test Manager pomocí oprávnění správce. Pokud jste vybrali emulaci sítě pro jiné role, je nutné ověřit, že testovací agent na počítači pro tuto roli používá uživatelský účet, který je členem skupiny administrators. Další informace o tom, jak nastavit účet pro testovacího agenta, najdete v části [instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).

> [!NOTE]
> Účet Network Service, což je výchozí účet pro testovacího agenta, není členem skupiny administrators.

**Skutečná emulace sítě**

Visual Studio používá pro všechny typy testu skutečnou síťovou softwarovou emulaci. Patří sem zátěžové testy. Skutečná emulace sítě simuluje stavy sítě prostřednictvím přímé manipulace se síťovými pakety. Emulátor skutečné sítě může emulovat chování drátové i bezdrátové sítě pomocí spolehlivého fyzického propojení, jako je Ethernet. Následující atributy sítě jsou začleněny do emulace sítě:

- Časem přenosu v síti (čekací doba)

- Množství dostupné šířky pásma

- Chování řízení front

- Ztráta paketů

- Změna pořadí paketů

- Šíření chyb.

Skutečná emulace sítě také poskytuje flexibilitu při filtrování síťových paketů na základě IP adresy nebo protokoly, například TCP, UDP a ICMP.

Skutečná emulace sítě umožňuje založené na síti vývojářům a testerům emulovat požadované zkušební prostředí, hodnotit výkon, odhadnout účinky změn nebo rozhodovat o optimalizaci technologie. Srovnání s vrstvami testovacího hardwaru je skutečná emulace sítě mnohem levnější a pružnější řešení.

## <a name="configure-network-emulation-for-your-test-settings"></a>Konfigurace emulace sítě pro nastavení testu

Před provedením kroků v tomto postupu je nutné otevřít nastavení testů ze sady Visual Studio a vyberte **dat a diagnostiky** stránky.

### <a name="to-configure-network-emulation-for-your-test-settings"></a>Konfigurace emulace sítě pro nastavení testu

1.  Vyberte roli, které chcete použít k emulaci určité sítě.

    > [!NOTE]
    > Budete muset nakonfigurovat adaptér emulace sítě pouze v roli klienta nebo role serveru. Není nutné použít adaptér pro obě role. Adaptér emuluje rušení v síti, která má vliv na komunikaci mezi oběma rolemi, takže není nutné jej používat u obou. Pokud to není nezbytné, měli byste vybrat roli klienta adaptéru emulace sítě, aby se zabránilo další režii v roli serveru.

2.  Vyberte **emulace sítě** a klikněte na tlačítko **konfigurovat**.

     Zobrazí se dialogové okno pro konfiguraci emulace sítě.

3.  Klikněte na šipku vedle položky **vyberte profil sítě na používání**a vyberte typ sítě, kterou chcete emulovat při spuštění testu (například **kabel-DSL, 768 kb /**).

    > [!WARNING]
    > Pokud spustíte testy na skutečné síti, která je pomalejšího typu než síť, kterou emulujete, test bude stále spuštěn pomocí pomalejší rychlosti sítě. Emulace můžete pouze zpomalit síťové prostředí, ne zrychlit.

4.  Pokud zahrnete emulaci adaptéru diagnostických dat sítě v nastavení testu a máte v úmyslu použít na místním počítači, pak musíte také svázat ovladač emulace sítě do jednoho ze síťových adaptérů v počítači. Ovladač emulace sítě je vyžadován pro adaptér diagnostických dat síťové emulace na funkci. Ovladač emulace sítě je nainstalován a svázán k adaptéru dvěma způsoby:

    -   **Ovladač pro emulaci sítě nainstalovaný s Microsoft Visual Studio Test Agent:** The Microsoft Visual Studio Test Agent lze použít na vzdálených počítačích a v místním počítači. Když instalujete Visual Studio Test Agent, instalační proces zahrnuje krok konfigurace, spojující ovladač emulace sítě se síťovou kartou. Další informace najdete v tématu [instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).

    -   **Ovladač pro emulaci sítě nainstalovaný s Microsoft Visual Studio Test Professional:** při prvním použití emulace sítě, budete vyzváni k vytvoření vazby ovladač emulace sítě se síťovou kartou.

    > [!TIP]
    > Můžete také nainstalovat ovladač emulace sítě z příkazového řádku na místním počítači bez instalace testovacího agenta sady Visual Studio pomocí následujícího příkazu: **VSTestConfig NETWORKEMULATION/Install**

## <a name="see-also"></a>Viz také:

- [Shromažďování diagnostických údajů pomocí nastavení testů](../test/collect-diagnostic-information-using-test-settings.md)
- [Spouštění ručních testů (Azure testovací plány)](/azure/devops/test/run-manual-tests?view=vsts)