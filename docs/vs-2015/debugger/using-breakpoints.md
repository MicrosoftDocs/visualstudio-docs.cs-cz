---
title: Použití zarážek | Microsoft Docs
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
ms.openlocfilehash: bbe2ecf89f94cc75ff9036285ae9acbf9cf3b657
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534495"
---
# <a name="using-breakpoints"></a>Použití zarážek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Můžete nastavit zarážky, pokud chcete zastavit provádění ladicího programu, například zobrazit stav proměnných kódu nebo zobrazit zásobník volání. Jsou jedním z nejdůležitějších technik ladění v sadě nástrojů pro vývojáře.
  
## <a name="setting-a-function-breakpoint-in-source-code"></a><a name="BKMK_Overview"></a>Nastavení zarážky funkce ve zdrojovém kódu  
 Zarážku funkce ve zdrojovém kódu nastavíte kliknutím na levý okraj souboru zdrojového kódu nebo vložením kurzoru na řádek kódu a stisknutím klávesy F9. Zarážka se zobrazí jako červená tečka na levém okraji a řádek kódu je také barevný:  
  
 ![Nastavení zarážky](../debugger/media/basicbreakpoint.png "BasicBreakpoint")  
  
 Při spuštění tohoto kódu v ladicím programu, spuštění se zastaví pokaždé, když je dosaženo zarážky, před provedením kódu na tomto řádku. Řádek zdrojového kódu je žlutě barevný:  
  
 ![Spuštění zarážky bylo zastaveno.](../debugger/media/breakpointexecution.png "BreakpointExecution")  
  
 V tomto okamžiku `testInt` je hodnota stále 1.  
  
 Můžete se podívat na aktuální stav aplikace, včetně hodnot proměnných a zásobníku volání. Další informace o zásobníku volání naleznete v tématu [Postupy: použití okna zásobník volání](../debugger/how-to-use-the-call-stack-window.md).  
  
 Zarážku můžete nastavit na jakémkoli řádku spustitelného kódu. Například v kódu jazyka C# můžete nastavit zarážku na deklaraci proměnné, `for` smyčku nebo libovolný kód uvnitř `for` smyčky, ale nemůžete nastavit zarážku na deklaracech oboru názvů nebo třídy nebo na signaturu metody.  
  
## <a name="setting-other-kinds-of-breakpoints"></a><a name="BKMK_Set_a_breakpoint_in_a_source_file"></a>Nastavení dalších druhů zarážek  
 Můžete také nastavit zarážky v zásobníku volání, v okně zpětný překlad a v nativním kódu jazyka C++, v datové podmínce nebo adrese paměti.  
  
## <a name="setting-a-breakpoint-in-the-call-stack-window"></a><a name="BKMK_Set_a_breakpoint_in_the_call_stack_window"></a>Nastavení zarážky v okně zásobník volání  
 Můžete přerušit provádění v instrukci nebo řádku, na který se volání funkce vrátí, nastavením zarážky v okně **zásobník volání** . Další informace o zásobníku volání naleznete v tématu [Postupy: použití okna zásobník volání](../debugger/how-to-use-the-call-stack-window.md). Ladicí program musí zastavit provádění.  
  
1. Spusťte ladění aplikace a počkejte na zastavení (například na zarážce). Otevřete okno **zásobník volání** (**ladění/Windows/zásobník volání**nebo **CTRL + ALT + C**).  
  
2. Klikněte pravým tlačítkem myši na volání funkce a vyberte **zarážku/Vložit zarážku**, nebo jen použijte klávesovou zkratku **F9**.  
  
3. Symbol zarážky se zobrazí v levém okraji zásobníku volání vedle názvu volání funkce.  
  
   V okně **zarážky** se Zarážka zásobníku volání zobrazí jako adresa s umístěním v paměti, které odpovídá další spustitelné instrukci ve funkci. Ladicí program přeruší provádění v instrukci.  
  
   Chcete-li vizuálně sledovat zarážky během provádění kódu, viz [metody map v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
## <a name="setting-a-breakpoint-in-the-disassembly-window"></a>Nastavení zarážky v okně zpětný překlad  
 Chcete-li nastavit zarážku v instrukci sestavení, musí být ladicí program v režimu pozastavení.  
  
1. Spusťte ladění aplikace a počkejte na zastavení (například na zarážce). Otevřete okno **zpětný překlad** (**ladit/Windows/zpětný překlad**nebo **CTRL + ALT + D**).  
  
2. Klikněte na levý okraj u instrukce, u které chcete narušit, nebo nastavte kurzor na pokyn a stiskněte klávesu **F9**.  
  
## <a name="setting-a-data-breakpoint-native-c-only"></a><a name="BKMK_set_a_data_breakpoint_native_cplusplus_only"></a>Nastavení datové zarážky (pouze nativní C++)  
 Datové zarážky přeruší provádění, když se změní hodnota uložená v zadané adrese paměti. Pokud je hodnota čtena, ale nemění se, provádění není přerušeno. Chcete-li nastavit zarážky dat, musí být ladicí program v režimu pozastavení.  
  
1. Spusťte ladění aplikace a počkejte na dosažení zarážky. V nabídce **ladění** vyberte Nová zarážka **/data zarážka** (nebo otevřete okno **zarážky** a vyberte možnost **Nová/datová zarážka**.  
  
2. Do pole **adresa** zadejte adresu paměti nebo výraz, který se vyhodnotí na adresu paměti. Například zadejte, že `&avar` se má přerušit, když se změní obsah proměnné `avar` .  
  
3. V rozevíracím seznamu **počet bajtů** vyberte počet bajtů, které má ladicí program sledovat. Pokud například vyberete **4**, ladicí program bude sledovat čtyři bajty počínaje `&avar` a přerušit, pokud kterákoli z těchto bajtů změní hodnotu.  
  
   Pamatujte, že datové zarážky závisí na použitelnosti konkrétních adres paměti.  
  
- Adresa proměnné se mění z jedné relace ladění na další. Datové zarážky jsou na konci každé relace ladění automaticky zakázané.  
  
- Pokud nastavíte zarážku dat na lokální proměnné, zarážka zůstane povolena, když funkce skončí, ale adresa paměti již není platná a chování zarážky je nepředvídatelné. Pokud nastavíte zarážku dat na lokální proměnné, měli byste před ukončením funkce odebrat nebo zakázat zarážku.  
  
  Datové zarážky nefungují za těchto podmínek:  
  
- Proces, který neladí zápisy do umístění v paměti  
  
- Umístění v paměti je sdíleno mezi dvěma nebo více procesy.  
  
- Umístění v paměti je aktualizováno v rámci jádra. Například pokud je paměť předána funkci 32 Windows `ReadFile` , bude paměť aktualizována z režimu jádra a ladicí program nebude při zápisu do paměti přerušen.  
  
## <a name="setting-a-breakpoint-with-a-memory-address-native-c-only"></a>Nastavení zarážky s adresou paměti (pouze nativní C++)  
 Můžete také použít adresu objektu pro nastavení zarážky pro metodu volanou v konkrétní instanci třídy.  Tady je příklad:  
  
 Například s ohledem na objekt typu `my_class` s adresou můžete nastavit zarážku funkce pro metodu s názvem `my_method` volanou z této instance.  
  
1. Nastavte zarážku někam po vytvoření instance třídy.  
  
2. Najděte adresu instance (říkáme ji `0xcccccccc` ).  
  
3. Klikněte na položku **ladit/Nová zarážka zarážky/funkce** (nebo **ALT + F9, B**).  
  
4. Do pole **název funkce** přidejte následující text:  
  
    ```cpp  
    ((my_class *) 0xcccccccc)->my_method  
    ```  
  
## <a name="managing-breakpoints"></a><a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a>Správa zarážek  
 Chcete-li zobrazit všechny zarážky, které jste nastavili ve vašem řešení, můžete použít okno **zarážky** (**ladění/Windows/zarážky**nebo **CTRL + ALT + B**):  
  
 ![Zarážky – okno](../debugger/media/breakpointswindow.png "BreakpointsWindow")  
  
 Okno **zarážky** poskytuje centrální místo pro správu všech zarážek, což může být obzvláště užitečné ve velkém řešení nebo složitém scénáři ladění, kde jsou zarážky kritické. Pokud potřebujete uložit nebo sdílet stav a umístění sady zarážek, můžete exportovat a importovat zarážky pouze z okna **zarážky** .  
  
## <a name="advanced-breakpoints"></a><a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>Rozšířené zarážky  
  
## <a name="breakpoint-conditions"></a>Podmínky zarážky  
 Můžete určit, kdy a kde se zarážka spustí, nastavením podmínek.  
  
1. Klikněte pravým tlačítkem myši na zarážku, nebo najeďte myší na zarážku a vyberte ikonu nastavení.  
  
2. V místní nabídce vyberte **podmínky**. Otevře se okno **Nastavení zarážky** :  
  
   ![Nastavení zarážky](../debugger/media/breakpointsettings.png "BreakpointSettings")  
  
   Když zaškrtnete políčko **podmínky** , okno se rozbalí a zobrazí se různé druhy podmínek.  
  
   **Podmíněný výraz:** Když vyberete podmíněný výraz, můžete zvolit dvě podmínky: **je true** a **při změně**. Vyberte **hodnotu true** , pokud chcete přerušit, když je výraz splněn, nebo pokud chcete přerušit, když se změní hodnota výrazu, vyberte možnost **když se změní** .  
  
   V následujícím příkladu nastavíme zarážku tak, aby se dosáhla pouze v případě, že hodnota `testInt` je **4**:  
  
   ![Podmínka zarážky je pravdivá.](../debugger/media/breakpointconditionistrue.png "BreakpointConditionIsTrue")  
  
   V následujícím příkladu nastavíme zarážku tak, aby se dosáhla pouze v případě, že se `testInt` změní hodnota:  
  
   ![Zarážka při změně](../debugger/media/breakpointwhenchanged.png "BreakpointWhenChanged")  
  
   Chování pole když se změnilo v různých programovacích jazycích. Pokud se rozhodnete **pro nativní** kód, ladicí program nepovažuje první vyhodnocení podmínky za změnu, takže zarážka nebude dosaženo prvního vyhodnocení. Pokud zvolíte, že se má u spravovaného kódu **změnit** , zarážka se vykoná při prvním vyhodnocení po výběru možnosti **změnit** .  
  
   Pokud nastavíte podmínku zarážky s neplatnou syntaxí, zobrazí se varovná zpráva. Zadáte-li podmínku zarážky s platnou syntaxí, ale neplatnou sémantikou, zobrazí se při prvním průchodu zarážky zpráva s upozorněním. V obou případech ladicí program přeruší provádění, když je dosaženo neplatné zarážky. Zarážka je přeskočena pouze v případě, že je podmínka platná a je vyhodnocena jako `false` .  
  
   Podmínkou může být libovolný platný výraz, který je rozpoznán ladicím programem. Další informace o platných výrazech naleznete v tématu [výrazy v ladicím programu](../debugger/expressions-in-the-debugger.md).  
  
## <a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>Použití ID objektů v podmínkách zarážek (C# a F #)  
 Existují situace, kdy chcete sledovat chování určitého objektu; Například můžete chtít zjistit, proč byl objekt v kolekci vložen více než jednou. V jazyce C# a F # můžete vytvořit ID objektů pro konkrétní instance [odkazových typů](https://msdn.microsoft.com/library/801cf030-6e2d-4a0d-9daf-1431b0c31f47) a použít je v podmínkách zarážek. ID objektu je vygenerováno službami ladění modulu CLR (Common Language Runtime) a přidruženy k objektu.  Chcete-li vytvořit ID objektu, postupujte následovně:  
  
1. Nastavte zarážku v kódu nějakým časem po vytvoření objektu.  
  
2. Spusťte ladění a když se spuštění zastaví na zarážce, najděte zarážku v okně **místní** hodnoty, klikněte na ni pravým tlačítkem myši a vyberte **vytvořit ID objektu**.  
  
    **$** V okně **místní** hodnoty by se měla zobrazit znaménko plus. Toto je ID objektu.  
  
3. Přidejte novou podmíněnou zarážku v bodu, který chcete prozkoumat, například když se má objekt přidat do kolekce.  
  
4. V poli podmíněný výraz použijte ID objektu. Například pokud existuje proměnná `item` odkazující na objekt, který má být přidán do kolekce, měli byste umístit **Item = = $n**, kde **n** je číslo ID objektu.  
  
    Spuštění bude přerušeno v okamžiku, kdy má být objekt přidán do kolekce.  
  
   Pokud budete později chtít odstranit ID objektu, můžete kliknout pravým tlačítkem myši na proměnnou v okně **místní** hodnoty a vybrat **Odstranit ID objektu**.  
  
   Všimněte si, že ID objektů vytvářejí slabé odkazy a nebrání vyshromažďování paměti objektu. Jsou platné pouze pro aktuální relaci ladění.  
  
## <a name="hit-count"></a>Počet volání  
 Pokud máte podezření, že se smyčka v kódu začne chovat po určitém počtu iterací, můžete nastavit zarážku, aby zastavila provádění po zadaném počtu úspěšných přístupů do přidruženého řádku kódu, a nemusíte tak opakovaně stisknout klávesu **F5** , aby se dosáhlo úrovně iterace.  
  
 V okně **Nastavení zarážky** nastavte podmínku na **Počet přístupů**. Pak můžete zadat počet iterací. V následujícím příkladu nastavíme zarážku tak, aby se vyčerpala v každé jiné iteraci:  
  
 ![Počet volání zarážky](../debugger/media/breakpointhitcount.png "BreakpointHitCount")  
  
## <a name="filter"></a>Filtrovat  
 Zarážku můžete omezit tak, aby se aktivovala jenom na zadaných zařízeních, nebo v zadaných procesech a vláknech.  
  
 V okně **Nastavení zarážky**nastavte podmínku na **Filtr**. Zadejte jeden nebo více následujících výrazů.  
  
- Nazev_pocitace = "Name"  
  
- ProcessId = hodnota  
  
- Název procesu = "Name"  
  
- IDvlákna = hodnota  
  
- Thread = "Name"  
  
  Uzavřete řetězcové hodnoty do dvojitých uvozovek. Klauzule lze kombinovat pomocí `&` (a), `||` (nebo), `!` (NOT) a závorek.  
  
## <a name="breakpoint-actions-and-tracepoints"></a><a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a>Akce zarážek a trasováním  
 Zarážka s trasováním je zarážka, která vytiskne zprávu do okna výstup. Zarážka s trasováním může fungovat jako dočasný příkaz trace v programovacím jazyce.  
  
 V okně **Nastavení zarážky** zaškrtněte políčko **Akce** . V okně Skupina **akcí** vyberte možnost **Protokolovat zprávu do okna výstup** . Můžete vytisknout obecný řetězec, například **Toto je test**. Chcete-li zahrnout hodnotu proměnné nebo výrazu, vložte ji do složených závorek.  
  
 Chcete-li přerušit provádění, když je dosaženo zarážka s trasováním, zrušte zaškrtnutí políčka **pokračovat v provádění** . Když je zaškrtnuto políčko **pokračovat v provádění** , provádění se neukončí. V obou případech se zpráva vytiskne.  
  
 Ve **zprávě**můžete použít následující speciální klíčová slova.  
  
|Klíčové slovo|Popis|  
|-|-|  
|**$ADDRESS**|Aktuální instrukce|  
|**$CALLER**|Název volající funkce|  
|**$CALLSTACK**|Zásobník volání|  
|**$FUNCTION**|Název aktuální funkce|  
|**$PID**|ID procesu|  
|**$PNAME**|Název procesu|  
|**$TID**|ID vlákna|  
|**$TNAME**|Název vlákna|  
|**$TICK**||  
|**$TNAME**||  
  
## <a name="breakpoint-labels"></a><a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a>Popisky zarážek  
 Popisky zarážek se používají pouze v okně **zarážky** k řazení a filtrování seznamu zarážek. Chcete-li přidat popisek ke zarážce, zvolte řádek zarážky a pak v místní nabídce zvolte možnost **popisek** .  
  
## <a name="export-and-import-breakpoints"></a>Export a import zarážek  
 Zarážku můžete exportovat do souboru XML tak, že kliknete pravým tlačítkem na zarážku a vyberete **exportovat**. Soubor je ve výchozím nastavení uložen v adresáři řešení. Chcete-li importovat zarážky, otevřete okno **zarážky** (**CTRL + ALT + B**) a na panelu nástrojů klikněte na šipku vpravo (popisek je **importovat zarážky ze souboru**).  
  
## <a name="troubleshoot-breakpoints"></a>Řešení potíží se zarážkami  
  
### <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>Odstranil (a) jsem zarážku, ale po opětovném spuštění ladění se I nadále narazí  
 Pokud jste při ladění odstranili zarážku, v některých případech můžete zarážku opakovat při příštím spuštění ladění. Chcete-li ukončit tuto zarážku, zajistěte, aby všechny instance zarážky byly odebrány z okna **zarážky** .  
  
### <a name="the-debugger-cant-locate-the-correct-version-of-the-source-file-for-a-breakpoint"></a>Ladicí program nemůže najít správnou verzi zdrojového souboru pro zarážku.  
 Pokud se změnil zdrojový soubor a zdroj již neodpovídá kódu, který ladíte, může ladicí program najít zdrojový soubor, který odpovídá zarážce, i když zdrojový soubor existuje.  
  
1. Pokud chcete, aby aplikace Visual Studio zobrazovala zdrojový kód, který se neshoduje s verzí, kterou ladíte, vyberte možnost **ladění/možnosti a nastavení**. Na stránce **ladění/obecné** zrušte zaškrtnutí políčka **vyžadovat zdrojové soubory, které přesně odpovídají původní verzi** .  
  
2. Zarážku můžete také navazovat na zdrojový soubor. Vyberte zarážku a v místní nabídce zvolte **podmínky** . Ověřte, **že se zdrojový kód liší od původní** v okně **Nastavení zarážky** .  
  
### <a name="breakpoints-dont-work-in-a-dll"></a>Zarážky nefungují v knihovně DLL.  
 Nelze nastavit zarážku ve zdrojovém souboru, pokud ladicí program nenačte informace o ladění pro modul, kde se nachází kód. Mezi příznaky můžou patřit zprávy, jako například **zarážka nebude nastavena**. Glyf zarážky upozornění se zobrazí v umístění zarážky. Tyto varovné zarážky se však stanou skutečnými zarážkami při načtení kódu. Další informace o načítání symbolů naleznete v tématu [určení symbolu (. pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
## <a name="see-also"></a>Viz také  
 [Procházení kódu s ladicím programem](../debugger/navigating-through-code-with-the-debugger.md)
