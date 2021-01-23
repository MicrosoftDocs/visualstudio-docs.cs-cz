---
title: Co je nového v profilování v aplikaci Visual Studio 2017 | Microsoft Docs
description: Přečtěte si, že diagnostické nástroje obsahují nové vizualizace, které vám pomůžou identifikovat problémy v aplikaci, které potřebují opravit.
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
ms.openlocfilehash: 57ccf59de6ce5d18aab0a461cff91875cc74486d
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2021
ms.locfileid: "98723098"
---
# <a name="whats-new-in-profiling-tools-in-includevs_dev15"></a>Co je nového v nástrojích pro profilaci v nástroji [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

Diagnostické nástroje obsahují nové vizualizace, které vám pomůžou identifikovat problémy ve vaší aplikaci, které potřebují opravit. Diagnostické nástroje teď zahrnují podporu pro aplikace ASP.NET.

Další informace najdete v [poznámkách k verzi [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] pro ](/visualstudio/releasenotes/vs2017-relnotes).

Do nástrojů se přidala karta **Souhrn** , která vám pomůže soustředit se na klíčové oblasti pro analýzu výkonu. Tato karta zobrazuje, kolik událostí se objevilo, umožňuje pořizovat snímky haldy a umožňuje rychle Povolit shromažďování dat o využití procesoru. Toto zobrazení ukazuje všechny události [Application Insights](/azure/azure-monitor/app/visual-studio) nebo [Analýza uživatelského rozhraní](/visualstudio/releasenotes/vs2017-relnotes) . Kromě toho pro Visual Studio Enterprise toto zobrazení také zobrazuje události IntelliTrace.

![Karta souhrn nástrojů pro diagnostiku](../profiling/media/diag-tools-summary-tab-2.png "DiagToolsSummaryTab")

Nástroj využití CPU má [nové vizualizace](../profiling/Beginners-Guide-to-Performance-Profiling.md) , které vám pomůžou identifikovat funkce, které nejpravděpodobněji způsobují problémy s výkonem. Nové zobrazení **volající/volaný** umožňuje prozkoumat náklady na volání funkcí a z vybrané funkce.

![Zobrazení volajícího volaných nástrojů pro diagnostiku](../profiling/media/diag-tools-caller-callee-2.png "DiagToolsCallerCallee")

## <a name="see-also"></a>Viz také

- [Profil v aplikaci Visual Studio](../profiling/index.yml)
- [První seznámení s nástroji pro profilaci](../profiling/profiling-feature-tour.md)