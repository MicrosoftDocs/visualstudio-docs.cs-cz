---
title: Použití zarážek | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vs.debug.breakpointswin
- vs.debug.disassembly.insert
- vs.debug.sourcewin.edit
- vs.debug.file
- vs.debug.breakpt.new
- vs.debug.whenbreakpointishit
- vs.debug.breakpt.choose
- vs.debug.breakpt.location.address
- vs.debug.breakpt.constraints
- vs.debug.breakpoints.delete
- vs.debug.breakpt.location.data
- vc.breakpoints
- vs.debug.breakpt.condition
- vs.debug.breakpt.location.function
- vs.debug.breakpoints
- vs.debug.menu.insert
- vs.debug.filenames
- vs.debug.breakpt.action
- vs.debug.sourcewin.insert
- vs.debug.address
- vs.debug.data
- vs.debug.func
- vs.debug.breakpt.location.file
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- breakpoints, about breakpoints
ms.assetid: 020b2e97-3b3e-4b2c-872d-b5c6025e120e
caps.latest.revision: 63
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d980fd2367545eb5c824bacc507d9ced9aa2d723
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765958"
---
# <a name="using-breakpoints"></a>Použití zarážek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Můžete nastavit zarážky, pokud chcete zastavit spuštění ladicího programu, třeba tak, aby stavu kódu proměnné naleznete v tématu nebo si prohlédnout zásobníku volání. Jsou jedním z nejdůležitějších technik ladění mezi nástroji pro vývojáře sady nástrojů.
  
##  <a name="BKMK_Overview"></a> Nastavení zarážky funkce ve zdrojovém kódu  
 Nastavení zarážky funkce ve zdrojovém kódu kliknutím do levého okraje soubor zdrojového kódu nebo vložení kurzor na řádek kódu a stiskněte klávesu F9. Zarážka se zobrazí jako červená tečka na levém okraji a také znázorněná na řádek kódu:  
  
 ![Nastavit zarážku](../debugger/media/basicbreakpoint.png "BasicBreakpoint")  
  
 Při spuštění tohoto kódu v ladicím programu, zastaví provádění pokaždé, když se dosažení zarážky, před provedením kódu na daném řádku. Řádek zdrojového kódu se žlutou:  
  
 ![Zastavit provádění zarážku](../debugger/media/breakpointexecution.png "BreakpointExecution")  
  
 V tomto okamžiku hodnotu `testInt` je stále 1.  
  
 Můžete si prohlédnout aktuální stav aplikace, včetně hodnot proměnných a zásobníku volání. Další informace o zásobníku volání, naleznete v tématu [postupy: použití okna zásobník volání](../debugger/how-to-use-the-call-stack-window.md).  
  
 Můžete nastavit zarážku na kterýkoli řádek spustitelného kódu. Například v jazyce C# kód výše si můžete můžete nastavit zarážku na deklaraci proměnné `for` smyčku, nebo žádný kód uvnitř `for` smyčky, ale nelze nastavit zarážku v podpisu metody nebo deklarace oboru názvů nebo třídy.  
  
##  <a name="BKMK_Set_a_breakpoint_in_a_source_file"></a> Nastavení jiné druhy zarážky  
 Můžete také nastavit zarážky v zásobníku volání, v okně zpětný překlad a, v nativním kódu C++, podmínky dat nebo adresu paměti.  
  
## <a name="BKMK_Set_a_breakpoint_in_the_call_stack_window"></a> Nastavením zarážky v okně zásobník volání  
 Můžete přerušit běh na pokynu nebo řádku, který se funkce volání vrací, nastavením zarážky **zásobník volání** okna. Další informace o zásobníku volání, naleznete v tématu [postupy: použití okna zásobník volání](../debugger/how-to-use-the-call-stack-window.md). Ladicí program musí mít byl zastaven při provádění.  
  
1. Spusťte ladění aplikace a zastavením spuštění čekání (například na zarážce). Otevřít **zásobník volání** okno (**ladění / Windows / zásobník volání**, nebo **CTRL + ALT + C**).  
  
2. Klikněte pravým tlačítkem na volající funkci a pak vyberte **zarážky nebo vložit zarážku**, nebo použijte klávesovou zkratku **F9**.  
  
3. Na levém okraji zásobník volání, vedle názvu volání funkce se zobrazí symbol zarážky.  
  
   V **zarážky** okna, zarážky zásobníku volání se zobrazí jako adresy s oblastí paměti, která odpovídá další spustitelné instrukci ve funkci. Ladicí program přeruší provádění podle instrukce.  
  
   Vizuálně sledovat zarážky během provádění kódu, naleznete v tématu [mapování metod v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
## <a name="setting-a-breakpoint-in-the-disassembly-window"></a>Nastavením zarážky v okně zpětný překlad  
 Nastavit zarážku na instrukci sestavení, musí být ladicí program v režimu pozastavení.  
  
1.  Spusťte ladění aplikace a zastavením spuštění čekání (například na zarážce). Otevřít **zpětný překlad** okno (**ladění / Windows / zpětný překlad**, nebo **Ctrl + Alt + D**).  
  
2.  Klikněte na levý okraj na pokyn, který chcete zarážku nebo nastavte kurzor na instrukci a stiskněte klávesu **F9**.  
  
## <a name="BKMK_set_a_data_breakpoint_native_cplusplus_only"></a> Nastavení datové zarážky (pouze nativní C++)  
 Body zarážek přeruší provádění když hodnota, která je zde zadaná paměťová adresa změní. Pokud hodnota je číst, ale nebyl změněn, spuštění nebude přerušeno. K nastavení datové zarážky, musí být ladicí program v režimu pozastavení.  
  
1. Spusťte ladění aplikace a počkejte, dokud není dosaženo zarážky. Na **ladění** nabídce zvolte **Nová zarážka / datová zarážka** (nebo otevřít **zarážky** okno a zvolte **nový / datová zarážka**.  
  
2. V **adresu** zadejte adresu paměti nebo výraz, který vyhodnocuje adresu paměti. Zadejte například `&avar` pro přerušení, když obsah proměnné `avar` změny.  
  
3. V **počet bajtů** rozevíracím seznamu vyberte počet bajtů, které chcete ladicí program sledoval. Pokud vyberete třeba **4**, ladicí program bude sledovat čtyři bajty počínaje `&avar` a přerušit, pokud některý z těchto bajtů změní hodnotu.  
  
   Mějte na paměti, že datové zarážky závisí na použitelnost adresy konkrétní paměti.  
  
- Adresa proměnné se změní z jedné relace ladění na další. Na konci každé relace ladění jsou automaticky zakázány datové zarážky.  
  
- Pokud nastavíte zarážku dat na lokální proměnné, zarážka zůstane povolena po skončení funkce, ale adresa paměti není nadále vhodné, a nepředvídatelné chování zarážky. Pokud nastavíte zarážku dat na lokální proměnné, odstranit nebo zakázat zarážku před ukončením funkce.  
  
  Zarážky data nefungují za těchto podmínek:  
  
- Proces, který se neladí zapíše do umístění v paměti  
  
- Umístění v paměti je sdíleno mezi dvěma nebo více procesů  
  
- Umístění v paměti je aktualizováno v rámci jádra. Například, pokud je paměť předána 32bitové Windows `ReadFile` funkce, paměť se budou aktualizovat z režimu jádra a nedojde k narušení ladicího programu pro zápis paměti.  
  
## <a name="setting-a-breakpoint-with-a-memory-address-native-c-only"></a>Nastavením zarážky s adresou paměti (pouze nativní C++)  
 Nastavit zarážku v metodě, volá se na konkrétní instanci třídy můžete také použít adresu objektu.  Tady je příklad:  
  
 Mějme například objekt typu `my_class` s adresou, můžete nastavit zarážku funkce na metodu s názvem `my_method` volat z této instance.  
  
1.  Nastavte zarážku někde po vytvoření instance této instance třídy.  
  
2.  Najít adresu instance (kliknu na něm `0xcccccccc`).  
  
3.  Klikněte na tlačítko **ladění / Nová zarážka / funkce zarážky** (nebo **ALT + F9, B**).  
  
4.  Přidejte následující text, který má **název funkce** pole:  
  
    ```cpp  
    ((my_class *) 0xcccccccc)->my_method  
    ```  
  
##  <a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> Správa zarážky  
 Můžete použít **zarážky** okno (**ladění / Windows / zarážky**, nebo **CTRL + ALT + B**) zobrazíte všechny zarážky jste nastavili ve vašem řešení:  
  
 ![Okno zarážek](../debugger/media/breakpointswindow.png "BreakpointsWindow")  
  
 **Zarážky** okno vám poskytne centrální místo pro správu všechny vašich zarážek, což může být zvláště užitečné ve velkých projektech nebo při scénáři složitého ladění kde jsou zarážky nezbytné. Pokud potřebujete uložit nebo sdílet stav a umístění sady zarážek, můžete exportovat a importovat zarážky pouze z **zarážky** okna.  
  
##  <a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a> Pokročilé zarážky  
  
## <a name="breakpoint-conditions"></a>Podmínky zarážky  
 Můžete řídit, kdy a kde se zarážky spouštějí nastavením podmínky.  
  
1. Klikněte pravým tlačítkem na zarážku, nebo ukazatel myši zarážka a vyberte ikonu nastavení.  
  
2. V místní nabídce vyberte **podmínky**. Tím se otevře **nastavení zarážek** okno:  
  
   ![Nastavení zarážek](../debugger/media/breakpointsettings.png "BreakpointSettings")  
  
   Když zkontrolujete **podmínky** dialogovém okně se rozbalí a zobrazí různé druhy podmínky.  
  
   **Podmíněný výraz:** při výběru podmíněného výrazu, pak můžete použít dvě podmínky: **platí** a **při změně**. Zvolte **platí** Pokud chcete přerušit při výraz je spokojeni, nebo zvolte **při změně** Pokud chcete přerušit, pokud je hodnota výrazu se změnila.  
  
   V následujícím příkladu jsme nastavili zarážku zadat pouze tehdy, když hodnota `testInt` je **4**:  
  
   ![Při splnění podmínky zarážky](../debugger/media/breakpointconditionistrue.png "BreakpointConditionIsTrue")  
  
   V následujícím příkladu jsme nastavili zarážku zadat pouze tehdy, když hodnota `testInt` změny:  
  
   ![Zarážky při změně](../debugger/media/breakpointwhenchanged.png "BreakpointWhenChanged")  
  
   Chování When změněné pole je pro různé programovací jazyky. Pokud se rozhodnete **při změně** pro nativní kód, ladicí program nezahrne hodnocení první podmínku, která má být změněna, takže zarážka nebude dosažena při prvním hodnocení. Pokud se rozhodnete **při změně** pro spravovaný kód, je zarážka dosažena při prvním hodnocení po **při změně** zaškrtnuto.  
  
   Pokud nastavíte podmínku zarážky s neplatnou syntaxí, zobrazí se zpráva s upozorněním. Pokud zadáte podmínku zarážky s platnou syntaxi ale s neplatnou sémantikou, zobrazí se upozornění při prvním dosažení zarážky. V obou případech ladicí program zruší spuštění, když je volání zarážky neplatné. Zarážka je vynechána pouze v případě, že podmínka platí a je vyhodnocena jako `false`.  
  
   Podmínka může být libovolný platný výraz, který je rozpoznán v ladicím programu. Další informace o zobrazení platných výrazů naleznete v tématu [výrazy v ladicím programu](../debugger/expressions-in-the-debugger.md).  
  
## <a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>Pomocí ID objektů v podmínky zarážky (C# a F#)  
 Existují situace, kdy budete chtít sledovat chování konkrétního objektu. můžete třeba chtít zjistit, proč byl objekt vložen více než jednou do kolekce. V C# a F#, můžete vytvořit objekt ID pro určité instance [referenční typy](http://msdn.microsoft.com/library/801cf030-6e2d-4a0d-9daf-1431b0c31f47) a jejich použití v podmínky zarážky. ID objektu je generována modulem common language runtime (CLR) ladění služeb a přidružená k objektu.  Pokud chcete vytvořit ID objektu, postupujte takto:  
  
1. Nastavte zarážku v kódu nějakou dobu, po vytvoření objektu.  
  
2. Spustit ladění a v zarážky zastaví provádění, najdete ve zarážku **místní hodnoty** okně pravým tlačítkem myši a vyberte **Ujistěte se, ID objektu**.  
  
    Měli byste vidět **$** plus číslo v **místní hodnoty** okna. To je ID objektu.  
  
3. Přidáte nový podmíněné zarážky v okamžiku, že který chcete prozkoumat, například když je přidán do kolekce.  
  
4. V poli podmíněného výrazu použijte ID objektu. Například, pokud je proměnná `item` odkazující na objekt, který má být přidán do kolekce, vložíte **položky == $n**, kde **n** je číslo ID objektu.  
  
    Spuštění se přeruší v okamžiku, když je přidán do kolekce.  
  
   Pokud chcete později odstranit ID objektu, můžete kliknout pravým tlačítkem na proměnnou v **lokální** okna a vyberte **odstranit ID objektu**.  
  
   Všimněte si, že ID objektů vytvořit slabé odkazy a nezabrání objektu je uvolněna z paměti. Jsou platné pouze pro aktuální relaci ladění.  
  
## <a name="hit-count"></a>Počet přístupů  
 Pokud máte podezření, že smyčka v kódu se začíná chovat neplatně po určitém počtu iterací, můžete nastavit zarážku pro zastavení provádění po zadaném počtu přístupů k k přidruženému řádku kódu raději než vynutit na opakovaně stiskněte  **F5** k dosažení úrovně iterace.  
  
 V **nastavení zarážek** okno, nastavte podmínku na **počet volání**. Potom můžete zadat počet iterací. V následujícím příkladu jsme nastavili zarážku narazí při každé iteraci:  
  
 ![Počet průchodů zarážky](../debugger/media/breakpointhitcount.png "BreakpointHitCount")  
  
## <a name="filter"></a>Filtr  
 Můžete omezit zarážku, chcete-li vyvolat pouze na zadané zařízení nebo v konkrétních procesů a vláken.  
  
 V **nastavení zarážky**okno, nastavte podmínku na **filtr**. Zadejte jednu nebo více z těchto výrazů.  
  
- MachineName = "name"  
  
- ProcessId = hodnota  
  
- ProcessName = "name"  
  
- ThreadId = hodnota  
  
- ThreadName = "name"  
  
  Řetězcové hodnoty uzavřete do dvojitých uvozovek. Můžete kombinovat klauzule pomocí `&` (a), `||` (nebo), `!` (NOT) a závorkami.  
  
##  <a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a> Akce zarážek a zarážky s trasováním  
 Trasování je zarážka, která vytiskne zprávu do okna výstup. Trasování může sloužit jako dočasný příkaz trasování v programovacím jazyce.  
  
 V **nastavení zarážek** okna, zkontrolujte **akce** pole. Zvolte **zapsat zprávu do okna výstup** v **akce** skupiny. Můžete vytisknout řetězec obecný **Toto je test**. Chcete-li přidat hodnotu proměnné nebo výrazu, uzavřete ho do složených závorek.  
  
 Chcete-li přerušit běh při dosažení zarážky s trasováním, zrušte **pokračovat v provádění** zaškrtávací políčko. Když **pokračovat v provádění** je zaškrtnuto, provádění neskončí. V obou případech je zpráva vytištěna.  
  
 Můžete použít následující speciální klíčová slova v **zpráva**.  
  
|||  
|-|-|  
|**$ADDRESS**|Aktuální instrukce|  
|**$CALLER**|Název funkce volání|  
|**$CALLSTACK**|Zásobník volání|  
|**$FUNCTION**|Název aktuální funkce|  
|**$PID**|id procesu|  
|**$PNAME**|Název procesu|  
|**$TID**|id vlákna|  
|**$TNAME**|Název vlákna|  
|**$TICK**||  
|**$TNAME**||  
  
##  <a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a> Štítky zarážek  
 Štítky zarážek se používají pouze v **zarážky** okna k řazení a filtrováni seznamu zarážek. Chcete-li přidat popisek k zarážce, vyberte řádek zarážky a zvolte **popisek** v místní nabídce.  
  
## <a name="export-and-import-breakpoints"></a>Export a Import zarážky  
 Zarážky můžete exportovat do souboru XML tak, že kliknete pravým tlačítkem na zarážku a vyberete **exportovat**. Soubor je uložen v adresáři řešení ve výchozím nastavení. Chcete-li importovat zarážky, otevřete **zarážky** okno (**CTRL + ALT + B**) a na panelu nástrojů klikněte na šipku vpravo (je popis tlačítka **importuje zarážky ze souboru**) .  
  
## <a name="troubleshoot-breakpoints"></a>Zarážky Poradce při potížích  
  
### <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>Odstraněné zarážky, ale I nadále přístupů je při spuštění ladění znovu  
 Pokud jste odstranili zarážce při ladění, v některých případech může dostanete k zarážce znovu při příštím spuštění ladění. Pokud chcete zastavit dosažení této zarážky, ujistěte se, že všechny instance této zarážky se odeberou z **zarážky** okna.  
  
### <a name="the-debugger-cant-locate-the-correct-version-of-the-source-file-for-a-breakpoint"></a>Ladicí program nemůže najít správnou verzi zdrojového souboru pro zarážku  
 Pokud došlo ke změně zdrojového souboru a zdroj již neodpovídá kódu, který ladíte, ladicí program může najít zdrojový soubor, který odpovídá zarážce, i když existuje zdrojový soubor.  
  
1.  Pokud chcete zobrazit zdrojový kód, který neodpovídá verzi Visual Studio, kterou ladíte, zvolte **ladění / možnosti a nastavení**. Na **ladění/Obecné** zrušte **vyžaduje zdrojové soubory přesně shodovaly s originály** možnost.  
  
2.  Můžete také navázat zarážku na zdrojový soubor. Vyberte zarážku a zvolte **podmínky** v místní nabídce. Zkontrolujte **povolit zdrojový kód lišil od původního** v **nastavení zarážek** okna.  
  
### <a name="breakpoints-dont-work-in-a-dll"></a>Zarážky nefungují v knihovně DLL  
 Nelze nastavit zarážku ve zdrojovém souboru Když ladicí program nenačetl informace o ladění pro modul ve kterém je kód umístěn. Příznaky mohou zahrnovat zprávy, jako **zarážka se nenastaví**. Piktogram zarážky upozornění se zobrazí v místě zarážky. Tyto body přerušení upozornění však budou skutečnými zarážkami při načítání kódu. Další informace o načítání symbolů, naleznete v tématu [zadejte symbolu (.pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
## <a name="see-also"></a>Viz také  
 [Procházení kódu s ladicím programem](../debugger/navigating-through-code-with-the-debugger.md)



