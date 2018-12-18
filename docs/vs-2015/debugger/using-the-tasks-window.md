---
title: Using the Tasks Window | Dokumentace Microsoftu
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
manager: ghogen
ms.openlocfilehash: fa59e1e57750c9c2075c10c76ab5c518ed0e8686
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793898"
---
# <a name="using-the-tasks-window"></a>Používání okna úloh
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Úlohy** okno vypadá podobně jako **vlákna** okna, s tím rozdílem, že se zobrazuje informace o <xref:System.Threading.Tasks.Task?displayProperty=fullName>, [task_handle –](http://msdn.microsoft.com/library/b4af5b28-227d-4488-8194-0a0d039173b7), nebo [WinJS.Promise ](http://msdn.microsoft.com/library/windows/apps/br211867.aspx) objekty namísto každé vlákno. Například vlákna úlohy představuje asynchronní operace, které můžou běžet souběžně; ale více úkolů může spustit ve stejném vlákně. Zobrazit [asynchronní programování v jazyce JavaScript (aplikace pro Windows Store)](http://msdn.microsoft.com/library/windows/apps/hh700330.aspx) Další informace.  
  
 Ve spravovaném kódu, můžete použít **úlohy** okno při práci s <xref:System.Threading.Tasks.Task?displayProperty=fullName> objekty nebo se **await** a **asynchronní** klíčová slova (**Await** a **asynchronní** v VisualBasic). Další informace o úlohách ve spravovaném kódu najdete v tématu [paralelního programování](http://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d).  
  
 V nativním kódu, můžete použít **úlohy** okno při práci s [skupiny úloh](http://msdn.microsoft.com/library/42f05ac3-2098-494a-ba84-737fcdcad077), [paralelní algoritmy](http://msdn.microsoft.com/library/045dca7b-4d73-4558-a44c-383b88a28473), [asynchronních agentů](http://msdn.microsoft.com/library/6cf6ccc6-87f1-4e14-af15-ea8ba58fef1a), a [prostých úloh](http://msdn.microsoft.com/library/9aba278c-e0c9-4ede-b7c6-fedf7a365d90). Další informace o úlohách v nativním kódu, naleznete v tématu [Concurrency Runtime](http://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c).  
  
 V jazyce JavaScript můžete použít okno úlohy při práci s kódem .then promise.  
  
 Můžete použít **úlohy** okna pokaždé, když jste přerušení ladicího programu. Je k dispozici na **ladění** nabídky kliknutím **Windows** a pak levým na **úlohy**. Je vidět na následujícím obrázku **úlohy** okna v její výchozí režim.  
  
 ![Okno Paralelní úkoly](../debugger/media/parallel-tasks-window.png "Parallel_Tasks_Window")  
  
> [!NOTE]
>  Ve spravovaném kódu <xref:System.Threading.Tasks.Task> , který je ve stavu <xref:System.Threading.Tasks.TaskStatus>, <xref:System.Threading.Tasks.TaskStatus>, nebo <xref:System.Threading.Tasks.TaskStatus> nemusí být zobrazeny v okně úlohy při spravovaná vlákna jsou v režimu spánku nebo připojení stavu.  
  
## <a name="tasks-column-information"></a>Informace o sloupci úlohy  
 Sloupce v **úlohy** v okně zobrazí následující informace.  
  
|Název sloupce|Popis|  
|-----------------|-----------------|  
|**příznaky**|Zobrazuje úlohy, které jsou označeny příznakem a umožňuje označit nebo zrušit označení příznakem úlohu.|  
|**Ikony**|Žlutá šipka označuje aktuální úlohu. Aktuální úkol je úkol úplně nahoře v aktuálním vláknu.<br /><br /> Bílé šipka označuje zásadní úloh, to znamená, ten, který byl aktuální v době byla vyvolána ladicí program.<br /><br /> Ikona pozastavení označuje úlohu, která byla zmrazené uživatelem. Můžete ukotvit a uvolnění úlohy kliknutím pravým tlačítkem myši v seznamu.|  
|**ID**|Číslo poskytnuté systémem pro úlohu. V nativním kódu jde o adresu úkolu.|  
|**Status**|Aktuální stav (naplánované, aktivní, jeví jako zablokované, čekání nebo dokončené) úlohy. Naplánované úlohy je ten, který dosud nebyla spuštěna a proto se ještě nemá zásobník volání, přiřazené vlákno nebo související informace.<br /><br /> Aktivní úlohy je ten, který se spouští kód před přerušení v ladicím programu.<br /><br /> Čekání úlohy je ten, který je zablokovaná, protože se čeká na událost má být signalizován, uvolnění zámku nebo na dokončení jiné úlohy.<br /><br /> Jeví jako zablokované úkol je úkol čekání, jehož vlákna je zablokovaná s jiným vláknem.<br /><br /> Najeďte myší **stav** buňky jeví jako zablokované nebo čekající úlohy zobrazíte další informace o bloku. **Upozornění:** **úlohy** okno hlásí zablokování pouze pro zablokování úkol, který používá synchronizační jednoduchého typu, který je podporovaný počkejte procházení řetězce (WCT). Například pro jeví jako zablokované <xref:System.Threading.Tasks.Task> objektu, který používá WCT, ladicí program hlásí **zablokována čekáním**. Jeví jako zablokované úkolu, který je spravovaný nástrojem modulu Runtime souběžnosti, který nepoužívá WCT, ladicí program hlásí **čekání**. Další informace o WCT najdete v tématu [počkejte procházení řetězu](http://msdn.microsoft.com/library/ms681622\(VS.85\).aspx).|  
|**Čas spuštění**|Doba, jakou úloha začal být aktivní.|  
|**Doba trvání**|Počet sekund, po které byl aktivní úloha.|  
|**Čas dokončení**|Čas, kdy úloha dokončena.|  
|**Poloha**|Aktuální umístění v zásobníku volání úlohy. Najeďte myší tuto buňku, chcete-li zobrazit celý zásobník volání pro úlohu. Naplánované úlohy nemají hodnotu v tomto sloupci.|  
|**Úloha**|Metoda počáteční a všechny argumenty, které byly předány pro úkol při vytvoření rovnou uložil.|  
|**Nadřazené**|ID úkolu, který vytvořil tuto úlohu. Pokud je toto pole prázdné, úloha nemá žádný nadřazený objekt. To platí pouze pro spravované aplikace.|  
|**Přiřazení vlákna**|ID a název vlákna, na kterém je spuštěn úkol.|  
|**Návratový stav**|Stav úlohy po jeho dokončení. Návratový stav hodnoty jsou **úspěch**, **zrušeno**, a **chyba**.|  
|**AppDomain**|Pro spravovaný kód domény aplikace, ve kterém je spuštěn úkol.|  
|**task_group**|Pro nativní kód, adresa [task_group –](http://msdn.microsoft.com/library/b4af5b28-227d-4488-8194-0a0d039173b7) objekt, který naplánované úlohy. Asynchronní agenti a jednoduché úlohy je tento sloupec nastavena na 0.|  
|Proces|ID procesu, který je spuštěn úkol na.|  
|Asynchronní stav|Pro spravovaný kód, stav úlohy. Ve výchozím nastavení je tento sloupec skrytý. Chcete-li zobrazit tento sloupec, otevřete kontextovou nabídku pro jednu z záhlaví sloupců. Zvolte **sloupce**, **AsyncState**.|  
  
 Sloupce můžete přidat do zobrazení tak, že pravým tlačítkem myši na záhlaví sloupce a následným výběrem sloupce, které chcete. (Odebrat sloupce tím, že zrušíte výběr). Můžete také změnit uspořádání sloupců jejich přetažením doleva nebo doprava. Místní nabídka sloupce je zobrazena na následujícím obrázku.  
  
 ![Zobrazit nabídku v okno paralelní úkoly](../debugger/media/parallel-tasks-contextmenu.png "Parallel_Tasks_ContextMenu")  
  
## <a name="sorting-tasks"></a>Řazení úkolů  
 Seřadit podle sloupce kritéria úloh, klikněte na záhlaví sloupce. Například klepnutím **ID** záhlaví sloupce můžete řazení úloh podle ID úlohy: 1,2,3,4,5 a tak dále. Chcete-li změnit směr řazení, znovu klikněte na záhlaví sloupce. Aktuální řazení sloupců a pořadí řazení je indikován šipku ve sloupci.  
  
## <a name="grouping-tasks"></a>Seskupení úkolů  
 Můžete seskupit podle libovolného sloupce v zobrazení seznamu úloh. Například kliknutím pravým tlačítkem myši **stav** záhlaví sloupce a pak levým na **Seskupit podle stavu**, lze použít k seskupení všechny úlohy, které mají stejný stav. Například je možné rychle, uvidíte čekání úlohy tak, aby se mohli soustředit na Proč jsou zablokované. Můžete také sbalit skupiny, které nejsou zajímavé během relace ladění. Stejným způsobem můžete seskupit podle jiných sloupců. Skupinu lze (zrušit) příznakem jednoduše kliknutím na tlačítko vedle záhlaví skupiny. Je vidět na následujícím obrázku **úlohy** okno v seskupených režimu.  
  
 ![Seskupené režim v okně paralelní úlohy](../debugger/media/parallel-tasks-groupedmode.png "Parallel_Tasks_GroupedMode")  
  
## <a name="parent-child-view"></a>Nadřazeného a podřízeného prvku  
 (Toto zobrazení je k dispozici pouze pro spravovaný kód). Pravým tlačítkem myši na záhlaví sloupce a poté klepnutím na **nadřazeného a podřízeného prvku**, seznam úkolů můžete změnit hierarchické zobrazení, ve kterých každé podřízené úlohy je dílčí uzel, který můžete zobrazení nebo skrytí podle svého nadřazeného objektu. Na následujícím obrázku jsou uvedeny úlohy v zobrazení nadřízený podřízený.  
  
 ![Nadřazené&#45;podřízené zobrazení, v okno paralelní úkoly](../debugger/media/parallel-tasks-parentchildview.png "Parallel_Tasks_ParentChildView")  
  
## <a name="flagging-tasks"></a>Nastavení příznaku úlohy  
 Můžete označit příznakem vlákna seznam úloh, na kterém je úloha spuštěná tak, že vyberete úlohu položky a následným výběrem možnosti **příznak** v místní nabídce nebo kliknutím na ikonu příznaku v prvním sloupci. Pokud označíte některé úlohy, můžete pak seřadit sloupec příznaku uveďte všechny úkoly s příznakem do horní části tak, aby se mohli soustředit na nich. Můžete také použít **paralelní zásobníky** okna, chcete-li zobrazit pouze označená příznakem úlohy. To vám umožňuje odfiltrovat úlohy, které vás zajímají není pro ladění. Příznaky nejsou trvalé mezi relacemi ladění.  
  
## <a name="freezing-and-thawing-tasks"></a>Zmrazení a uvolnění úloh  
 Může zablokovat vlákno, na kterém je úloha spuštěná pravým tlačítkem na položku seznamu úkolů a potom klikněte na **zablokovat přiřazené vlákno**. (Pokud je již zmrazen úkol, je příkaz **uvolnit přiřazené vlákno**.) Po ukotvení vlákno nebude spuštěno toto vlákno při krokovat kód po aktuální zarážku. **Zablokovat všechna vlákna, ale tento** příkazu se zablokuje všechna vlákna kromě toho, který provádí položky seznamu úkolů.  
  
 Následující obrázek znázorňuje dalšími položkami nabídky pro každý úkol.  
  
 ![Vlákno nabídku v okno paralelní úkoly](../debugger/media/parallel-tasks-contextmenu2.png "Parallel_Tasks_ContextMenu2")  
  
## <a name="see-also"></a>Viz také  
 [Základy ladicího programu](../debugger/debugger-basics.md)   
 [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)   
 [Paralelní programování](http://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)   
 [Concurrency Runtime](http://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c)   
 [Použití okna paralelní zásobníky](../debugger/using-the-parallel-stacks-window.md)   
 [Návod: Ladění paralelní aplikace](../debugger/walkthrough-debugging-a-parallel-application.md)



