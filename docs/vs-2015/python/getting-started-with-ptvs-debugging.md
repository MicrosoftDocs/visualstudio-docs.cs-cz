---
title: 'Začínáme s PTVS: ladění | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82803559-1d60-4c57-98fb-2dc1e0182b42
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 8a92eb3779abf5be00f39bd4aa3e66238a729ded
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49204922"
---
# <a name="getting-started-with-ptvs-debugging"></a>Začínáme s PTVS: Ladění
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Interaktivní ladicího programu sady Visual Studio umožňuje snadno diagnostikovat a vyřešit problémy v kódu Pythonu.  
  
 Můžete sledovat tyto pokyny ve velmi krátké [videa youtube](https://www.youtube.com/watch?v=bO7wpzgy74A&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=4).  
  
 V předchozím úvodním tématu Začínáme vytvořte prázdný projekt aplikace v Pythonu a zadat následující kód do PythonApplication1.py:  
  
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
  
 Za normálních okolností při práci na kódu v sadě Visual Studio, budete začnete spouštění kódu stisknutím klávesy F5.  Tento příkaz vytvoří všechny části vašeho projektu, které potřebujete k sestavení a spuštění kódu v ladicím programu.  Můžete stisknutím Ctrl + F5 sestavte a spusťte váš kód bez ladicího programu.  Pomocí ladicího programu váš kód spustí o něco pomaleji, ale získání skvělé možnosti ladění pro náklady.  
  
 Dalším způsobem, jak spustit kód je příkazem Krok dovnitř (obvykle vázán na F11).  Je třeba F5, ale pozastaví provádění na každý příkaz.  Pokud chcete přerušit program v určitém bodě, můžete stisknutím tlačítka vlevo ukazatel do levého okraje editoru kódu pro nastavení zarážky.  Po stisknutí klávesy F5, vykonávání programu bude přerušení nebo ukončení řádku se zarážkou.  V nabídce ladění má více možností pro krokování; například krok přes volání funkcí (F10), krokování s vnořením do volání funkcí (F11), nebo přeskočit na konci – funkce (shift-F11).  
  
 Existuje více, které vám pomůžou při analýze v ladicím programu.  V okně místních hodnot zobrazuje aktuální hodnoty pro lokální proměnné.  Jak krokování kódu automaticky aktualizuje zobrazení místních hodnot.  Okně Automatické hodnoty, který zobrazuje proměnné v aktuálním řádku kde provádění zastaveno.  V okně kukátka můžete zadat libovolný výraz Pythonu, který ladicí program automaticky aktualizuje každý čas provádění zastaví.  Můžete také umístění ukazatele myši proměnné v oknech editoru zobrazíte rozbalovací zobrazení hodnoty proměnné a zobrazení dat tip umožňuje kontrolu do objektů.  Některé typy dat mají zvláštní vizualizátory, které jsou přístupné ze zobrazení datového tipu (například řetězce s zvláštní formátování, jako jsou HTML, XML nebo JSON).  
  
 V okně zásobník volání se zobrazí čekající volání, které vedly k aktuálnímu příkazu, kde je zastavený ladicím programu.  Jiný zásobník snímků (řádky v zásobníku volání) můžete přeskočit, pokud kód bude pokračovat v provádění v každé funkci, hodnoty proměnných, a tak dále.  
  
 Můžete sledovat tyto pokyny ve velmi krátké [videa youtube](https://www.youtube.com/watch?v=bO7wpzgy74A&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=4).  
  
## <a name="see-also"></a>Viz také  
 [Dokumentace ke službě Wiki](https://github.com/Microsoft/PTVS/wiki/Debugging)   
 [Videa můžete začít a Deep Dive PTVS](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)

