---
title: Zakázat analýzu starších kódů
ms.date: 10/04/2019
description: Naučte se, jak zapnout a vypnout analýzu binárního kódu v aplikaci Visual Studio. Viz jak nakonfigurovat tuto funkci v projektech spravovaného kódu.
ms.custom: SEO-VS-2020
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: c10aa602c2c9af3c51812073d62d5bd9bff06664
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860071"
---
# <a name="how-to-enable-and-disable-binary-code-analysis-for-managed-code"></a>Postupy: povolení a zákaz analýzy binárního kódu pro spravovaný kód

Můžete nakonfigurovat starší verzi analýzy kódu (binární analýzu), která se spustí po každém sestavení spravovaného kódu projektu. Pro každou konfiguraci sestavení můžete mít také různá nastavení, například ladění a vydání.

> [!NOTE]
> Starší verze analýzy není k dispozici pro novější typy projektů, jako jsou například .NET Core a aplikace .NET Standard. Tyto projekty používají [analyzátory kódu založené na .NET Compiler Platform](roslyn-analyzers-overview.md) k analýze kódu, a to v reálném čase i v době sestavování. Informace o zakázání analýzy zdrojového kódu v těchto projektech naleznete v tématu [Jak zakázat analýzu zdrojového kódu](disable-code-analysis.md).

Povolení nebo zakázání analýzy starších verzí kódu:

1. V **Průzkumník řešení** vyberte a podržte (nebo klikněte pravým tlačítkem myši) na projekt a pak vyberte **vlastnosti**.

2. V dialogovém okně Vlastnosti projektu, přejít na kartu **Analýza kódu** .

3. Zadejte typ sestavení v **konfiguraci** a cílovou platformu na **platformě**. (Jenom projekty Non-.NET Core/. NET Standard)

::: moniker range="vs-2017"

4. Chcete-li povolit nebo zakázat automatickou analýzu kódu, zaškrtněte nebo zrušte zaškrtnutí políčka **Povolit analýzu kódu při sestavení** .

::: moniker-end

::: moniker range=">=vs-2019"

4. Chcete-li povolit nebo zakázat automatickou analýzu kódu, zaškrtněte nebo zrušte zaškrtnutí políčka **Spustit při sestavení** v části **binární analyzátory** .

   ![Spuštění analýzy binárního kódu pro možnost sestavení v aplikaci Visual Studio](media/run-on-build-binary-analyzers.png)

::: moniker-end

> [!NOTE]
> Zakázání analýzy binárního kódu při sestavení neovlivní [.NET Compiler Platform analyzátory kódu založené na](roslyn-analyzers-overview.md), které jsou vždy spouštěny v sestavení, pokud jste je nainstalovali jako balíček NuGet. Informace o zakázání analýzy z těchto analyzátorů naleznete v tématu [Jak zakázat analýzu zdrojového kódu](disable-code-analysis.md).
