---
title: 'Začínáme s PTVS: Úprava kódu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: b412c87c-2f09-4e25-9cc8-ab54f4c44412
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 2e883970b4b265b1864d53ef6e1f347160e5aeb9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62550909"
---
# <a name="getting-started-with-ptvs-editing-code"></a>Začínáme s PTVS: Úpravy kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

PTVS poskytuje produktivní prostředí editoru Visual studia pro Python.  
  
 Tyto pokyny můžete sledovat ve velmi krátkém [videu YouTube](https://www.youtube.com/watch?v=uZGZNEyyeKs&index=3&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff).  
  
 Začněte se základní šablonou projektu aplikace Python.  
  
 Začněte psát `from … import` řádek v editoru.  Zobrazí se seznam dokončených oken s úplným seznamem modulů, které jsou k dispozici pro import.  Tento seznam se liší podle vaší verze Pythonu a těch knihoven, které jste nainstalovali.  Použijte jako příklad knihovnu Math.  Všimněte si, že když zadáte seznam doplňování pro tyto položky, včetně znaků, které jste zadali.  Dokončete příkaz importováním `sin` identifikátoru.  
  
```python  
from math import sin  
  
```  
  
 Při kódování, pokud použijete identifikátor, který je nevázaný, ale který lze najít ve vašich knihovnách, PTVS nabízí místní rychlou opravu pro přidání příslušného příkazu pro import, který potřebujete.  Pokud jste například zadali `cos` , pak byste viděli **Import ze matematického** nabízení.  
  
 K vygenerování kódu můžete použít fragment kódu.  V nabídce Upravit zvolte IntelliSense a pak vložit fragment.  Nyní zvolte Python a pak na def.  Zavolejte funkci `make_dot_string` a přidejte jeden parametr `x` .  Nyní můžete přidat kontrolní výrazy do souboru pro vývoj řízený testováním a vidíte, že PTVS již může nabízet novou funkci v seznamech pro doplňování.  
  
```python  
assert make_dot_string(90) == '          o'  
assert make_dot_string(180) == 'o'  
  
```  
  
 Nyní se vraťte k nové funkci a začněte psát následující text:  
  
```python  
return " " * int(10 * cos(radians(x)) + 10) + "o"  
  
```  
  
 Vidíte, že PTVS předpokládá, že parametr je celé číslo, protože PTVS analyzoval weby volání do této funkce.   K importu budete taky muset použít rychlou opravu `radians` .  
  
 Pomocí jiného fragmentu kódu vytvořte hlavní blok zadáním `main` na nejvyšší úrovni, vyvoláním uživatelského rozhraní inteligentních značek a pomocí karty vyberte možnost "def Main...".  Napište smyčku Basic pro volání `make_dot_string` .  Vidíte, že PTVS ví, že funkce vrátí řetězec, když stisknete tečku a zobrazí se nabídka dokončení.  Tyto informace o typu budou v celém programu předávány, takže všude, kde končí vaše hodnoty, můžeme poskytnout popisy a doplňování, které vám pomohou lépe pochopit a napsat kód.  
  
 Přidejte volání pro tisk a měli byste mít hlavní podobnou následující:  
  
```python  
def main ():  
    for i in range(10000000):  
        s = make_dot_string(i)  
        print(s)  
```  
  
 Když stisknete klávesu F5, kód se spustí v cmd.exe okně a zobrazí se kolísání tečky zpátky.  
  
 Tyto pokyny můžete sledovat ve velmi krátkém [videu YouTube](https://www.youtube.com/watch?v=uZGZNEyyeKs&index=3&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff).  
  
## <a name="see-also"></a>Viz také  
 [Dokumentace k wikiwebu](https://github.com/Microsoft/PTVS/wiki/Editor-Features)   
 [PTVS Začínáme a rozsáhlá podrobně videa](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
