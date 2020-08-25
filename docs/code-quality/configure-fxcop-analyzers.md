---
title: Konfigurace analyzátorů kvality kódu .NET pomocí editorconfig
ms.date: 09/23/2019
ms.topic: conceptual
helpviewer_keywords:
- .NET analyzers
- FxCop analyzers, configuring
- code quality
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a131b7d69eec61f9b9106f7a4274b3882c51f0ff
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88800733"
---
# <a name="configure-net-code-quality-analyzers"></a>Konfigurace analyzátorů kvality kódu .NET

Pro určité analyzátory kvality kódu .NET (které mají začínající identifikátory `CA` ) můžete upřesnit, které části základu kódu by měly být aplikovány na [Konfigurovatelné možnosti](fxcop-analyzer-options.md). Každá možnost je určena přidáním páru klíč-hodnota k souboru [EditorConfig](https://editorconfig.org) . Konfigurační soubor může být specifický pro soubor, projekt, řešení nebo celé úložiště.

> [!TIP]
> Přidejte soubor. editorconfig do projektu kliknutím pravým tlačítkem myši na projekt v **Průzkumník řešení** a výběrem možnosti **Přidat**  >  **novou položku**. V okně **Přidat novou položku** do vyhledávacího pole zadejte **editorconfig** . Vyberte šablonu **soubor editorconfig (výchozí)** a zvolte **Přidat**.
>
> ![Přidat soubor editorconfig do projektu v aplikaci Visual Studio](media/add-editorconfig-file.png)

::: moniker range=">=vs-2019"

Informace o konfiguraci závažnosti pravidla (například o tom, jestli se jedná o chybu nebo upozornění) najdete v tématu [nastavení závažnosti pravidla v souboru EditorConfig](use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file). Případně můžete vybrat jeden z předdefinovaných [EditorConfig souborů nebo sad pravidel](analyzer-rule-sets.md) a rychle povolit nebo zakázat kategorii pravidel.

::: moniker-end

Zbývající část tohoto článku popisuje obecnou syntaxi pro [Možnosti, které upřesňují](fxcop-analyzer-options.md) , kde se používají analyzátory kvality kódu .NET.

## <a name="option-scopes"></a>Obory možností

Každou možnost zpřesnění lze nakonfigurovat pro všechna pravidla, pro kategorii pravidel (například pro pojmenování nebo návrh) nebo pro konkrétní pravidlo.

### <a name="all-rules"></a>Všechna pravidla

Syntaxe pro konfiguraci možnosti pro *všechna* pravidla je následující:

|Syntax|Příklad|
|-|-|
| dotnet_code_quality. Parametr Option = OptionValue | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>Kategorie pravidel

Syntaxe pro konfiguraci možnosti pro *kategorii* pravidel (například pojmenování, návrh nebo výkon) je následující:

|Syntax|Příklad|
|-|-|
| dotnet_code_quality. RuleCategory. Option = OptionValue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>Konkrétní pravidlo

Syntaxe pro konfiguraci možnosti pro *konkrétní* pravidlo je následující:

|Syntax|Příklad|
|-|-|
| dotnet_code_quality. RuleId. Option = OptionValue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="enabling-editorconfig-based-configuration"></a>Povolení konfigurace založené na Editorconfig

Pro následující rozsahy je možné povolit konfiguraci analyzátoru založené na EditorConfig:

- Konkrétní dokument (y)
- Konkrétní složky
- Konkrétní projekt (y)
- Konkrétní řešení
- Celé úložiště

Chcete-li povolit konfiguraci, přidejte soubor *. editorconfig* s možnostmi v příslušném adresáři. Tento soubor může také obsahovat konfigurační položky konfigurace diagnostiky založené na EditorConfig. Další podrobnosti najdete [tady](use-roslyn-analyzers.md#rule-severity).

## <a name="see-also"></a>Viz také

- [Možnosti oboru pravidla pro analyzátory kvality kódu .NET](fxcop-analyzer-options.md)
- [Konfigurace analyzátoru](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [Konvence kódování .NET pro EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
