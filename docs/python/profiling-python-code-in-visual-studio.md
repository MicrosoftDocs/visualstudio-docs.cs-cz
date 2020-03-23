---
title: Měření výkonu kódu Pythonu
description: Pomocí profileru Visual Studio zkontrolujte výkon kódu Pythonu při použití překladačů založených na Jazyce CPython.
ms.date: 11/12/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: e31286a9b0ea3852ad1fe788d4ff6c4c66e7e4f0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62784264"
---
# <a name="profile-python-code"></a>Profil ový kód Pythonu

Můžete profilovat aplikaci Pythonu při použití interpretů založených na CPython. (Viz [Matice funkcí – profilování](overview-of-python-tools-for-visual-studio.md#matrix-profiling) dostupnosti této funkce pro různé verze sady Visual Studio.)

## <a name="profiling-for-cpython-based-interpreters"></a>Profilování pro překladače založené na CPython

Profilování se spustí pomocí příkazu **Analyzovat** > **spuštění profilování pythonu,** který otevře dialogové okno konfigurace:

![Dialogové okno Konfigurace profilování](media/profiling-start.png)

Když vyberete **OK**, spustí se profiler a otevře sestavu výkonu, pomocí které můžete prozkoumat, jak je čas strávený v aplikaci:

![Sestava výkonu profilování](media/profiling-results.png)

> [!Note]
> V současné době Visual Studio podporuje pouze tuto úroveň profilování plné aplikace, ale určitě chceme slyšet váš názor na budoucí možnosti. Tlačítko **Zpětná vazba produktu** v dolní části této stránky použijte.

## <a name="profiling-for-ironpython"></a>Profilování pro IronPython

Protože IronPython není interpret založený na CPython, výše uvedené funkce profilování nefunguje.

Místo toho použijte visual studio .NET profiler spuštěním *ipy.exe* přímo jako cílová aplikace, pomocí příslušných argumentů ke spuštění spouštěcího skriptu. Zahrnout `-X:Debug` na příkazovém řádku, abyste zajistili, že veškerý kód Pythonu lze ladit a profilovat. Tento argument generuje zprávu o výkonu včetně času stráveného v modulu runtime IronPython a váš kód. Váš kód je identifikován pomocí poškamotných názvů.

Alternativně IronPython má některé vlastní vestavěné profilování, ale v současné době neexistuje žádný dobrý vizualizér pro něj. Přečtěte si, co je k dispozici, najdete v [tématu IronPython Profiler](https://blogs.msdn.microsoft.com/curth/2009/03/30/an-ironpython-profiler/) (Blogy MSDN).
