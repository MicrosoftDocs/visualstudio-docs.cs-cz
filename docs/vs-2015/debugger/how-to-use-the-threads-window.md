---
title: 'Postupy: použití okna vláken | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.threads
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- Thread.Name property
- debugger, Threads window
- SetThreadName function
- Threads window
- '@TIB'
- debugging [Visual Studio], threads
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
caps.latest.revision: 48
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: da41524fcb231ea399dbbd2a2904afd935e5c4f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "67824244"
---
# <a name="how-to-use-the-threads-window"></a>Postupy: Použití okna vláken
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V okně **vlákna** můžete prozkoumávat a pracovat s vlákny v aplikaci, kterou ladíte.  
  
 Okno **vlákna** obsahuje tabulku, kde každý řádek představuje vlákno ve vaší aplikaci. Ve výchozím nastavení tabulka obsahuje seznam všech vláken v aplikaci, ale můžete filtrovat seznam, aby se zobrazila pouze vlákna, která vás zajímají. Každý sloupec obsahuje jiný typ informací. Můžete také skrýt některé sloupce. Pokud zobrazíte všechny sloupce, zobrazí se v zleva doprava následující informace:  
  
- Sloupec příznak, kde můžete označit vlákno, pro které chcete věnovat zvláštní pozornost. Informace o tom, jak označit vlákno, naleznete v tématu [How to: flag and unflags](../debugger/how-to-flag-and-unflag-threads.md)Threads.  
  
- Sloupec aktivního vlákna, kde žlutá šipka označuje aktivní vlákno. Obrys šipky označuje vlákno, ve kterém se provádění podařilo přerušit do ladicího programu.  
  
- Sloupec **ID** , který obsahuje identifikační číslo pro každé vlákno.  
  
- Sloupec **spravovaného ID** , který obsahuje spravovaná identifikační čísla pro spravovaná vlákna.  
  
- Sloupec **kategorie** , který zařadí vlákna do kategorií jako vlákna uživatelského rozhraní, obslužné rutiny pro vzdálené volání procedur nebo pracovní vlákna. Speciální kategorie identifikuje hlavní vlákno aplikace.  
  
- Sloupec **Name** , který identifikuje jednotlivá vlákna podle názvu, pokud má jednu, nebo jako \<No Name> .  
  
- Sloupec **umístění** , který ukazuje, kde je vlákno spuštěno. Můžete rozbalit toto umístění a zobrazit plný zásobník volání pro vlákno.  
  
- Sloupec **priority** , který obsahuje prioritu nebo prioritu, kterou systém přiřadil ke každému vláknu.  
  
- Sloupec **masky spřažení** , což je rozšířený sloupec, který je obvykle skrytý. V tomto sloupci se zobrazuje maska spřažení procesoru pro každé vlákno. V systému s více procesory určuje maska spřažení procesory, ve kterých může být vlákno spuštěno.  
  
- Sloupec **pozastaveného počtu** , který obsahuje počet pozastavených. Tento počet Určuje, zda může být vlákno spuštěno. Vysvětlení pozastaveného počtu najdete v části "zmrazení a rozmrazování vláken" dále v tomto tématu.  
  
- Sloupec **název procesu** , který obsahuje proces, ke kterému patří každé vlákno. Tento sloupec může být užitečný při ladění více procesů, ale je obvykle skrytý.  
  
### <a name="to-display-the-threads-window-in-break-mode-or-run-mode"></a>Zobrazení okna vlákna v režimu pozastavení nebo režimu spuštění  
  
- V nabídce **ladění** přejděte na příkaz **Windows**a potom klikněte na možnost **vlákna**.  
  
### <a name="to-display-or-hide-a-column"></a>Zobrazení nebo skrytí sloupce  
  
- Na panelu nástrojů v horní části okna **vlákna** klikněte na **sloupce**a potom vyberte nebo zrušte zaškrtnutí názvu sloupce, který chcete zobrazit nebo skrýt.  
  
### <a name="to-switch-the-active-thread"></a>Přepnutí aktivního vlákna  
  
- Proveďte jeden z následujících kroků:  
  
  - Dvakrát klikněte na jakékoli vlákno.  

  - Klikněte pravým tlačítkem na vlákno a klikněte na **Přepnout do vlákna**.  

    Žlutá šipka se zobrazí vedle nového aktivního vlákna. Šedý obrys šipky identifikuje vlákno, ve kterém se provádění podařilo přerušit do ladicího programu.  
  
## <a name="grouping-and-sorting-threads"></a>Seskupování a řazení vláken  
 Při seskupování vláken se v tabulce zobrazí záhlaví pro každou skupinu. Nadpis obsahuje popis skupiny, například "pracovní vlákno" nebo "neoznačené vlákna" a ovládací prvek stromu. Členská vlákna každé skupiny se zobrazí pod záhlavím skupiny. Chcete-li skrýt členské vlákna pro skupinu, můžete k sbalení skupiny použít ovládací prvek strom.  
  
 Vzhledem k tomu, že seskupování mají přednost před řazením, můžete seskupit vlákna podle kategorií, například a seřadit je podle ID v rámci každé kategorie.  
  
#### <a name="to-sort-threads"></a>Řazení vláken  
  
1. Na panelu nástrojů v horní části okna **vlákna** klikněte na tlačítko v horní části libovolného sloupce.  
  
     Vlákna jsou nyní seřazena podle hodnot v tomto sloupci.  
  
2. Pokud chcete změnit pořadí řazení, klikněte znovu na stejné tlačítko.  
  
     Vlákna, která se objevila v horní části seznamu, se teď zobrazují dole.  
  
#### <a name="to-group-threads"></a>Seskupení vláken  
  
- Na panelu nástrojů okna **vlákna** klikněte na seznam **Seskupit podle** a potom klikněte na kritéria, podle kterých chcete seskupit vlákna.  
  
#### <a name="to-sort-threads-within-groups"></a>Řazení vláken v rámci skupin  
  
1. Na panelu nástrojů v horní části okna **vlákna** klikněte na seznam **Seskupit podle** a potom klikněte na kritéria, podle kterých chcete seskupit vlákna.  
  
2. V okně **vlákna** klikněte na tlačítko v horní části libovolného sloupce.  
  
     Vlákna jsou nyní seřazena podle hodnot v tomto sloupci.  
  
#### <a name="to-expand-or-collapse-all-groups"></a>Chcete-li rozbalit nebo sbalit všechny skupiny  
  
- Na panelu nástrojů v horní části okna **vlákna** klikněte na **Rozbalit skupiny** nebo **sbalit skupiny**.  
  
## <a name="searching-for-specific-threads"></a>Hledání konkrétních vláken  
 V nástroji [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] můžete vyhledat vlákna, které odpovídají zadanému řetězci. Při hledání vláken v okně **vlákna** zobrazí okno všechna vlákna, která odpovídají hledanému řetězci v libovolném sloupci. Tyto informace zahrnují umístění vlákna, které se zobrazí v horní části zásobníku volání ve sloupci **umístění** . Ve výchozím nastavení se ale neprohledávají úplný zásobník volání.  
  
#### <a name="to-search-for-specific-threads"></a>Hledání konkrétních vláken  
  
- Na panelu nástrojů v horní části okna **vlákna** klikněte do **vyhledávacího** pole a buď na:  
  
  - Zadejte hledaný řetězec a stiskněte klávesu ENTER.  

    \- ani  

  - Klikněte na rozevírací seznam vedle pole **hledání** a vyberte hledaný řetězec z předchozího hledání.  
  
- Volitelné Chcete-li do hledání zahrnout plný zásobník volání, vyberte možnost **zásobník volání vyhledávání**.  
  
## <a name="freezing-and-thawing-threads"></a>Zamrznutí a rozmrazit vlákna  
 Při zablokování vlákna systém nespustí provádění vlákna, i když jsou prostředky k dispozici.  
  
 V nativním kódu můžete pozastavit nebo obnovit vlákna voláním funkcí systému Windows `SuspendThread` a `ResumeThread` nebo funkcí MFC [CWinThread:: SuspendThread](https://msdn.microsoft.com/library/57189c7e-fd71-42e5-bc4b-3de7cd373d28) a [CWinThread:: ResumeThread](https://msdn.microsoft.com/library/d6f97a2f-5c9f-4ee1-b978-d74938784db5). Pokud voláte `SuspendThread` nebo `ResumeThread` , změníte *počet pozastavených*, který se zobrazí v okně **vlákna** . Nicméně pokud zadáte nebo odblokovat nativní vlákno, nebudete měnit počet pozastavených. V nativním kódu vlákno nemůže být spuštěno, pokud není uvolněno a má pozastavený počet nula.  
  
 Ve spravovaném kódu zamrznutí nebo rozmrazení vlákna změní počet pozastavených. Ve spravovaném kódu má zmrazený podproces počet pozastavených vláken 1. V nativním kódu, zmrazené vlákno má pozastavený počet 0, pokud vlákno nebylo pozastaveno `SuspendThread` voláním.  
  
> [!NOTE]
> Při ladění volání z nativního kódu do spravovaného kódu je spravovaný kód spuštěn ve stejném fyzickém vlákně jako nativní kód, který jej volal. Pozastavení nebo zmrazení nativního vlákna zablokuje také spravovaný kód.  
  
#### <a name="to-freeze-or-thaw-execution-of-a-thread"></a>Zablokování nebo odmrazení spuštění vlákna  
  
- Na panelu nástrojů v horní části okna **vlákna** klikněte na **ukotvit vlákna** nebo **uvolnit vlákna**.  
  
     Tato akce ovlivní pouze vlákna, která jsou vybrána v okně **vlákna** .  
  
## <a name="displaying-flagged-threads"></a>Zobrazení vláken s příznakem  
 Můžete označit vlákno, které chcete poskytnout zvláštní pozornost, a to tak, že ho označíte ikonou v okně **vlákna** . Další informace naleznete v tématu [How to: Flags and unflags Threads](../debugger/how-to-flag-and-unflag-threads.md). V okně vlákna se můžete rozhodnout zobrazit všechna vlákna nebo pouze vlákna označená příznakem.  
  
#### <a name="to-display-only-flagged-threads"></a>Chcete-li zobrazit pouze vlákna označená příznakem  
  
- Klikněte na tlačítko příznak v levém horním rohu okna **vlákna** .  
  
## <a name="displaying-thread-call-stacks-and-switching-between-frames"></a>Zobrazení zásobníků volání vlákna a přepínání mezi snímky  
 V programu s více vlákny má každé vlákno vlastní zásobník volání. Okno **vlákna** nabízí pohodlný způsob, jak tyto zásobníky zobrazit.  
  
#### <a name="to-view-the-call-stack-of-a-thread"></a>Zobrazení zásobníku volání vlákna  
  
- Ve sloupci **umístění** klikněte na Obrácený trojúhelník vedle umístění vlákna.  
  
     Umístění rozbalí pro zobrazení zásobníku volání pro vlákno.  
  
#### <a name="to-view-or-collapse-the-call-stacks-of-all-threads"></a>Zobrazení nebo sbalení zásobníků volání všech vláken  
  
- Na panelu nástrojů v horní části okna **vlákna** klikněte na **Rozbalit zásobníky volání** nebo **sbalení zásobníků volání**.  
  
## <a name="see-also"></a>Viz také  
 [Ladění vícevláknových aplikací](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Návod: Ladění vícevláknové aplikace](../debugger/walkthrough-debugging-a-multithreaded-application.md)
