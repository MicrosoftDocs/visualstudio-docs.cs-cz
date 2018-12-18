---
title: 'Postupy: použití okna zásobník volání | Dokumentace Microsoftu'
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
- vs.debug.callstack
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- aspx
helpviewer_keywords:
- threading [Visual Studio], displaying calls to or from
- functions [debugger], viewing code on call stack
- disassembly code
- breakpoints, Call Stack window
- debugging [Visual Studio], switching to another stack frame
- debugging [Visual Studio], Call Stack window
- Call Stack window, viewing source code for functions on the call stack
- stack, switching stack frames
- Call Stack window, viewing disassembly code for functions on the call stack
ms.assetid: 5154a2a1-4729-4dbb-b675-db611a72a731
caps.latest.revision: 45
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c45f0a645945e68b7b3d21eefe2f981b9b4b352f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751014"
---
# <a name="how-to-use-the-call-stack-window"></a>Postupy: Použití okna Zásobník volání
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

S použitím **zásobník volání** okně můžete zobrazit volání funkce nebo procedury, které jsou aktuálně na zásobníku.  
  
 **Zásobník volání** okně se zobrazí název jednotlivých funkcí a programovací jazyk, který je napsán. Název funkce nebo procedury mohou doprovázet volitelné informace, jako je například název modulu, číslo řádku a názvy parametrů, typy a hodnoty. Zobrazení této volitelné informace můžete zapnout nebo vypnout.  
  
 Žlutá šipka označuje zásobník snímků, kde je nyní umístěn ukazatel spuštění. Ve výchozím nastavení, jedná o rámec, jehož informace se zobrazí ve zdroji, **zpětný překlad**, **lokální**, **Watch**, a **automatické hodnoty** systému windows. Pokud chcete změnit kontext na jiný rámec v zásobníku, můžete to udělat **zásobník volání** okna.  
  
 Pokud nejsou k dispozici pro celý zásobník volání symboly pro ladění **zásobník volání** okna nemusí být schopno zobrazit správné informace pro tuto část zásobníku volání. Zobrazí se následující zápis:  
  
 [Rámce uvedené níže nemusí být správné nebo chybí, se nenačetly žádné symboly pro name.dll]  
  
 Ve spravovaném kódu ve výchozím nastavení. **zásobník volání** okno skrývá informace o neuživatelském kódu. Následující zápis se zobrazí místo skryté informace:  
  
 **[\<Externí kód >]**  
  
 Neuživatelský kód je jakýkoli kód, který není "můj kód můžete zobrazit informace v zásobníku volání pro neuživatelský kód pomocí místní nabídky.  
  
 Pomocí místní nabídky můžete zvolit, jestli se má zobrazit volání mezi vlákny.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které se zobrazí mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, vyberte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-the-call-stack-window-in-break-mode-or-in-run-mode"></a>Chcete-li zobrazit okno zásobníku volání v režimu přerušení nebo v režimu spuštění  
  
-   Na **ladění** nabídce vyberte možnost **Windows** a potom klikněte na tlačítko **zásobník volání**.  
  
### <a name="to-change-the-optional-information-displayed"></a>Změna zobrazených volitelných informací  
  
-   Klikněte pravým tlačítkem myši **zásobník volání** okno a set nebo zrušte **zobrazit \<**  _informace, které mají_ **>**.  
  
### <a name="to-display-non-user-code-frames-in-the-call-stack-window"></a>K zobrazení snímků bez uživatelského kódu v okně zásobník volání  
  
-   Klikněte pravým tlačítkem myši **zásobník volání** okna a vyberte **zobrazit externí kód**.  
  
### <a name="to-switch-to-another-stack-frame"></a>Chcete-li přepnout na jiný rámec zásobníku  
  
1.  V **zásobník volání** okna, klikněte pravým tlačítkem myši rámec jehož kód a data, která chcete zobrazit.  
  
2.  Vyberte **přepnout na rámec**.  
  
     Zelená šipka s vlnitým ocáskem se objeví vedle snímku, který jste vybrali. Spuštění ukazatele zůstane v původním rámci stále označeno žlutou šipkou. Pokud vyberete **krok** nebo **pokračovat** z **ladění** nabídky, spuštění bude pokračovat v původním rámci, ne ve vámi vybraném.  
  
### <a name="to-display-calls-to-or-from-another-thread"></a>K zobrazení volání do nebo z jiného vlákna  
  
-   Klikněte pravým tlačítkem myši **zásobník volání** okna a vyberte **zahrnout hovory do/z jiných podprocesů**.  
  
### <a name="to-view-the-source-code-for-a-function-on-the-call-stack"></a>Chcete-li zobrazit zdrojový kód pro funkci v zásobníku volání  
  
-   V **zásobník volání** okna, klikněte pravým tlačítkem na funkci, jejíž zdrojový kód chcete zobrazit a vybrat **přejít ke zdrojovému kódu**.  
  
### <a name="to-visually-trace-the-call-stack"></a>Vizuální trasování zásobníku volání  
  
1.  V **zásobník volání** okno, otevřete místní nabídku. Zvolte **zobrazit zásobník volání na mapě kódu**. (Klávesnice: **CTRL** + **SHIFT** + **`**)  
  
     Zobrazit [mapování metod v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
### <a name="to-view-the-disassembly-code-for-a-function-on-the-call-stack"></a>Chcete-li zobrazit zpětný překlad kódu pro funkci v zásobníku volání  
  
-   V **zásobník volání** okna, klikněte pravým tlačítkem na funkci, jejíž zpětně přeložený kód chcete zobrazit a vybrat **přejít na zpětný překlad**.  
  
### <a name="to-run-to-a-specific-function-from-the-call-stack-window"></a>Spuštění specifické funkce z okna zásobník volání  
  
-  V **zásobník volání** okna, vyberte funkci, klepněte pravým tlačítkem myši a zvolte **spustit ke kurzoru**.  
  
### <a name="to-set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>Nastavení zarážky ve výstupním bodě volání funkce  
  
-   Zobrazit [nastavení zarážky na volání funkce zásobníku](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_the_call_stack_window).  
  
### <a name="to-load-symbols-for-a-module"></a>Načtení symbolů pro modul  
  
-   V **zásobník volání** okna, klikněte pravým tlačítkem myši na rámeček, který zobrazuje modul, jehož symboly chcete znovu načíst a vyberte **načíst symboly**.  
  
## <a name="loading-symbols"></a>Načítání symbolů  
 V **zásobník volání** okno, které můžete načíst symboly ladění pro kód, který nemá aktuálně načtené symboly. Tyto symboly mohou být v rozhraní .NET Framework nebo systémové symboly stažené ze serverů Microsoft veřejnými symboly nebo symboly v symbolické cestě v počítači, který ladíte.  
  
 Zobrazit [zadání symbolu (.pdb) a zdrojové soubory](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols"></a>Načtení symbolů  
  
1.  V **zásobník volání** okna, klikněte pravým tlačítkem na snímek pro symboly, které nejsou načtené. Snímek bude nepřístupný.  
  
2.  Přejděte na **načíst symboly z** a potom klikněte na tlačítko **Microsoft Symbol Servers** nebo **cesty k symbolu**.  
  
#### <a name="to-set-the-symbol-path"></a>Chcete-li nastavit cestu k symbolu  
  
1.  V **zásobník volání** okně zvolte **nastavení symbolu** z místní nabídky.  
  
     **Možnosti** zobrazí se dialogové okno a **symboly** zobrazí se stránka.  
  
2.  Klikněte na tlačítko **Symbol nastavení**.  
  
3.  V **možnosti** dialogovém okně klikněte na ikonu složky.  
  
     V **Symbol umístění souborů (.pdb)** pole, se zobrazí kurzor.  
  
4.  Zadejte cestu adresáře na umístění symbolu v počítači, který ladíte. Pro místní ladění je to místního počítače. Pro vzdálené ladění, je vzdáleném počítači.  
  
5.  Klikněte na tlačítko **OK** zavřete **možnosti** dialogové okno.  
  
## <a name="see-also"></a>Viz také  
 [Smíšený kód a chybějící informace v okně zásobníku volání](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)   
 [Postupy: Změna numerického formátu ladicí program Windows](http://msdn.microsoft.com/library/cd593847-a625-411d-a430-b798346ef18f)   
 [Zobrazení dat v ladicím programu](../debugger/viewing-data-in-the-debugger.md)   
 [Zadání symbolu (.pdb) a zdrojové soubory](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Použití zarážek](../debugger/using-breakpoints.md)





