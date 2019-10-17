---
title: Upozornění globalizace
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.globalizationrules
helpviewer_keywords:
- warnings, globalization
- globalization warnings
- globalization [Visual Studio], warnings
- managed code analysis warnings, globalization warnings
ms.assetid: a8d12d41-14bf-4b43-af24-168312d7c390
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 264f94a537bc9c067a2f0016115a4cc1bd387fb8
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72449001"
---
# <a name="globalization-warnings"></a>Upozornění globalizace
Upozornění globalizace podporují knihovny a aplikace připravené pro použití ve světě.

## <a name="in-this-section"></a>V tomto oddílu

|Pravidlo|Popis|
|----------|-----------------|
|[CA1300: Zadejte možnosti MessageBoxOptions](../code-quality/ca1300-specify-messageboxoptions.md)|Chcete-li správně zobrazit okno pro kultury, které používají směr čtení zprava doleva, musí být členy RightAlign a RtlReading výčtu MessageBoxOptions předány metodě Show.|
|[CA1301: Vyhněte se duplicitním akcelerátorům](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Přístupová klávesa neboli akcelerátor umožňuje klávesnici přístup k ovládacímu prvku pomocí klávesy ALT. Pokud má více ovládacích prvků duplicitní přístupové klíče, není chování přístupového klíče správně definované.|
|[CA1302: Nekódujte pevně řetězce závislé na národním prostředí](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|Výčet System.Environment.SpecialFolder obsahuje členy, které odkazují na speciální systémové složky. Umístění těchto složek mohou mít různé hodnoty v různých operačních systémech; uživatel může změnit některé z míst; a místa jsou lokalizována. Metoda Environment. GetFolderPath vrací umístění, která jsou přidružená k prostředí. výčet SpecialFolder, lokalizovaný a vhodný pro aktuálně běžící počítač.|
|[CA1303: Nepředávejte literály jako lokalizované parametry](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Externě viditelná metoda předává řetězcový literál jako parametr konstruktoru nebo metodě .NET a tento řetězec by měl být Lokalizovatelný.|
|[CA1304: Zadejte možnosti CultureInfo](../code-quality/ca1304-specify-cultureinfo.md)|Metoda nebo konstruktor volá člen, který má přetížení přijímající parametr System.Globalization.CultureInfo, a tato metoda nebo konstruktor nevolá přetížení přebírající parametr CultureInfo. Pokud objekt CultureInfo nebo System.IFormatProvider není zadán, nemusí mít výchozí hodnota zadaná pomocí přetíženého členu ve všech národních prostředích požadovaný efekt.|
|[CA1305: Zadejte možnosti IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)|Metoda nebo konstruktor volá jeden nebo více členů, které mají přetížení přijímající parametr System.IFormatProvider, a tato metoda nebo konstruktor nevolá přetížení, která přebírá parametr IFormatProvider. Pokud objekt System.Globalization.CultureInfo nebo IFormatProvider není zadán, nemusí mít výchozí hodnota zadaná pomocí přetíženého členu ve všech národních prostředích požadovaný efekt.|
|[CA1306: Nastavte národního prostředí pro datové typy](../code-quality/ca1306-set-locale-for-data-types.md)|Národní prostředí určuje prvky prezentace specifické kultury pro data, například formátování použité pro číselné hodnoty, symboly měny a pořadí řazení. Při vytváření objektu DataSet nebo DataTable byste měli explicitně nastavit národní prostředí.|
|[CA1307: Zadejte možnosti StringComparison](../code-quality/ca1307-specify-stringcomparison.md)|Operace porovnání řetězců používá přetížení metody, které nenastavuje parametr StringComparison.|
|[CA1308: Normalizujte řetězce na velká písmena](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Řetězce by měly být normalizovány na velká písmena. Malá skupina znaků nedokáže po převodu na malá písmena provést zpáteční cestu.|
|[CA1309: Použijte řadový StringComparison](../code-quality/ca1309-use-ordinal-stringcomparison.md)|Nelingvistická operace porovnání řetězců nemá nastaven parametr StringComparison na hodnotu Ordinal ani na hodnotu OrdinalIgnoreCase. Explicitním nastavením parametru na hodnotu StringComparison.Ordinal nebo StringComparison.OrdinalIgnoreCase dojde ke zrychlení kódu a zvýšení přesnosti a spolehlivosti.|
|[CA2101: Určete zařazování pro argumenty řetězce volání nespravovaného kódu](../code-quality/ca2101.md)|Člen vyvolání platformy umožňuje částečně důvěryhodných volajících, má řetězcový parametr a explicitně nezařazuje řetězec. To může způsobit potenciální ohrožení zabezpečení.|
