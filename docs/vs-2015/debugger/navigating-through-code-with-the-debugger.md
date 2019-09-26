---
title: Navigace v kódu pomocí ladicího programu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.execution
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
caps.latest.revision: 47
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f79ece781db19f2483ef1dd6cb0a81ff7cf78e06
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "64836314"
---
# <a name="navigating-through-code-with-the-debugger"></a>Procházení kódu s ladicím programem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Seznamte se s příkazy a zástupci pro navigaci v kódu v ladicím programu a díky tomu je rychlejší a snazší najít a vyřešit problémy ve vaší aplikaci. Při procházení kódu v ladicím programu můžete [zkontrolovat stav vaší aplikace](https://msdn.microsoft.com/library/mt243867.aspx#BKMK_Inspect_Variables) nebo se dozvědět více o jeho toku provádění.  
  
## <a name="start-debugging"></a>Spustit ladění  
 Často se**spouští ladicí relace** / s použitím klávesy **F5** (ladění**Začínáme**). Tento příkaz spustí aplikaci pomocí připojeného ladicího programu.  
  
 Zelená šipka také spustí ladicí program (totéž jako **F5**).  
  
 ![DBG&#95;Basics&#95;Start&#95;Debugging](../debugger/media/dbg-basics-start-debugging.png "DBG_Basics_Start_Debugging")  
  
 Několik dalších způsobů, jak můžete aplikaci spustit pomocí připojeného ladicího programu, zahrnují **F11** ([Krok do kódu](#BKMK_Step_into__over__or_out_of_the_code)), **F10** ([Krok přes kód](#BKMK_Step_over_Step_out)) nebo pomocí možnosti **Spustit ke kurzoru**.  Informace o tom, co tyto možnosti dělají, najdete v dalších částech tohoto tématu.  
  
 Když ladíte, žlutá čára zobrazí kód, který bude proveden jako další.  
  
 ![DBG&#95;Basics&#95;Break&#95;Mode](../debugger/media/dbg-basics-break-mode.png "DBG_Basics_Break_Mode")  
  
 Během ladění můžete přepínat mezi příkazy jako **F5**, **F11** a používat další funkce popsané v tomto tématu (například zarážky), abyste se rychle dostali ke kódu, který chcete zobrazit.  
  
 Většina funkcí ladicího programu, jako je například zobrazení hodnot proměnných v okně místních hodnot nebo vyhodnocování výrazů v okno Kukátko, jsou k dispozici pouze v případě, že ladicí program je pozastaven (označovaný také jako *režim přerušení*). Když je ladicí program pozastaven, stav aplikace je pozastaven, zatímco funkce, proměnné a objekty zůstávají v paměti. V režimu pozastavení můžete zkontrolovat, že prvky a stavy jsou pro hledání porušení nebo chyby. U některých typů projektů lze také provést úpravy aplikace v režimu přerušení.  
  
## <a name="BKMK_Step_into__over__or_out_of_the_code"></a>Krokovat do kódu, řádek po řádku  
 Chcete-li zastavit u každého řádku kódu (každý příkaz) při ladění, použijte klávesovou zkratku **F11** (nebo krok **ladění** / **do** nabídky).  
  
> [!TIP]
> Při provádění jednotlivých řádků kódu můžete umístit ukazatele myši nad proměnné, abyste viděli jejich hodnoty, nebo pomocí oken [místní](../debugger/autos-and-locals-windows.md) hodnoty a [kukátka](../debugger/autos-and-locals-windows.md) sledovat jejich změny.  
  
 Tady jsou některé podrobnosti o chování **kroku do**:  
  
- U volání vnořené funkce **Krokovat s vnořením** přejde k nejhlouběji vnořené funkci. Použijete-li **Krok into** pro volání jako `Func1(Func2())`, ladicí program kroky do funkce. `Func2`  
  
- Ladicí program ve skutečnosti provádí příkazy kódu místo fyzických řádků. Například `if` klauzuli lze zapsat na jeden řádek:  
  
  ```csharp  
  int x = 42;  
  string s = "Not answered";  
  if( int x == 42) s = "Answered!";  
  ```  
  
  ```vb  
  Dim x As Integer = 42  
  Dim s As String = "Not answered"  
  If x = 42 Then s = "Answered!"  
  ```  
  
   Při krokovat s tímto řádkem ladicí program považuje podmínku za jeden krok a jako jiný (v tomto příkladu je podmínka pravdivá).  
  
  Chcete-li vizuálně sledovat zásobník volání při krokování do funkcí, viz [metody map v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
## <a name="BKMK_Step_over_Step_out"></a>Krokovat kód, přeskočí funkce  
 Při spouštění kódu v ladicím programu často budete vědět, že nepotřebujete vidět, co se děje v konkrétní funkci (nezáleží na tom, zda funguje, jako dobře testovaný kód knihovny). Tyto příkazy použijte k přeskočení kódu (funkce se stále spouštějí, ale ladicí program je přeskočí).  
  
|Příkaz klávesnice|Příkaz nabídky|Popis|  
|----------------------|------------------|-----------------|  
|**F10**|**Krok přes**|Pokud aktuální řádek obsahuje volání funkce, **krok po** spuštění kódu pak pozastaví provádění na prvním řádku kódu po návratu volané funkce.|  
|**Shift+F11**|**Krokovat s Vystoupením**|**Krok ven** pokračuje v běhu kódu a pozastaví provádění, když se vrátí aktuální funkce (ladicí program přeskočí aktuální funkce).|  
  
> [!TIP]
> Pokud je potřeba najít vstupní bod ve vaší aplikaci, začněte s **F10** nebo **F11**. Tyto příkazy jsou často užitečné při kontrole stavu aplikace nebo při pokusu o získání dalších informací o jeho toku provádění.  
  
## <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> Spuštění do určitého umístění nebo – funkce  
 Upřednostňovanou metodou ladění kódu je často, že tyto metody jsou užitečné, pokud přesně víte, jaký kód chcete zkontrolovat, nebo alespoň víte, kde chcete spustit ladění.  
  
- **Nastavení zarážek v kódu**  
  
     Chcete-li v kódu nastavit jednoduchou zarážku, otevřete zdrojový soubor v editoru sady Visual Studio. Nastavte kurzor na řádek kódu, kde chcete pozastavit provádění, a pak klikněte pravým tlačítkem myši v okně kód, aby se zobrazila kontextová nabídka a zvolte **zarážka/vložení zarážky** (nebo stiskněte **F9**). Ladicí program pozastaví provádění přímo před provedením řádku.  
  
     ![Nastavit zarážku](../debugger/media/dbg-basics-setbreakpoint.png "DBG_Basics_SetBreakpoint")  
  
     Zarážky v sadě Visual Studio poskytují další funkce, jako je například podmíněné zarážky a sledované body. Viz [použití zarážek](../debugger/using-breakpoints.md).  
  
- **Spustit do umístění kurzoru**  
  
     Chcete-li spustit do umístění kurzoru, umístěte kurzor na spustitelný řádek kódu v okně zdroje. V kontextové nabídce editoru (klikněte pravým tlačítkem myši v editoru) vyberte možnost **Spustit ke kurzoru**. Toto je jako nastavení dočasné zarážky.  
  
- **Ručně přerušit do kódu**  
  
     Chcete-li přejít na další dostupný řádek kódu ve spuštěné aplikaci, vyberte možnost **ladit**, **přerušit vše** (klávesnice: **CTRL + ALT + BREAK**).  
  
     Pokud přerušíte provádění kódu bez odpovídajícího zdrojového souboru nebo souborů symbolů (PDB), ladicí program zobrazí stránku **nenalezené zdrojové soubory** nebo **symboly nenalezeny** , které vám pomohou najít příslušné soubory. Viz [určení symbolu (. pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Pokud nemůžete získat přístup k podpůrným souborům, můžete přesto ladit pokyny sestavení v okně zpětný překlad.  
  
- **Spustit do funkce v zásobníku volání**  
  
     V okně **zásobník volání** (k dispozici při ladění) vyberte funkci, klikněte pravým tlačítkem myši a zvolte možnost **Spustit ke kurzoru**. Vizuální trasování zásobníku volání, viz [mapování metod v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
- **Spustit do funkce určené podle názvu**  
  
     Můžete sdělit ladicímu programu, aby spustil vaši aplikaci, dokud nedosáhne zadané funkce. Můžete zadat funkci podle názvu nebo si ji můžete vybrat ze zásobníku volání.  
  
     Chcete-li zadat funkci podle názvu, zvolte možnost **ladit**, **Nová zarážka**, **funkce break**on a potom zadejte název funkce a další identifikační informace.  
  
     ![Nová zarážka – Dialogové okno](../debugger/media/dbg-execution-newbreakpoint.png "DBG_Execution_NewBreakpoint")  
  
     Pokud je funkce přetížena nebo je ve více oborech názvů, můžete zvolit požadované funkce v dialogovém okně **Vybrat zarážky** .  
  
     ![Vybrat zarážky – dialogové okno](../debugger/media/dbg-execution-overloadedbreakpoints.png "DBG_Execution_OverloadedBreakpoints")  
  
## <a name="BKMK_Set_the_next_statement_to_execute"></a> Přesuňte ukazatel Změna toku provádění  
 I když je ladicí program pozastaven, lze přesunout ukazatel instrukcí pro nastavení dalšího příkazu kódu, který má být proveden. Žlutá šipka na okraji zdrojového nebo zpětnýho okna označuje umístění dalšího příkazu, který má být proveden. Přesunutím této šipky můžete přeskočit část kódu nebo vrátit na řádek, který byl dříve proveden. Tuto možnost můžete použít v situacích, jako je například přeskočení oddílu kódu, který obsahuje známou chybu.  
  
 ![Priklad2](../debugger/media/dbg-basics-example2.png "DBG_Basics_Example2")  
  
 Chcete-li nastavit další příkaz, který má být spuštěn, použijte jeden z následujících postupů:  
  
- V okně zdroje přetáhněte žlutou šipku na místo, kde chcete nastavit další příkaz ve stejném zdrojovém souboru.  
  
- V okně zdroje nastavte kurzor na řádku, který chcete spustit dále, klikněte pravým tlačítkem myši a vyberte možnost **nastavit další příkaz**.  
  
- V okně zpětný překlad nastavte kurzor na instrukci sestavení, kterou chcete spustit dále, klikněte pravým tlačítkem myši na a vyberte možnost **nastavit další příkaz**.  
  
> [!CAUTION]
> Nastavení dalšího příkazu způsobí, že čítač programu Přeskočí přímo do nového umístění. Použijte tento příkaz opatrně:  
> 
> - Pokyny mezi starými a novými body spuštění nejsou provedeny.  
>   - Pokud přesunete bod provádění zpět, nekončí se žádné pokyny.  
>   - Přesunutí dalšího příkazu do jiné funkce nebo rozsahu obvykle za následek poškození zásobníku volání, což způsobí runtime chybu nebo výjimku. Při přesunutí dalšího příkazu do jiného oboru, ladicí program otevře dialogové okno s upozorněním a dává vám možnost zrušit operaci. V jazyce Visual Basic nemůžete přesunout do jiného oboru nebo funkce další příkaz.  
>   - V nativním kódu C++ Pokud máte kontroly za běhu povoleno, nastavení dalšího příkazu může způsobit výjimku, která je vyvolána, když spuštění dosáhne konce metody.  
>   - Když upravit a pokračovat je povoleno, **nastavit další příkaz** nezdaří, pokud jste provedli změny, které upravit a pokračovat nemůže ihned opětovně mapovat. Tato situace může nastat, například, pokud se po úpravě kódu v bloku catch. V takovém případě se zobrazí chybová zpráva oznamující, že operace není podporována.  
> 
> [!NOTE]
> Ve spravovaném kódu nelze přesunout další příkaz za následujících podmínek:  
> 
> - Další příkaz je v jiné metody než aktuální příkaz.  
>   - Ladění bylo spuštěno pomocí ladění za běhu.  
>   - Probíhá zásobník volání unwind.  
>   - Byla vyvolána výjimka System.StackOverflowException or System.Threading.ThreadAbortException.  
  
 Nejde nastavit další příkaz, když je vaše aplikace aktivně spuštěná. Chcete-li nastavit další příkaz, musí být ladicí program v režimu pozastavení.  
  
## <a name="step-into-non-user-code"></a>Krokovat s jiným neuživatelským kódem  
 Ve výchozím nastavení se ladicí program pokusí zobrazit pouze kód aplikace během ladění, což je určeno nastavením ladicího programu s názvem *pouze můj kód*. (Další informace o tom, jak to funguje pro různé typy projektů a jazyky a jak se chování přizpůsobit, najdete v tématu [pouze můj kód](../debugger/just-my-code.md) .) V některých případech však budete chtít sledovat kód rozhraní, kód knihovny třetí strany nebo volání operačního systému (systémová volání).  
  
 Pouze můj kód můžete vypnout tak, že kliknete na **nástroje** / **ladění** **možností** / a zrušíte zaškrtnutí políčka **Povolit pouze můj kód** .  
  
 Když je Pouze můj kód zakázaný, ladicí program může Krokovat s neuživatelským kódem a neuživatelský kód se zobrazí v oknech ladicího programu.  
  
> [!NOTE]
> Funkce pouze můj kód není podporována pro projekty zařízení.  
  
 **Krokovat s vnořením do systémových volání**  
  
 Pokud jste načetli symboly ladění pro systémový kód a Pouze můj kód není povolen, můžete krokovat se systémovým voláním stejně jako jakékoli jiné volání.  
  
 Chcete-li získat přístup k souborům symbolů společnosti Microsoft, přečtěte si téma [použití serverů symbolů pro hledání souborů symbolů, které nejsou na vašem místním počítači](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine) , v tématu [určení symbolu (PDB) a zdrojové soubory](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) .  
  
 Načtení symbolů pro konkrétní systémovou komponentu při ladění:  
  
1. Otevřete okno moduly (klávesnice: **CTRL + ALT + U**).  
  
2. Vyberte modul, pro který chcete načíst symboly.  
  
     Můžete zjistit, které moduly mají načtené symboly, a to tak, že prohlížíte sloupec **stav symbolu** .  
  
3. V místní nabídce vyberte možnost **načíst symboly** .  
  
## <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Krokovat přes vlastnosti a operátory ve spravovaném kódu  
 Ladicí program přes vlastnosti a operátory ve spravovaném kódu ve výchozím nastavení. Ve většině případů to poskytuje lepší možnosti ladění. Chcete-li povolit krokování s vnořením do vlastností nebo operátorů, zvolte **ladění** / **možnosti**. Na stránce**Obecné** **ladění** / zrušte zaškrtnutí políčka **Krokovat přes vlastnosti a operátory (pouze spravované)** .
