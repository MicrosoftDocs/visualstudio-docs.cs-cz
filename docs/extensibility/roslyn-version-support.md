---
title: Podporovaná mapování verzí balíčku Roslyn
description: V tomto článku se dozvíte, které verze balíčků platformy .NET Compiler (Roslyn) jsou podporované pro různé verze sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 04/29/2019
ms.topic: reference
helpviewer_keywords:
- roslyn package versions
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8fd9e62de70dd5bff81b5fdaee05822c7171981e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060507"
---
# <a name="net-compiler-platform-package-version-reference"></a>Reference k verzi balíčku platformy .NET Compiler

Následující tabulka uvádí, které verze [balíčků rozhraní .NET Compiler Platform (Roslyn)](https://www.nuget.org/packages/Microsoft.Net.Compilers/) jsou podporovány pro různé verze sady Visual Studio.

Jako příklad pro zajištění, že vlastní analyzátor funguje na všech verzích sady Visual Studio 2017, by měl cílit na verzi 2,0 rozhraní Microsoft.Net. compilers.

| Verze balíčku Roslyn | Minimální podporovaná verze sady Visual Studio |
| - | - |
| 3.x | Visual Studio 2019 |
| 2.10.0 | Visual Studio 2017 verze 15,9 |
| 2.9.0 | Visual Studio 2017 verze 15,8 |
| ve verzi 2.8.2 | Visual Studio 2017 verze 15.7 |
| 2.7.0 | Visual Studio 2017 verze 15.6 |
| 2.6.1 | Visual Studio 2017 verze 15.5 |
| 2.4.0 | Visual Studio 2017 verze 15.4 |
| 2.3.2 | Visual Studio 2017 verze 15.3 |
| 2.2.0 | Visual Studio 2017 verze 15.2 |
| 2.1.0 | Visual Studio 2017 verze 15.1 |
| 2.0.0 | Visual Studio 2017 RTM |
| 1.3.2 | Visual Studio 2015 Update 3 |
| 1.2.2 | Visual Studio 2015 Update 2 |
| 1.1.1 | Visual Studio 2015 Update 1 |
| 1.0.1 | Visual Studio 2015 RTM |

> [!TIP]
> V případě balíčků Roslyn, kde minimální podporovaná verze sady Visual Studio je verze sady Visual Studio 2017, jsou také podporovány všechny verze sady Visual Studio 2019, protože byly později dodány.

## <a name="see-also"></a>Viz také

- [Sada .NET Compiler Platform SDK](/dotnet/csharp/roslyn-sdk/)
- [Začínáme s analyzátory Roslyn](getting-started-with-roslyn-analyzers.md)
