---
title: 'DA0505: průměrné soukromé bajty přidělené pro proces, který je profilované | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0505
- vs.performance.rules.DA0505
- vs.performance.505
ms.assetid: 32c612ea-d077-44ba-8e6f-3a96333bad00
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cff41d3ff03efd70eb876531a2d7b8602d3f8796
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2019
ms.locfileid: "72910161"
---
# <a name="da0505-average-private-bytes-allocated-for-the-process-being-profiled"></a>DA0505: Průměr Nesdílených bajtů přidělených pro profilovaný Proces

|||
|-|-|
|ID pravidla|DA0505|
|Kategorie|Správa prostředků|
|Metoda profilace|Všechny|
|Zpráva|Tyto informace se shromáždily jenom pro informace. Čítač procesu soukromých bajtů měří virtuální paměť přidělenou procesem, který vytváříte profilování. Hodnota hlášené je průměr vypočítaný ve všech intervalech měření.|
|Typ pravidla|Informace o|

 Když použijete profilování pomocí vzorkování, paměti .NET nebo způsobů kolizí prostředků, musíte pro aktivaci tohoto pravidla shromáždit aspoň 10 vzorků.

## <a name="rule-description"></a>Popis pravidla
 Tato zpráva oznamuje průměrnou velikost virtuální paměti, kterou proces aktuálně přidělil v bajtech (nesdílené bajty). Soukromé bajty představují umístění virtuální paměti, která byla přidělena procesu, ke kterému lze přistupovat pouze v vláknech spuštěných uvnitř procesu.

 Pro 32 procesy běžící na 32 počítači je horní limit soukromé části adresního prostoru procesu 2 GB. Pomocí přepínače [/3Gb](https://support.microsoft.com/help/833721/available-switch-options-for-the-windows-xp-and-the-windows-server-200) Boot. ini můžou 32 procesy získat až 3 GB virtuální paměti. 32 proces, který běží na 64 počítači, může získat až 4 GB privátní virtuální paměti.

 64 proces, který běží na 64 počítači, může získat až 8 TB privátní virtuální paměti.

 Hodnota hlášené je průměrem ve všech intervalech měření, ve kterých je proces profilace aktivní.

 Další informace o adresních prostorech procesu najdete v tématu [virtuální adresní prostor](/windows/win32/memory/virtual-address-space) v dokumentaci ke službě Správa paměti systému Windows.

## <a name="how-to-use-rule-data"></a>Jak používat data pravidla
 Pomocí hlášené hodnoty můžete porovnávat výkon různých verzí nebo sestavení programu nebo porozumět výkonu aplikace v rámci různých scénářů profilace.