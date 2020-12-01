---
title: Povolit nebo nainstalovat analyzátory .NET First stran
ms.date: 08/03/2018
description: Naučte se, jak povolit analyzátory .NET First stran ze sady .NET SDK nebo nainstalovat tyto analyzátory jako balíček NuGet.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- .NET analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 60eb4828d4c8450376178c2fdccf7d4c0f63d989
ms.sourcegitcommit: 208bd1edebfe6dec5d3bb92c63b5c1e093677e35
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/01/2020
ms.locfileid: "96440376"
---
# <a name="enable-or-install-first-party-net-analyzers"></a>Povolit nebo nainstalovat analyzátory .NET First stran

## <a name="overview"></a>Přehled

Analyzátory platformy .NET Compiler Platform (Roslyn) kontrolují kód jazyka C# nebo Visual Basic z hlediska problémů s kvalitou a stylem kódu. Analyzátory .NET pro první stranu můžete povolit nebo nainstalovat jedním z následujících způsobů:

- **Povolení ze sady .NET SDK**: počínaje verzí Visual Studio 2019 16,8 a .NET 5,0 jsou tyto analyzátory [součástí sady .NET SDK](/dotnet/fundamentals/code-analysis/overview). Analýza je ve výchozím nastavení povolená pro projekty, které cílí na .NET 5,0 nebo novější. Můžete povolit analýzu kódu pro projekty, které cílí na starší verze rozhraní .NET, nastavením `EnableNETAnalyzers` vlastnosti na `true` . Můžete také zakázat analýzu kódu pro projekt nastavením `EnableNETAnalyzers` na `false` .

- **Nainstalovat jako balíček NuGet**: případně můžete tyto analyzátory nainstalovat instalací `Microsoft.CodeAnalysis.NetAnalyzers` [balíčku NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers) do sady Visual Studio 2019. Pokud jste v aplikaci Visual Studio 2017, nainstalujte nejnovější `2.9.x` verzi `Microsoft.CodeAnalysis.FxCopAnalyzers` [balíčku NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/).

> [!NOTE]
> Doporučuje se povolit analyzátory ze sady .NET SDK namísto instalace `Microsoft.CodeAnalysis.NetAnalyzers` [balíčku NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers), pokud je to možné. Povolení analyzátorů ze sady .NET SDK zajistí, že automaticky získáte opravy chyb analyzátoru a nové analyzátory hned po aktualizaci sady SDK.

## <a name="see-also"></a>Viz také

- [Přehled analyzátorů kódu v aplikaci Visual Studio](roslyn-analyzers-overview.md)
- [Použití analyzátorů kódu v aplikaci Visual Studio](use-roslyn-analyzers.md)
- [Migrace ze starší verze analýzy na analyzátory .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Migrace z analyzátorů FxCop na analyzátory .NET](migrate-from-fxcop-analyzers-to-net-analyzers.md)
