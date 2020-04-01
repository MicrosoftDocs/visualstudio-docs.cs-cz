---
title: Obecné, ladění, dialogové okno Možnosti | Dokumenty společnosti Microsoft
ms.date: 11/12/2019
ms.topic: reference
f1_keywords:
- vs.debug.options.General
- VS.ToolsOptionsPages.Debugger.General
- VS.ToolsOptionsPages.Debugger.ENC
- vs.debug.options.ENC
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Options dialog box, debugging
ms.assetid: b33aee0b-43c3-4c26-8ed4-bc673f491503
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 98bbd65d11b26d9b35000e4acbe4d28a585f8ddc
ms.sourcegitcommit: ce3d0728ec1063ab548dac71c8eaf26d20450acc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2020
ms.locfileid: "80472698"
---
# <a name="general-debugging-options"></a>Obecné možnosti ladění

Chcete-li nastavit volby ladicího programu sady Visual Studio, vyberte**možnosti** **nástroje** > a v části **Ladění** vyberte nebo odznačte políčka vedle **obecných** možností. Všechna výchozí nastavení můžete obnovit pomocí **nástroje** > **Import a Nastavení exportu** > **Obnovte všechna nastavení**. Chcete-li obnovit podmnožinu nastavení, uložte nastavení pomocí **Průvodce nastavením importu a exportu** před provedením změn, které chcete otestovat, a potom importujte uložená nastavení.

Můžete nastavit následující **obecné** možnosti:

**Před odstraněním všech zarážek**požadovat: Vyžaduje potvrzení před dokončením příkazu **Odstranit všechny zarážky.**

**Přerušit všechny procesy při přerušení jednoho procesu**: Současně přeruší všechny procesy, ke kterým je připojen ladicí program, když dojde k přerušení.

**Break, když výjimky překračují AppDomain nebo spravované/nativní hranice**: V ladění spravovaného nebo smíšeného režimu může čas ový čas common jazyka zachytit výjimky, které překračují hranice domény aplikace nebo spravované/nativní hranice, pokud jsou splněny následující podmínky:

1. Když nativní kód volá spravovaný kód pomocí COM Interop a spravovaný kód vyvolá výjimku. Viz [Úvod do COM Interop](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).

2. Při spravovaném kódu spuštěném v doméně aplikace 1 volá spravovaný kód v doméně aplikace 2 a kód v doméně aplikace 2 vyvolá výjimku. Viz [Programování s aplikačními doménami](/dotnet/articles/framework/app-domains/index).

3. Když kód volá funkci pomocí reflexe a tato funkce vyvolá výjimku. Viz [Reflexe](/dotnet/framework/reflection-and-codedom/reflection).

V podmínkách 2 a 3 je výjimka `mscorlib` někdy zachycena spravovaným kódem, nikoli běžným jazykovým runtime. Tato možnost nemá vliv na rozdělení `mscorlib`na výjimky zachycené .

**Povolit ladění na úrovni adresy**: Umožňuje rozšířené funkce pro ladění na úrovni adresy (okno **demontáže,** okno **Registry** a zarážky adresy).

- **Zobrazit demontáž, pokud zdroj není k dispozici**: Automaticky zobrazí okno **Demontáže** při ladění kódu, pro který zdroj není k dispozici.

**Povolit filtry zarážky**: Umožňuje nastavit filtry na zarážky tak, aby ovlivnily pouze určité procesy, vlákna nebo počítače.

**Použijte nový pomocník pro výjimky**: Povolí pomocníka pro výjimky, který nahradí pomocníka pro výjimky. (Pomocník výjimek je podporován od spuštění v sadě Visual Studio 2017)

> [!NOTE]
> Pro spravovaný kód byla tato možnost dříve nazvána **Povolit pomocníka pro výjimky** .

**Povolit pouze můj kód**: Ladicí program zobrazí a kroky do uživatelského kódu ("Můj kód" pouze, ignoruje systémový kód a další kód, který je optimalizován nebo který nemá ladicí symboly.

- **Upozornit, pokud při spuštění není žádný uživatelský kód (pouze spravovaný):** Když je povoleno ladění s povolenou povolenou možností Jen můj kód, tato možnost vás upozorní, pokud neexistuje žádný uživatelský kód ("Můj kód").

**Povolit krokování zdroje rozhraní .NET Framework**: Umožňuje ladicímu programu krokovat do zdroje rozhraní .NET Framework. Povolením této možnosti se automaticky zakáže pouze můj kód. Symboly rozhraní .NET Framework budou staženy do umístění mezipaměti. Změňte umístění mezipaměti pomocí dialogového okna **Možnosti,** kategorie **Ladění,** **Symboly.**

**Krok přes vlastnosti a operátory (pouze spravované)**: Zabrání ladicí program krokování do vlastností a operátorů ve spravovaném kódu.

**Povolit vyhodnocení vlastností a další implicitní volání funkcí**: Zapne automatické vyhodnocení vlastností a volání implicitních funkcí v oknech proměnných a v dialogovém okně **QuickWatch.**

- **Funkce převodu volání řetězce u objektů v proměnných windows (pouze C# a JavaScript)**: Provede volání implicitního převodu řetězce při vyhodnocování objektů v oknech proměnných. Výsledek se zobrazí jako řetězec namísto názvu typu. Platí pouze při ladění v kódu jazyka C#. Toto nastavení může být přepsáno atributem DebuggerDisplay (viz [Použití atributu DebuggerDisplay).](../debugger/using-the-debuggerdisplay-attribute.md)

**Povolit podporu zdrojového serveru**: Říká ladicímu programu sady Visual Studio získat`srcsrv.dll`zdrojové soubory ze zdrojových serverů, které implementují protokol SrcSrv ( ). Team Foundation Server a ladicí nástroje pro Windows jsou dva zdrojové servery, které implementují protokol. Další informace o nastavení SrcSrv naleznete v dokumentaci [srcsrv.](/windows-hardware/drivers/debugger/srcsrv) Kromě toho viz [Určení symbolu (.pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

> [!IMPORTANT]
> Vzhledem k tomu, že čtení souborů *PDB* může v souborech spustit libovolný kód, ujistěte se, že serveru důvěřujete.

- **Tisk diagnostických zpráv zdrojového serveru do okna Výstup**: Pokud je povolena podpora zdrojového serveru, toto nastavení zapne diagnostické zobrazení.

- **Povolit zdrojový server pro sestavení s částečnou důvěryhodností (pouze spravovaná)**: Pokud je povolena podpora zdrojového serveru, toto nastavení přepíše výchozí chování nenačítání zdrojů pro sestavení s částečnou důvěryhodností.

- **Vždy spouštět nedůvěryhodné příkazy zdrojového serveru bez zobrazení výzvy**: Pokud je povolena podpora zdrojového serveru, toto nastavení přepíše výchozí chování zobrazení při spuštění nedůvěryhodného příkazu.

**Povolit podporu zdrojového odkazu**: Sděluje ladicímu programu sady Visual Studio stahování zdrojových souborů pro soubory *PDB,* které obsahují informace o zdrojovém propojení. Další informace o zdrojovém odkazu naleznete ve [specifikaci zdrojového odkazu](/dotnet/standard/library-guidance/sourcelink).

> [!IMPORTANT]
> Vzhledem k tomu, že zdrojový odkaz bude stahovat soubory pomocí protokolu HTTP nebo https, ujistěte se, že souboru *PDB* důvěřujete.

- **Vraťte se zpět k ověřování Git Credential Manager pro všechny požadavky zdrojového odkazu**: Pokud je povolena podpora zdrojového odkazu a požadavek zdrojového odkazu se nezdaří ověřování, Visual Studio pak volá Správce přihlašovacích údajů Git.

**Zvýrazněte celý řádek pro zarážky a aktuální příkaz (pouze C++):** Když ladicí program zvýrazní zarážku nebo aktuální příkaz, zvýrazní celý řádek.

**Vyžadovat, aby zdrojové soubory přesně odpovídaly původní verzi**: Informuje ladicí program o ověření, že zdrojový soubor odpovídá verzi zdrojového kódu použitého k vytvoření spustitelného souboru, který ladíte. Pokud se verze neshoduje, budete vyzváni k nalezení odpovídajícího zdroje. Pokud není nalezen odpovídající zdroj, zdrojový kód se během ladění nezobrazí.

**Přesměrovat veškerý text okna Výstup do okna Okamžité**: Odešle všechny ladicí zprávy, které by se obvykle zobrazily v okně **Výstup,** do okna **Okamžité.**

**Zobrazit nezpracovaná struktura objektů v oknech proměnných**: Vypne všechna vlastní nastavení zobrazení struktury objektů. Další informace o vlastním nastavení zobrazení naleznete v [tématu Vytvoření vlastních zobrazení spravovaných objektů](../debugger/create-custom-views-of-managed-objects.md).

**Potlačit optimalizaci JIT při načtení modulu (pouze spravovaný)**: Zakáže optimalizaci JIT spravovaného kódu při načtení modulu a JIT je zkompilován při připojení ladicího programu. Zakázání optimalizace může usnadnit ladění některých problémů, i když na úkor výkonu. Pokud používáte just my code, potlačení optimalizace JIT může způsobit, že se neuživatelský kód zobrazí jako uživatelský kód ("Můj kód"). Další informace naleznete v tématu [optimalizace jit a ladění](../debugger/jit-optimization-and-debugging.md).

**Povolit ladění jazyka JavaScript pro ASP.NET (Chrome, Microsoft Edge a IE):** Povolí ladicí program skriptu pro ASP.NET aplikace. Při prvním použití v Chromu se možná budete muset přihlásit do prohlížeče, abyste povolili rozšíření Chrome, která jste nainstalovali. Zakázat tuto možnost vrátit ke staršímu chování.

**Povolit nástroje edge developer pro aplikace JavaScript UWP (Experimental):** Povolí vývojářské nástroje pro aplikace Jazyka JavaScript UWP v microsoft edge.

**Povolit starší ladicí program Chrome JavaScript pro ASP.NET**: Povolí starší ladicí program skriptu JavaScript chrome pro ASP.NET aplikace. Při prvním použití v Chromu se možná budete muset přihlásit do prohlížeče, abyste povolili rozšíření Chrome, která jste nainstalovali.

**Pomocí experimentálního způsobu spuštění ladění Jazyka JavaScript chrome při spuštění sady Visual Studio jako správce**: Aplikace Visual Studio vyzkouší nový způsob spuštění Chromu během ladění JavaScriptu.

**Načíst exportdll (pouze nativní)**: Načte tabulky exportu dll. Informace o symbolech z tabulek exportu knihovny DLL mohou být užitečné, pokud pracujete se zprávami systému Windows, postupy systému Windows (WindowProcs), objekty COM nebo zařazováním nebo libovolnou knihovnou DLL, pro kterou nemáte symboly. Čtení informací o exportu dll zahrnuje určitou režii. Proto tato možnost je ve výchozím nastavení vypnuta.

Chcete-li zjistit, jaké symboly jsou k `dumpbin /exports`dispozici v tabulce exportu dll, použijte . Symboly jsou k dispozici pro libovolnou 32bitovou systémovou dll. Po přečtení `dumpbin /exports` výstupu můžete zobrazit přesný název funkce, včetně nealfanumerických znaků. To je užitečné pro nastavení zarážky na funkci. Názvy funkcí z tabulek exportu dll se mohou jevit zkráceně jinde v ladicím programu. Volání jsou uvedena v pořadí volání s aktuální funkcí (nejhlouběji vnořených) nahoře. Další informace naleznete v [tématu dumpbin /exports](/cpp/build/reference/dash-exports).

**Zobrazit diagram paralelních zásobníků zdola nahoru**: Určuje směr, ve kterém jsou zásobníky zobrazeny v okně **Paralelní hromádky.**

**Ignorovat výjimky přístupu do paměti GPU, pokud zapsaná data nezměnila hodnotu**: Ignoruje konflikty časování, které byly zjištěny během ladění, pokud se data nezměnila. Další informace naleznete [v tématu Ladění kódu GPU](../debugger/debugging-gpu-code.md).

**Použít režim spravované kompatibility**: Nahradí výchozí ladicí modul starší verzí, aby povolil tyto scénáře:

- Používáte jiný jazyk .NET než C#, Visual Basic nebo F#, který poskytuje vlastní vyhodnocení výrazu (to zahrnuje C++/CLI).

- Chcete povolit upravit a pokračovat pro projekty jazyka C++ během ladění ve smíšeném režimu.

> [!NOTE]
> Volba režimu spravované kompatibility zakáže některé funkce, které jsou implementovány pouze ve výchozím ladicím modulu. Starší ladicí modul byl nahrazen v sadě Visual Studio 2012.

**Použijte starší vyhodnocení výrazů C# a VB**: Ladicí program použije vyhodnocení výrazů Visual Studio 2013 C# nebo Visual Basic místo vyhodnocení výrazů založených na jazyce Visual Studio 2015 Roslyn.

**Upozornit při použití vlastních vizualizérů ladicího programu proti potenciálně nebezpečným procesům (pouze spravované):** Visual Studio vás upozorní, když používáte vlastní vizualizér ladicího programu, který běží kód v ladicím procesu, protože může být spuštěn nebezpečný kód.

**Povolit alokátor haldy ladění systému Windows (pouze nativní)**: Povolí haldě ladění systému Windows zlepšit diagnostiku haldy. Povolení této možnosti bude mít vliv na výkon ladění.

Povolit nástroje pro ladění uživatelského **prostředí pro XAML**: Živý vizuální strom a okna Live Property Explore se zobrazí, když začnete ladit (**F5**) podporovaný typ projektu. Další informace naleznete [v tématu Kontrola vlastností XAML při ladění](../xaml-tools/inspect-xaml-properties-while-debugging.md).

- **Náhled vybraných prvků v živém vizuálním stromu**: Prvek XAML, jehož kontext je vybrán, je také vybrán v okně **Živý vizuální strom.**

- **Zobrazit nástroje runtime v aplikaci**: Zobrazí příkazy **Živé vizuální stromy** na panelu nástrojů v hlavním okně aplikace XAML, která je právě laděna. Tato možnost byla zavedena v aktualizaci Visual Studio 2015 Update 2.

- **Povolit xaml hot reload**: Umožňuje používat funkci XAML Hot Reload s kódem XAML, když je aplikace spuštěná. (Tato funkce byla dříve nazvána "Úprava a pokračování XAML")

::: moniker range=">= vs-2019" 
- **Povolit pouze můj XAML**: Počínaje Visual Studio 2019 verze 16.4, **Live Visual Tree** ve výchozím nastavení zobrazuje pouze XAML, který je klasifikován jako uživatelský kód. Pokud tuto možnost zakážete, zobrazí se v nástroji veškerý generovaný kód XAML.

- **Vypnutí režimu výběru při výběru prvku** Počínaje visual studio 2019 verze 16.4, v aplikaci tlačítko pro výběr prvků panelu nástrojů (**Povolit výběr**) vypne, když je vybraný prvek. Pokud tuto možnost zakážete, výběr prvků zůstane zapnutý, dokud znovu neklepnete na tlačítko panelu nástrojů v aplikaci.
::: moniker-end

**Povolit diagnostické nástroje při ladění**: Při ladění se zobrazí okno Diagnostické **nástroje.**

**Zobrazit uplynulý čas PerfTip při ladění**: Okno kódu zobrazí uplynulý čas daného volání metody při ladění.

**Povolit úpravy a pokračovat:** Povolí funkci Upravit a Pokračovat při ladění.

- **Povolit nativní úpravy a pokračovat:** Můžete použít funkci Upravit a pokračovat při ladění nativního kódu C++. Další informace naleznete v [tématu Úpravy a pokračování (C++)](../debugger/edit-and-continue-visual-cpp.md).

- **Použít změny na continue (pouze nativní):** Visual Studio automaticky zkompiluje a použije všechny zbývající změny kódu, které jste provedli při pokračování procesu ze stavu přerušení. Pokud není vybrána, můžete použít změny pomocí položky **Použít změny kódu** v nabídce **Ladění.**

- **Upozornit na zastaralý kód (pouze nativní):** Získejte upozornění na zastaralý kód.

**Zobrazit tlačítko Spustit na tlačítko click v editoru při ladění**: Pokud je vybrána tato možnost, tlačítko [Spustit k kliknutí](../debugger/debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) se zobrazí při ladění.

**Automaticky zavřete konzolu při ladění zastaví**: Říká Visual Studio zavřít konzolu na konci relace ladění.

::: moniker range=">= vs-2019"
**Povolit rychlé vyhodnocení výrazu (pouze spravované)**: Umožňuje ladicímu programu pokusit se o rychlejší vyhodnocení simulací provádění jednoduchých vlastností a metod.
::: moniker-end

## <a name="options-available-in-older-versions-of-visual-studio"></a>Možnosti dostupné ve starších verzích sady Visual Studio

Pokud používáte starší verzi sady Visual Studio, mohou být k dispozici některé další možnosti.

**Povolit pomocníka pro výjimky**: Pro spravovaný kód povolí pomocníka s výjimkou. Počínaje Visual Studio 2017, Pomocník pro výjimky nahradil pomocníka pro výjimky.

**Unwind zásobníku volání na neošetřené výjimky**: Způsobí, že okno **zásobníku volání** vrátit zpět zásobníku volání do bodu před neošetřené výjimky došlo.

**Upozornit, pokud při spuštění nejsou žádné symboly (pouze nativní):** Zobrazí dialogové okno s upozorněním při ladění programu, pro který ladicí program nemá žádné informace o symbolu.

**Upozornit, pokud je ladění skriptů při spuštění zakázáno**: Zobrazí dialogové okno s upozorněním při spuštění ladicího programu se zakázaným laděním skriptů.

**Použít nativní režim kompatibility**: Pokud je vybrána tato možnost, ladicí program používá nativní ladicí program sady Visual Studio 2010 namísto nového nativního ladicího programu.

- Tuto možnost použijte při ladění kódu .NET C++, protože nový ladicí modul nepodporuje vyhodnocení výrazů .NET C++. Povolení režimu nativní kompatibility však zakáže mnoho funkcí, které závisí na aktuální implementaci ladicího programu pro provoz. Například starší modul postrádá mnoho vizualizérů `std::string` pro předdefinované typy, jako je v projektech Visual Studio 2015.   Použijte projekty Visual Studio 2013 pro optimální ladění prostředí v těchto případech.

## <a name="see-also"></a>Viz také

- [Ladění v sadě Visual Studio](../debugger/index.yml)
- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
