---
title: 'Začínáme s PTVS: ladění | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 82803559-1d60-4c57-98fb-2dc1e0182b42
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: b636dd4f3a5c5265231898573bfdf52de2dff84e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197715"
---
# <a name="getting-started-with-ptvs-debugging"></a>Začínáme s PTVS: Ladění
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Interaktivní ladicí program sady Visual Studio usnadňuje diagnostiku a řešení problémů v kódu Pythonu.  
  
 Tyto pokyny můžete sledovat ve velmi krátkém [videu YouTube](https://www.youtube.com/watch?v=bO7wpzgy74A&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=4).  
  
 V předchozím tématu Začínáme vytvoříte prázdný projekt aplikace v Pythonu a do PythonApplication1.py zadáte následující kód:  
  
```python  
from math import sin, cos, radians  
import sys  
  
def make_dot_string(x):  
    return ' ' * int(10 * cos(radians(x)) + 10) + 'o'  
  
assert make_dot_string(90) == "          o"  
assert make_dot_string(180) == "o"  
  
def main():  
    for i in range(10000000):  
        s = make_dot_string(i)  
        print(s)  
  
if __name__ == "__main__":  
    sys.exit(int(main() or 0))  
```  
  
 Normálně při práci s kódem v aplikaci Visual Studio spustíte kód stisknutím klávesy F5.  Tento příkaz sestaví všechny části projektu, které je třeba sestavit, a spustí kód v ladicím programu.  Stisknutím kombinace kláves CTRL + F5 můžete sestavit a spustit kód bez ladicího programu.  V ladicím programu váš kód běží trochu pomaleji, ale pro tyto náklady získáte skvělé funkce ladění.  
  
 Jiný způsob, jak spustit kód, je pomocí příkazu Step in (normálně vázaný na F11).  Funguje jako F5, ale pozastaví provádění u každého příkazu.  Pokud chcete ukončit program v určitém bodě, můžete stisknout levý ukazatel na levém okraji editoru kódu pro nastavení zarážky.  Po stisknutí klávesy F5 dojde k přerušení nebo zastavení běhu programu na řádku se zarážkou.  V nabídce ladění je více možností pro krokování; například Krokovat s voláním funkce (F10), Krokovat s voláním funkce (F11) nebo přeskočit na konci funkce (Shift-F11).  
  
 V ladicím programu můžete provádět více, v případě poškození.  Okno místní hodnoty zobrazuje aktuální hodnoty místních proměnných.  Při kroku kódu se místní zobrazení automaticky aktualizují.  Okno Automatické hodnoty, které zobrazuje proměnné poblíž aktuálního řádku, kde bylo provádění ukončeno.  V okno Kukátko můžete zadat libovolný výraz Pythonu, který ladicí program automaticky aktualizuje pokaždé, když se spuštění spustí.  Můžete také umístit ukazatel myši na proměnné v oknech editoru, aby se zobrazilo místní zobrazení hodnot proměnné, a tento zobrazený Tip dat vám umožní zkontrolovat objekty.  Některé typy dat mají speciální vizualizace, které jsou přístupné ze zobrazení tipů k datům (například řetězce se speciálním formátováním, jako je HTML, XML nebo JSON).  
  
 Okno zásobník volání zobrazuje volání probíhajících funkcí, které vedlo k aktuálnímu příkazu, ve kterém je ladicí program zastaven.  Můžete zvolit různé rámce zásobníku (řádky v zásobníku volání) k přechodu na místo, kde bude pokračovat v provádění každé funkce, vyhledat hodnoty proměnných a tak dále.  
  
 Tyto pokyny můžete sledovat ve velmi krátkém [videu YouTube](https://www.youtube.com/watch?v=bO7wpzgy74A&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=4).  
  
## <a name="see-also"></a>Viz také  
 [Dokumentace k wikiwebu](https://github.com/Microsoft/PTVS/wiki/Debugging)   
 [PTVS Začínáme a rozsáhlá podrobně videa](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
