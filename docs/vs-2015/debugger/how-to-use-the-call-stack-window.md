---
title: 'Postupy: použití okna zásobník volání | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 84c0bfead1633da13b4284cad04ace674045b057
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697477"
---
# <a name="how-to-use-the-call-stack-window"></a>Postupy: Použití okna Zásobník volání
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí okna **zásobník volání** můžete zobrazit volání funkce nebo procedury, které jsou aktuálně v zásobníku.  
  
 Okno **zásobník volání** zobrazuje název každé funkce a programovací jazyk, ve kterém je napsán. Název funkce nebo procedury může doprovázet volitelné informace, jako je název modulu, číslo řádku a názvy parametrů, typy a hodnoty. Zobrazení těchto volitelných informací lze zapnout nebo vypnout.  
  
 Žlutá šipka identifikuje rámec zásobníku, kde se aktuálně nachází ukazatel provádění. Ve výchozím nastavení se jedná o rámec, jehož informace se zobrazí v oknech zdroj, **zpětný překlad**, **místní**hodnoty, **kukátko**a **Automatické** hodnoty. Chcete-li změnit kontext na jiný rámec v zásobníku, můžete to provést v okně **zásobník volání** .  
  
 Pokud nejsou symboly ladění k dispozici pro část zásobníku volání, okno **zásobník volání** nemusí být schopno zobrazit správné informace pro danou část zásobníku volání. Zobrazí se následující zápis:  
  
 [Rámce uvedené níže nemusí být správné nebo chybí, pro name.dll nejsou načteny žádné symboly.]  
  
 Ve spravovaném kódu ve výchozím nastavení. okno **zásobník volání** skrývá informace o kódu, který není uživatelem. Místo skrytých informací se zobrazí následující notace:  
  
 **[\<External Code>]**  
  
 Neuživatelský kód je jakýkoli kód, který není "můj kód, můžete zvolit zobrazení informací zásobníku volání pro neuživatelský kód pomocí místní nabídky.  
  
 Pomocí místní nabídky můžete zvolit, zda se mají zobrazit volání mezi vlákny.  
  
> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **Nastavení importu a exportu** v nabídce **nástroje** . Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-the-call-stack-window-in-break-mode-or-in-run-mode"></a>Zobrazení okna zásobník volání v režimu pozastavení nebo v režimu spuštění  
  
- V nabídce **ladění** vyberte možnost **Windows** a potom klikněte na možnost **zásobník volání**.  
  
### <a name="to-change-the-optional-information-displayed"></a>Změna zobrazených volitelných informací  
  
- Klikněte pravým tlačítkem myši na okno **zásobník volání** a nastavte nebo zrušte zaškrtnutí **Zobrazit \<**_the information that you want_**> **.  
  
### <a name="to-display-non-user-code-frames-in-the-call-stack-window"></a>Zobrazení snímků neuživatelských kódů v okně zásobník volání  
  
- Klikněte pravým tlačítkem myši na okno **zásobník volání** a vyberte možnost **Zobrazit externí kód**.  
  
### <a name="to-switch-to-another-stack-frame"></a>Přepnutí na jiný rámec zásobníku  
  
1. V okně **zásobník volání** klikněte pravým tlačítkem myši na rámec, jehož kód a data chcete zobrazit.  
  
2. Vyberte **přepínač přepnout na rámec**.  
  
     Vedle vybraného rámce se zobrazí zelená šipka se zakončením. Ukazatel spuštění zůstane v původním snímku, který je stále označený žlutou šipkou. Pokud vyberete **Krok** nebo **pokračovat** z nabídky **ladění** , bude spuštění pokračovat v původním snímku, nikoli v rámci vybraného rámce.  
  
### <a name="to-display-calls-to-or-from-another-thread"></a>Zobrazení volání do nebo z jiného vlákna  
  
- Klikněte pravým tlačítkem myši na okno **zásobník volání** a vyberte možnost **Zahrnout volání do/z jiných vláken**.  
  
### <a name="to-view-the-source-code-for-a-function-on-the-call-stack"></a>Zobrazení zdrojového kódu funkce v zásobníku volání  
  
- V okně **zásobník volání** klikněte pravým tlačítkem myši na funkci, jejíž zdrojový kód chcete zobrazit, a vyberte **Přejít ke zdrojovému kódu**.  
  
### <a name="to-visually-trace-the-call-stack"></a>Vizuální trasování zásobníku volání  
  
1. V okně **zásobník volání** otevřete místní nabídku. Vyberte možnost **Zobrazit zásobník volání na mapě kódu**. (Klávesnice: **CTRL**  +  **SHIFT**  +  **`** )  
  
     Viz [metody map v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
### <a name="to-view-the-disassembly-code-for-a-function-on-the-call-stack"></a>Zobrazení kódu zpětného překladu pro funkci v zásobníku volání  
  
- V okně **zásobník volání** klikněte pravým tlačítkem myši na funkci, jejíž kód zpětného překladu chcete zobrazit, a vyberte možnost **Přejít na zpětný překlad**.  
  
### <a name="to-run-to-a-specific-function-from-the-call-stack-window"></a>Spuštění konkrétní funkce z okna zásobník volání  
  
- V okně **zásobník volání** vyberte funkci, klikněte pravým tlačítkem myši a zvolte možnost **Spustit ke kurzoru**.  
  
### <a name="to-set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>Nastavení zarážky v bodu ukončení volání funkce  
  
- Viz [Nastavení zarážky ve funkci zásobníku volání](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_the_call_stack_window).  
  
### <a name="to-load-symbols-for-a-module"></a>Načtení symbolů pro modul  
  
- V okně **zásobník volání** klikněte pravým tlačítkem myši na rámec, který zobrazuje modul, jehož symboly chcete znovu načíst, a vyberte možnost **načíst symboly**.  
  
## <a name="loading-symbols"></a>Načítání symbolů  
 V okně **zásobník volání** můžete načíst symboly ladění pro kód, který aktuálně nemá načteny symboly. Tyto symboly mohou být .NET Framework nebo systémové symboly stažené ze serverů Microsoft Public symbol Servers nebo symboly v cestě symbolů v počítači, který ladíte.  
  
 Viz [určení symbolu (. pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) .  
  
#### <a name="to-load-symbols"></a>Načtení symbolů  
  
1. V okně **zásobník volání** klikněte pravým tlačítkem myši na rámec, pro který nejsou načteny symboly. Rámec bude ztlumený.  
  
2. Najeďte na **načíst symboly z** a pak klikněte na **Microsoft Symbol Servers** nebo **cesta k symbolu**.  
  
#### <a name="to-set-the-symbol-path"></a>Nastavení cesty k symbolu  
  
1. V okně **zásobník volání** vyberte v místní nabídce možnost **Nastavení symbolu** .  
  
     Otevře se dialogové okno **Možnosti** a zobrazí se stránka **symboly** .  
  
2. Klikněte na **Nastavení symbolu**.  
  
3. V dialogovém okně **Možnosti** klikněte na ikonu složky.  
  
     V poli **umístění souborů symbolů (. pdb)** se zobrazí kurzor.  
  
4. Zadejte cestu k adresáři do umístění symbolu v počítači, který ladíte. Pro místní ladění je to váš místní počítač. Pro vzdálené ladění je to vzdálený počítač.  
  
5. Kliknutím na tlačítko **OK** zavřete dialogové okno **Možnosti** .  
  
## <a name="see-also"></a>Viz také  
 [Smíšený kód a chybějící informace v okně zásobník volání](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)   
 [Postupy: Změna číselného formátu oken ladicího programu](https://msdn.microsoft.com/library/cd593847-a625-411d-a430-b798346ef18f)   
 [Zobrazení dat v ladicím programu](../debugger/viewing-data-in-the-debugger.md)   
 [Zadat symbol (PDB) a zdrojové soubory](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Použití zarážek](../debugger/using-breakpoints.md)
