---
title: 'Začínáme s PTVS: Interactive Python | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: fa594314-bdd0-4da5-874a-57b03414b675
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 4fba8bf658a50a7a7e28abace1eb622ab14f5f26
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62550984"
---
# <a name="getting-started-with-ptvs-interactive-python"></a>Začínáme s PTVS: Interaktivní Python
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Interaktivní výzvy nebo čtení a vyhodnocení – tisk smyček (REPLs) jsou klíčovým nástrojem pro produktivní programovací jazyky.  Umožňují spouštět fragmenty kódu pro zjišťování a učení rozhraní API, experimentovat s používáním rozhraní API a interaktivně vyvíjet pracovní kód pro zahrnutí do projektů nebo programů.  
  
 Tyto pokyny můžete sledovat ve velmi krátkém [videu YouTube](https://www.youtube.com/watch?v=yc2CROtTsC0&index=5&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff).  
  
 V okně prostředí Pythonu se zobrazí seznam všech prostředí Pythonu.  Pro otevření interaktivního okna nebo REPL můžete vybrat kterýkoli z nich.  Pokud jste někdy spouštěli Python.exe na příkazovém řádku, dříve jste si REPL Pythonu.  REPL vás vyzve k zadání kódu, stisknutí klávesy ENTER a okamžitému zobrazení výsledků kódu.  Toto je živý kontext spuštění, který zahrnuje všechny stavy všech provedení, přiřazení proměnných atd.  Můžete odkazovat na proměnné s výsledky v pozdějších odesláních na výzvu REPL.  Můžete napsat více řádků kódu a spustit je všechny najednou (například deklarace metody nebo vícenásobné příkazy).  
  
 Když začnete používat novou knihovnu, REPL je skvělým způsobem, jak si tuto knihovnu vyzkoušet.  Knihovnu můžete importovat, zkontrolovat dílčí balíčky, třídy a funkce.  Python vám může sdělit všechny tyto informace prostřednictvím své `help()` funkce.  Kromě toho Python Tools for Visual Studio (PTVS) poskytuje návrhy a dokumentaci na základě modelování kódu používaného v editoru, který je bez nutnosti spustit knihovnu.  Při spouštění kódu PTVS používá informace z modulu runtime Pythonu pro zlepšení návrhů PTVS.  
  
 Interaktivní okno je také užitečné pro iterativní nebo Evolutionary vývoj kódu, včetně testování kódu při jeho vývoji.  V okně editoru můžete vybrat funkci, stisknout pravé tlačítko ukazatel a vybrat odeslat do interaktivního.  Tento příkaz zkopíruje výběr do interaktivního okna jako další vstup a provede ho.  Výsledky se okamžitě zobrazí.  Pokud potřebujete provést změny v předchozím vstupu, můžete stisknutím klávesy šipka nahoru získat zpět kód, upravit ho a stisknutím kombinace kláves CTRL + ENTER kód spustit.  Stisknutí klávesy ENTER na konci vstupu ho spustí, ale stisknutím klávesy ENTER uprostřed vstupu vložíte nový řádek.  
  
 Můžete otevřít interaktivní okno pro každou instalaci Pythonu, kolik chcete.  V horní části okna jsou tlačítka pro vymazání zobrazení, resetování kontextu spuštění atd.  Historie zůstane beze změny.  
  
 Tyto pokyny můžete sledovat ve velmi krátkém [videu YouTube](https://www.youtube.com/watch?v=yc2CROtTsC0&index=5&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff).  
  
## <a name="see-also"></a>Viz také  
 [Dokumentace k wikiwebu](https://github.com/Microsoft/PTVS/wiki/Interactive-REPL)   
 [PTVS Začínáme a rozsáhlá podrobně videa](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
