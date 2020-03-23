---
title: Kód Pythonu testu částí
description: Nastavení testování částí pro kód Pythonu v sadě Visual Studio plně využívá funkce Průzkumníka testů ke zjišťování, spouštění a ladění testů.
ms.date: 09/18/2019
ms.topic: include
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 09c67ace9db36cb8ee3d94296d339b62849e3c94
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "71254199"
---
# <a name="set-up-unit-testing-for-python-code"></a>Nastavení testování částí pro kód Pythonu

Testy částí jsou části kódu, které testují jiné jednotky kódu v aplikaci, obvykle izolované funkce, třídy a tak dále. Když aplikace projde všechny své testy částí, můžete alespoň důvěřovat, že její funkce nižší úrovně je správná.

Python používá testování částí značně k ověření scénářů při navrhování programu. Podpora Pythonu v sadě Visual Studio zahrnuje zjišťování, provádění a ladění testů částí v rámci procesu vývoje, aniž byste museli spouštět testy samostatně.

Tento článek obsahuje stručný přehled možností testování částí v sadě Visual Studio s Pythonem. Další informace o testování částí obecně naleznete v [tématu Testování částí kódu](../test/unit-test-your-code.md).

::: moniker range="vs-2017"

[!include[Testing Python code](includes/vs-2017/unit-testing-python.md)]

::: moniker-end

::: moniker range=">= vs-2019"

[!include[Testing Python code](includes/vs-2019/unit-testing-python.md)]

::: moniker-end