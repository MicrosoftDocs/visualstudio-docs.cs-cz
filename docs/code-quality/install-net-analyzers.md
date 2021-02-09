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
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: b41615e1826987cb42076ab3195fe7bfad235e7a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867890"
---
# <a name="enable-or-install-first-party-net-analyzers"></a>Povolit nebo nainstalovat analyzátory .NET First stran

## <a name="overview"></a>Přehled

Analyzátory platformy .NET Compiler Platform (Roslyn) kontrolují kód jazyka C# nebo Visual Basic z hlediska problémů s kvalitou a stylem kódu. Analyzátory .NET pro první stranu jsou **cílové platformy nezávislá**. To znamená, že váš projekt nemusí cílit na konkrétní platformu .NET. Analyzátory fungují pro projekty, které cílí `net5.0` i na starší verze rozhraní .NET, například `netcoreapp` , `netstandard` a `net472` .

Analyzátory .NET pro první stranu můžete povolit nebo nainstalovat jedním z následujících způsobů:

- **Povolení ze sady .NET SDK**: počínaje verzí Visual Studio 2019 16,8 a .NET 5,0 jsou tyto analyzátory [součástí sady .NET SDK](/dotnet/fundamentals/code-analysis/overview). Analýza je ve výchozím nastavení povolená pro projekty, které cílí na .NET 5,0 nebo novější. Můžete povolit analýzu kódu pro projekty, které cílí na starší verze rozhraní .NET, nastavením `EnableNETAnalyzers` vlastnosti na `true` . Můžete také zakázat analýzu kódu pro projekt nastavením `EnableNETAnalyzers` na `false` .

- **Instalovat jako balíček NuGet**: Pokud nechcete přejít na sadu .NET 5 + SDK, nebo pokud upřednostňujete model založený na balíčku NuGet, analyzátory jsou také k dispozici v `Microsoft.CodeAnalysis.NetAnalyzers` [balíčku NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers) v sadě Visual Studio 2019.  Můžete upřednostnit model založený na balíčku pro aktualizace verze na vyžádání. Pokud jste v aplikaci Visual Studio 2017, nainstalujte `2.9.x` místo toho nejnovější verzi `Microsoft.CodeAnalysis.FxCopAnalyzers` [balíčku NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) .

> [!NOTE]
> Doporučuje se povolit analyzátory ze sady .NET SDK namísto instalace `Microsoft.CodeAnalysis.NetAnalyzers` [balíčku NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers), pokud je to možné. Povolení analyzátorů ze sady .NET SDK zajistí, že automaticky získáte opravy chyb analyzátoru a nové analyzátory hned po aktualizaci sady SDK. V modelu NuGet je potřeba aktualizovat balíček NuGet pokaždé, když chcete mít nejnovější opravy chyb. Balíček NuGet se aktualizuje častěji.

## <a name="see-also"></a>Viz také

- [Přehled analyzátorů kódu v aplikaci Visual Studio](roslyn-analyzers-overview.md)
- [Použití analyzátorů kódu v aplikaci Visual Studio](use-roslyn-analyzers.md)
- [Migrace ze starší verze analýzy na analyzátory .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Migrace z analyzátorů FxCop na analyzátory .NET](migrate-from-fxcop-analyzers-to-net-analyzers.md)
