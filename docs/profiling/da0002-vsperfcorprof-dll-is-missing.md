---
title: 'DA0002: Chybí vsperfCorProf.dll | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0002
- vs.performance.2
- vs.performance.rules.DAVsPerfCorProfMissing
- vs.performance.rules.DA0002
ms.assetid: 76e614b3-ad7e-4b92-b7be-88dc1329be1d
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f768a35e7c50ec55867ae49901718063ca39bd0b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777748"
---
# <a name="da0002-vsperfcorprofdll-is-missing"></a>DA0002: Chybí knihovna VSPerfCorProf.dll

|||
|-|-|
|Id pravidla|DA0002 řekl:|
|Kategorie|Využití nástrojů profilování|
|Metody profilování|Profilování pomocí nástrojů příkazového řádku VSPerfCmd a VSPerfASPNETCmd|
|Zpráva|Zdá se, že soubor byl shromážděn bez řádného nastavení proměnných prostředí pomocí *VSPerfCLREnv.cmd*. Symboly pro spravované binární soubory se nemusí vyřešit.|
|Typ pravidla|Informace|

## <a name="cause"></a>Příčina
 Profiler nelze najít *VSPerfCorProf.dll* během profilování spustit. K tomuto upozornění dochází, když jsou nástroje příkazového řádku pro shromažďování dat profileru používány bez použití nástroje *VSPerfCLREnv.cmd* k inicializaci potřebných proměnných prostředí. Upozornění může také spustit, pokud je spuštěn jiný profiler při spuštění nástroje profilování.

## <a name="rule-description"></a>Popis pravidla
 Specifické proměnné prostředí musí být nastaveny před profilování spustit pro profiler přeložit symboly v binárních souborech rozhraní .NET Framework. Toto upozornění naznačuje, že nástroj *VSPerfCLREnv.cmd* nebyl spuštěn před shromažďováním dat profilování. Symboly pro spravované binární soubory se nemusí vyřešit. Další informace o použití nástrojů profilování z příkazového řádku naleznete v [tématu Profilování z příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md)

## <a name="how-to-fix-violations"></a>Jak opravit porušení
 Při profilování spravovaných aplikací pomocí nástrojů [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] příkazového řádku v nástrojích profilování spusťte nástroj příkazového řádku [VSPerfCLREnv](../profiling/vsperfclrenv.md) před zahájením shromažďování dat.
