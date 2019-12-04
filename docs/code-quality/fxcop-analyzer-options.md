---
title: Možnosti konfigurace analyzátoru FxCop
ms.date: 09/23/2019
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2d97552a79b520bd522cb8ec768d7d36fe2fb052
ms.sourcegitcommit: c222052906362bf1a3762ec4d4623170e4e06702
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74809808"
---
# <a name="rule-scope-options-for-fxcop-analyzers"></a>Možnosti oboru pravidla pro analyzátory FxCop

Některá pravidla analyzátoru FxCop umožňují Upřesnit, na které části základů kódu by se měly použít. Tato stránka obsahuje seznam dostupných možností konfigurace oboru, jejich povolených hodnot a pravidla, na která lze použít. Chcete-li použít tyto možnosti, zadejte je do [souboru EditorConfig](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

Tyto možnosti konfigurace jsou k dispozici od verze 2.6.3 balíčku NuGet [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) .

> [!TIP]
> Úplný seznam možností, které jsou k dispozici pro danou verzi balíčku FxCopAnalyzers, najdete v souboru *analyzátoru Configuration.MD* ve složce *dokumentace* pro daný balíček. Soubor se nachází v umístění *% USERPROFILE%\\. nuget\packages\microsoft.codeanalysis.fxcopanalyzers\\\<verze\>\documentation\Analyzer Configuration.MD*. Tento soubor dokumentace konfigurace je součástí každé verze balíčku počínaje verzí 2.6.5. Tady je příklad, jak je možnost popsána v souboru *analyzátoru Configuration.MD* :
>
> Název možnosti: `sufficient_IterationCount_for_weak_KDF_algorithm`\
> Hodnoty možností: integrální hodnoty \
> Výchozí hodnota: specifická pro každé konfigurovatelné pravidlo (ve výchozím nastavení je to pro většinu pravidel "100000") \
> Příklad: `dotnet_code_quality.CA5387.sufficient_IterationCount_for_weak_KDF_algorithm = 100000`

## <a name="api_surface"></a>api_surface

| Popis | Povolené hodnoty | Výchozí hodnota | Konfigurovatelná pravidla |
| - | - | - | - |
| Která část povrchu rozhraní API se má analyzovat | `public`<br/>`internal` Nebo `friend`<br/>`private`<br/>`all`<br/><br/>Více hodnot oddělte čárkou (,). | `public` | [CA1000](ca1000.md) [CA1003](ca1003.md) [CA1008](ca1008.md) [CA1010](ca1010.md)<br/>[CA1012](ca1012.md) [CA1024](ca1024.md) [CA1027](ca1027.md) [CA1028](ca1028.md)<br/>[CA1030](ca1030.md) [CA1036](ca1036.md) [CA1040](ca1040.md) [CA1041](ca1041.md)<br/>[CA1043](ca1043.md) [CA1044](ca1044.md) [CA1051](ca1051.md) [CA1052](ca1052.md)<br/>[CA1054](ca1054.md) [CA1055](ca1055.md) [CA1056](ca1056.md) [CA1058](ca1058.md)<br/>[CA1063](ca1063.md) [CA1708](ca1708.md) [CA1710](ca1710.md) [CA1711](ca1711.md)<br/>[CA1714](ca1714.md) [CA1715](ca1715.md) [CA1716](ca1716.md) [CA1717](ca1717.md)<br/>[CA1720](ca1720.md) [CA1721](ca1721.md) [CA1725](ca1725.md) [CA1801](ca1801.md)<br/>[CA1802](ca1802.md) [CA1815](ca1815.md) [CA1819](ca1819.md) [CA2217](ca2217.md)<br/>[CA2225](ca2225.md) [CA2226](ca2226.md) [CA2231](ca2231.md) [CA2234](ca2234.md)<br/>|

## <a name="exclude_async_void_methods"></a>exclude_async_void_methods

| Popis | Povolené hodnoty | Výchozí hodnota | Konfigurovatelná pravidla |
| - | - | - | - |
| Zda se mají ignorovat asynchronní metody, které nevracejí hodnotu | `true`<br/>`false` | `false` | [CA2007](ca2007.md) |

> [!NOTE]
> Ve verzi 2.6.3 a starším balíčku analyzátoru byla tato možnost pojmenována `skip_async_void_methods`.

## <a name="exclude_single_letter_type_parameters"></a>exclude_single_letter_type_parameters

| Popis | Povolené hodnoty | Výchozí hodnota | Konfigurovatelná pravidla |
| - | - | - | - |
| Určuje, zda mají být z pravidla vyloučeny [parametry typu](/dotnet/csharp/programming-guide/generics/generic-type-parameters) s jedním znakem, například `S` v `Collection<S>` | `true`<br/>`false` | `false` | [CA1715](ca1715.md) |

> [!NOTE]
> Ve verzi 2.6.3 a starším balíčku analyzátoru byla tato možnost pojmenována `allow_single_letter_type_parameters`.

## <a name="output_kind"></a>output_kind

| Popis | Povolené hodnoty | Výchozí hodnota | Konfigurovatelná pravidla |
| - | - | - | - |
| Určuje, že se má analyzovat kód v projektu, který generuje tento typ sestavení. | Jedno nebo více polí výčtu <xref:Microsoft.CodeAnalysis.OutputKind><br/><br/>Více hodnot oddělte čárkou (,). | Všechny druhy výstupu | [CA2007](ca2007.md) |

## <a name="required_modifiers"></a>required_modifiers

| Popis | Povolené hodnoty | Výchozí hodnota | Konfigurovatelná pravidla |
| - | - | - | - |
| Určuje požadované modifikátory pro rozhraní API, která by se měla analyzovat. | Jedna nebo více hodnot z níže uvedených povolených tabulek modifikátorů<br/><br/>Více hodnot oddělte čárkou (,). | Závisí na každém pravidle. | [CA1802](ca1802.md) |

| Povolený modifikátor | Přehled |
| --- | --- |
| `none` | Žádný požadavek na modifikátor |
| `static` Nebo `Shared` | Musí být deklarované jako ' static ' (' Shared ' v Visual Basic) |
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
| Bez ohledu na to, jestli se má přeskočit analýza pro parametr `this` rozšiřujících metod | `true`<br/>`false` | `false` | [CA1062](ca1062.md) |

## <a name="null_check_validation_methods"></a>null_check_validation_methods

| Popis | Povolené hodnoty | Výchozí hodnota | Konfigurovatelná pravidla |
| - | - | - | - |
| Názvy ověřovacích metod kontroly hodnoty null, které ověřují argumenty předané metodě, jsou jiné než null. | Povolené formáty názvů metod (oddělené `|`):<br/> -Pouze název metody (včetně všech metod s názvem, bez ohledu na obsahující typ nebo obor názvů)<br/> – Plně kvalifikované názvy ve [formátu ID dokumentace k](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)symbolu s volitelnou předponou `M:` | Žádné | [CA1062](ca1062.md) |

## <a name="additional_string_formatting_methods"></a>additional_string_formatting_methods

| Popis | Povolené hodnoty | Výchozí hodnota | Konfigurovatelná pravidla |
| - | - | - | - |
| Názvy dalších metod formátování řetězců | Povolené formáty názvů metod (oddělené `|`):<br/> -Pouze název metody (včetně všech metod s názvem, bez ohledu na obsahující typ nebo obor názvů)<br/> – Plně kvalifikované názvy ve [formátu ID dokumentace k](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)symbolu s volitelnou předponou `M:` | Žádné | [CA2241](ca2241.md) |

## <a name="excluded_type_names_with_derived_types"></a>excluded_type_names_with_derived_types

| Popis | Povolené hodnoty | Výchozí hodnota | Konfigurovatelná pravidla |
| - | - | - | - |
| Názvy typů, jako je vyloučení typu a všech jeho odvozených typů pro účely analýzy | Povolené formáty názvů symbolů (oddělené `|`):<br/> – Pouze název typu (zahrnuje všechny typy s názvem, bez ohledu na obsahující typ nebo obor názvů)<br/> – Plně kvalifikované názvy ve [formátu ID dokumentace k](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)symbolu s volitelnou předponou `T:` | Žádné | [CA1303](ca1303.md) |

## <a name="excluded_symbol_names"></a>excluded_symbol_names

| Popis | Povolené hodnoty | Výchozí hodnota | Konfigurovatelná pravidla |
| - | - | - | - |
| Názvy symbolů, které jsou vyloučeny pro analýzu | Povolené formáty názvů symbolů (oddělené `|`):<br/> – Pouze název symbolu (včetně všech symbolů s názvem, bez ohledu na obsahující typ nebo obor názvů)<br/> – Plně kvalifikované názvy ve [formátu ID dokumentace k](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)symbolu. Každý název symbolu vyžaduje předponu typu symbolu, jako je například "M:" prefix pro metody, předpona "T:" pro typy, předpona "N:" pro obory názvů atd.<br/> - `.ctor` pro konstruktory a `.cctor` pro statické konstruktory | Žádné | [CA1062](ca1062.md) [CA1303](ca1303.md) [CA2000](ca2000.md) [CA2100](ca2100.md) [CA2301](ca2301.md) [CA2302](ca2302.md)<br/>[CA2311](ca2311.md) [CA2312](ca2312.md) [CA2321](ca2321.md) [CA2322](ca2322.md) [CA2327](ca2327.md) [CA2328](ca2328.md)<br/>[CA2329](ca2329.md) [CA2330](ca2330.md) [CA3001](ca3001.md) [CA3002](ca3002.md) [CA3003](ca3003.md) [CA3004](ca3004.md)<br/>[CA3005](ca3005.md) [CA3006](ca3006.md) [CA3007](ca3007.md) [CA3008](ca3008.md) [CA3009](ca3009.md) [CA3010](ca3010.md)<br/>[CA3011](ca3011.md) [CA3012](ca3012.md) [CA5361](ca5361.md) CA5376 CA5377 [CA5378](ca5378.md)<br/>[CA5380](ca5380.md) [CA5381](ca5381.md) CA5382 CA5383 CA5384 CA5387<br/>CA5388 [CA5389](ca5389.md) CA5390 |

## <a name="disallowed_symbol_names"></a>disallowed_symbol_names

| Popis | Povolené hodnoty | Výchozí hodnota | Konfigurovatelná pravidla |
| - | - | - | - |
| Názvy symbolů, které jsou v kontextu analýzy zakázané | Povolené formáty názvů symbolů (oddělené `|`):<br/> – Pouze název symbolu (včetně všech symbolů s názvem, bez ohledu na obsahující typ nebo obor názvů)<br/> – Plně kvalifikované názvy ve [formátu ID dokumentace k](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)symbolu. Každý název symbolu vyžaduje předponu typu symbolu, jako je například "M:" prefix pro metody, předpona "T:" pro typy, předpona "N:" pro obory názvů atd.<br/> - `.ctor` pro konstruktory a `.cctor` pro statické konstruktory | Žádné | [CA1031](ca1031.md) |

