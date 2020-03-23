---
title: 'DA0506: Maximální počet soukromých bajtů přidělených pro profilovaný proces | Dokumenty společnosti Microsoft'
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779308"
---
# <a name="da0506-maximum-private-bytes-allocated-for-the-process-being-profiled"></a>DA0506: Maximum Nesdílených bajtů přidělených pro profilovaný Proces

|||
|-|-|
|Id pravidla|DA0506|
|Kategorie|Monitorování zdrojů|
|Metoda profilování|Všechny|
|Zpráva|Tyto informace byly shromážděny pouze pro informaci. Čítač Soukromé bajty procesu měří virtuální paměť přidělenou procesem, který profilujete. Uvedená hodnota je maximální pozorovaná ve všech intervalech měření.|
|Typ pravidla|Informace|

 Při profilování pomocí vzorkování, .NET paměti nebo prostředků konfliktmetody, je nutné shromáždit alespoň 10 vzorků k aktivaci tohoto pravidla.

## <a name="rule-description"></a>Popis pravidla
 Tato zpráva hlásí maximální množství virtuální paměti, které proces aktuálně přidělil v bajtů (soukromé bajty). Soukromé bajty představují umístění virtuální paměti, které byly přiděleny procesem, ke kterému lze přistupovat pouze podprocesy spuštěné uvnitř procesu.

 U 32bitových procesů spuštěných na 32bitovém počítači je horní limit soukromé části adresního prostoru procesu 2 GB. Pomocí přepínače [/3 GB](https://support.microsoft.com/help/833721/available-switch-options-for-the-windows-xp-and-the-windows-server-200) Boot.ini mohou 32bitové procesy získat až 3 GB virtuální paměti. 32bitový proces spuštěný na 64bitovém počítači může získat až 4 GB privátní virtuální paměti.

 64bitový proces spuštěný na 64bitovém počítači může získat až 8 TB privátní virtuální paměti.

 Vykázaná hodnota je maximální hodnota za všechny intervaly měření, ve kterých byl profilovaný proces aktivní.

 Další informace o adresních prostorech procesu naleznete v [tématu Virtual Address Space](/windows/win32/memory/virtual-address-space) v dokumentaci ke správě paměti systému Windows.

## <a name="how-to-use-rule-data"></a>Použití dat pravidla
 Pomocí hlášené hodnoty můžete porovnat výkon různých verzí nebo sestavení programu nebo pochopit výkon aplikace v různých scénářích profilování.

 Maximální hodnota soukromých bajtů procesu, která se blíží architektonickému limitu, jak velký může zvětšit adresní prostor procesu, může vést k výjimkám nedostatku paměti. Další informace naleznete v [tématu Zkoumání problémů s pamětí](https://msdn.microsoft.com/magazine/cc163528.aspx) v časopise MSDN.
