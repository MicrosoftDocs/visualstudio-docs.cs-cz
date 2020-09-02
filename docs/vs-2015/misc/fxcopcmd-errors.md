---
title: FxCopCmd chyby | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
caps.latest.revision: 12
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3e0770654f564c57cf576666dcd9575f47d9ce1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64787284"
---
# <a name="fxcopcmd-errors"></a>Chyby jazyka FxCopCmd
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
  
 Pro závažné chyby se vrátí Chyba analýzy. Indikuje, že se analýza nedala dokončit. V případě potřeby kód chyby také obsahuje původní příčinu závažné chyby. Následující podmínky generují závažné chyby:  
  
- Analýzu nelze provést kvůli nedostatečnému vstupu.  
  
- Analýza vyvolala výjimku, která není zpracována nástrojem FxCopCmd.  
  
- Zadaný soubor projektu nebyl nalezen nebo je poškozen.  
  
- Možnost Output nebyla zadána nebo soubor nelze zapsat.  
  
    > [!NOTE]
    > FxCopCmd návratový kód "Chyba odkazů na sestavení" 0x200 sám o sobě upozornění, nikoli chybu. Tento návratový kód označuje, že nebyly nalezeny chybějící nepřímé odkazy, ale že FxCopCmd je dokázal je zpracovat. Je to upozornění, že existuje možnost, že některé výsledky analýzy mohou být ohroženy. Pokud je v kombinaci s jakýmkoli jiným návratovým kódem, vezměte v úvahu chybu "odkazy na sestavení" jako chybu.  
  
## <a name="see-also"></a>Viz také  
 [Chyby aplikace Analýzy kódu](../code-quality/code-analysis-application-errors.md)