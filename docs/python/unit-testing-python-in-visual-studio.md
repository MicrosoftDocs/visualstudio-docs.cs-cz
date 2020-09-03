---
title: Kód Pythonu pro testování částí
description: Nastavení testování částí pro kód Pythonu v aplikaci Visual Studio plně využívá funkce Průzkumníka testů pro zjišťování, spouštění a ladění testů.
ms.date: 09/18/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 2a621cd56f980c8a1404ba8855cdf3544e58d39d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535320"
---
# <a name="set-up-unit-testing-for-python-code"></a>Nastavení testování částí kódu Pythonu

Testy jednotek jsou části kódu, které testují jiné jednotky kódu v aplikaci, obvykle izolované funkce, třídy a tak dále. Když aplikace projde všemi testy jednotek, můžete alespoň důvěřovat, že její funkce na nízké úrovni je správná.

Python často používá testy jednotek k ověření scénářů při navrhování programu. Podpora Pythonu v sadě Visual Studio zahrnuje zjišťování, spouštění a ladění testů jednotek v rámci kontextu procesu vývoje, aniž by bylo nutné spouštět testy samostatně.

Tento článek poskytuje stručný přehled možností testování částí v aplikaci Visual Studio pomocí Pythonu. Další informace o testování částí obecně najdete v tématu [testování částí kódu](../test/unit-test-your-code.md).

::: moniker range="vs-2017"

[!include[Testing Python code](includes/vs-2017/unit-testing-python.md)]

::: moniker-end

::: moniker range=">= vs-2019"

[!include[Testing Python code](includes/vs-2019/unit-testing-python.md)]

::: moniker-end