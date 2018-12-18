---
title: Zobrazit vlákna ve okna paralelní zásobníky | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/20/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelstacks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: f50efb78-5206-4803-bb42-426ef8133f2f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0bf1ca8fabf70f2d4fbe5920803773af07db0a99
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389225"
---
# <a name="view-threads-and-tasks-in-the-parallel-stacks-window"></a>Zobrazit vlákna a úkoly v okna paralelní zásobníky

**Paralelní zásobníky** okna se hodí při ladění aplikací s více vlákny. Obsahuje několik zobrazení:

- [Zobrazit vlákna](#threads-view) ukazuje informace v zásobníku volání pro všechna vlákna v aplikaci. Můžete přecházet mezi vlákny a rámce zásobníku na tato vlákna. 

- [Úlohy zobrazení](#tasks-view) ukazuje informace v zásobníku volání úkolů na střed. 
  - Ve spravovaném kódu **úlohy** zobrazení ukazuje volání zásobníků s <xref:System.Threading.Tasks.Task?displayProperty=fullName> objekty. 
  - V nativním kódu **úlohy** zobrazení ukazuje volání zásobníků s [skupiny úloh](/cpp/parallel/concrt/task-parallelism-concurrency-runtime), [paralelní algoritmy](/cpp/parallel/concrt/parallel-algorithms), [asynchronních agentů](/cpp/parallel/concrt/asynchronous-agents)a [prostých úloh](/cpp/parallel/concrt/task-scheduler-concurrency-runtime).  
  
- [Zobrazení metody](#method-view) otáčí zásobník volání pro vybranou metodu. 

## <a name="use-the-parallel-stacks-window"></a>Použití okna Paralelní zásobníky 

Chcete-li otevřít **paralelní zásobníky** okno, musí být v relaci ladění. Vyberte **ladění** > **Windows** > **paralelní zásobníky**. 

### <a name="toolbar-controls"></a>Ovládací prvky panelu nástrojů

**Paralelní zásobníky** má následující ovládací prvky panelu nástrojů okno: 

![Panel nástrojů v okna paralelní zásobníky](../debugger/media/parallel_stackstoolbar.png "nástrojů paralelních zásobníků")  
  
|Ikona|Ovládací prvek|Popis|  
|-|-|-|  
|![Pole se seznamem vláken nebo úloh](media/parallel_toolbar1.png "vláken nebo úloh – pole se seznamem")|**Vlákna**/**úlohy** – pole se seznamem|Přepíná zobrazení mezi zásobníky vlákna volání a volání zásobníků s úkoly. Další informace najdete v tématu [úkoly zobrazení](#tasks-view) a [vlákna zobrazení](#threads-view).|  
|![Zobrazit pouze označená příznakem ikonu](media/parallel_toolbar2.png "ikona Zobrazit pouze označená příznakem")|Zobrazit pouze označená příznakem|Zásobníky volání zobrazí pouze pro vlákna, která jsou označena v dalších oknech ladicího programu, jako **vlákna GPU** okno a **paralelní sledování** okna.|  
|![Přepnout zobrazení metody ikonu](media/parallel_toolbar3.png "ikonu Přepnout zobrazení metody")|Přepnout **zobrazení metody**|Přepne mezi zobrazení zásobníku volání a **zobrazení metody**. Další informace najdete v tématu [zobrazení metody](#method-view).|  
|![Automatické posunování aktuální ikony](media/parallel_toolbar4.png "automaticky přejít na aktuální ikona")|Automaticky přejít na aktuální rámec zásobníku|Autoscrolls grafu tak, aby zásobníku aktuálního rámce se v zobrazení. Tato funkce je užitečná, když se změní aktuální rámec zásobníku mezi jinými nebo při dosažení Nová zarážka ve velkých grafů.|  
|![Ikona přiblížení přepnout](media/parallel_toolbar5.png "ikona přiblížení přepínací tlačítko")|Přepnout ovládání lupy|Zobrazí nebo skryje ovládací prvek lupy v levé části okna. <br /><br />Bez ohledu na to, zda se ovládací prvek lupy, můžete také zvětšit stisknutím kombinace kláves **Ctrl** a zapnutí kolečka myši, nebo pomocí klávesy **Ctrl**+**Shift** + **+** přiblížit a **Ctrl**+**Shift** + **-** Chcete-li horizonální oddálení. |  
  
### <a name="stack-frame-icons"></a>Ikony rámce zásobníku
Následující ikony obsahují informace o aktivní a aktuální zásobník snímků ve všech zobrazeních:

|Ikona|Popis|  
|-|-|  
|![Žlutá šipka](media/icon_parallelyellowarrow.gif)|Označuje aktuální umístění aktuální vlákno (aktivní blok zásobníku).|
|![Ikona vláken](media/icon_parallelthreads.gif)|Označuje aktuální umístění (aktivní blok zásobníku) mimo aktuální vlákno.|
|![Zelená šipka](media/icon_parallelgreenarrow.gif)|Označuje aktuální blok zásobníku (aktuální kontext ladicího programu). Název metody je tučný všude, kde se zobrazí.|  

### <a name="context-menu-items"></a>Položek kontextové nabídky  
Následující položky místní nabídky jsou k dispozici, když kliknete pravým tlačítkem myši na metodu v **vlákna** zobrazení nebo **úlohy** zobrazení. Posledních šest položek jsou stejné jako v [okno zásobníku volání](how-to-use-the-call-stack-window.md).  

![Místní nabídky okna paralelní zásobníky](../debugger/media/parallel_contmenu.png "nabídku okna paralelní zásobníky")  

|Položka nabídky|Popis|  
|-|-|  
|**Příznak**|Označí vybrané položky.|  
|**Odznačit**|Unflags vybranou položku.|  
|**zablokování**|Zablokuje vybranou položku.|  
|**Uvolnit**|Thaws vybranou položku.|  
|**Přepnout na rámec**|Stejné jako odpovídající nabídky v příkazu **zásobník volání** okna. V systému **paralelní zásobníky** okno, jedna metoda může být v několika rámců. Rámce, který chcete, můžete vybrat v podnabídce pro tuto položku. Pokud jeden z rámce zásobníku v aktuálním vláknu, rámec se vybere ve výchozím nastavení v podnabídce.|  
|**Přejděte na úlohu** nebo **přejít k vláknu**|Přepne do **úloh** nebo **vlákna** zobrazení a udržuje stejné zvýrazněnou rámce zásobníku.|  
|**Přejít ke zdrojovému kódu**|Přejde na příslušné místo v okně zdrojového kódu. |  
|**Přejít na zpětný překlad**|Přejde na příslušné místo v **zpětný překlad** okna.|  
|**Zobrazit externí kód**|Zobrazí nebo skryje externí kód.|  
|**Hexadecimální zobrazení**|Přepíná mezi desetinných míst a hexadecimální zobrazení.|  
|**Zobrazit vlákna ve zdroji**|Příznaky umístění vlákna v okně zdrojového kódu. |  
|**Informace o načítání symbolů**|Otevře **informace o načítání symbolů** dialogové okno.|  
|**Nastavení symbolů**|Otevře **nastavení symbolu** dialogové okno. |  
  
## <a name="threads-view"></a>zobrazení vláken  

V **vlákna** zobrazení zásobníku a jsou modře zvýrazněna volání Cesta aktuálního vlákna. Aktuální umístění vlákna se zobrazí žlutou šipkou. 

Chcete-li změnit aktuální rámec zásobníku, dvakrát klikněte na jinou metodu. To může být také přepnout aktuálního vlákna, v závislosti na tom, zda metoda, kterou jste vybrali je součástí aktuální vlákno nebo jiné vlákno. 

Když **vlákna** zobrazit graf je příliš velký a nevejde se do okna **pohled z ptačí perspektivy** ovládací prvek se zobrazí v okně. Posunout snímek v ovládacím prvku přejít na různé části grafu.  
  
Následující obrázek znázorňuje jedno vlákno, která přejde na spravovaný nativní kód přechod z hlavní. Šest vlákna jsou v aktuální metodě. Jeden nadále Thread.Sleep a jiné pokračuje na Console.WriteLine a potom na SyncTextWriter.WriteLine.  

 ![Zobrazení okna paralelní zásobníky vlákna](../debugger/media/parallel_stack1.png "vlákna zobrazení okna paralelní zásobníky")  

Následující tabulka popisuje hlavní funkce **vlákna** zobrazení:  
  
|Popisek|Název elementu|Popis|  
|-|-|-|  
|1|Segment zásobník volání nebo uzlu|Obsahuje řadu metod pro jedno nebo více vláken. Pokud snímek neobsahuje žádné řádky šipky k ní připojená, rámce zobrazuje cestu celý volání vlákno/vlákna.|  
|2|Modré zvýraznění|Označuje volání cestu aktuální vlákno.|  
|3|Šipka řádky|Připojte uzly k vytvoření volání celou cestu pro podprocesy.|  
|4|Záhlaví uzlu|Zobrazuje počet procesů a vláken pro uzel.|  
|5|Metoda|Představuje jeden nebo více rámců zásobníku v stejným způsobem.|  
|6|Popisek tlačítka na – metoda|Zobrazí se při najetí myší metodu. V **vlákna** zobrazení, popisek zobrazí všechny vlákna v tabulce podobně jako **vlákna** okna. |  

## <a name="tasks-view"></a>Zobrazení úloh  
Pokud vaše aplikace používá <xref:System.Threading.Tasks.Task?displayProperty=fullName> objekty (spravovaný kód) nebo `task_handle` objekty (nativní kód) vyjádřete paralelismus, můžete použít **úlohy** zobrazení. **Úlohy** zobrazení ukazuje volání zásobníků s úkoly místo vlákna. 

V **úlohy** zobrazení:  
  
- Zásobníky volání vláken, které nejsou spuštěné úkoly se nezobrazují.  
- Zásobníky volání vláken, na kterých běží úlohy jsou vizuálně oříznut v horní a dolní, zobrazíte relevantní snímky pro úlohy.  
- Pokud některé úlohy jsou v jednom vlákně, zásobníky volání těchto úkolů jsou uvedeny v samostatné uzly.  

Pokud chcete zobrazit celý zásobník volání, přepněte zpět do **vlákna** zobrazení tak, že kliknete pravým tlačítkem v bloku zásobníku a vyberete **přejít k vláknu**.  

Je vidět na následujícím obrázku **vlákna** zobrazení nahoře a odpovídající **úlohy** zobrazení v dolní části.  

![Zobrazení vláknech a úkolech](../debugger/media/parallel_threads-tasks.png "vláknech a úkolech zobrazení")  

Najeďte myší metodu pro zobrazení popisu tlačítka společně s dalšími informacemi. V **úlohy** zobrazení, popisek zobrazuje všechny úkoly v tabulce podobně jako **úlohy** okna. 

Následující obrázek ukazuje popisek pro metody v **vlákna** zobrazení v horní části a pro odpovídající **úlohy** zobrazení v dolní části.  

![Popisy tlačítek vláknech a úkolech](../debugger/media/parallel_threads-tasks-tooltips.png "vláknech a úkolech popisy tlačítek")  

## <a name="method-view"></a>Zobrazení metody  
Buď z **vlákna** zobrazení nebo **úlohy** zobrazení, můžete vytvořit kontingenční graf na aktuální metodu tak, že vyberete **přepnout zobrazení metody** ikonu na panelu nástrojů. **Zobrazení metody** ukazuje na první pohled všechny metody na všech vláknech, které volají nebo jsou volány aktuální metoda. Následující obrázek ukazuje, jak vypadá stejných informací **vlákna** zobrazení na levé straně a v **zobrazení metody** na pravé straně.  

![Vlákna a metoda zobrazením](../debugger/media/parallel_methodview.png "vlákna zobrazení a zobrazení metody")  
  
Pokud přejdete na nový rámec zásobníku, provedete tuto metodu metodu aktuální a **zobrazení metody** ukazuje všechny volající a volané pro nové metody. To může způsobit, že některá vlákna se zobrazí nebo zmizí ze zobrazení, v závislosti na tom, zda se zobrazí na svých zásobníků volání metody. Chcete-li vrátit do zobrazení zásobníku volání, vyberte **zobrazení metody** znovu ikonu na panelu nástrojů.  
  
## <a name="see-also"></a>Viz také:  
 [Začínáme s laděním vícevláknových aplikací](../debugger/get-started-debugging-multithreaded-apps.md)   
 [Návod: Ladění paralelní aplikace](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Základy ladicího programu](../debugger/getting-started-with-the-debugger.md)   
 [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)   
 [Paralelní programování](/dotnet/standard/parallel-programming/index)   
 [Použití okna úloh](../debugger/using-the-tasks-window.md)   
 [Třída úlohy](../extensibility/debugger/task-class-internal-members.md)
