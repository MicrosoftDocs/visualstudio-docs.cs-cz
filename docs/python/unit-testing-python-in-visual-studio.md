---
title: Testování částí kódu v Pythonu
description: Nastavení testování jednotek pro kód Python v sadě Visual Studio plně využívá funkce Průzkumníka testů, které chcete zjišťovat, spouštějte a laďte testy.
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
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254199"
---
# <a name="set-up-unit-testing-for-python-code"></a>Nastavení testování jednotek pro kód v Pythonu

Testování částí jsou části kódu, které testují jiné jednotky kódu v aplikaci, obvykle izolované funkce, třídy a tak dále. Když aplikace úspěšně projde všemi jeho testy jednotek, můžete alespoň důvěřovat správnost její nízké úrovně funkčnosti.

Testy jednotek Python často používá k ověření scénáře při návrhu programu. Podpora Pythonu v sadě Visual Studio obsahuje zjišťování, spouštění a ladění testů jednotek v rámci vašeho vývojového procesu, aniž by bylo potřeba spustit samostatně.

Tento článek poskytuje stručný přehled testování funkce v sadě Visual Studio pomocí Pythonu. Další informace o testování obecně najdete v tématu [testování částí kódu](../test/unit-test-your-code.md).

::: moniker range="vs-2017"

[!include[Testing Python code](includes/vs-2017/unit-testing-python.md)]

::: moniker-end

::: moniker range=">= vs-2019"

[!include[Testing Python code](includes/vs-2019/unit-testing-python.md)]

::: moniker-end