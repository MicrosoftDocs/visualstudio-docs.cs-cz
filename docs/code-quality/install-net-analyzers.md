---
title: Povolit nebo nainstalovat analyzátory .NET
ms.date: 08/03/2018
description: Naučte se, jak povolit analyzátory .NET ze sady .NET SDK nebo nainstalovat tyto analyzátory jako balíček NuGet.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- .NET analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a14d89caba498a07c2447f9df1109e4da9f6a466
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/25/2020
ms.locfileid: "96112221"
---
# <a name="enable-or-install-net-analyzers"></a>Povolit nebo nainstalovat analyzátory .NET

## <a name="overview"></a>Přehled

Analyzátory platformy .NET Compiler Platform (Roslyn) kontrolují kód jazyka C# nebo Visual Basic z hlediska problémů s kvalitou a stylem kódu. Tyto analyzátory můžete povolit nebo nainstalovat jedním z následujících způsobů:

- **Povolení ze sady .NET SDK**: počínaje verzí Visual Studio 2019 16,8 a .NET 5,0 jsou tyto analyzátory [součástí sady .NET SDK](/dotnet/fundamentals/code-analysis/overview). Analýza je ve výchozím nastavení povolená pro projekty, které cílí na .NET 5,0 nebo novější. Můžete povolit analýzu kódu pro projekty, které cílí na starší verze rozhraní .NET, nastavením `EnableNETAnalyzers` vlastnosti na `true` . Můžete také zakázat analýzu kódu pro projekt nastavením `EnableNETAnalyzers` na `false` .

- **Nainstalovat jako balíček NuGet**: případně můžete tyto analyzátory nainstalovat instalací `Microsoft.CodeAnalysis.NetAnalyzers` [balíčku NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers) do sady Visual Studio 2019. Pokud jste v aplikaci Visual Studio 2017, nainstalujte nejnovější `2.9.x` verzi `Microsoft.CodeAnalysis.FxCopAnalyzers` [balíčku NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/).

> [!NOTE]
> Doporučuje se povolit analyzátory ze sady .NET SDK namísto instalace `Microsoft.CodeAnalysis.NetAnalyzers` [balíčku NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers), pokud je to možné. Povolení analyzátorů ze sady .NET SDK zajistí, že automaticky získáte opravy chyb analyzátoru a nové analyzátory hned po aktualizaci sady SDK.

## <a name="see-also"></a>Viz také

- [Přehled analyzátorů kódu v aplikaci Visual Studio](roslyn-analyzers-overview.md)
- [Použití analyzátorů kódu v aplikaci Visual Studio](use-roslyn-analyzers.md)
- [Migrace ze starší verze z analýzy do analyzátorů .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Migrace z analyzátorů FxCop do analyzátorů .NET](migrate-from-fxcop-analyzers-to-net-analyzers.md)
