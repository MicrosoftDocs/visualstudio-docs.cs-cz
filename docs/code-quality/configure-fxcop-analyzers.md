---
title: Konfigurace analyzátorů kvality kódu .NET pomocí editorconfig
ms.date: 09/01/2020
ms.topic: conceptual
helpviewer_keywords:
- .NET analyzers
- FxCop analyzers, configuring
- code quality
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: bc237082ec1188d71241facead975db1df2cf3af
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2020
ms.locfileid: "90035427"
---
# <a name="configure-net-code-quality-analysis-with-editorconfig"></a>Konfigurace analýzy kvality kódu .NET pomocí EditorConfig

Každý analyzátor kvality kódu (s ID, jejichž ID začíná `CA` na), lze upravit tak, aby se pro části vašeho základu kódu mohl vztahovat na konfigurovatelné možnosti. Každá možnost je určena přidáním páru klíč-hodnota k souboru [EditorConfig](https://editorconfig.org) . Konfigurační soubor může být specifický pro soubor, projekt, řešení nebo celé úložiště.

> [!TIP]
> Přidejte soubor. editorconfig do projektu kliknutím pravým tlačítkem myši na projekt v **Průzkumník řešení** a výběrem možnosti **Přidat**  >  **novou položku**. V okně **Přidat novou položku** do vyhledávacího pole zadejte **editorconfig** . Vyberte šablonu **soubor editorconfig (výchozí)** a zvolte **Přidat**.
>
> ![Přidat soubor EditorConfig do projektu v aplikaci Visual Studio](media/add-editorconfig-file.png)

::: moniker range=">=vs-2019"

Informace o konfiguraci závažnosti pravidla (například o tom, jestli se jedná o chybu nebo upozornění) najdete v tématu [nastavení závažnosti pravidla v souboru EditorConfig](use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file). Případně můžete vybrat jeden z předdefinovaných [EditorConfig souborů nebo sad pravidel](analyzer-rule-sets.md) a rychle povolit nebo zakázat kategorii pravidel.

::: moniker-end

Zbývající část tohoto článku popisuje obecnou syntaxi pro možnosti, které upřesňují, kde se používají analyzátory kvality kódu .NET.

## <a name="option-scopes"></a>Obory možností

Každou možnost zpřesnění lze nakonfigurovat pro všechna pravidla, pro kategorii pravidel (například pro zabezpečení nebo návrh) nebo pro konkrétní pravidlo.

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

## <a name="enabling-editorconfig-based-configuration"></a>Povolení konfigurace založené na EditorConfig

Pro následující rozsahy je možné povolit konfiguraci analyzátoru založené na EditorConfig:

- Konkrétní dokument (y)
- Konkrétní složky
- Konkrétní projekt (y)
- Konkrétní řešení
- Celé úložiště

Chcete-li povolit konfiguraci, přidejte soubor *. editorconfig* s možnostmi v příslušném adresáři. Tento soubor může také obsahovat konfigurační položky konfigurace diagnostiky založené na EditorConfig. Další podrobnosti najdete [tady](use-roslyn-analyzers.md#configure-severity-levels).

## <a name="enable-a-category-of-rules"></a>Povolení kategorie pravidel

Balíčky analyzátoru můžou zahrnovat předdefinované soubory [EditorConfig](use-roslyn-analyzers.md#configure-severity-levels) a/nebo [sady pravidel](using-rule-sets-to-group-code-analysis-rules.md) , které usnadňují a usnadňují povolování kategorií pravidel, jako jsou pravidla zabezpečení nebo návrhu. Balíček [Microsoft. CodeAnalysis. NetAnalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) NuGet Analyzer zahrnuje jak soubory EditorConfig, tak sady pravidel. Povolením konkrétní kategorie pravidel můžete identifikovat cílené problémy a konkrétní podmínky.

> [!NOTE]
> Povolení pravidel analyzátoru a nastavení jejich závažnosti pomocí souboru EditorConfig se podporuje počínaje verzí Visual Studio 2019 verze 16,3.

Balíček NuGet NetAnalyzers zahrnuje předdefinované soubory EditorConfig a sady pravidel pro následující kategorie pravidel:

- Všechna pravidla
- Tok dat
- Návrh
- Dokumentace
- Globalizace
- Interoperabilita
- Udržovatelnost
- Pojmenování
- Výkon
- Portovaná z FxCop
- Spolehlivost
- Zabezpečení
- Využití

Každá z těchto kategorií pravidel má EditorConfig nebo soubor sady pravidel:

- Povolit všechna pravidla v kategorii (a zakázat všechna ostatní pravidla)
- Použít výchozí závažnost každého pravidla a povolit výchozí nastavení (a zakázat všechna ostatní pravidla)

> [!TIP]
> Kategorie všechna pravidla obsahuje další EditorConfig nebo soubor sady pravidel pro zákaz všech pravidel. Tento soubor použijte k rychlému odstranění všech upozornění analyzátoru nebo chyb v projektu.

> [!TIP]
> Pokud migrujete ze starší analýzy "FxCop" na analýzu kódu na základě .NET Compiler Platform, soubory EditorConfig a sady pravidel vám umožní pokračovat v používání podobných konfigurací pravidel pro ty, [které jste použili dříve](rule-set-reference.md).

## <a name="predefined-editorconfig-files"></a>Předdefinované soubory EditorConfig

Předdefinované soubory EditorConfig pro balíček Microsoft. CodeAnalysis. NetAnalyzers Analyzer jsou umístěné v adresáři *% USERPROFILE% \\ . nuget\packages\microsoft.CodeAnalysis.netanalyzers \\ \<version\> \editorconfig* . Například soubor EditorConfig pro povolení všech pravidel zabezpečení je umístěný v souboru *% USERPROFILE% \\ . nuget\packages\microsoft.CodeAnalysis.netanalyzers \\ \<version\> \editorconfig\SecurityRulesEnabled \\ . EditorConfig*.

Zkopírujte zvolený soubor. editorconfig do kořenového adresáře vašeho projektu.

## <a name="predefined-rule-sets"></a>Předdefinované sady pravidel

Předdefinované soubory sady pravidel pro balíček Microsoft. CodeAnalysis. NetAnalyzers Analyzer jsou umístěné v adresáři *% USERPROFILE% \\ . nuget\packages\microsoft.CodeAnalysis.netanalyzers \\ \<version\> \rulesets* . Například soubor sady pravidel pro povolení všech pravidel zabezpečení je umístěný v *% USERPROFILE% \\ . nuget\packages\microsoft.CodeAnalysis.netanalyzers \\ \<version\> \rulesets\SecurityRulesEnabled.ruleset*.

Zkopírujte jednu nebo více sad pravidel a vložte je do adresáře, který obsahuje projekt aplikace Visual Studio, nebo přímo do **Průzkumník řešení**.

Můžete také [přizpůsobit předdefinované pravidlo](how-to-create-a-custom-rule-set.md) , které je nastaveno na vaše preference. Můžete například změnit závažnost jednoho nebo více pravidel tak, aby se v **Seznam chyb**zobrazovaly chyby nebo upozornění.


## <a name="rule-scope-options-for-net-code-quality-analyzers"></a>Možnosti oboru pravidla pro analyzátory kvality kódu .NET

V [souboru EditorConfig](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project)můžete zadat možnosti. Můžete například zadat následující možnosti.

> [!TIP]
> Úplný seznam dostupných možností najdete v tomto [souboru analyzátoru Configuration.MD](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md). Tady je příklad, jak je možnost popsána v souboru *analyzátoru Configuration.MD* :
>
> Název možnosti: `sufficient_IterationCount_for_weak_KDF_algorithm`\
> Hodnoty možností: integrální hodnoty \
> Výchozí hodnota: specifická pro každé konfigurovatelné pravidlo (ve výchozím nastavení je to pro většinu pravidel "100000") \
> Příklad: `dotnet_code_quality.CA5387.sufficient_IterationCount_for_weak_KDF_algorithm = 100000`

## <a name="api_surface"></a>api_surface

| Popis | Povolené hodnoty | Výchozí hodnota | Konfigurovatelná pravidla |
| - | - | - | - |
| Která část povrchu rozhraní API se má analyzovat | `public`<br/>`internal` nebo `friend`<br/>`private`<br/>`all`<br/><br/>Více hodnot oddělte čárkou (,). | `public` | [CA1000](ca1000.md) [CA1003](ca1003.md) [CA1008](ca1008.md) [CA1010](ca1010.md)<br/>[CA1012](ca1012.md) [CA1024](ca1024.md) [CA1027](ca1027.md) [CA1028](ca1028.md)<br/>[CA1030](ca1030.md) [CA1036](ca1036.md) [CA1040](ca1040.md) [CA1041](ca1041.md)<br/>[CA1043](ca1043.md) [CA1044](ca1044.md) [CA1051](ca1051.md) [CA1052](ca1052.md)<br/>[CA1054](ca1054.md) [CA1055](ca1055.md) [CA1056](ca1056.md) [CA1058](ca1058.md)<br/>[CA1063](ca1063.md) [CA1708](ca1708.md) [CA1710](ca1710.md) [CA1711](ca1711.md)<br/>[CA1714](ca1714.md) [CA1715](ca1715.md) [CA1716](ca1716.md) [CA1717](ca1717.md)<br/>[CA1720](ca1720.md) [CA1721](ca1721.md) [CA1725](ca1725.md) [CA1801](ca1801.md)<br/>[CA1802](ca1802.md) [CA1815](ca1815.md) [CA1819](ca1819.md) [CA2217](ca2217.md)<br/>[CA2225](ca2225.md) [CA2226](ca2226.md) [CA2231](ca2231.md) [CA2234](ca2234.md)<br/>|

## <a name="exclude_async_void_methods"></a>exclude_async_void_methods

| Popis | Povolené hodnoty | Výchozí hodnota | Konfigurovatelná pravidla |
| - | - | - | - |
| Zda se mají ignorovat asynchronní metody, které nevracejí hodnotu | `true`<br/>`false` | `false` | [CA2007](ca2007.md) |

> [!NOTE]
> Ve verzi 2.6.3 a starším balíčku analyzátoru byla tato možnost pojmenována `skip_async_void_methods` .

## <a name="exclude_single_letter_type_parameters"></a>exclude_single_letter_type_parameters

| Popis | Povolené hodnoty | Výchozí hodnota | Konfigurovatelná pravidla |
| - | - | - | - |
| Určuje, zda mají být z pravidla vyloučeny [parametry typu](/dotnet/csharp/programming-guide/generics/generic-type-parameters) s jedním znakem, například `S` v `Collection<S>` | `true`<br/>`false` | `false` | [CA1715](ca1715.md) |

> [!NOTE]
> Ve verzi 2.6.3 a starším balíčku analyzátoru byla tato možnost pojmenována `allow_single_letter_type_parameters` .

## <a name="output_kind"></a>output_kind

| Popis | Povolené hodnoty | Výchozí hodnota | Konfigurovatelná pravidla |
| - | - | - | - |
| Určuje, že se má analyzovat kód v projektu, který generuje tento typ sestavení. | Jedno nebo více polí <xref:Microsoft.CodeAnalysis.OutputKind> výčtu<br/><br/>Více hodnot oddělte čárkou (,). | Všechny druhy výstupu | [CA2007](ca2007.md) |

## <a name="required_modifiers"></a>required_modifiers

| Popis | Povolené hodnoty | Výchozí hodnota | Konfigurovatelná pravidla |
| - | - | - | - |
| Určuje požadované modifikátory pro rozhraní API, která by se měla analyzovat. | Jedna nebo více hodnot z níže uvedených povolených tabulek modifikátorů<br/><br/>Více hodnot oddělte čárkou (,). | Závisí na každém pravidle. | [CA1802](ca1802.md) |

| Povolený modifikátor | Shrnutí |
| --- | --- |
| `none` | Žádný požadavek na modifikátor |
| `static` nebo `Shared` | Musí být deklarované jako ' static ' (' Shared ' v Visual Basic) |
| `const` | Musí být deklarovaný jako const |
| `readonly` | Musí se deklarovat jako ReadOnly. |
| `abstract` | Musí se deklarovat jako abstract. |
| `virtual` | Musí se deklarovat jako Virtual |
| `override` | Musí se deklarovat jako override. |
| `sealed` | Musí se deklarovat jako Sealed. |
| `extern` | Musí být deklarované jako extern. |
| `async` | Se musí deklarovat jako Async. |

## <a name="exclude_extension_method_this_parameter"></a>exclude_extension_method_this_parameter

| Popis | Povolené hodnoty | Výchozí hodnota | Konfigurovatelná pravidla |
| - | - | - | - |
| Bez ohledu na to, jestli se má přeskočit analýza `this` parametru rozšiřujících metod | `true`<br/>`false` | `false` | [CA1062](ca1062.md) |

## <a name="null_check_validation_methods"></a>null_check_validation_methods

| Popis | Povolené hodnoty | Výchozí hodnota | Konfigurovatelná pravidla |
| - | - | - | - |
| Názvy ověřovacích metod kontroly hodnoty null, které ověřují argumenty předané metodě, jsou jiné než null. | Povolené formáty názvu metody (oddělené `|` ):<br/> -Pouze název metody (včetně všech metod s názvem, bez ohledu na obsahující typ nebo obor názvů)<br/> – Plně kvalifikované názvy ve [formátu ID dokumentace k](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)symbolu s volitelnou `M:` předponou | Žádné | [CA1062](ca1062.md) |

## <a name="additional_string_formatting_methods"></a>additional_string_formatting_methods

| Popis | Povolené hodnoty | Výchozí hodnota | Konfigurovatelná pravidla |
| - | - | - | - |
| Názvy dalších metod formátování řetězců | Povolené formáty názvu metody (oddělené `|` ):<br/> -Pouze název metody (včetně všech metod s názvem, bez ohledu na obsahující typ nebo obor názvů)<br/> – Plně kvalifikované názvy ve [formátu ID dokumentace k](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)symbolu s volitelnou `M:` předponou | Žádné | [CA2241](ca2241.md) |

## <a name="excluded_type_names_with_derived_types"></a>excluded_type_names_with_derived_types

| Popis | Povolené hodnoty | Výchozí hodnota | Konfigurovatelná pravidla |
| - | - | - | - |
| Názvy typů, jako je vyloučení typu a všech jeho odvozených typů pro účely analýzy | Povolené formáty názvů symbolů (oddělené symbolem `|` ):<br/> – Pouze název typu (zahrnuje všechny typy s názvem, bez ohledu na obsahující typ nebo obor názvů)<br/> – Plně kvalifikované názvy ve [formátu ID dokumentace k](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)symbolu s volitelnou `T:` předponou | Žádné | [CA1303](ca1303.md) |

## <a name="excluded_symbol_names"></a>excluded_symbol_names

| Popis | Povolené hodnoty | Výchozí hodnota | Konfigurovatelná pravidla |
| - | - | - | - |
| Názvy symbolů, které jsou vyloučeny pro analýzu | Povolené formáty názvů symbolů (oddělené symbolem `|` ):<br/> – Pouze název symbolu (včetně všech symbolů s názvem, bez ohledu na obsahující typ nebo obor názvů)<br/> – Plně kvalifikované názvy ve [formátu ID dokumentace k](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)symbolu. Každý název symbolu vyžaduje předponu typu symbolu, jako je například "M:" prefix pro metody, předpona "T:" pro typy, předpona "N:" pro obory názvů atd.<br/> - `.ctor` pro konstruktory a `.cctor` pro statické konstruktory | Žádné | [CA1062](ca1062.md) [CA1303](ca1303.md) [CA2000](ca2000.md) [CA2100](ca2100.md) [CA2301](ca2301.md) [CA2302](ca2302.md)<br/>[CA2311](ca2311.md) [CA2312](ca2312.md) [CA2321](ca2321.md) [CA2322](ca2322.md) [CA2327](ca2327.md) [CA2328](ca2328.md)<br/>[CA2329](ca2329.md) [CA2330](ca2330.md) [CA3001](ca3001.md) [CA3002](ca3002.md) [CA3003](ca3003.md) [CA3004](ca3004.md)<br/>[CA3005](ca3005.md) [CA3006](ca3006.md) [CA3007](ca3007.md) [CA3008](ca3008.md) [CA3009](ca3009.md) [CA3010](ca3010.md)<br/>[CA3011](ca3011.md) [CA3012](ca3012.md) [CA5361](ca5361.md) CA5376 CA5377 [CA5378](ca5378.md)<br/>[CA5380](ca5380.md) [CA5381](ca5381.md) CA5382 CA5383 CA5384 CA5387<br/>CA5388 [CA5389](ca5389.md) CA5390 |

## <a name="disallowed_symbol_names"></a>disallowed_symbol_names

| Popis | Povolené hodnoty | Výchozí hodnota | Konfigurovatelná pravidla |
| - | - | - | - |
| Názvy symbolů, které jsou v kontextu analýzy zakázané | Povolené formáty názvů symbolů (oddělené symbolem `|` ):<br/> – Pouze název symbolu (včetně všech symbolů s názvem, bez ohledu na obsahující typ nebo obor názvů)<br/> – Plně kvalifikované názvy ve [formátu ID dokumentace k](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)symbolu. Každý název symbolu vyžaduje předponu typu symbolu, jako je například "M:" prefix pro metody, předpona "T:" pro typy, předpona "N:" pro obory názvů atd.<br/> - `.ctor` pro konstruktory a `.cctor` pro statické konstruktory | Žádné | [CA1031](ca1031.md) |

## <a name="see-also"></a>Viz také

- [Konfigurace analyzátoru](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [Konvence kódování .NET pro EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
