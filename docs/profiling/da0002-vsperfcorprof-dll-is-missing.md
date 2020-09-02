---
title: DA0002-VSPerfCorProf.dll chybí | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 36c9f3b33eab8428cd14aa26896c3813422d3dd7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537069"
---
# <a name="da0002-vsperfcorprofdll-is-missing"></a>DA0002: Chybí knihovna VSPerfCorProf.dll

|Položka|Hodnota|
|-|-|
|ID pravidla|DA0002|
|Kategorie|Využití Nástroje pro profilaci|
|Metody profilace|Profilace pomocí nástrojů příkazového řádku VSPerfCmd a VSPerfASPNETCmd|
|Zpráva|Zdá se, že soubor byl shromážděn bez správného nastavení proměnných prostředí pomocí *VSPerfCLREnv. cmd*. Symboly pro spravované binární soubory se nemůžou přeložit.|
|Typ pravidla|Informace|

## <a name="cause"></a>Příčina
 Profiler nemohl během běhu profilace najít *VSPerfCorProf.dll* . K tomuto upozornění dochází, když se nástroje příkazového řádku pro kolekci dat profileru používají bez použití nástroje *VSPerfCLREnv. cmd* k inicializaci nezbytných proměnných prostředí. Upozornění může také vyvolat, zda je při spuštění Nástroje pro profilaci spuštěn jiný profiler.

## <a name="rule-description"></a>Popis pravidla
 Aby bylo možné v profileru vyřešit symboly v .NET Framework binárních souborech, je nutné nastavit konkrétní proměnné prostředí před spuštěním profilace. Toto upozornění naznačuje, že nástroj *VSPerfCLREnv. cmd* nebyl spuštěn před tím, než byly shromážděna data profilování. Symboly pro spravované binární soubory se nemusí přeložit. Další informace o použití Nástroje pro profilaci z příkazového řádku najdete v tématu [profilace z příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md) .

## <a name="how-to-fix-violations"></a>Jak opravit porušení
 Při profilování spravovaných aplikací pomocí nástrojů příkazového řádku v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci spusťte nástroj příkazového řádku [VSPerfCLREnv](../profiling/vsperfclrenv.md) před zahájením shromažďování dat.
