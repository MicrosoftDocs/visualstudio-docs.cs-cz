---
title: 'DA0506: maximální počet privátních bajtů přidělených procesu pro profilování | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DA0506
- vs.performance.DA0506
- vs.performance.506
ms.assetid: e9c43554-9a85-4d98-9fa4-3b19986e7b62
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7600e65beb3035fac6d5ea58b25f6965d681f83a
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779308"
---
# <a name="da0506-maximum-private-bytes-allocated-for-the-process-being-profiled"></a>DA0506: Maximum Nesdílených bajtů přidělených pro profilovaný Proces

|||
|-|-|
|Id pravidla|DA0506|
|Kategorie|Monitorování prostředků|
|Metoda profilace|Vše|
|Zpráva|Tyto informace se shromáždily jenom pro informace. Čítač procesu soukromých bajtů měří virtuální paměť přidělenou procesem, který vytváříte profilování. Hodnota hlášené je maximální pozorována ve všech intervalech měření.|
|Typ pravidla|Informace o nástroji|

 Když použijete profilování pomocí vzorkování, paměti .NET nebo způsobů kolizí prostředků, musíte pro aktivaci tohoto pravidla shromáždit aspoň 10 vzorků.

## <a name="rule-description"></a>Popis pravidla
 Tato zpráva oznamuje maximální velikost virtuální paměti, kterou proces aktuálně přidělil v bajtech (nesdílené bajty). Soukromé bajty představují umístění virtuální paměti, která byla přidělena procesu, ke kterému lze přistupovat pouze v vláknech spuštěných uvnitř procesu.

 Pro 32 procesy běžící na 32 počítači je horní limit soukromé části adresního prostoru procesu 2 GB. Pomocí přepínače Boot. ini [/3 GB](https://support.microsoft.com/help/833721/available-switch-options-for-the-windows-xp-and-the-windows-server-200) mohou 32 procesy získat až 3 GB virtuální paměti. 32 proces, který běží na 64 počítači, může získat až 4 GB privátní virtuální paměti.

 64 proces, který běží na 64 počítači, může získat až 8 TB privátní virtuální paměti.

 Nahlášená hodnota je maximální hodnota ve všech intervalech měření, ve kterých je proces profilace aktivní.

 Další informace o adresních prostorech procesu najdete v tématu [virtuální adresní prostor](/windows/win32/memory/virtual-address-space) v dokumentaci ke službě Správa paměti systému Windows.

## <a name="how-to-use-rule-data"></a>Jak používat data pravidla
 Pomocí hlášené hodnoty můžete porovnávat výkon různých verzí nebo sestavení programu nebo porozumět výkonu aplikace v rámci různých scénářů profilace.

 Maximální hodnota nesdílených bajtů procesu, která se blíží omezení architektury, jak velký adresní prostor procesu může růst, může způsobit výjimky z paměti. Další informace najdete v tématu [zkoumání problémů s pamětí](https://msdn.microsoft.com/magazine/cc163528.aspx) na webu MSDN Magazine.
