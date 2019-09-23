---
title: Konfigurace analyzátorů FxCop pomocí editorconfig
ms.date: 09/23/2019
ms.topic: conceptual
helpviewer_keywords:
- FxCop analyzers, configuring
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 7619b040343720198e190f551741f565e62fa145
ms.sourcegitcommit: 88f576ac32af31613c1a10c1548275e1ce029f4f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71186395"
---
# <a name="configure-fxcop-analyzers"></a>Konfigurace analyzátorů FxCop

[Balíček analyzátorů FxCop](install-fxcop-analyzers.md) se skládá z nejdůležitějších pravidel "FxCop" z analyzátoru starších verzí převedených na analyzátory kódu založené na .NET Compiler Platform. U určitých pravidel FxCop můžete upřesnit, které části základu kódu by měly být aplikovány na [Konfigurovatelné možnosti](fxcop-analyzer-options.md). Každá možnost je určena přidáním páru klíč-hodnota k souboru [EditorConfig](https://editorconfig.org) . Konfigurační soubor může být [specifický pro projekt](#per-project-configuration) nebo může být [sdílen](#shared-configuration) mezi dvěma nebo více projekty.

> [!TIP]
> Do projektu můžete přidat soubor. editorconfig tak, že kliknete pravým tlačítkem na projekt v **Průzkumník řešení** a vyberete **Přidat** > **novou položku**. V okně **Přidat novou položku** do vyhledávacího pole zadejte **editorconfig** . Vyberte šablonu **soubor editorconfig (výchozí)** a zvolte **Přidat**.
>
> ![Přidat soubor editorconfig do projektu v aplikaci Visual Studio](media/add-editorconfig-file.png)

::: moniker range=">=vs-2019"

Informace o konfiguraci závažnosti pravidla (například o tom, jestli se jedná o chybu nebo upozornění) najdete v tématu [nastavení závažnosti pravidla v souboru EditorConfig](use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file). Nebo můžete vybrat některou z předdefinovaných [sad pravidel](analyzer-rule-sets.md) , abyste mohli rychle povolit nebo zakázat kategorii pravidel.

::: moniker-end

Zbývající část tohoto článku popisuje obecnou syntaxi pro [Možnosti, které upřesňují](fxcop-analyzer-options.md) , kde se používají pravidla FxCop.

> [!NOTE]
> Starší pravidla FxCop nejde nakonfigurovat pomocí souboru EditorConfig. Informace o rozdílech mezi staršími analyzátory analýz a FxCop najdete v tématu [Nejčastější dotazy k analyzátorům FxCop](fxcop-analyzers-faq.md).

## <a name="option-scopes"></a>Obory možností

Každou možnost zpřesnění lze nakonfigurovat pro všechna pravidla, pro kategorii pravidel (například pro pojmenování nebo návrh) nebo pro konkrétní pravidlo.

### <a name="all-rules"></a>Všechna pravidla

Syntaxe pro konfiguraci možnosti pro *všechna* pravidla je následující:

|Syntaxe|Příklad|
|-|-|
| dotnet_code_quality.OptionName = OptionValue | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>Kategorie pravidel

Syntaxe pro konfiguraci možnosti pro *kategorii* pravidel (například pojmenování, návrh nebo výkon) je následující:

|Syntaxe|Příklad|
|-|-|
| dotnet_code_quality.RuleCategory.OptionName = OptionValue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>Konkrétní pravidlo

Syntaxe pro konfiguraci možnosti pro *konkrétní* pravidlo je následující:

|Syntaxe|Příklad|
|-|-|
| dotnet_code_quality.RuleId.OptionName = OptionValue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="per-project-configuration"></a>Konfigurace pro jednotlivé projekty

Chcete-li povolit konfiguraci analyzátoru založeného na EditorConfig pro konkrétní projekt, přidejte soubor *. EditorConfig* do kořenového adresáře projektu.

V současné době není k dispozici žádná hierarchická podpora pro kombinování souborů. editorconfig, které existují na různých úrovních adresáře, například řešení a na úrovni projektu.

## <a name="shared-configuration"></a>Sdílená konfigurace

Můžete sdílet soubor. editorconfig pro konfiguraci FxCop Analyzer mezi dvěma nebo více projekty, ale vyžaduje některé další kroky.

1. Uložte soubor *. editorconfig* do společného umístění.

2. Vytvořte soubor *. props* s následujícím obsahem:

   ```xml
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <PropertyGroup>
       <SkipDefaultEditorConfigAsAdditionalFile>true</SkipDefaultEditorConfigAsAdditionalFile>
     </PropertyGroup>
     <ItemGroup Condition="Exists('<your path>\.editorconfig')" >
       <AdditionalFiles Include="<your path>\.editorconfig" />
     </ItemGroup>
   </Project>
   ```

3. Přidejte řádek do souboru *. csproj* nebo *. vbproj* pro import souboru *. props* , který jste vytvořili v předchozím kroku. Tento řádek musí být umístěn před řádky, které importují soubory FxCop Analyzer *. props* . Například pokud má soubor. props název *editorconfig. props*:

   ```xml
   ...
   <Import Project="..\..\editorconfig.props" Condition="Exists('..\..\editorconfig.props')" />
   <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
   ...
   ```

4. Znovu načtěte projekt.

> [!NOTE]
> Libovolné sdílené umístění souboru EditorConfig popsaného zde se vztahuje pouze na konfiguraci rozsahu určitých pravidel nástroje FxCop Analyzer. Pro další nastavení, jako je závažnost pravidla, nastavení obecného editoru a styl kódu, musí být soubor EditorConfig vždy umístěn ve složce projektu nebo v nadřazené složce.

## <a name="see-also"></a>Viz také:

- [Možnosti oboru pravidla pro analyzátory FxCop](fxcop-analyzer-options.md)
- [Konfigurace analyzátoru](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [Analyzátory FxCop](install-fxcop-analyzers.md)
- [Konvence kódování .NET pro EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
