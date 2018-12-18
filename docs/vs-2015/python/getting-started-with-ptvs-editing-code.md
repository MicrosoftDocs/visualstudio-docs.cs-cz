---
title: 'Začínáme s PTVS: úpravy kódu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b412c87c-2f09-4e25-9cc8-ab54f4c44412
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: ef0a84523a2d828e696fb50f641f392ab7bbd39f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49265782"
---
# <a name="getting-started-with-ptvs-editing-code"></a>Začínáme s PTVS: Úpravy kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

PTVS poskytuje produktivní prostředí editoru sady Visual Studio pro jazyk Python.  
  
 Můžete sledovat tyto pokyny ve velmi krátké [videa youtube](https://www.youtube.com/watch?v=uZGZNEyyeKs&index=3&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff).  
  
 Začněte s základní prázdná šablona projektu aplikace v Pythonu.  
  
 Začněte psát `from … import` řádek v editoru.  Zobrazí se že seznam rozbalovací dokončení obsahuje úplný seznam modulů, které jsou k dispozici pro import.  Tento seznam se liší v závislosti na vaší verzi Pythonu, co jste nainstalovali knihovny.  Knihovny math slouží jako příklad.  Můžete si všimnout, že při psaní seznam filtrů dokončování těchto položek, včetně znaků jste zadali.  Dokončení příkazu importováním `sin` identifikátor.  
  
```python  
from math import sin  
  
```  
  
 Při psaní kódu, pokud použijete identifikátor, který není vázaný, ale, který najdete ve vašich knihovnách, PTVS nabízí místní rychlé opravy pro přidání odpovídající příkaz import, které potřebujete.  Například, pokud jste zadali `cos`, pak byste viděli **importovat z matematické** nabízí.  
  
 Fragment kódu můžete použít ke generování kódu.  V části nabídky Úpravy zvolte technologie IntelliSense a potom vložit fragment kódu.  Teď zvolte Pythonu a potom def.  Volání funkce `make_dot_string` a přidejte jeden parametr `x`.  Do souboru pro vývoj řízených testů můžete přidat kontrolní výrazy a uvidíte, že už PTVS může nabídnout nové funkce do seznamů dokončení.  
  
```python  
assert make_dot_string(90) == '          o'  
assert make_dot_string(180) == 'o'  
  
```  
  
 Nyní přejděte zpět na tuto novou funkci a začít zápis následující text:  
  
```python  
return " " * int(10 * cos(radians(x)) + 10) + "o"  
  
```  
  
 Uvidíte, že PTVS předpokládá, že parametr je celé číslo, protože PTVS je analyzován lokalit volání této funkce.   Budete také muset použít rychlé opravy pro import `radians`.  
  
 Pomocí jiného fragmentu kódu vytvořte hlavní blok zadáním `main` na nejvyšší úrovně, vyvolání inteligentní značky uživatelského rozhraní pomocí tabulátoru zvolit "def hlavní..."  Napsat smyčku základní volání `make_dot_string`.  Uvidíte, že PTVS ví, že funkce vrátí řetězec podle Pokud stisknete období a najdete v článku nabízené dokončování.  Informace o tomto typu se budou přenášet v rámci celého programu, tak bez ohledu na svoje hodnoty ukládaly, můžeme poskytnout popisy tlačítek a dokončování, které vám pomůže lépe pochopit a psát kód.  
  
 Přidejte volání pro tisk a měli byste mít hlavní podobný následujícímu:  
  
```python  
def main ():  
    for i in range(10000000):  
        s = make_dot_string(i)  
        print(s)  
```  
  
 Pokud stisknete klávesu F5, spustí kód v okně cmd.exe a zobrazí tečku oscilační vpřed a zpět.  
  
 Můžete sledovat tyto pokyny ve velmi krátké [videa youtube](https://www.youtube.com/watch?v=uZGZNEyyeKs&index=3&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff).  
  
## <a name="see-also"></a>Viz také  
 [Dokumentace ke službě Wiki](https://github.com/Microsoft/PTVS/wiki/Editor-Features)   
 [Videa můžete začít a Deep Dive PTVS](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)

