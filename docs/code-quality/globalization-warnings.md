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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fecc46ac6e1221cb547e98711d95b743010d4c6c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587573"
---
# <a name="globalization-warnings"></a>Upozornění globalizace
Upozornění globalizace podporují knihovny a aplikace připravené pro použití ve světě.

## <a name="in-this-section"></a>V tomto oddílu

|Pravidlo|Popis|
|----------|-----------------|
|[CA1300: Zadejte možnosti MessageBoxOptions](../code-quality/ca1300.md)|Chcete-li správně zobrazit okno pro kultury, které používají směr čtení zprava doleva, musí být členy RightAlign a RtlReading výčtu MessageBoxOptions předány metodě Show.|
|[CA1301: Vyhněte se duplicitním akcelerátorům](../code-quality/ca1301.md)|Přístupová klávesa neboli akcelerátor umožňuje klávesnici přístup k ovládacímu prvku pomocí klávesy ALT. Pokud má více ovládacích prvků duplicitní přístupové klíče, není chování přístupového klíče správně definované.|
|[CA1302: Nekódujte pevně řetězce závislé na národním prostředí](../code-quality/ca1302.md)|Výčet System.Environment.SpecialFolder obsahuje členy, které odkazují na speciální systémové složky. Umístění těchto složek mohou mít různé hodnoty v různých operačních systémech; uživatel může změnit některé z míst; a místa jsou lokalizována. Metoda Environment. GetFolderPath vrací umístění, která jsou přidružená k prostředí. výčet SpecialFolder, lokalizovaný a vhodný pro aktuálně běžící počítač.|
|[CA1303: Nepředávejte literály jako lokalizované parametry](../code-quality/ca1303.md)|Externě viditelná metoda předává řetězcový literál jako parametr konstruktoru nebo metodě .NET a tento řetězec by měl být Lokalizovatelný.|
|[CA1304: Zadejte možnosti CultureInfo](../code-quality/ca1304.md)|Metoda nebo konstruktor volá člen, který má přetížení přijímající parametr System.Globalization.CultureInfo, a tato metoda nebo konstruktor nevolá přetížení přebírající parametr CultureInfo. Pokud objekt CultureInfo nebo System.IFormatProvider není zadán, nemusí mít výchozí hodnota zadaná pomocí přetíženého členu ve všech národních prostředích požadovaný efekt.|
|[CA1305: Zadejte možnosti IFormatProvider](../code-quality/ca1305.md)|Metoda nebo konstruktor volá jeden nebo více členů, které mají přetížení přijímající parametr System.IFormatProvider, a tato metoda nebo konstruktor nevolá přetížení, která přebírá parametr IFormatProvider. Pokud objekt System.Globalization.CultureInfo nebo IFormatProvider není zadán, nemusí mít výchozí hodnota zadaná pomocí přetíženého členu ve všech národních prostředích požadovaný efekt.|
|[CA1306: Nastavte národního prostředí pro datové typy](../code-quality/ca1306.md)|Národní prostředí určuje prvky prezentace specifické kultury pro data, například formátování použité pro číselné hodnoty, symboly měny a pořadí řazení. Při vytváření objektu DataSet nebo DataTable byste měli explicitně nastavit národní prostředí.|
|[CA1307: Zadejte možnosti StringComparison](../code-quality/ca1307.md)|Operace porovnání řetězců používá přetížení metody, které nenastavuje parametr StringComparison.|
|[CA1308: Normalizujte řetězce na velká písmena](../code-quality/ca1308.md)|Řetězce by měly být normalizovány na velká písmena. Malá skupina znaků nedokáže po převodu na malá písmena provést zpáteční cestu.|
|[CA1309: Použijte řadový StringComparison](../code-quality/ca1309.md)|Nelingvistická operace porovnání řetězců nemá nastaven parametr StringComparison na hodnotu Ordinal ani na hodnotu OrdinalIgnoreCase. Explicitním nastavením parametru na hodnotu StringComparison.Ordinal nebo StringComparison.OrdinalIgnoreCase dojde ke zrychlení kódu a zvýšení přesnosti a spolehlivosti.|
|[CA2101: Určete zařazování pro argumenty řetězce volání nespravovaného kódu](../code-quality/ca2101.md)|Člen vyvolání platformy umožňuje částečně důvěryhodných volajících, má řetězcový parametr a explicitně nezařazuje řetězec. To může způsobit potenciální ohrožení zabezpečení.|
