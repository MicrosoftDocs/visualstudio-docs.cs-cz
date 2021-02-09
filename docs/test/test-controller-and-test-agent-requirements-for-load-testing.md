---
title: Testovací kontrolér/požadavky testovacího agenta (zátěžové testování)
description: Přečtěte si o požadavcích testovacího kontroleru a testovacího agenta pro zátěžové testování. Visual Studio podporuje několik typů testů.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- agents, requirements
- controllers, requirements
ms.assetid: 372d97ce-12e4-46a9-9863-da508adba68f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: a123a147d038a41f799c2fdf9d4fb26eaa4f3490
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894488"
---
# <a name="test-controller-and-test-agent-requirements-for-load-testing"></a>Testovací kontrolér a požadavky testovacího agenta pro zátěžové testování

Do sady Visual Studio je integrováno několik typů testů, včetně jednotek, webového výkonu, zátěže a manuálních testů. Visual Studio umožňuje uživatelům správy životního cyklu aplikací sady Visual Studio spouštět testy na vzdálených počítačích pomocí testovacího kontroléru a jednoho nebo více agentů. Viz [instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="hardware-and-software-requirements"></a>Požadavky na hardware a software

Testovací kontrolér i počítače testovacího agenta mají specifické požadavky na hardware a software. Kromě toho, pokud chcete nasadit testovací kontrolér a počítače testovacího agenta v několika jazycích, je nutné naplánovat, jak tyto jazyky podporují.

### <a name="hardware-requirements"></a>Požadavky na hardware

V následující tabulce jsou uvedeny doporučené hardwarové požadavky pro nasazení testovacího kontroleru a testovacích agentů.

|**Konfigurace**|**Komponenta**|**Procesor**|**REŽIM**|**Memory (Paměť)**|
|-|-------------------|-|------------|-|
|Virtuální uživatelé < 500|Testovací agent|2,6 GHz|10 GB|2 GB|
|Virtuální uživatelé < 1000|Testovací agent|Dvoujádrový procesor 2,6 GHz|10 GB|2 GB|
|Virtuální uživatelé N x 1000|Testovací agent|Horizontální navýšení kapacity na N agentů s duální 2,6 GHz|OVLADAČ|GB|
|\< 30 počítačů v testovacím prostředí. To zahrnuje agenty a testované servery.|Test Controller|2,6 GHz|||
|N x 30 počítačů v testovacím prostředí. To zahrnuje agenty a testované servery.|Test Controller|Procesory N 2,6 GHz|||

> [!NOTE]
> Počet virtuálních uživatelů se bude výrazně lišit od testu až po otestování. Klíčovou příčinou této odchylky je odchylka v *časech pomýšlení* nebo zpoždění uživatele. Další informace najdete v tématu [úpravy časů pomýšlení pro simulaci zpoždění lidské interakce webu](../test/edit-think-times-in-load-test-scenarios.md). V zátěžovém testu jsou webové testy obecně efektivnější a generují větší zátěž než testování částí. Čísla v předchozí tabulce jsou platná pro spouštění webových testů s 3-5 sekundami v typické webové aplikaci.

Zde uvedené pokyny jsou k dispozici jako obecné pokyny k plánování hardwaru. Výkon testu se výrazně liší v závislosti na množství testovacích dat a počtu testovacích agentů. V případě testovacích agentů je dostupná rychlost procesoru a paměť, aby se zátěž testu omezila. Řadiče testů potřebují větší prostředky v závislosti na počtu testovacích agentů a množství dat zapojených do testů.

Server se spuštěnou sadou Visual Studio by měl mít spolehlivé síťové připojení s minimální šířkou pásma 1 MB/s a maximální latencí 350ms. Mezi testovacími agenty a testovacím kontrolérem nesmí být žádná brána firewall. Pokud váš testovací výkon nesplňuje vaše očekávání, zvažte upgrade konfigurace hardwaru.

### <a name="additional-hardware-considerations"></a>Další požadavky na hardware

Testovací agenti generují velké množství dat na řadičích testů v závislosti na době trvání testu a velikosti testu. Obecně platí, že byste měli naplánovat dalších 10 GB úložiště pevného disku pro každých 24 hodin testovacích dat.

Kromě doporučeného hardwaru byste měli zvážit další hardware pro důležité servery, jako jsou redundantní zdroje napájení a redundantní ventilátory.

### <a name="language-requirements"></a>Jazykové požadavky

Aby nedocházelo k nejasnostem a zjednodušili operace, je třeba nakonfigurovat testovací kontrolér a testovací agenty tak, aby používaly stejný jazyk jako operační systém počítače a Team Foundation Server. Pokud je testovací agent a kontroler testů nainstalován v různých počítačích, musí být nakonfigurovány tak, aby používaly stejný jazyk. Můžete však nainstalovat jinou jazykovou verzi sady Visual Studio do operačního systému anglické jazykové verze, pokud tento jazyk odpovídá Team Foundation Server nasazení.

## <a name="monitor-agent-resources"></a>Monitorování prostředků agenta

Můžete monitorovat počítače agenta a určit jejich potřeby prostředků tím, že budou sledovat procesy *QTAgent \* . exe* , které se během testů spouštějí a mění. Nejběžnějším kritickým bodem pro procesy *QTAgent \* . exe* je využití procesoru. Pokud je využití procesoru konzistentně ve velkém nineties, pak je známkou toho, že se agent načítá silně. Dalším běžným kritickým bodem je využití paměti. V případě náročných testů vám monitorování těchto prostředků pomůže určit, jestli byste měli zvýšit nároky na prostředky počítače nebo distribuovat testy jinak.

## <a name="see-also"></a>Viz také

- [Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md)
