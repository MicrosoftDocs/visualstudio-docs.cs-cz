---
title: FxCopCmd – chyby
ms.date: 10/19/2016
ms.topic: reference
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
ms.author: gewarren
author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1892fa9f47e0b3b315531adc51cf538ff7fe4dee
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72449016"
---
# <a name="fxcopcmd-tool-errors"></a>Chyby nástroje FxCopCmd

FxCopCmd nepovažuje všechny chyby za závažné. Pokud má FxCopCmd dostatek informací pro provedení částečné analýzy, provede analýzu a nahlásí chyby, ke kterým došlo. Kód chyby, který je 32 celé číslo, obsahuje bitovou kombinaci číselných hodnot, které odpovídají chybám.

Následující tabulka popisuje kódy chyb vrácené funkcí FxCopCmd:

|Chyba|Číselná hodnota|
|-----------|-------------------|
|Žádné chyby|0x0|
|Chyba analýzy|0x1|
|Výjimky pravidla|0x2|
|Chyba načtení projektu|0x4|
|Chyba načtení sestavení|0x8|
|Chyba načtení knihovny pravidel|0x10|
|Chyba při importu načtení sestavy|0x20|
|Výstupní chyba|0x40|
|Chyba přepínače příkazového řádku|0x80|
|Chyba inicializace|0x100|
|Chyba odkazů na sestavení|0x200|
|BuildBreakingMessage|0x400|
|Neznámá chyba|0x1000000|

Pro závažné chyby se vrátí **Chyba analýzy** . Indikuje, že se analýza nedala dokončit. V případě potřeby kód chyby také obsahuje původní příčinu závažné chyby. Následující podmínky generují závažné chyby:

- Analýzu nelze provést z důvodu nedostatečného vstupu.

- Analýza vyvolala výjimku, která není zpracována nástrojem FxCopCmd.

- Zadaný soubor projektu nebyl nalezen nebo je poškozen.

- Možnost Output nebyla zadána nebo soubor nelze zapsat.

> [!NOTE]
> Sestavení návratového kódu FxCopCmd **odkazuje na chybu** 0x200 samotným upozorněním, nikoli chybou. Tento návratový kód označuje, že chybí nepřímý odkaz, ale který FxCopCmd byl schopný je zpracovat. Upozornění znamená, že existuje možnost, že některé výsledky analýzy mohou být ohroženy. Považovat **chybu odkazů na sestavení** za chybu, pokud je kombinována s jakýmkoli jiným návratovým kódem.

## <a name="see-also"></a>Viz také:

- [Chyby aplikace Analýzy kódu](../code-quality/code-analysis-application-errors.md)
