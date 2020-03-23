---
title: 'DA0505: Průměrné soukromé bajty přidělené pro profilovaný proces | Dokumenty společnosti Microsoft'
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
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b905b0de69110f5f7cd684deb6fe6c5955bb4b0c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777400"
---
# <a name="da0505-average-private-bytes-allocated-for-the-process-being-profiled"></a>DA0505: Průměr Nesdílených bajtů přidělených pro profilovaný Proces

|||
|-|-|
|Id pravidla|DA0505|
|Kategorie|Správa prostředků|
|Metoda profilování|Všechny|
|Zpráva|Tyto informace byly shromážděny pouze pro informaci. Čítač Soukromé bajty procesu měří virtuální paměť přidělenou procesem, který profilujete. Vykázaná hodnota je průměr vypočítaný ve všech intervalech měření.|
|Typ pravidla|Informace|

 Při profilování pomocí vzorkování, .NET paměti nebo prostředků konfliktmetody, je nutné shromáždit alespoň 10 vzorků k aktivaci tohoto pravidla.

## <a name="rule-description"></a>Popis pravidla
 Tato zpráva hlásí průměrné množství virtuální paměti, které proces aktuálně přidělil v bajtů (soukromé bajty). Soukromé bajty představují umístění virtuální paměti, které byly přiděleny procesem, ke kterému lze přistupovat pouze podprocesy spuštěné uvnitř procesu.

 U 32bitových procesů spuštěných na 32bitovém počítači je horní limit soukromé části adresního prostoru procesu 2 GB. Pomocí přepínače [/3GB](https://support.microsoft.com/help/833721/available-switch-options-for-the-windows-xp-and-the-windows-server-200) Boot.ini mohou 32bitové procesy získat až 3 GB virtuální paměti. 32bitový proces spuštěný na 64bitovém počítači může získat až 4 GB privátní virtuální paměti.

 64bitový proces spuštěný na 64bitovém počítači může získat až 8 TB privátní virtuální paměti.

 Vykázaná hodnota je průměr za všechny intervaly měření, ve kterých byl profilovaný proces aktivní.

 Další informace o adresních prostorech procesu naleznete v [tématu Virtual Address Space](/windows/win32/memory/virtual-address-space) v dokumentaci ke správě paměti systému Windows.

## <a name="how-to-use-rule-data"></a>Použití dat pravidla
 Pomocí hlášené hodnoty můžete porovnat výkon různých verzí nebo sestavení programu nebo pochopit výkon aplikace v různých scénářích profilování.
