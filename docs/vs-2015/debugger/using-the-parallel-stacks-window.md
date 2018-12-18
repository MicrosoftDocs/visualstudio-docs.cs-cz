---
title: Použití paralelních zásobníků okno | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.parallelstacks
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: f50efb78-5206-4803-bb42-426ef8133f2f
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 602fdd683ecb1b3244289c305e4fc850d337b03e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792031"
---
# <a name="using-the-parallel-stacks-window"></a>Použití okna Paralelní zásobníky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Paralelní zásobníky** okna je užitečné při ladění aplikací s více vlákny. Jeho **zobrazení vláken** ukazuje informace v zásobníku volání pro všechna vlákna ve vaší aplikaci. Umožňuje procházet mezi vlákny a rámce zásobníku na tato vlákna. Ve spravovaném kódu **zobrazení úkolů** ukazuje volání zásobníků s <xref:System.Threading.Tasks.Task?displayProperty=fullName> objekty. V nativním kódu **zobrazení úkolů** ukazuje volání zásobníků s [skupiny úloh](http://msdn.microsoft.com/library/42f05ac3-2098-494a-ba84-737fcdcad077), [paralelní algoritmy](http://msdn.microsoft.com/library/045dca7b-4d73-4558-a44c-383b88a28473), [asynchronních agentů](http://msdn.microsoft.com/library/6cf6ccc6-87f1-4e14-af15-ea8ba58fef1a)a [prostých úloh](http://msdn.microsoft.com/library/9aba278c-e0c9-4ede-b7c6-fedf7a365d90).  
  
## <a name="threads-view"></a>Zobrazení vláken  
 Následující obrázek znázorňuje jedno vlákno, které se nezdařilo z hlavní a b a pak na některé externí kód. Dvě ostatní vlákna spustit z externího kódu a pak se nepovedlo A, ale jedno z vláken pokračování b a pak na některé externí kód a další vlákno pokračuje na C a potom na některé AnonymousMethod.  
  
 ![Zobrazení okna paralelní zásobníky vlákna](../debugger/media/parallel-stacksthread.png "Parallel_StacksThread")  
  
 Na obrázku je modře zvýrazněna volání cestu aktuální vlákno a aktivní blok zásobníku jsou označeny žlutou šipkou. Aktuální rámec zásobníku můžete změnit tak, že vyberete jinou metodu v **paralelní zásobníky** okna. To může způsobit také přepínání aktuálního vlákna, v závislosti na tom, zda je součást již aktuální vlákno nebo jiné vlákno metodu, kterou jste vybrali. Následující tabulka popisuje hlavní funkce **paralelní zásobníky** okna, jak je znázorněno na obrázku.  
  
|Popisek písmeno|Název elementu|Popis|  
|--------------------|------------------|-----------------|  
|OBJEKT|Segment zásobník volání nebo uzlu|Obsahuje řadu metoda kontexty pro jedno nebo více vláken. Pokud uzel nemá žádné řádky šipky k ní připojená, to představuje cestu celý volání pro podprocesy.|  
|B|Modré zvýraznění|Označuje volání cestu aktuální vlákno.|  
|C|Šipka řádky|Připojte uzly k vytvoření volání celou cestu pro podprocesy.|  
|D|Popisek tlačítka na záhlaví uzlu|Zobrazí ID a uživatelem definovaný název každé vlákno, jehož cesta volání sdílí tento uzel.|  
|E|Kontext – metoda|Představuje jeden nebo více rámců zásobníku v stejným způsobem.|  
|F|Popis pro kontext – metoda|V zobrazení vláken, zobrazuje všechna vlákna v tabulce podobně jako **vlákna** okna. V zobrazení úlohy zobrazuje všechny úkoly v tabulce podobně jako **paralelní úlohy** okna.|  
  
 Kromě toho ukazuje okna paralelní zásobníky **pohled z ptačí perspektivy** ikonu v hlavním podokně při graf je příliš velký a nevejde se do okna. Můžete kliknout na ikonu zobrazíte celý graf v okně.  
  
## <a name="method-context-icons"></a>Ikony kontextu – metoda  
 Následující tabulka popisuje ikony, které obsahují informace o aktivní a aktuální rámců:  
  
|||  
|-|-|  
|Ikona|Popis|  
|![Paralelních zásobníků žlutá šipka](../debugger/media/icon-parallelyellowarrow.gif "Icon_ParallelYellowArrow")|Označuje, že metoda kontext obsahuje aktivní blok zásobníku aktuálního vlákna.|  
|![Paralelních zásobníků ikony vlákna](../debugger/media/icon-parallelthreads.gif "Icon_ParallelThreads")|Označuje, že metoda kontext obsahuje aktivní blok zásobníku vlákna neaktuální.|  
|![Paralelních zásobníků zelenou šipku](../debugger/media/icon-parallelgreenarrow.gif "Icon_ParallelGreenArrow")|Označuje, že metoda kontext obsahuje aktuální rámec zásobníku. Tento název metody je ve všech uzlech, ve které se zobrazí tučně.|  
  
## <a name="toolbar-controls"></a>Ovládací prvky panelu nástrojů  
 Následující obrázek a tabulka popisovat kontrolní mechanismy, které jsou k dispozici v panelu nástrojů paralelních zásobníků.  
  
 ![Panel nástrojů v okna paralelní zásobníky](../debugger/media/parallel-stackstoolbar.png "Parallel_StacksToolbar")  
  
|Popisek písmeno|Ovládací prvek|Popis|  
|--------------------|-------------|-----------------|  
|OBJEKT|Pole se seznamem vláken nebo úloh|Přepíná zobrazení mezi zásobníky vlákna volání a volání zásobníků s úkoly. Další informace najdete v zobrazení úloh a zobrazení vláken.|  
|B|Zobrazit pouze označená příznakem|Zásobníky volání zobrazí pouze pro vlákna, která jsou označena jako v jiných oknech ladění **vlákna GPU** okno a **paralelní sledování** okna.|  
|C|Přepnout zobrazení metody|Přepne mezi zobrazením zásobníku a metody. Další informace najdete v tématu zobrazení metody.|  
|D|Automaticky přejít na aktuální rámec zásobníku|Autoscrolls diagramu tak, aby zásobníku aktuálního rámce se v zobrazení. Tato funkce je užitečná, pokud změníte aktuální rámec zásobníku mezi jinými nebo pokud dosahujete Nová zarážka ve velkých diagramů.|  
|E|Přepnout ovládání lupy|Zobrazí nebo skryje ovládací prvek lupy. Můžete také přiblížit pomocí klávesy CTRL a kolečka myši, bez ohledu na to, zda se ovládací prvek lupy zapíná nebo pomocí **CTRL + SHIFT + '+'** přiblížit a **CTRL + SHIFT + "-"** zmenšíte. Stisknutím klávesy **CTRL + F8** změní měřítko na celou obrazovku.|  
  
### <a name="context-menu-items"></a>Položek kontextové nabídky  
 Následující obrázek a tabulka popisují položky místní nabídky, které jsou k dispozici, když kliknete pravým tlačítkem na metodu kontextu v zobrazení vláken nebo v zobrazení úlohy. Posledních šest položek jsou si přímo z okna zásobník volání a zavést žádné nové chování.  
  
 ![Místní nabídky okna paralelní zásobníky](../debugger/media/parallel-contmenu.png "Parallel_ContMenu")  
  
|Položka nabídky|Popis|  
|---------------|-----------------|  
|Příznak|Označí vybrané položky.|  
|Odznačit|Unflags vybranou položku.|  
|zablokování|Zablokuje vybranou položku.|  
|Uvolnit|Thaws vybranou položku.|  
|Přejít k úloze (vlákno)|Provádí stejnou funkci jako pole se seznamem na panelu nástrojů, ale udržuje stejné zvýrazněnou rámce zásobníku.|  
|Přejít ke zdrojovému kódu|Přejde do umístění ve zdrojovém kódu, který odpovídá rámce zásobníku, který klikli pravým tlačítkem myši uživatele.|  
|Přepnout na rámec|Stejné jako odpovídající příkaz nabídky v okně zásobník volání. Pomocí paralelní zásobníky, ale může více snímků odpovídají kontextu jednu metodu. Proto má položka nabídky podnabídky, z nichž každý představuje konkrétního zásobníku. Pokud jeden z rámce zásobníku v aktuálním vlákně, je vybraná nabídka, která odpovídá tohoto rámce zásobníku.|  
|Přejít na zpětný překlad|Přejde do umístění v okně zpětný překlad, která odpovídá rámce zásobníku, který klikli pravým tlačítkem myši uživatele.|  
|Zobrazit externí kód|Zobrazí nebo skryje externí kód.|  
|Hexadecimální zobrazení|Přepíná mezi desetinných míst a hexadecimální zobrazení.|  
|Informace o načítání symbolů|Zobrazí dialogové okno odpovídající.|  
|Nastavení symbolů|Zobrazí dialogové okno odpovídající.|  
  
## <a name="tasks-view"></a>Zobrazení úloh  
 Pokud vaše aplikace používá <xref:System.Threading.Tasks.Task?displayProperty=fullName> objekty (spravovaný kód) nebo `task_handle` objekty (nativní kód) vyjádřete paralelismus, můžete použít pole se seznamem na panelu nástrojů okna paralelní zásobníky přepnout na *zobrazení úkolů*. Úlohy zobrazení uvádí zásobníky volání úkolů místo vlákna. Zobrazení úloh se liší od zobrazení vláken následujícím způsobem:  
  
- Zásobníky volání vláken, které nejsou spuštěné úkoly se nezobrazují.  
  
- Zásobníky volání vláken, na kterých běží úlohy jsou vizuálně oříznut v horní a dolní části můžete zobrazit nejrelevantnější bloky, které se vztahují na úlohy.  
  
- Po několika úloh v jednom vlákně se oddělit zásobníky volání těchto úkolů do samostatné uzly.  
  
  Následující obrázek znázorňuje paralelní zásobníky – zobrazení úloh na pravé straně a odpovídající zobrazení vláken na levé straně.  
  
  ![Úlohy zobrazení okna paralelní zásobníky](../debugger/media/parallel-tasksview.png "Parallel_TasksView")  
  
  Pokud chcete zobrazit celý zásobník volání, stačí přepnout zpět na zobrazení vláken pravým tlačítkem myši na rámec zásobníku a poté klepnutím na **přejít k vláknu**.  
  
  Jak je popsáno v předchozí tabulce, podržením ukazatele nad metoda kontextu, zobrazí se další informace. Následující obrázek ukazuje informace v popisu pro zobrazení vláken a zobrazení úloh.  
  
  ![Popisy tlačítek v okna paralelní zásobníky](../debugger/media/parallel-stack-tooltips.png "Parallel_Stack_Tooltips")  
  
## <a name="method-view"></a>Zobrazení metody  
 Ze zobrazení zobrazení vláken nebo úloh můžete vytvořit kontingenční graf v aktuální metodě kliknutím na ikonu zobrazení metody na panelu nástrojů. Metoda zobrazení ukazuje na první pohled všechny metody v všechna vlákna, které volají nebo jsou volány aktuální metoda. Následující obrázek znázorňuje zobrazení vláken a také jak vypadá stejné informace v zobrazení metody.  
  
 ![Zobrazení metody v okna paralelní zásobníky](../debugger/media/parallel-methodview.png "Parallel_MethodView")  
  
 Přepnutím na nový rámec zásobníku, proveďte tuto metodu aktuální metoda a způsobit, že v okně zobrazíte všechny volající a volané pro nové metody. To může způsobit, že některá vlákna se zobrazí nebo zmizí ze zobrazení, v závislosti na tom, zda se zobrazí na svých zásobníků volání metody. Pokud chcete vrátit do zobrazení za sebou, klikněte na tlačítko panelu nástrojů zobrazení metody znovu.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Ladění paralelní aplikace](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Základy ladicího programu](../debugger/debugger-basics.md)   
 [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)   
 [Paralelní programování](http://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)   
 [Používání okna úloh](../debugger/using-the-tasks-window.md)   
 [Návod: Ladění paralelní aplikace](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Task – třída](../extensibility/debugger/task-class-internal-members.md)



