---
title: Co je nového v profilování v aplikaci Visual Studio 2017 | Microsoft Docs
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling
- what's new
ms.assetid: d4736cc8-8961-4089-be9e-d5190ce8353c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 0512c6e95f0a26184593f7af5ba08c31c33a3299
ms.sourcegitcommit: 53bc4c11b82882ab658e34c65ae374060f823531
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71128343"
---
# <a name="whats-new-in-profiling-tools-in-includevs_dev15miscincludesvs_dev15_mdmd"></a>Co je nového v nástrojích pro profilaci v nástroji[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

Diagnostické nástroje obsahují nové vizualizace, které vám pomůžou identifikovat problémy ve vaší aplikaci, které potřebují opravit. Diagnostické nástroje teď zahrnují podporu pro aplikace ASP.NET.

Další informace najdete v [poznámkách k verzi [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]pro ](/visualstudio/releasenotes/vs2017-relnotes).

Do nástrojů se přidala karta **Souhrn** , která vám pomůže soustředit se na klíčové oblasti pro analýzu výkonu. Tato karta zobrazuje, kolik událostí se objevilo, umožňuje pořizovat snímky haldy a umožňuje rychle Povolit shromažďování dat o využití procesoru. Toto zobrazení ukazuje všechny události [Application Insights](/azure/azure-monitor/app/visual-studio) nebo [Analýza uživatelského rozhraní](/visualstudio/releasenotes/vs2017-relnotes) . Kromě toho pro Visual Studio Enterprise toto zobrazení také zobrazuje události IntelliTrace.

![Karta souhrn nástrojů pro diagnostiku](../profiling/media/diag-tools-summary-tab-2.png "DiagToolsSummaryTab")

Nástroj využití CPU má [nové vizualizace](../profiling/Beginners-Guide-to-Performance-Profiling.md) , které vám pomůžou identifikovat funkce, které nejpravděpodobněji způsobují problémy s výkonem. Nové zobrazení **volající/volaný** umožňuje prozkoumat náklady na volání funkcí a z vybrané funkce.

![Zobrazení volajícího volaných nástrojů pro diagnostiku](../profiling/media/diag-tools-caller-callee-2.png "DiagToolsCallerCallee")

## <a name="see-also"></a>Viz také:

- [Profil v aplikaci Visual Studio](../profiling/index.yml)
- [Nejdřív se podívejte na nástroje pro profilaci](../profiling/profiling-feature-tour.md)