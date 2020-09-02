---
title: Použití okna úlohy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.paralleltasks
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: bd5e0612-a0dc-41cf-a7af-1e87d0d5c35f
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 267a04e0d717bde311423aae7f35fba07ca6f39b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684041"
---
# <a name="using-the-tasks-window"></a>Používání okna úloh
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okno **úlohy** se podobá oknu **vlákna** , s tím rozdílem, že zobrazuje informace o <xref:System.Threading.Tasks.Task?displayProperty=fullName> objektech, [task_handle](https://msdn.microsoft.com/library/b4af5b28-227d-4488-8194-0a0d039173b7)nebo [WinJS. promise](https://msdn.microsoft.com/library/windows/apps/br211867.aspx) místo každého vlákna. Podobně jako vlákna, úlohy reprezentují asynchronní operace, které mohou běžet souběžně; ve stejném vlákně ale může běžet víc úloh. Další informace najdete [v tématu asynchronní programování v JavaScriptu (aplikace pro Windows Store)](https://msdn.microsoft.com/library/windows/apps/hh700330.aspx) .  
  
 Ve spravovaném kódu můžete použít okno **úlohy** při práci s <xref:System.Threading.Tasks.Task?displayProperty=fullName> objekty nebo s klíčovým slovem **await** a **Async** (**await** a **Async** v VisualBasic). Další informace o úlohách ve spravovaném kódu naleznete v tématu  [paralelní programování](https://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d).  
  
 V nativním kódu můžete použít okno **úlohy** při práci se [skupinami úloh](https://msdn.microsoft.com/library/42f05ac3-2098-494a-ba84-737fcdcad077), [paralelními algoritmy](https://msdn.microsoft.com/library/045dca7b-4d73-4558-a44c-383b88a28473), [asynchronními agenty](https://msdn.microsoft.com/library/6cf6ccc6-87f1-4e14-af15-ea8ba58fef1a)a [jednoduchými úlohami](https://msdn.microsoft.com/library/9aba278c-e0c9-4ede-b7c6-fedf7a365d90). Další informace o úlohách v nativním kódu naleznete v tématu [Concurrency Runtime](https://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c).  
  
 V jazyce JavaScript můžete použít okno úlohy při práci se příslib. potom Code.  
  
 Můžete použít okno **úlohy** při každém přerušení do ladicího programu. K němu máte přístup v nabídce **ladění** kliknutím na **Windows** a potom kliknutím na **úlohy**. Následující obrázek znázorňuje okno **úlohy** ve výchozím režimu.  
  
 ![Okno Paralelní úlohy](../debugger/media/parallel-tasks-window.png "Parallel_Tasks_Window")  
  
> [!NOTE]
> Ve spravovaném kódu, <xref:System.Threading.Tasks.Task> který má stav <xref:System.Threading.Tasks.TaskStatus> , <xref:System.Threading.Tasks.TaskStatus> , nebo <xref:System.Threading.Tasks.TaskStatus> nemusí být zobrazen v okně úlohy, pokud jsou spravovaná vlákna ve stavu spánku nebo JOIN.  
  
## <a name="tasks-column-information"></a>Informace o sloupci úlohy  
 Sloupce v okně **úlohy** obsahují následující informace.  
  
|Název sloupce|Popis|  
|-----------------|-----------------|  
|**Flag**|Zobrazuje, které úkoly jsou označené příznakem, a umožňuje označit nebo zrušit označení úlohy.|  
|**Ikony**|Žlutá šipka indikuje aktuální úlohu. Aktuální úloha je nejvyšším úkolem v aktuálním vlákně.<br /><br /> Bílá šipka označuje úlohu, která je v aktuálním okamžiku, kdy byl ladicí program vyvolán.<br /><br /> Ikona pozastavit označuje úlohu, která byla zmrazena uživatelem. Úkol můžete zablokovat a uvolnit tak, že na něj kliknete pravým tlačítkem myši v seznamu.|  
|**ID**|Číslo zadané systémem pro úlohu. V nativním kódu se jedná o adresu úkolu.|  
|**Stav**|Aktuální stav úlohy (plánovaný, aktivní, blokovaný, čekající nebo dokončený). Naplánovaná úloha je ta, která ještě není spuštěná, a proto zatím nemá zásobník volání, přiřazené vlákno nebo související informace.<br /><br /> Aktivní úkol je ten, který spustil kód před přerušením v ladicím programu.<br /><br /> Čeká se na odpověď, která je blokována, protože čeká na událost, která má být signalizována, zámek k vydání nebo jiná úloha, která má být dokončena.<br /><br /> Zablokovaný úkol je čekající úloha, jejíž vlákno je zablokované jiným vláknem.<br /><br /> Pokud chcete zobrazit další informace o bloku, najeďte myší na buňku **stavu** pro zablokovaný nebo čekající úkol. **Upozornění:**  Okno **úlohy** hlásí pouze zablokování pro blokovaný úkol, který používá primitivu synchronizace, která je podporována v WCT (Wait Chaining). Například pro zablokované <xref:System.Threading.Tasks.Task> objekty, které používají WCT, ladicí program hlásí **čekání na zablokování**. Pro zablokovaný úkol, který je spravován Concurrency Runtime, který nepoužívá WCT, sestavy ladicího programu **čekají**. Další informace o WCT naleznete v tématu [průchod řetězu čekání](https://msdn.microsoft.com/library/ms681622\(VS.85\).aspx).|  
|**Čas spuštění**|Čas, kdy se úkol stala aktivním|  
|**Doba trvání**|Počet sekund, po které byl úkol aktivní|  
|**Čas dokončení**|Čas, kdy byla úloha dokončena.|  
|**Umístění**|Aktuální umístění v zásobníku volání úlohy. Najeďte myší na tuto buňku, aby se zobrazil celý zásobník volání pro daný úkol. Naplánované úlohy nemají v tomto sloupci žádnou hodnotu.|  
|**Úkol**|Počáteční metoda a všechny argumenty, které byly před vytvořením úlohy předány.|  
|**Parent**|ID úlohy, která vytvořila tento úkol. Pokud je toto pole prázdné, úloha nemá nadřazený objekt. To platí jenom pro spravované programy.|  
|**Přiřazení vlákna**|ID a název vlákna, na kterém je úloha spuštěna.|  
|**Návratový stav**|Stav úkolu po jeho dokončení. Hodnoty návratového stavu jsou **úspěšné**, **zrušené**a **Chyba**.|  
|**AppDomain**|Pro spravovaný kód se jedná o doménu aplikace, ve které je úloha spuštěna.|  
|**task_group**|Pro nativní kód adresa [task_groupho](https://msdn.microsoft.com/library/b4af5b28-227d-4488-8194-0a0d039173b7) objektu, který úlohu naplánoval. U asynchronních agentů a nenáročných úloh je tento sloupec nastaven na hodnotu 0.|  
|Proces|ID procesu, ve kterém je úloha spuštěna.|  
|Asynchronní stav|Pro spravovaný kód se jedná o stav úlohy. Ve výchozím nastavení je tento sloupec skrytý. Chcete-li zobrazit tento sloupec, otevřete kontextovou nabídku pro jedno ze záhlaví sloupců. Vyberte **sloupce**, **AsyncState**.|  
  
 Sloupce můžete do zobrazení přidat tak, že kliknete pravým tlačítkem na záhlaví sloupce a pak vyberete požadované sloupce. (Odstranit sloupce vymazáním výběrů.) Sloupce můžete změnit také přetažením doleva nebo doprava. Místní nabídka sloupce je znázorněna na následujícím obrázku.  
  
 ![Místní nabídka zobrazení v okně Paralelní úlohy](../debugger/media/parallel-tasks-contextmenu.png "Parallel_Tasks_ContextMenu")  
  
## <a name="sorting-tasks"></a>Řazení úloh  
 Chcete-li seřadit úkoly podle kritérií sloupce, klikněte na záhlaví sloupce. Například kliknutím na záhlaví sloupce **ID** můžete seřadit úkoly podle ID úkolu: 1, 2, 3, 4, 5 atd. Chcete-li změnit pořadí řazení, klikněte znovu na záhlaví sloupce. Aktuální sloupec řazení a pořadí řazení jsou označeny šipkou ve sloupci.  
  
## <a name="grouping-tasks"></a>Seskupování úloh  
 Úkoly můžete seskupit na základě libovolného sloupce v zobrazení seznamu. Například kliknutím pravým tlačítkem myši na záhlaví sloupce **stav** a potom kliknutím na možnost **Seskupit podle stavu**můžete seskupit všechny úkoly, které mají stejný stav. Můžete například rychle zobrazit čekající úlohy, abyste se mohli soustředit na to, proč jsou zablokované. Můžete také sbalit skupinu, která není zajímavá během relace ladění. Stejným způsobem můžete seskupit podle dalších sloupců. Skupinu můžete (zrušit) příznakem, stačí kliknout na tlačítko vedle záhlaví skupiny. Následující obrázek znázorňuje okno **úlohy** v seskupeném režimu.  
  
 ![Seskupený režim v okně Paralelní úlohy](../debugger/media/parallel-tasks-groupedmode.png "Parallel_Tasks_GroupedMode")  
  
## <a name="parent-child-view"></a>Nadřazené podřízené zobrazení  
 (Toto zobrazení je k dispozici pouze pro spravovaný kód.) Kliknutím pravým tlačítkem myši na záhlaví sloupce a následným kliknutím na **nadřazené podřízené zobrazení**můžete změnit seznam úkolů na hierarchické zobrazení, ve kterém je každá podřízená úloha poduzlem, který můžete zobrazit nebo skrýt pod svým nadřazeným prvkem. Následující ilustrace znázorňuje úkoly v zobrazení nadřízený-podřízený.  
  
 ![Nadřazené zobrazení podřízené&#45;v okně Paralelní úlohy](../debugger/media/parallel-tasks-parentchildview.png "Parallel_Tasks_ParentChildView")  
  
## <a name="flagging-tasks"></a>Označování úkolů  
 Můžete označit vlákno úlohou, na které je úloha spuštěná, a to tak, že vyberete položku seznamu úkolů a potom v kontextové nabídce vyberete **příznak** , nebo kliknutím na ikonu příznaku v prvním sloupci. Pokud označíte několik úkolů, můžete řadit podle sloupce příznak a přenést tak všechny úkoly označené příznakem do horní části, abyste se mohli zaměřit jenom na ty. Okno **paralelní zásobníky** můžete použít také k zobrazení pouze úkolů označených příznakem. To vám umožní vyfiltrovat úkoly, které vás zajímají pro ladění. Mezi relacemi ladění nejsou zachovány příznaky.  
  
## <a name="freezing-and-thawing-tasks"></a>Mrznutí a rozmrazení úloh  
 Vlákno, na kterém je úloha spuštěná, můžete zablokovat tak, že kliknete pravým tlačítkem myši na položku seznamu úkolů a potom kliknete na **ukotvit přiřazené vlákno**. (Pokud je úkol již zmrazený, příkaz **rozmrazí přiřazené vlákno**.) Při zablokování vlákna nebude toto vlákno provedeno při procházení kódu po aktuální zarážce. **Zamrznutí všech vláken, ale tento** příkaz zablokuje všechna vlákna s výjimkou toho, který provádí položku seznamu úkolů.  
  
 Následující ilustrace znázorňuje další položky nabídky pro každý úkol.  
  
 ![Nabídka zástupce vlákna v okně Paralelní úlohy](../debugger/media/parallel-tasks-contextmenu2.png "Parallel_Tasks_ContextMenu2")  
  
## <a name="see-also"></a>Viz také  
 [Základy ladicího programu](../debugger/debugger-basics.md)   
 [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)   
 [Paralelní programování](https://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)   
 [Concurrency Runtime](https://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c)   
 [Použití okna Paralelní zásobníky](../debugger/using-the-parallel-stacks-window.md)   
 [Návod: Ladění paralelní aplikace](../debugger/walkthrough-debugging-a-parallel-application.md)
