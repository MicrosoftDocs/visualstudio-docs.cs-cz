---
title: Možnosti konfigurace analyzátoru FxCop
ms.date: 09/23/2019
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ae16a0fd101005f0bc81a3f5f204f5e774976ebb
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305838"
---
# <a name="rule-scope-options-for-fxcop-analyzers"></a>Možnosti oboru pravidla pro analyzátory FxCop

Některá pravidla analyzátoru FxCop umožňují Upřesnit, na které části základů kódu by se měly použít. Tato stránka obsahuje seznam dostupných možností konfigurace oboru, jejich povolených hodnot a pravidla, na která lze použít. Chcete-li použít tyto možnosti, zadejte je do [souboru EditorConfig](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

Tyto možnosti konfigurace jsou k dispozici od verze 2.6.3 balíčku NuGet [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) .

> [!TIP]
> Úplný seznam možností, které jsou k dispozici pro danou verzi balíčku FxCopAnalyzers, najdete v souboru *analyzátoru Configuration.MD* ve složce *dokumentace* pro daný balíček. Soubor je umístěn v umístění *% USERPROFILE% \\. nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers @ no__t-2 @ no__t-3version @ no__t-4\documentation\Analyzer Configuration.MD*. Tento soubor dokumentace konfigurace je součástí každé verze balíčku počínaje verzí 2.6.5. Tady je příklad, jak je možnost popsána v souboru *analyzátoru Configuration.MD* :
>
> Název možnosti: `sufficient_IterationCount_for_weak_KDF_algorithm` @ no__t-1
> Hodnoty možností: integrální hodnoty \
> Výchozí hodnota: Specifické pro každé konfigurovatelné pravidlo (ve výchozím nastavení je to pro většinu pravidel "100000") \
> Příklad: `dotnet_code_quality.CA5387.sufficient_IterationCount_for_weak_KDF_algorithm = 100000`

## <a name="api_surface"></a>api_surface

| Popis | Povolené hodnoty | Výchozí hodnota | Konfigurovatelná pravidla |
| - | - | - | - |
| Která část povrchu rozhraní API se má analyzovat | `public`<br/>`internal` Nebo `friend`<br/>`private`<br/>`all`<br/><br/>Více hodnot oddělte čárkou (,). | `public` | [CA1000](ca1000-do-not-declare-static-members-on-generic-types.md)<br/>[CA1003](ca1003-use-generic-event-handler-instances.md)<br/>[CA1008](ca1008-enums-should-have-zero-value.md)<br/>[CA1010](ca1010-collections-should-implement-generic-interface.md)<br/>[CA1012](ca1012-abstract-types-should-not-have-constructors.md)<br/>[CA1024](ca1024-use-properties-where-appropriate.md)<br/>[CA1027](ca1027-mark-enums-with-flagsattribute.md)<br/>[CA1028](ca1028-enum-storage-should-be-int32.md)<br/>[CA1030](ca1030-use-events-where-appropriate.md)<br/>[CA1036](ca1036-override-methods-on-comparable-types.md)<br/>[CA1040](ca1040-avoid-empty-interfaces.md)<br/>[CA1041](ca1041-provide-obsoleteattribute-message.md)<br/>[CA1043](ca1043-use-integral-or-string-argument-for-indexers.md)<br/>[CA1044](ca1044-properties-should-not-be-write-only.md)<br/>[CA1051](ca1051-do-not-declare-visible-instance-fields.md)<br/>[CA1052](ca1052-static-holder-types-should-be-sealed.md)<br/>[CA1054](ca1054-uri-parameters-should-not-be-strings.md)<br/>[CA1055](ca1055-uri-return-values-should-not-be-strings.md)<br/>[CA1056](ca1056-uri-properties-should-not-be-strings.md)<br/>[CA1058](ca1058-types-should-not-extend-certain-base-types.md)<br/>[CA1063](ca1063-implement-idisposable-correctly.md)<br/>[CA1708](ca1708-identifiers-should-differ-by-more-than-case.md)<br/>[CA1710](ca1710-identifiers-should-have-correct-suffix.md)<br/>[CA1711](ca1711-identifiers-should-not-have-incorrect-suffix.md)<br/>[CA1714](ca1714-flags-enums-should-have-plural-names.md)<br/>[CA1715](ca1715-identifiers-should-have-correct-prefix.md)<br/>[CA1716](ca1716-identifiers-should-not-match-keywords.md)<br/>[CA1717](ca1717-only-flagsattribute-enums-should-have-plural-names.md)<br/>[CA1720](ca1720-identifiers-should-not-contain-type-names.md)<br/>[CA1721](ca1721-property-names-should-not-match-get-methods.md)<br/>[CA1725](ca1725-parameter-names-should-match-base-declaration.md)<br/>[CA1802](ca1802.md)<br/>[CA1815](ca1815.md)<br/>[CA1819](ca1819.md)<br/>[CA2217](ca2217-do-not-mark-enums-with-flagsattribute.md)<br/>[CA2225](ca2225-operator-overloads-have-named-alternates.md)<br/>[CA2226](ca2226-operators-should-have-symmetrical-overloads.md)<br/>[CA2231](ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)<br/>[CA2234](ca2234-pass-system-uri-objects-instead-of-strings.md) |

## <a name="exclude_async_void_methods"></a>exclude_async_void_methods

| Popis | Povolené hodnoty | Výchozí hodnota | Konfigurovatelná pravidla |
| - | - | - | - |
| Zda se mají ignorovat asynchronní metody, které nevracejí hodnotu | `true`<br/>`false` | `false` | [CA2007](ca2007-do-not-directly-await-task.md) |

> [!NOTE]
> Ve verzi 2.6.3 a starším balíčku analyzátoru byla tato možnost pojmenována `skip_async_void_methods`.

## <a name="exclude_single_letter_type_parameters"></a>exclude_single_letter_type_parameters

| Popis | Povolené hodnoty | Výchozí hodnota | Konfigurovatelná pravidla |
| - | - | - | - |
| Určuje, zda mají být z pravidla vyloučeny [parametry typu](/dotnet/csharp/programming-guide/generics/generic-type-parameters) s jedním znakem, například `S` v `Collection<S>`. | `true`<br/>`false` | `false` | [CA1715](ca1715-identifiers-should-have-correct-prefix.md) |

> [!NOTE]
> Ve verzi 2.6.3 a starším balíčku analyzátoru byla tato možnost pojmenována `allow_single_letter_type_parameters`.

## <a name="output_kind"></a>output_kind

| Popis | Povolené hodnoty | Výchozí hodnota | Konfigurovatelná pravidla |
| - | - | - | - |
| Určuje, že se má analyzovat kód v projektu, který generuje tento typ sestavení. | Jedno nebo více polí výčtu <xref:Microsoft.CodeAnalysis.OutputKind><br/><br/>Více hodnot oddělte čárkou (,). | Všechny druhy výstupu | [CA2007](ca2007-do-not-directly-await-task.md) |