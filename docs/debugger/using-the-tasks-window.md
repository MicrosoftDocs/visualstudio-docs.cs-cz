---
title: Použití okna úlohy | Microsoft Docs
ms.date: 03/18/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.paralleltasks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: bd5e0612-a0dc-41cf-a7af-1e87d0d5c35f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b32dc6372a6ce4983e9bd11e05a4a662d0ad44ba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62901578"
---
# <a name="using-the-tasks-window-c-visual-basic-c"></a>Použití okna úlohy (C#, Visual Basic, C++)

Okno **úlohy** se podobá oknu **vlákna** , s tím rozdílem, že zobrazuje informace o <xref:System.Threading.Tasks.Task?displayProperty=fullName> objektech, [task_handle](/cpp/parallel/concrt/reference/task-group-class)nebo [WinJS. promise](/previous-versions/windows/apps/br211867(v=win.10)) místo každého vlákna. Podobně jako vlákna, úlohy reprezentují asynchronní operace, které mohou běžet souběžně; ve stejném vlákně ale může běžet víc úloh.

Ve spravovaném kódu můžete použít okno **úlohy** při práci s <xref:System.Threading.Tasks.Task?displayProperty=fullName> objekty nebo s klíčovým slovem **await** a **Async** (**await** a **Async** v VisualBasic). Další informace o úlohách ve spravovaném kódu naleznete v tématu  [paralelní programování](/dotnet/standard/parallel-programming/index).

V nativním kódu můžete použít okno **úlohy** při práci se [skupinami úloh](/cpp/parallel/concrt/task-parallelism-concurrency-runtime), [paralelními algoritmy](/cpp/parallel/concrt/parallel-algorithms), [asynchronními agenty](/cpp/parallel/concrt/asynchronous-agents)a [jednoduchými úlohami](/cpp/parallel/concrt/task-scheduler-concurrency-runtime). Další informace o úlohách v nativním kódu naleznete v tématu [Concurrency Runtime](/cpp/parallel/concrt/concurrency-runtime).

V jazyce JavaScript můžete použít okno úlohy, když pracujete s `.then` kódem příslib. Další informace najdete [v tématu asynchronní programování v JavaScriptu (aplikace pro UWP)](/previous-versions/windows/apps/hh700330(v=win.10)) .

Můžete použít okno **úlohy** při každém přerušení do ladicího programu. K němu máte přístup v nabídce **ladění** kliknutím na **Windows** a potom kliknutím na **úlohy**. Následující obrázek znázorňuje okno **úlohy** ve výchozím režimu.

![Okno úlohy](../debugger/media/parallel_tasks_window.png "Parallel_Tasks_Window")

> [!NOTE]
> Ve spravovaném kódu, <xref:System.Threading.Tasks.Task> který má stav [stav úkolu. Created](<xref:System.Threading.Tasks.TaskStatus.Created>), [stav úkolu. WaitingForActivation](<xref:System.Threading.Tasks.TaskStatus.WaitingForActivation>)nebo [stav úkolu. WaitingToRun](<xref:System.Threading.Tasks.TaskStatus.WaitingToRun>) se nemusí zobrazit v okně **úlohy** , pokud jsou spravovaná vlákna ve stavu spánku nebo JOIN.

## <a name="tasks-column-information"></a>Informace o sloupci úlohy

Sloupce v okně **úlohy** obsahují následující informace.

|Název sloupce|Popis|
|-----------------|-----------------|
|**Flag**|Zobrazuje, které úkoly jsou označené příznakem, a umožňuje označit nebo zrušit označení úlohy.|
|**Ikony**|Žlutá šipka indikuje aktuální úlohu. Aktuální úloha je nejvyšším úkolem v aktuálním vlákně.<br /><br /> Bílá šipka označuje úlohu, která je v aktuálním okamžiku, kdy byl ladicí program vyvolán.<br /><br /> Ikona pozastavit označuje úlohu, která byla zmrazena uživatelem. Úkol můžete zablokovat a uvolnit tak, že na něj kliknete pravým tlačítkem myši v seznamu.|
|**ID**|Číslo zadané systémem pro úlohu. V nativním kódu se jedná o adresu úkolu.|
|**Stav**|Aktuální stav (naplánováno, aktivní, blokované, zablokované, očekáváno nebo dokončeno) úkolu. Naplánovaná úloha je ta, která ještě není spuštěná, a proto zatím nemá zásobník volání, přiřazené vlákno nebo související informace.<br /><br /> Aktivní úkol je ten, který spustil kód před přerušením v ladicím programu.<br /><br /> Neočekávaný nebo blokovaný úkol je blokovaný, protože čeká na událost, která má být signalizována, zámek k uvolnění nebo další úloha, která se má dokončit.<br /><br /> Zablokovaný úkol je čekající úloha, jejíž vlákno je zablokované jiným vláknem.<br /><br /> Pokud chcete zobrazit další informace o bloku, najeďte myší na buňku **stavu** pro blokovaný nebo očekávaný úkol. **Upozornění:**  Okno **úlohy** hlásí pouze zablokování pro blokovaný úkol, který používá primitivu synchronizace, která je podporována v WCT (Wait Chaining). Například pro zablokované <xref:System.Threading.Tasks.Task> objekty, které používají WCT, ladicí program **čeká na zablokování**. Pro zablokovaný úkol, který je spravován Concurrency Runtime, který nepoužívá WCT, sestavy ladicího programu **čekají**. Další informace o WCT naleznete v tématu [průchod řetězu čekání](/windows/desktop/Debug/wait-chain-traversal).|
|**Čas spuštění**|Čas, kdy se úkol stala aktivním|
|**Doba trvání**|Počet sekund, po které byl úkol aktivní|
|**Čas dokončení**|Čas, kdy byla úloha dokončena.|
|**Umístění**|Aktuální umístění v zásobníku volání úlohy. Najeďte myší na tuto buňku, aby se zobrazil celý zásobník volání pro daný úkol. Naplánované úlohy nemají v tomto sloupci žádnou hodnotu.|
|**Úkol**|Počáteční metoda a všechny argumenty, které byly před vytvořením úlohy předány.|
|**AsyncState**|Pro spravovaný kód se jedná o stav úlohy. Ve výchozím nastavení je tento sloupec skrytý. Chcete-li zobrazit tento sloupec, otevřete kontextovou nabídku pro jedno ze záhlaví sloupců. Vyberte **sloupce**, **AsyncState**.|
|**Parent**|ID úlohy, která vytvořila tento úkol. Pokud je toto pole prázdné, úloha nemá nadřazený objekt. To platí jenom pro spravované programy.|
|**Přiřazení vlákna**|ID a název vlákna, na kterém je úloha spuštěna.|
|**AppDomain**|Pro spravovaný kód se jedná o doménu aplikace, ve které je úloha spuštěna.|
|**task_group**|Pro nativní kód adresa [task_groupho](/cpp/parallel/concrt/reference/task-group-class) objektu, který úlohu naplánoval. U asynchronních agentů a nenáročných úloh je tento sloupec nastaven na hodnotu 0.|
|**Proces**|ID procesu, ve kterém je úloha spuštěna.|

 Sloupce můžete do zobrazení přidat tak, že kliknete pravým tlačítkem na záhlaví sloupce a pak vyberete požadované sloupce. (Odstranit sloupce vymazáním výběrů.) Sloupce můžete změnit také přetažením doleva nebo doprava. Místní nabídka sloupce je znázorněna na následujícím obrázku.

 ![Místní nabídka zobrazení v okně úlohy](../debugger/media/parallel_tasks_contextmenu.png "Parallel_Tasks_ContextMenu")

## <a name="sorting-tasks"></a>Řazení úloh
 Chcete-li seřadit úkoly podle kritérií sloupce, klikněte na záhlaví sloupce. Například kliknutím na záhlaví sloupce **ID** můžete seřadit úkoly podle ID úkolu: 1, 2, 3, 4, 5 atd. Chcete-li změnit pořadí řazení, klikněte znovu na záhlaví sloupce. Aktuální sloupec řazení a pořadí řazení jsou označeny šipkou ve sloupci.

## <a name="grouping-tasks"></a>Seskupování úloh
 Úkoly můžete seskupit na základě libovolného sloupce v zobrazení seznamu. Například kliknutím pravým tlačítkem myši na záhlaví sloupce **stav** a následným kliknutím na položku **Seskupit podle**  >  **[*stav*]** můžete seskupit všechny úkoly, které mají stejný stav. Můžete například rychle zobrazit čekající úlohy, abyste se mohli soustředit na to, proč jsou zablokované. Můžete také sbalit skupinu, která není zajímavá během relace ladění. Stejným způsobem můžete seskupit podle dalších sloupců. Skupinu můžete (zrušit) příznakem, stačí kliknout na tlačítko vedle záhlaví skupiny. Následující obrázek znázorňuje okno **úlohy** v seskupeném režimu.

 ![Seskupený režim v okně úlohy](../debugger/media/parallel_tasks_groupedmode.png "Parallel_Tasks_GroupedMode")

## <a name="parent-child-view"></a>Nadřazené podřízené zobrazení
 (Toto zobrazení je k dispozici pouze pro spravovaný kód.) Kliknutím pravým tlačítkem myši na záhlaví sloupce **stav** a potom kliknutím na možnost **Seskupit podle**  >  **nadřazené položky**můžete změnit seznam úkolů na hierarchické zobrazení, ve kterém je každá podřízená úloha poduzlem, který lze zobrazit nebo skrýt pod svým nadřazeným prvkem.

## <a name="flagging-tasks"></a>Označování úkolů
 Můžete označit vlákno úlohou, na které je úloha spuštěná, a to tak, že vyberete položku seznamu úkolů a potom v kontextové nabídce kliknete na ikonu **přidělené vlákno** , nebo kliknutím na ikonu příznaku v prvním sloupci. Pokud označíte několik úkolů, můžete řadit podle sloupce příznak a přenést tak všechny úkoly označené příznakem do horní části, abyste se mohli zaměřit jenom na ty. Okno **paralelní zásobníky** můžete použít také k zobrazení pouze úkolů označených příznakem. To vám umožní vyfiltrovat úkoly, které vás zajímají pro ladění. Mezi relacemi ladění nejsou zachovány příznaky.

## <a name="freezing-and-thawing-tasks"></a>Mrznutí a rozmrazení úloh
 Vlákno, na kterém je úloha spuštěná, můžete zablokovat tak, že kliknete pravým tlačítkem myši na položku seznamu úkolů a potom kliknete na **ukotvit přiřazené vlákno**. (Pokud je úkol již zmrazený, příkaz **rozmrazí přiřazené vlákno**.) Při zablokování vlákna nebude toto vlákno provedeno při procházení kódu po aktuální zarážce. **Zamrznutí všech vláken, ale tento jeden** příkaz zablokuje všechna vlákna s výjimkou toho, který provádí položku seznamu úkolů.

 Následující ilustrace znázorňuje další položky nabídky pro každý úkol.

 ![Nabídka zástupce vlákna v okně úlohy](../debugger/media/parallel_tasks_contextmenu2.png "Parallel_Tasks_ContextMenu2")

## <a name="switching-the-active-task-or-frame"></a>Přepínání aktivní úlohy nebo rámce

Příkaz **Přepnout na úkol** provede aktuální úlohu aktivním úkolem. Příkaz **Přepnout na rámec** nastaví vybraný rámec zásobníku jako aktivní rámec zásobníku. Kontext ladicího programu se přepne na aktuální úlohu nebo na vybraný rámec zásobníku.

## <a name="see-also"></a>Viz také

- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
- [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)
- [Paralelní programování](/dotnet/standard/parallel-programming/index)
- [Concurrency Runtime](/cpp/parallel/concrt/concurrency-runtime)
- [Použití okna Paralelní zásobníky](../debugger/using-the-parallel-stacks-window.md)
- [Návod: Ladění paralelní aplikace](../debugger/walkthrough-debugging-a-parallel-application.md)