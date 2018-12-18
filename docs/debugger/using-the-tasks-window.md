---
title: Using the Tasks Window | Dokumentace Microsoftu
ms.custom: ''
ms.date: 03/18/2018
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6d22202e50c973c52bf2b47374b9eda583fb3fe8
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280880"
---
# <a name="using-the-tasks-window"></a>Používání okna úloh

**Úlohy** okno vypadá podobně jako **vlákna** okna, s tím rozdílem, že se zobrazuje informace o <xref:System.Threading.Tasks.Task?displayProperty=fullName>, [task_handle –](/cpp/parallel/concrt/reference/task-group-class), nebo [WinJS.Promise ](/previous-versions/windows/apps/br211867(v=win.10)) objekty namísto každé vlákno. Například vlákna úlohy představuje asynchronní operace, které můžou běžet souběžně; ale více úkolů může spustit ve stejném vlákně.

Ve spravovaném kódu, můžete použít **úlohy** okno při práci s <xref:System.Threading.Tasks.Task?displayProperty=fullName> objekty nebo se **await** a **asynchronní** klíčová slova (**Await** a **asynchronní** v VisualBasic). Další informace o úlohách ve spravovaném kódu najdete v tématu [paralelního programování](/dotnet/standard/parallel-programming/index).

V nativním kódu, můžete použít **úlohy** okno při práci s [skupiny úloh](/cpp/parallel/concrt/task-parallelism-concurrency-runtime), [paralelní algoritmy](/cpp/parallel/concrt/parallel-algorithms), [asynchronních agentů](/cpp/parallel/concrt/asynchronous-agents), a [prostých úloh](/cpp/parallel/concrt/task-scheduler-concurrency-runtime). Další informace o úlohách v nativním kódu, naleznete v tématu [Concurrency Runtime](/cpp/parallel/concrt/concurrency-runtime).

V jazyce JavaScript, můžete použít okno úlohy při práci s promise `.then` kódu. Zobrazit [asynchronní programování v jazyce JavaScript (aplikace pro UPW)](/previous-versions/windows/apps/hh700330(v=win.10)) Další informace.

Můžete použít **úlohy** okna pokaždé, když jste přerušení ladicího programu. Je k dispozici na **ladění** nabídky kliknutím **Windows** a pak levým na **úlohy**. Je vidět na následujícím obrázku **úlohy** okna v její výchozí režim.

![Okno úlohy](../debugger/media/parallel_tasks_window.png "Parallel_Tasks_Window")

> [!NOTE]
> Ve spravovaném kódu <xref:System.Threading.Tasks.Task> , který je ve stavu [TaskStatus.Created](<xref:System.Threading.Tasks.TaskStatus.Created>), [TaskStatus.WaitingForActivation](<xref:System.Threading.Tasks.TaskStatus.WaitingForActivation>), nebo [TaskStatus.WaitingToRun](<xref:System.Threading.Tasks.TaskStatus.WaitingToRun>) nemusí být zobrazí v **úlohy** okno při spravovaná vlákna jsou v režimu spánku nebo připojení stavu.

## <a name="tasks-column-information"></a>Informace o sloupci úlohy

Sloupce v **úlohy** v okně zobrazí následující informace.

|Název sloupce|Popis|
|-----------------|-----------------|
|**příznaky**|Zobrazuje úlohy, které jsou označeny příznakem a umožňuje označit nebo zrušit označení příznakem úlohu.|
|**Ikony**|Žlutá šipka označuje aktuální úlohu. Aktuální úkol je úkol úplně nahoře v aktuálním vláknu.<br /><br /> Bílé šipka označuje zásadní úloh, to znamená, ten, který byl aktuální v době byla vyvolána ladicí program.<br /><br /> Ikona pozastavení označuje úlohu, která byla zmrazené uživatelem. Můžete ukotvit a uvolnění úlohy kliknutím pravým tlačítkem myši v seznamu.|
|**ID**|Číslo poskytnuté systémem pro úlohu. V nativním kódu jde o adresu úkolu.|
|**Status**|Aktuální stav (naplánované, aktivní, zablokování, jeví jako zablokované, čeká na nebo dokončené) úlohy. Naplánované úlohy je ten, který dosud nebyla spuštěna a proto se ještě nemá zásobník volání, přiřazené vlákno nebo související informace.<br /><br /> Aktivní úlohy je ten, který se spouští kód před přerušení v ladicím programu.<br /><br /> Čeká se na nebo zablokování úlohy je ten, který je zablokovaná, protože se čeká na událost má být signalizován, uvolnění zámku nebo na dokončení jiné úlohy.<br /><br /> Jeví jako zablokované úkol je úkol čekání, jehož vlákna je zablokovaná s jiným vláknem.<br /><br /> Najeďte myší **stav** buňky pro jeví jako zablokované nebo čeká na úlohu zobrazíte další informace o bloku. **Upozornění:** **úlohy** okno hlásí zablokování pouze pro zablokování úkol, který používá synchronizační jednoduchého typu, který je podporovaný počkejte procházení řetězce (WCT). Například pro jeví jako zablokované <xref:System.Threading.Tasks.Task> objektu, který používá WCT, ladicí program hlásí **zablokována čeká na**. Jeví jako zablokované úkolu, který je spravovaný nástrojem modulu Runtime souběžnosti, který nepoužívá WCT, ladicí program hlásí **čekání**. Další informace o WCT najdete v tématu [počkejte procházení řetězu](/windows/desktop/Debug/wait-chain-traversal).|
|**Čas spuštění**|Doba, jakou úloha začal být aktivní.|
|**Doba trvání**|Počet sekund, po které byl aktivní úloha.|
|**Čas dokončení**|Čas, kdy úloha dokončena.|
|**Poloha**|Aktuální umístění v zásobníku volání úlohy. Najeďte myší tuto buňku, chcete-li zobrazit celý zásobník volání pro úlohu. Naplánované úlohy nemají hodnotu v tomto sloupci.|
|**Úloha**|Metoda počáteční a všechny argumenty, které byly předány pro úkol při vytvoření rovnou uložil.|
|**Stav AsyncState**|Pro spravovaný kód, stav úlohy. Ve výchozím nastavení je tento sloupec skrytý. Chcete-li zobrazit tento sloupec, otevřete kontextovou nabídku pro jednu z záhlaví sloupců. Zvolte **sloupce**, **AsyncState**.|
|**Nadřazené**|ID úkolu, který vytvořil tuto úlohu. Pokud je toto pole prázdné, úloha nemá žádný nadřazený objekt. To platí pouze pro spravované aplikace.|
|**Přiřazení vlákna**|ID a název vlákna, na kterém je spuštěn úkol.|
|**AppDomain**|Pro spravovaný kód domény aplikace, ve kterém je spuštěn úkol.|
|**task_group**|Pro nativní kód, adresa [task_group –](/cpp/parallel/concrt/reference/task-group-class) objekt, který naplánované úlohy. Asynchronní agenti a jednoduché úlohy je tento sloupec nastavena na 0.|
|**Proces**|ID procesu, který je spuštěn úkol na.|

 Sloupce můžete přidat do zobrazení tak, že pravým tlačítkem myši na záhlaví sloupce a následným výběrem sloupce, které chcete. (Odebrat sloupce tím, že zrušíte výběr). Můžete také změnit uspořádání sloupců jejich přetažením doleva nebo doprava. Místní nabídka sloupce je zobrazena na následujícím obrázku.

 ![Místní nabídka zobrazení v okně úlohy](../debugger/media/parallel_tasks_contextmenu.png "Parallel_Tasks_ContextMenu")

## <a name="sorting-tasks"></a>Řazení úkolů
 Seřadit podle sloupce kritéria úloh, klikněte na záhlaví sloupce. Například klepnutím **ID** záhlaví sloupce můžete řazení úloh podle ID úlohy: 1,2,3,4,5 a tak dále. Chcete-li změnit směr řazení, znovu klikněte na záhlaví sloupce. Aktuální řazení sloupců a pořadí řazení je indikován šipku ve sloupci.

## <a name="grouping-tasks"></a>Seskupení úkolů
 Můžete seskupit podle libovolného sloupce v zobrazení seznamu úloh. Například kliknutím pravým tlačítkem myši **stav** záhlaví sloupce a pak levým na **Seskupit podle** > **[*stav*]**, můžete si všechny úlohy, které mají stejný stav skupiny. Například může rychle zjistit, očekáváno úloh tak, aby se mohli soustředit na Proč jsou zablokované. Můžete také sbalit skupiny, které nejsou zajímavé během relace ladění. Stejným způsobem můžete seskupit podle jiných sloupců. Skupinu lze (zrušit) příznakem jednoduše kliknutím na tlačítko vedle záhlaví skupiny. Je vidět na následujícím obrázku **úlohy** okno v seskupených režimu.

 ![Seskupené režim v okně úlohy](../debugger/media/parallel_tasks_groupedmode.png "Parallel_Tasks_GroupedMode")

## <a name="parent-child-view"></a>Nadřazeného a podřízeného prvku
 (Toto zobrazení je k dispozici pouze pro spravovaný kód). Kliknutím pravým tlačítkem myši **stav** záhlaví sloupce a pak levým na **Seskupit podle** > **nadřazené**, hierarchické zobrazení, ve kterém můžete změnit seznam úkolů Každá podřízená úloha je dílčí uzel, který můžete zobrazení nebo skrytí podle svého nadřazeného objektu.

## <a name="flagging-tasks"></a>Nastavení příznaku úlohy
 Můžete označit příznakem vlákna seznam úloh, na kterém je úloha spuštěná tak, že vyberete úlohu položky a následným výběrem možnosti **označit přiřazené vlákno** v místní nabídce nebo kliknutím na ikonu příznaku v prvním sloupci. Pokud označíte některé úlohy, můžete pak seřadit sloupec příznaku uveďte všechny úkoly s příznakem do horní části tak, aby se mohli soustředit na nich. Můžete také použít **paralelní zásobníky** okna, chcete-li zobrazit pouze označená příznakem úlohy. To vám umožňuje odfiltrovat úlohy, které vás zajímají není pro ladění. Příznaky nejsou trvalé mezi relacemi ladění.

## <a name="freezing-and-thawing-tasks"></a>Zmrazení a uvolnění úloh
 Může zablokovat vlákno, na kterém je úloha spuštěná pravým tlačítkem na položku seznamu úkolů a potom klikněte na **zablokovat přiřazené vlákno**. (Pokud je již zmrazen úkol, je příkaz **uvolnit přiřazené vlákno**.) Po ukotvení vlákno nebude spuštěno toto vlákno při krokovat kód po aktuální zarážku. **Zablokovat všechna vlákna, ale tento jeden** příkazu se zablokuje všechna vlákna kromě toho, který provádí položky seznamu úkolů.

 Následující obrázek znázorňuje dalšími položkami nabídky pro každý úkol.

 ![Vlákno nabídku v okně úlohy](../debugger/media/parallel_tasks_contextmenu2.png "Parallel_Tasks_ContextMenu2")

## <a name="switching-the-active-task-or-frame"></a>Přepnout aktivní úlohy nebo rámce

**Přejít k úloze** příkaz zjednodušuje aktuální úlohu na aktivní úlohy. **Přepnout na rámec** příkaz provede vybraného zásobníku rámce aktivní blok zásobníku. Kontext ladicího programu se přepne do aktuální úlohu nebo vybrané zásobníku.

## <a name="see-also"></a>Viz také:

- [Základy ladicího programu](../debugger/getting-started-with-the-debugger.md)
- [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)
- [Paralelní programování](/dotnet/standard/parallel-programming/index)
- [Concurrency Runtime](/cpp/parallel/concrt/concurrency-runtime)
- [Použití okna Paralelní zásobníky](../debugger/using-the-parallel-stacks-window.md)
- [Návod: Ladění paralelní aplikace](../debugger/walkthrough-debugging-a-parallel-application.md)