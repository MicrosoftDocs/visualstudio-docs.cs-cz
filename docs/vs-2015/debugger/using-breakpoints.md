---
title: Použití zarážek | Dokumenty společnosti Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
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
manager: jillfra
ms.openlocfilehash: cadaf069bb53c9d212e6de5ebd6ea2cf9efe7bb1
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302467"
---
# <a name="using-breakpoints"></a>Použití zarážek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Zarážky můžete nastavit, pokud chcete zastavit spuštění ladicího programu, možná zobrazit stav proměnných kódu nebo se podívat na zásobník volání. Jedná se o jednu z nejdůležitějších ladicích technik v sadě nástrojů vývojáře.
  
## <a name="setting-a-function-breakpoint-in-source-code"></a><a name="BKMK_Overview"></a>Nastavení zarážky funkce ve zdrojovém kódu  
 Zarážku funkce nastavíte ve zdrojovém kódu kliknutím na levý okraj souboru zdrojového kódu nebo vložením kurzoru na řádek kódu a stisknutím klávesy F9. Zarážka se zobrazí jako červená tečka na levém okraji a řádek kódu je také barevný:  
  
 ![Nastavení zarážky](../debugger/media/basicbreakpoint.png "Základní bod přerušení")  
  
 Při spuštění tohoto kódu v ladicím programu se provádění zastaví vždy, když je zarážka přístupů, před spuštěním kódu na tomto řádku. Řádek zdrojového kódu je zbarven žlutě:  
  
 ![Spuštění zarážky bylo zastaveno.](../debugger/media/breakpointexecution.png "Spuštění zarážky")  
  
 V tomto okamžiku `testInt` je hodnota stále 1.  
  
 Můžete se podívat na aktuální stav aplikace, včetně hodnot proměnných a zásobníku volání. Další informace o zásobníku volání najdete v [tématu Postup: Použití okna zásobníku volání](../debugger/how-to-use-the-call-stack-window.md).  
  
 Zarážku můžete nastavit na libovolném řádku spustitelného kódu. Například v kódu C# výše můžete nastavit zarážku `for` na deklaraci proměnné, `for` smyčky nebo libovolný kód uvnitř smyčky, ale nelze nastavit zarážku na oboru názvů nebo deklarace třídy nebo podpis metody.  
  
## <a name="setting-other-kinds-of-breakpoints"></a><a name="BKMK_Set_a_breakpoint_in_a_source_file"></a>Nastavení jiných druhů zarážek  
 Můžete také nastavit zarážky v zásobníku volání, v okně Dissemontáž a v nativním kódu C++ na stav dat nebo adresu paměti.  
  
## <a name="setting-a-breakpoint-in-the-call-stack-window"></a><a name="BKMK_Set_a_breakpoint_in_the_call_stack_window"></a>Nastavení zarážky v okně zásobníku volání  
 Spuštění můžete přerušit na instrukce nebo řádek, který volá funkce vrátí nastavením zarážky v okně **zásobníku volání.** Další informace o zásobníku volání najdete v [tématu Postup: Použití okna zásobníku volání](../debugger/how-to-use-the-call-stack-window.md). Ladicí program musel být zastaven provádění.  
  
1. Spusťte ladění aplikace a čekání spuštění je zastaveno (například na zarážky). Otevřete okno **Zásobník volání** ( Ladění / Windows /**Zásobník volání**nebo CTRL + ALT **+ C**).  
  
2. Klepněte pravým tlačítkem myši na volající funkci a pak vyberte **zarážku / vložit zarážku**nebo použijte klávesovou zkratku **F9**.  
  
3. Symbol zarážky se zobrazí v levém okraji zásobníku volání vedle názvu volání funkce.  
  
   V okně **Zarážky** se zarážka zásobníku volání zobrazí jako adresa s umístěním paměti, které odpovídá další spustitelné instrukci ve funkci. Ladicí program přeruší provádění na instrukce.  
  
   Vizuálně trasovat zarážky během spuštění kódu, naleznete [v tématu Map metody v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
## <a name="setting-a-breakpoint-in-the-disassembly-window"></a>Nastavení zarážky v okně demontáže  
 Chcete-li nastavit zarážku na instrukci sestavení, ladicí program musí být v režimu přerušení.  
  
1. Spusťte ladění aplikace a čekání spuštění je zastaveno (například na zarážky). Otevřete okno **Demontáže** (**Ladění / Windows / Demontáž**nebo Ctrl + Alt + **D**).  
  
2. Klikněte na levý okraj na pokyn, který chcete přerušit, nebo nastavte kurzor na instrukce a stiskněte **klávesu F9**.  
  
## <a name="setting-a-data-breakpoint-native-c-only"></a><a name="BKMK_set_a_data_breakpoint_native_cplusplus_only"></a>Nastavení zarážky dat (pouze nativní jazyk C++)  
 Zarážky dat zalomení spuštění při změně hodnoty, která je uložena na zadané adrese paměti. Pokud je hodnota přečtena, ale není změněna, spuštění se nepřeruší. Chcete-li nastavit zarážky dat, ladicí program musí být v režimu přerušení.  
  
1. Spusťte ladění aplikace a počkejte, dokud není dosaženo zarážky. V nabídce **Ladění** zvolte **Nová zarážka / Zarážky dat** (nebo otevřete okno **Zarážky** a zvolte **Nová / Zarážky dat**.  
  
2. Do pole **Adresa** zadejte adresu paměti nebo výraz, který je vyhodnocen jako adresa paměti. Zadejte `&avar` například přerušení, když se `avar` změní obsah proměnné.  
  
3. V rozevíracím souboru **Počet bajtů** vyberte počet bajtů, které má ladicí program sledovat. Pokud například vyberete **4**, ladicí program bude sledovat `&avar` čtyři bajty začínající na a přerušit, pokud některý z těchto bajtů změnit hodnotu.  
  
   Mějte na paměti, že zarážky dat závisí na použitelnosti konkrétní adresy paměti.  
  
- Adresa proměnné se změní z jedné relace ladění na další. Zarážky dat jsou automaticky zakázány na konci každé relace ladění.  
  
- Pokud nastavíte zarážky dat na místní proměnné, zarážka zůstane povolena, když funkce končí, ale adresa paměti již není použitelná a chování zarážky je nepředvídatelné. Pokud nastavíte zarážky dat na místní proměnné, měli byste odebrat nebo zakázat zarážku před ukončením funkce.  
  
  Zarážky dat nefungují za těchto podmínek:  
  
- Proces, který není laděn, zapisuje do umístění v paměti  
  
- Umístění paměti je sdíleno mezi dvěma nebo více procesy.  
  
- Umístění paměti je aktualizováno v rámci jádra. Pokud je například paměť předána 32bitové funkci systému Windows, `ReadFile` paměť bude aktualizována z režimu jádra a ladicí program se při zápisu do paměti nepřeruší.  
  
## <a name="setting-a-breakpoint-with-a-memory-address-native-c-only"></a>Nastavení zarážky s adresou paměti (pouze nativní jazyk C++)  
 Adresu objektu můžete také použít k nastavení zarážky metody volané pro konkrétní instanci třídy.  Tady je příklad:  
  
 Například daný objekt typu `my_class` s adresou můžete nastavit zarážku `my_method` funkce na metodu s názvem z této instance.  
  
1. Nastavte zarážku někde po této instance třídy je vytvořena instance.  
  
2. Najděte adresu instance (řekneme, že `0xcccccccc`je ).  
  
3. Klepněte na **položku Ladění / Nová zarážka / Zarážky funkce** (nebo **ALT + F9, B**).  
  
4. Do pole Název **funkce** přidejte následující text:  
  
    ```cpp  
    ((my_class *) 0xcccccccc)->my_method  
    ```  
  
## <a name="managing-breakpoints"></a><a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a>Správa zarážek  
 Pomocí okna **Zarážky** (**Ladění / Windows / Zarážky**nebo CTRL + ALT + **B)** můžete zobrazit všechny zarážky, které jste nastavili v řešení:  
  
 ![Zarážky – okno](../debugger/media/breakpointswindow.png "ZarážkyOkno")  
  
 Okno **Zarážky** poskytuje centrální místo pro správu všech zarážek, což může být užitečné zejména ve velkém řešení nebo složitém scénáři ladění, kde jsou kritické zarážky. Pokud potřebujete uložit nebo sdílet stav a umístění sady zarážek, můžete exportovat a importovat zarážky pouze z okna **Zarážky.**  
  
## <a name="advanced-breakpoints"></a><a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>Upřesňující zarážky  
  
## <a name="breakpoint-conditions"></a>Podmínky zarážky  
 Nastavením podmínek můžete určit, kdy a kde se zarážka spustí.  
  
1. Klikněte pravým tlačítkem myši na zarážku nebo najeďte na zarážku a zvolte ikonu nastavení.  
  
2. V místní nabídce vyberte **Podmínky**. Otevře se okno **Nastavení zarážky:**  
  
   ![Nastavení zarážky](../debugger/media/breakpointsettings.png "Nastavení zarážky")  
  
   Když zaškrtnete políčko **Podmínky,** okno se rozbalí a zobrazí různé druhy podmínek.  
  
   **Podmíněný výraz:** Když vyberete Podmíněný výraz, můžete zvolit dvě podmínky: **Je true** a **Při změně**. Zvolte **Je true,** pokud chcete přerušit, když je výraz splněn, nebo zvolte **Při změně,** pokud chcete přerušit, když se změnila hodnota výrazu.  
  
   V následujícím příkladu nastavíme zarážku `testInt` na přístup pouze v případě, že hodnota je **4**:  
  
   ![Podmínka zarážky je pravdivá](../debugger/media/breakpointconditionistrue.png "Hodnota podmínky přerušení je true")  
  
   V následujícím příkladu nastavíme zarážku `testInt` na přístup pouze v případě, že hodnota změn:  
  
   ![Zarážka při změně](../debugger/media/breakpointwhenchanged.png "ZarážkaPři změně")  
  
   Chování pole Při změně se liší pro různé programovací jazyky. Pokud zvolíte **Při změně** pro nativní kód ladicí program nepovažuje první vyhodnocení podmínky za změnu, takže zarážka nebude přístupů na první hodnocení. Pokud zvolíte **Při změně** pro spravovaný kód, je zarážka přístupů na první vyhodnocení po **Při změně** je vybrána.  
  
   Pokud nastavíte podmínku zarážky s neplatnou syntaxí, zobrazí se varovná zpráva. Pokud zadáte podmínku zarážky s platnou syntaxí, ale neplatnou sémantikou, zobrazí se při prvním zásahu zarážky varovná zpráva. V obou případech ladicí program přeruší provádění při neplatné zarážky je přístupů. Zarážka je přeskočena pouze v `false`případě, že je podmínka platná a vyhodnocuje se .  
  
   Podmínkou může být libovolný platný výraz, který je rozpoznán ladicím programem. Další informace o platných výrazech naleznete [v tématu Výrazy v ladicím programu](../debugger/expressions-in-the-debugger.md).  
  
## <a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>Použití ID objektů v podmínkách zarážky (C# a F#)  
 Jsou chvíle, kdy chcete sledovat chování určitého objektu; Můžete například chtít zjistit, proč byl objekt vložen více než jednou do kolekce. V C# a F# můžete vytvořit ID objektů pro konkrétní instance [typů odkazů](https://msdn.microsoft.com/library/801cf030-6e2d-4a0d-9daf-1431b0c31f47) a použít je v podmínkách zarážky. ID objektu je generováno služby ladění clr (COMMON Language runtime) a je přidruženo k objektu.  Chcete-li vytvořit ID objektu, postupujte takto:  
  
1. Nastavte zarážku v kódu nějaký čas po vytvoření objektu.  
  
2. Spusťte ladění a když se provádění zastaví v zarážky, najděte zarážku v okně **Locals,** klepněte na ni pravým tlačítkem myši a vyberte **Vytvořit ID objektu**.  
  
    V okně **$** **Locals** byste měli vidět plus číslo. Toto je ID objektu.  
  
3. Přidejte novou podmíněnou zarážku v bodě, který chcete prozkoumat, například když má být objekt přidán do kolekce.  
  
4. V poli Podmíněný výraz použijte ID objektu. Například pokud je proměnná `item` odkazující na objekt, který má být přidán do kolekce, by dal **položku == $n**, kde **n** je číslo ID objektu.  
  
    Spuštění bude přerušit v okamžiku, kdy má být tento objekt přidán do kolekce.  
  
   Pokud později chcete ID objektu odstranit, můžete klepnout pravým tlačítkem myši na proměnnou v okně **Locals** a vybrat **příkaz Odstranit ID objektu**.  
  
   Všimněte si, že ID objektu vytvořit slabé odkazy a nebrání objektu jsou uvolněny. Jsou platné pouze pro aktuální relaci ladění.  
  
## <a name="hit-count"></a>Počet přístupů  
 Pokud máte podezření, že smyčka v kódu začne nechová po určitý počet iterací, můžete nastavit zarážku zastavit provádění po zadaný počet přístupů na přidružený řádek kódu, spíše než nuceni opakovaně stiskněte **klávesu F5** k dosažení úrovně iterace.  
  
 V okně **Nastavení zarážky** nastavte podmínku na **Počet přístupů**. Potom můžete zadat počet iterací. V následujícím příkladu nastavíme zarážku tak, aby byla přístupována na každou další iteraci:  
  
 ![Počet přístupů zarážky](../debugger/media/breakpointhitcount.png "Počet zásahů zarážky")  
  
## <a name="filter"></a>Filtr  
 Zarážku můžete omezit na spálení pouze na určených zařízeních nebo v určených procesech a vláknech.  
  
 V okně **Nastavení zarážky**nastavte podmínku na **Filtrovat**. Zadejte jeden nebo více z následujících výrazů.  
  
- Název_počítače = "název"  
  
- ProcessId = hodnota  
  
- Název_procesu = "název"  
  
- ThreadId = hodnota  
  
- Název_vlákna = "název"  
  
  Uzavřete hodnoty řetězce do dvojitých uvozovek. Můžete kombinovat klauzule `&` pomocí `||` (AND), `!` (OR), (NOT) a závorek.  
  
## <a name="breakpoint-actions-and-tracepoints"></a><a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a>Akce zarážky a stopovací body  
 Trasovací bod je zarážka, která vytiskne zprávu do okna Výstup. Trasovací bod může fungovat jako dočasný příkaz trasování v programovacím jazyce.  
  
 V okně **Nastavení zarážky** zaškrtněte políčko **Akce.** Ve skupině **Akce** zvolte **Protokolovat zprávu do výstupního okna.** Obecný řetězec můžete vytisknout, například **se jedná o test**. Chcete-li zahrnout hodnotu proměnné nebo výrazu, uzavřete ji do složených závorek.  
  
 Chcete-li přerušit provádění při přístupu trasovací bod, zrušte zaškrtnutí políčka **Pokračovat v provádění.** Při **continue execution** je zaškrtnuto, provádění není zastaveno. V obou případech je zpráva vytištěna.  
  
 Ve **zprávě**můžete použít následující speciální klíčová slova .  
  
|||  
|-|-|  
|**$ADDRESS**|Aktuální instrukce|  
|**$CALLER**|Název volající funkce|  
|**$CALLSTACK**|Zásobník volání|  
|**$FUNCTION**|Název aktuální funkce|  
|**$PID**|Id procesu|  
|**$PNAME**|Název procesu|  
|**$TID**|Id vlákna|  
|**$TNAME**|Název vlákna|  
|**$TICK**||  
|**$TNAME**||  
  
## <a name="breakpoint-labels"></a><a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a>Popisky zarážky  
 Popisky zarážky se používají pouze v okně **Zarážky** k řazení a filtrování seznamu zarážek. Chcete-li přidat popisek k zarážky, zvolte řádek zarážky a pak v místní nabídce zvolte **Label.**  
  
## <a name="export-and-import-breakpoints"></a>Zarážky exportu a importu  
 Zarážku můžete exportovat do souboru XML klepnutím pravým tlačítkem myši na zarážku a výběrem **možnosti Exportovat**. Soubor je ve výchozím nastavení uložen v adresáři řešení. Chcete-li importovat zarážky, otevřete okno **Zarážky** (**CTRL + ALT + B**) a na panelu nástrojů klepněte na šipku směřující doprava (popis je Import **zarážek ze souboru).**  
  
## <a name="troubleshoot-breakpoints"></a>Poradce při potížích s zarážky  
  
### <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>Po odstranění zarážky, ale i nadále hit to, když začnu ladění znovu  
 Pokud jste odstranili zarážku při ladění, v některých případech může zasáhnout zarážku znovu při příštím spuštění ladění. Chcete-li zastavit bít tuto zarážku, ujistěte se, že všechny instance zarážky jsou odebrány z okna **Zarážky.**  
  
### <a name="the-debugger-cant-locate-the-correct-version-of-the-source-file-for-a-breakpoint"></a>Ladicí program nemůže najít správnou verzi zdrojového souboru pro zarážku.  
 Pokud se zdrojový soubor změnil a zdroj již neodpovídá kódu, který ladíte, ladicí program může vyhledat zdrojový soubor, který odpovídá zarážky, i když zdrojový soubor existuje.  
  
1. Pokud chcete, aby Visual Studio zobrazovala zdrojový kód, který neodpovídá verzi, kterou ladíte, zvolte **Ladění / Možnosti a nastavení**. Na stránce **Ladění/obecné** zrušte zaškrtnutí možnosti **Vyžadovat zdrojové soubory, které přesně odpovídají původní verzi.**  
  
2. Zarážku můžete také svázat se zdrojovým souborem. Vyberte zarážku a v místní nabídce zvolte **Podmínky.** Zaškrtněte **políčko Povolit, aby se zdrojový kód lišil od původního** v okně **Nastavení zarážky.**  
  
### <a name="breakpoints-dont-work-in-a-dll"></a>Zarážky nefungují v dll  
 Zarážku ve zdrojovém souboru nelze nastavit, pokud ladicí program nenačetl informace o ladění modulu, ve kterém je kód umístěn. Příznaky mohou zahrnovat **zprávy, jako je například zarážka nebude nastavena**. Glyf zarážky upozornění se zobrazí v umístění zarážky. Tyto zarážky upozornění však stanou skutečné zarážky při načtení kódu. Další informace o načítání symbolů naleznete [v tématu Určení symbolu (.pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
## <a name="see-also"></a>Viz také  
 [Procházení kódu s ladicím programem](../debugger/navigating-through-code-with-the-debugger.md)
