---
title: Zobrazit vlákna v okně paralelní zásobníky | Microsoft Docs
ms.date: 11/20/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9728346bc4c6d805bb0febd3a0d5bef0ed809a5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62902292"
---
# <a name="view-threads-and-tasks-in-the-parallel-stacks-window-c-visual-basic-c"></a>Zobrazení vláken a úloh v okně paralelní zásobníky (C#, Visual Basic, C++)

Okno **paralelní zásobníky** je užitečné pro ladění aplikací s více vlákny. Má několik zobrazení:

- [Zobrazení vlákna](#threads-view) zobrazuje informace zásobníku volání pro všechna vlákna v aplikaci. V těchto vláknech můžete přecházet mezi vlákny a bloky zásobníku.

- [Zobrazení úlohy](#tasks-view) ukazuje informace o zásobníku volání na základě úloh.
  - Ve spravovaném kódu zobrazuje zobrazení **úloh** zásobníky volání <xref:System.Threading.Tasks.Task?displayProperty=fullName> objektů.
  - V nativním kódu zobrazuje zobrazení **úloh** balíčky volání [skupin úloh](/cpp/parallel/concrt/task-parallelism-concurrency-runtime), [paralelní algoritmy](/cpp/parallel/concrt/parallel-algorithms), [Asynchronní agenty](/cpp/parallel/concrt/asynchronous-agents)a [jednoduché úlohy](/cpp/parallel/concrt/task-scheduler-concurrency-runtime).

- [Zobrazení metody](#method-view) pivote zásobník volání na vybrané metodě.

## <a name="use-the-parallel-stacks-window"></a>Použití okna Paralelní zásobníky

Chcete-li otevřít okno **paralelní zásobníky** , musíte být v relaci ladění. Vyberte **ladit**  >  **Windows**  >  **paralelní zásobníky**Windows.

### <a name="toolbar-controls"></a>Ovládací prvky panelu nástrojů

Okno **paralelní zásobníky** má následující ovládací prvky panelu nástrojů:

![Panel nástrojů v okně paralelní zásobníky](../debugger/media/parallel_stackstoolbar.png "Panel nástrojů paralelní zásobníky")

|Ikona|Řízení|Popis|
|-|-|-|
|![Pole se seznamem vláken/úloh](media/parallel_toolbar1.png "Pole se seznamem vláken/úloh")|**Vlákna** / Pole se seznamem **úloh**|Přepíná zobrazení mezi zásobníky volání vláken a zásobníků volání úkolů. Další informace najdete v tématu [zobrazení úkolů](#tasks-view) a [zobrazení vláken](#threads-view).|
|![Zobrazit pouze ikonu s příznakem](media/parallel_toolbar2.png "Zobrazit pouze ikonu s příznakem")|Zobrazit pouze označené příznakem|Zobrazuje zásobníky volání pouze pro vlákna, která jsou označena v jiných oknech ladicího programu, například okno **vlákna GPU** a okno **paralelní kukátko** .|
|![Přepnout ikonu zobrazení metody](media/parallel_toolbar3.png "Přepnout ikonu zobrazení metody")|Přepnout **zobrazení metody**|Přepíná mezi zobrazeními zásobníku volání a **zobrazením metody**. Další informace naleznete v tématu [zobrazení metod](#method-view).|
|![Automaticky přejít na aktuální ikonu](media/parallel_toolbar4.png "Automaticky přejít na aktuální ikonu")|Automaticky přejít na aktuální rámec zásobníku|Automaticky posune graf tak, aby byl aktuální rámec zásobníku zobrazen. Tato funkce je užitečná v případě, že změníte aktuální rámec zásobníku z jiných oken nebo když ve velkém grafu narazíte na novou zarážku.|
|![Přepnout ikonu lupy](media/parallel_toolbar5.png "Přepnout ikonu lupy")|Přepnout ovládací prvek Lupa|Zobrazí nebo skryje ovládací prvek zvětšení v levé části okna. <br /><br />Bez ohledu na viditelnost ovládacího prvku Lupa můžete také zvětšit zobrazením klávesy **CTRL** a zapnutím kolečka myši nebo stisknutím **kombinace kláves CTRL** + **SHIFT** , + **+** **Ctrl** + **Shift** + **-** abyste se přiblížili. |

### <a name="stack-frame-icons"></a>Ikony rámce zásobníku
Následující ikony obsahují informace o aktivním a aktuálním snímku zásobníku ve všech zobrazeních:

|Ikona|Popis|
|-|-|
|![Žlutá šipka](media/icon_parallelyellowarrow.gif)|Označuje aktuální umístění (aktivní rámec zásobníku) aktuálního vlákna.|
|![Ikona vláken](media/icon_parallelthreads.gif)|Označuje aktuální umístění (aktivní rámec zásobníku) neaktuálního vlákna.|
|![Zelená šipka](media/icon_parallelgreenarrow.gif)|Označuje aktuální rámec zásobníku (aktuální kontext ladicího programu). Název metody je tučný bez ohledu na to, kde se vyskytuje.|

### <a name="context-menu-items"></a>Položky místní nabídky
Následující položky místní nabídky jsou k dispozici, když kliknete pravým tlačítkem myši na metodu v zobrazení **vlákna** nebo zobrazení **úkolů** . Posledních šest položek je stejný jako v [okně zásobník volání](how-to-use-the-call-stack-window.md).

![Místní nabídka v okně paralelní zásobníky](../debugger/media/parallel_contmenu.png "Místní nabídka v okně paralelní zásobníky")

|Položka nabídky|Popis|
|-|-|
|**Příznak**|Označí vybranou položku jako příznak.|
|**Odznačit**|Odoznačí vybranou položku.|
|**Uvolnění**|Zablokuje vybranou položku.|
|**Uvolnění**|Rozmrazí vybranou položku.|
|**Přepnout na rámec**|Stejné jako v odpovídajícím příkazu nabídky v okně **zásobník volání** . V okně **paralelní zásobníky** však může být jedna metoda v několika snímcích. V podnabídce této položky můžete vybrat rámec, který chcete. Je-li jeden z rámců zásobníku v aktuálním vlákně, je tento rámec vybrán ve výchozím nastavení v podnabídce.|
|**Přejít na úlohu** nebo **Přejít do vlákna**|Přepne na zobrazení **úkolu** nebo **vlákna** a zachová stejný rámec zásobníku.|
|**Přejít ke zdrojovému kódu**|Přejde do odpovídajícího umístění v okně zdrojového kódu. |
|**Přejít na zpětný překlad**|Přejde do odpovídajícího umístění v okně **zpětný překlad** .|
|**Zobrazit externí kód**|Zobrazí nebo skryje externí kód.|
|**Hexadecimální zobrazení**|Přepíná mezi zobrazením typu Decimal a hexadecimální.|
|**Zobrazit vlákna ve zdroji**|Označí umístění vlákna v okně zdrojového kódu. |
|**Informace o načítání symbolů**|Otevře dialogové okno **informace o načtení symbolu** .|
|**Nastavení symbolu**|Otevře dialogové okno **Nastavení symbolu** . |

## <a name="threads-view"></a>zobrazení vláken

V zobrazení **vláken** je zvýrazněný rámec zásobníku a cesta volání aktuálního vlákna. Aktuální umístění vlákna je zobrazené žlutou šipkou.

Chcete-li změnit aktuální rámec zásobníku, dvakrát klikněte na jinou metodu. To může také přepínat aktuální vlákno v závislosti na tom, zda je metoda, kterou vyberete, součástí aktuálního vlákna nebo jiného vlákna.

Když je graf zobrazení **vláken** moc velký, aby se vešel do okna, zobrazí se v okně Ovládací prvek **zobrazení očí v pohledech** . Můžete přesunout rámec v ovládacím prvku a přejít tak na různé části grafu.

Následující ilustrace znázorňuje jedno vlákno, které přechází z hlavního na přechod nativního kódu do spravovaného. V aktuální metodě jsou šest vláken. Druhý pokračuje do vlákna. Sleep a další pokračuje do Console. WriteLine a pak na SyncTextWriter. WriteLine.

 ![Zobrazení vláken v okně paralelní zásobníky](../debugger/media/parallel_stack1.png "Zobrazení vláken v okně paralelní zásobníky")

Následující tabulka popisuje hlavní funkce zobrazení **vlákna** :

|Popisek|Název elementu|Popis|
|-|-|-|
|1|Segment zásobníku volání nebo uzel|Obsahuje řadu metod pro jedno nebo více vláken. Pokud k rámečku nejsou připojeny žádné čáry šipek, je v tomto snímku uvedena celá cesta volání pro vlákna.|
|2|Modrá zvýraznění|Označuje cestu volání aktuálního vlákna.|
|3|Šipky – čáry|Uzly připojte, chcete-li vytvořit úplnou cestu volání pro vlákna.|
|4|Záhlaví uzlu|Zobrazuje počet procesů a vláken pro uzel.|
|5|Metoda|Reprezentuje jeden nebo více rámců zásobníku ve stejné metodě.|
|6|Popis metody v metodě|Zobrazí se při najetí myší na metodu. V zobrazení **vlákna** zobrazuje popisek všechna vlákna v tabulce podobné oknu **vlákna** . |

## <a name="tasks-view"></a>Zobrazení úloh
Pokud vaše aplikace používá <xref:System.Threading.Tasks.Task?displayProperty=fullName> objekty (spravovaný kód) nebo `task_handle` objekty (nativní kód) k vyjádření paralelismu, můžete použít zobrazení **úkolů** . Zobrazení **úlohy** zobrazuje zásobníky volání úkolů místo vláken.

V zobrazení **úlohy** :

- Nezobrazuje se zásobníky volání vláken, která neběží v úlohách.
- Zásobníky volání vláken, která běží na úlohách, se vizuálně oříznou v horní a dolní části, aby se zobrazily relevantní rámce pro úlohy.
- V případě, že je několik úloh v jednom vlákně, jsou zásobníky volání těchto úloh zobrazeny v samostatných uzlech.

Chcete-li zobrazit celý zásobník volání, přepněte zpět do zobrazení **vlákna** kliknutím pravým tlačítkem na rámec zásobníku a výběrem možnosti **Přejít ke vláknu**.

Následující ilustrace znázorňuje zobrazení **vláken** v horní části a odpovídající zobrazení **úkolů** v dolní části.

![Zobrazení vlákna a úloh](../debugger/media/parallel_threads-tasks.png "Zobrazení vlákna a úloh")

Když najedete myší na metodu, zobrazí se popis s dalšími informacemi. V zobrazení **úlohy** se v popisu zobrazí všechny úkoly v tabulce podobné oknu **úlohy** .

Následující obrázek ukazuje popis metody v zobrazení **vláken** v horní části a pro odpovídající zobrazení **úkolů** v dolní části.

![Popisy vláken a úloh](../debugger/media/parallel_threads-tasks-tooltips.png "Popisy vláken a úloh")

## <a name="method-view"></a>Zobrazení metody
V zobrazení **vlákna** nebo zobrazení **úkolů** můžete graf na aktuální metodě pivotovat tak, že na panelu nástrojů vyberete ikonu **zobrazení přepínací metody** . **Zobrazení metody** ukazuje na první pohled na všechny metody ve všech vláknech, které buď volají nebo jsou volány aktuální metodou. Následující obrázek ukazuje, jak se v zobrazení **vlákna** na levé straně a v **zobrazení metody** na pravé straně zobrazují stejné informace.

![Zobrazení vláken a zobrazení metod](../debugger/media/parallel_methodview.png "Zobrazení vláken a zobrazení metod")

Pokud přepnete na nový rámec zásobníku, provedete tuto metodu aktuální metodou a **zobrazení metody** zobrazí všechny volající a volané pro novou metodu. To může způsobit, že se některá vlákna objeví nebo zmizí ze zobrazení v závislosti na tom, jestli se tato metoda objeví na svých zásobníkech volání. Chcete-li se vrátit do zobrazení zásobníku volání, vyberte ikonu panelu nástrojů **zobrazení metody** znovu.

## <a name="see-also"></a>Viz také
- [Začínáme s laděním vícevláknové aplikace](../debugger/get-started-debugging-multithreaded-apps.md)
- [Návod: Ladění paralelní aplikace](../debugger/walkthrough-debugging-a-parallel-application.md)
- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
- [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)
- [Paralelní programování](/dotnet/standard/parallel-programming/index)
- [Použití okna úloh](../debugger/using-the-tasks-window.md)
- [Task – třída](../extensibility/debugger/task-class-internal-members.md)
