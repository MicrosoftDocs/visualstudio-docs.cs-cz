---
title: FxCopCmd – chyby
ms.date: 10/19/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
ms.author: gewarren
author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 657e650f9244fb97d4990e04a60b9e1f93794af4
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31924258"
---
# <a name="fxcopcmd-tool-errors"></a>Chyby jazyka FxCopCmd nástroj

Fxcopcmd – nebere v úvahu všechny chyby jako kritické. Pokud jazyka FxCopCmd má dostatečné informace k provedení částečné analýzy, provede analýzu a sestavy chybách, ke kterým došlo k chybě. Kód chyby, která je 32bitové celé číslo, obsahuje bitovou kombinaci číselných hodnot, které odpovídají chyby.

Následující tabulka popisuje kódů chyb vrácených nástrojem jazyka FxCopCmd:

|Chyba|Číselná hodnota|
|-----------|-------------------|
|Žádné chyby|0x0|
|Chyba analýzy|0x1|
|Pravidlo výjimky|0x2|
|Chyba načtení projektu|0x4|
|Chyba načtení sestavení|0x8|
|Chyba načtení knihovny pravidlo|0x10|
|Chyba při importu sestavy zatížení|0x20|
|Chyby výstupu|0x40|
|Chyba přepínače příkazového řádku|0x80|
|Chyba inicializace|0x100|
|Chyba odkazy na sestavení|0x200|
|BuildBreakingMessage|0x400|
|Neznámá chyba|0x1000000|

**Chyba analýzy** vrátí k závažným chybám. Označuje, že analýza nelze dokončit. V případě potřeby obsahuje kód chyby taky základní příčinu této závažné chyby. Tyto podmínky generovat závažné chyby:

- Analýzy nelze provést z důvodu nedostatečných vstup.

- Analýza došlo k výjimce, který není zpracováván jazyka FxCopCmd.

- Soubor zadaného projektu nebyl nalezen nebo je poškozen.

- Nebyla zadána možnost output nebo soubor nelze zapsat.

> [!NOTE]
> Jazyka FxCopCmd návratový kód **sestavení odkazuje na chyby** 0x200 sám o sobě je upozornění, nikoli k chybě. Tento návratový kód označuje, která existuje chybí nepřímé odkazy, ale, že fxcopcmd – bylo možné zpracovat je. Upozornění znamená, že je možné, že některé výsledky analýzy může mít dojde k narušení bezpečnosti. Považovat **sestavení odkazuje na chyby** jako chybu při kombinaci s jakýkoli návratový kód.

## <a name="see-also"></a>Viz také

- [Chyby aplikace Analýzy kódu](../code-quality/code-analysis-application-errors.md)