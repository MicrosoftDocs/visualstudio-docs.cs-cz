---
title: Kód Pythonu pro testování částí
description: Nastavení testování částí pro kód Pythonu v aplikaci Visual Studio plně využívá funkce Průzkumníka testů pro zjišťování, spouštění a ladění testů.
ms.date: 09/18/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: aec13b3b35c75ecaad938cd3200f3af2a87d2441
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920686"
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