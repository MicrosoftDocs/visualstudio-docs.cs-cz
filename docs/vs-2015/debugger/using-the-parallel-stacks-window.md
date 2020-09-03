---
title: Použití okna Paralelní zásobníky | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: e89125c8e1dea25ab02fe64c21b8166e9d65194a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542217"
---
# <a name="using-the-parallel-stacks-window"></a>Použití okna Paralelní zásobníky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okno **paralelní zásobníky** je užitečné při ladění aplikací s více vlákny. **Zobrazení vlákna** zobrazuje informace zásobníku volání pro všechna vlákna ve vaší aplikaci. Umožňuje procházet mezi vlákny a bloky zásobníku v těchto vláknech. Ve spravovaném kódu zobrazuje **zobrazení úloh** zásobníky volání <xref:System.Threading.Tasks.Task?displayProperty=fullName> objektů. V nativním kódu **zobrazení úlohy** zobrazuje zásobníky volání [skupin úloh](https://msdn.microsoft.com/library/42f05ac3-2098-494a-ba84-737fcdcad077), [paralelní algoritmy](https://msdn.microsoft.com/library/045dca7b-4d73-4558-a44c-383b88a28473), [Asynchronní agenti](https://msdn.microsoft.com/library/6cf6ccc6-87f1-4e14-af15-ea8ba58fef1a)a [jednoduché úlohy](https://msdn.microsoft.com/library/9aba278c-e0c9-4ede-b7c6-fedf7a365d90).  
  
## <a name="threads-view"></a>Zobrazení vláken  
 Následující ilustrace znázorňuje jedno vlákno, které přešlo z hlavního na a do B a potom do nějakého externího kódu. Druhá vlákna začala z nějakého externího kódu a pak přešla do, ale jedna z vláken pokračuje do B a následně do nějakého externího kódu a druhé vlákno pokračuje v C a pak na některé AnonymousMethod.  
  
 ![Zobrazení vláken v okně paralelní zásobníky](../debugger/media/parallel-stacksthread.png "Parallel_StacksThread")  
  
 Na obrázku je cesta volání aktuálního vlákna zvýrazněna modře a aktivní rámec zásobníku je označený žlutou šipkou. Aktuální rámec zásobníku můžete změnit tak, že v okně **paralelní zásobníky** vyberete jinou metodu. To může mít za následek také přepínání aktuálního vlákna v závislosti na tom, zda je metoda, kterou jste vybrali, součástí aktuálního vlákna, nebo jiného vlákna. Následující tabulka popisuje hlavní funkce okna **paralelní zásobníky** , jak je znázorněno na obrázku.  
  
|Popisek – písmeno|Název prvku|Popis|  
|--------------------|------------------|-----------------|  
|A|Segment zásobníku volání nebo uzel|Obsahuje řadu kontextů metod pro jedno nebo více vláken. Pokud k uzlu nejsou připojeny žádné čáry šipek, představuje úplnou cestu volání pro vlákna.|  
|B|Modrá zvýraznění|Označuje cestu volání aktuálního vlákna.|  
|C|Šipky – čáry|Uzly připojte, chcete-li vytvořit úplnou cestu volání pro vlákna.|  
|D|Popis tlačítka v záhlaví uzlu|Zobrazuje ID a uživatelsky definované názvy všech vláken, jejichž cesta volání sdílí tento uzel.|  
|E|Kontext metody|Reprezentuje jeden nebo více rámců zásobníku ve stejné metodě.|  
|F|Popis tlačítka v kontextu metody|V zobrazení vlákna zobrazuje všechna vlákna v tabulce podobně jako okno **vlákna** . V zobrazení úloh se zobrazí všechny úkoly v tabulce podobné oknu **Paralelní úlohy** .|  
  
 Kromě toho okno paralelní zásobníky zobrazuje ikonu **zobrazení pohled na oči** v hlavním podokně, když je graf příliš velký, aby se vešel do okna. Kliknutím na ikonu můžete zobrazit celý graf v okně.  
  
## <a name="method-context-icons"></a>Ikony kontextu metody  
 Následující tabulka popisuje ikony, které poskytují informace o aktivním a aktuálním snímku zásobníku:  
  
|Ikona|Popis|  
|-|-|
|![Žlutá šipka pro paralelní zásobníky](../debugger/media/icon-parallelyellowarrow.gif "Icon_ParallelYellowArrow")|Označuje, že kontext metody obsahuje aktivní rámec zásobníku aktuálního vlákna.|  
|![Ikona vláken paralelních zásobníků](../debugger/media/icon-parallelthreads.gif "Icon_ParallelThreads")|Označuje, že kontext metody obsahuje aktivní rámec zásobníku v neaktuálním vlákně.|  
|![Paralelní zásobníky – zelená šipka](../debugger/media/icon-parallelgreenarrow.gif "Icon_ParallelGreenArrow")|Označuje, že kontext metody obsahuje aktuální rámec zásobníku. Tento název metody je tučný na všech uzlech, ve kterých se zobrazí.|  
  
## <a name="toolbar-controls"></a>Ovládací prvky panelu nástrojů  
 Následující ilustrace a tabulka popisují ovládací prvky, které jsou k dispozici na panelu nástrojů paralelní zásobníky.  
  
 ![Panel nástrojů v okně paralelní zásobníky](../debugger/media/parallel-stackstoolbar.png "Parallel_StacksToolbar")  
  
|Popisek – písmeno|Řízení|Popis|  
|--------------------|-------------|-----------------|  
|A|Pole se seznamem vláken/úloh|Přepíná zobrazení mezi zásobníky volání vláken a zásobníků volání úkolů. Další informace najdete v tématu zobrazení úkolů a zobrazení vláken.|  
|B|Zobrazit pouze označené příznakem|Zobrazuje zásobníky volání pouze pro vlákna, která jsou označena v jiných oknech ladění, například okno **vlákna GPU** a okno **paralelní kukátko** .|  
|C|Přepnout zobrazení metody|Přepíná mezi zobrazením zásobníku a zobrazením metody. Další informace naleznete v tématu zobrazení metod.|  
|D|Automaticky přejít na aktuální rámec zásobníku|Automaticky posouvá diagram tak, aby byl aktuální rámec zásobníku zobrazen. Tato funkce je užitečná v případě, že měníte aktuální rámec zásobníku z jiných oken nebo když zasáhnete novou zarážku ve velkých diagramech.|  
|E|Přepnout ovládací prvek Lupa|Zobrazí nebo skryje ovládací prvek Lupa. Můžete také přiblížit stisknutím kombinace kláves CTRL a vypnutím kolečka myši, bez ohledu na viditelnost ovládacího prvku zvětšení nebo pomocí **kombinace kláves CTRL + SHIFT + +** **k přiblížení a** oddálení. Stisknutím **kombinace kláves Ctrl + F8** se přiblíží obrazovka.|  
  
### <a name="context-menu-items"></a>Položky místní nabídky  
 Následující ilustrace a tabulka popisují položky místní nabídky, které jsou k dispozici, když kliknete pravým tlačítkem myši na kontext metody v zobrazení vlákna nebo zobrazení úkolů. Posledních šest položek je vypůjčeno přímo z okna zásobník volání a nezavádí žádné nové chování.  
  
 ![Místní nabídka v okně paralelní zásobníky](../debugger/media/parallel-contmenu.png "Parallel_ContMenu")  
  
|Položka nabídky|Popis|  
|---------------|-----------------|  
|Příznak|Označí vybranou položku jako příznak.|  
|Odznačit|Odoznačí vybranou položku.|  
|Uvolnění|Zablokuje vybranou položku.|  
|Uvolnění|Rozmrazí vybranou položku.|  
|Přejít na úlohu (vlákno)|Provede stejnou funkci jako pole se seznamem na panelu nástrojů, ale zachová stejný rámeček zásobníku, který je zvýrazněný.|  
|Přejít ke zdrojovému kódu|Přejde do umístění ve zdrojovém kódu, který odpovídá bloku zásobníku, na který uživatel kliknul pravým tlačítkem.|  
|Přepnout na rámec|Stejné jako odpovídající příkaz nabídky v okně zásobníku volání. Nicméně s paralelními zásobníky může více rámců odpovídat jednomu kontextu metody. Proto položka nabídky obsahuje podnabídky, z nichž každý představuje konkrétní rámec zásobníku. Je-li jeden z rámců zásobníku v aktuálním vlákně, je vybrána nabídka, která odpovídá danému bloku zásobníku.|  
|Přejít na zpětný překlad|Přejde do umístění v okně zpětný překlad, které odpovídá rámečku zásobníku, na který uživatel kliknul pravým tlačítkem.|  
|Zobrazit externí kód|Zobrazí nebo skryje externí kód.|  
|Hexadecimální zobrazení|Přepíná mezi zobrazením typu Decimal a hexadecimální.|  
|Informace o načítání symbolů|Zobrazí příslušné dialogové okno.|  
|Nastavení symbolu|Zobrazí příslušné dialogové okno.|  
  
## <a name="tasks-view"></a>Zobrazení úloh  
 Pokud vaše aplikace používá <xref:System.Threading.Tasks.Task?displayProperty=fullName> objekty (spravovaný kód) nebo `task_handle` objekty (nativní kód) k vyjádření paralelismu, můžete použít pole se seznamem na panelu nástrojů okna Paralelní zásobníky k přepnutí na *zobrazení úkolů*. Zobrazení úlohy zobrazuje zásobníky volání úkolů místo vláken. Zobrazení úkoly se od zobrazení vláken liší následujícím způsobem:  
  
- Nezobrazuje se zásobníky volání vláken, která nejsou spuštěnými úlohami.  
  
- Zásobníky volání vláken, která běží na úlohách, se vizuálně oříznou v horní a dolní části, aby se zobrazily relevantní rámce, které se vztahují k úkolům.  
  
- Pokud je více úloh v jednom vlákně, jsou zásobníky volání těchto úloh rozděleny do samostatných uzlů.  
  
  Následující ilustrace znázorňuje zobrazení úlohy paralelní zásobníky na pravé straně a odpovídající zobrazení vlákna na levé straně.  
  
  ![Zobrazení úlohy v okně paralelní zásobníky](../debugger/media/parallel-tasksview.png "Parallel_TasksView")  
  
  Chcete-li zobrazit celý zásobník volání, stačí přepnout zpět na zobrazení vláken kliknutím pravým tlačítkem myši na rámec zásobníku a následným kliknutím na příkaz **Přejít ke vláknu**.  
  
  Jak je popsáno v předchozí tabulce, přesunutím ukazatele myši na kontext metody můžete zobrazit další informace. Následující obrázek ukazuje informace v popisu zobrazení vlákna a zobrazení úkolů.  
  
  ![Popisy tlačítek v paralelních zásobnících okna](../debugger/media/parallel-stack-tooltips.png "Parallel_Stack_Tooltips")  
  
## <a name="method-view"></a>Zobrazení metody  
 V zobrazení vlákna nebo zobrazení úkolů můžete graf na aktuální metodě otočit kliknutím na ikonu zobrazení metody na panelu nástrojů. Zobrazení metody ukazuje na první pohled na všechny metody ve všech vláknech, které buď volají nebo jsou volány aktuální metodou. Následující ilustrace znázorňuje zobrazení vlákna a také způsob, jak vypadají stejné informace v zobrazení metody.  
  
 ![Zobrazení metody v okně paralelních zásobníků](../debugger/media/parallel-methodview.png "Parallel_MethodView")  
  
 Přepnutím na nový rámec zásobníku provedete tuto metodu aktuální metodou a způsobí, že okno zobrazí všechny volající a volané pro novou metodu. To může způsobit, že se některá vlákna objeví nebo zmizí ze zobrazení v závislosti na tom, jestli se tato metoda objeví na svých zásobníkech volání. Pokud se chcete vrátit do zobrazení zásobníku, klikněte znovu na tlačítko zobrazení metody panelu nástrojů.  
  
## <a name="see-also"></a>Viz také  
 [Návod: ladění paralelní aplikace](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Základy ladicího programu](../debugger/debugger-basics.md)   
 [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)   
 [Paralelní programování](https://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)   
 [Používání okna úlohy](../debugger/using-the-tasks-window.md)   
 [Návod: ladění paralelní aplikace](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Task – třída](../extensibility/debugger/task-class-internal-members.md)
