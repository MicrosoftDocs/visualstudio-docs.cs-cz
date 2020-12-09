---
title: Obecné, ladění, dialogové okno Možnosti | Microsoft Docs
description: Nastavte možnosti ladicího programu sady Visual Studio tak, aby splňovaly vaše požadavky na ladění. Můžete nakonfigurovat chování přerušení, úrovně ladění, chování zobrazení a mnoho dalšího.
ms.custom: SEO-VS-2020
ms.date: 06/04/2020
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
ms.openlocfilehash: 1b052c2cce3d396debb4fbaf8ce688ede3effb98
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/08/2020
ms.locfileid: "96863007"
---
# <a name="general-debugging-options"></a>Obecné možnosti ladění

Chcete-li nastavit možnosti ladicího programu sady Visual Studio, vyberte možnost **nástroje**  >  **Options** a v části **ladění** zaškrtněte nebo zrušte zaškrtnutí políček u **obecných** možností. Můžete obnovit všechna výchozí nastavení pomocí **nástrojů** pro  >  **Import a export nastavení**  >  **Obnovit všechna nastavení**. Chcete-li obnovit podmnožinu nastavení, uložte nastavení pomocí **Průvodce importem a exportem nastavení** před provedením změn, které chcete otestovat, a pak import uložených nastavení proveďte později.

Můžete nastavit následující **Obecné** možnosti:

**Dotázat se před smazáním všech zarážek**: vyžaduje potvrzení před dokončením příkazu **Odstranit všechny zarážky** .

**Přerušit všechny procesy při přerušení jednoho procesu**: souběžně dojde k přerušení všech procesů, ke kterým je připojen ladicí program, když dojde k přerušení.

**Přerušení při výjimkách mezi doménou AppDomain nebo spravované/nativní hranice**: ve spravovaném nebo kombinovaném režimu ladění může modul common language runtime zachytit výjimky, které překračují hranice aplikační domény, nebo spravované/nativní hranice, pokud jsou splněné následující podmínky:

1. Když nativní kód volá spravovaný kód pomocí zprostředkovatele komunikace s objekty COM a spravovaný kód vyvolá výjimku. Viz [Úvod do zprostředkovatele komunikace s objekty COM](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).

2. Pokud spravovaný kód spuštěný v doméně aplikace 1 volá spravovaný kód v aplikační doméně 2 a kód v aplikační doméně 2 vyvolá výjimku. Viz téma [programování s aplikačními doménami](/dotnet/articles/framework/app-domains/index).

3. Když kód volá funkci pomocí reflexe a tato funkce vyvolá výjimku. Viz [reflexe](/dotnet/framework/reflection-and-codedom/reflection).

V podmínkách 2 a 3 je výjimka někdy zachycena spravovaným kódem `mscorlib` spíše než modulem CLR (Common Language Runtime). Tato možnost neovlivňuje přerušení u výjimek zachycených v `mscorlib` .

**Povolit ladění na úrovni adres**: povoluje rozšířené funkce pro ladění na úrovni adresy (okno **zpětný překlad** , okno **Registry** a zarážky adres).

- **Zobrazit zpětný překlad, pokud není k dispozici zdroj**: automaticky zobrazí okno **zpětný překlad** při ladění kódu, pro který zdroj není k dispozici.

**Povolit filtry zarážek**: umožňuje nastavit filtry na zarážekch, takže budou mít vliv jenom na konkrétní procesy, vlákna nebo počítače.

**Použití nového pomocníka výjimky**: povolí pomocníka výjimky, který nahradí pomocníka výjimky. (Pomocník s výjimkou je podporován od sady Visual Studio 2017)

> [!NOTE]
> Pro spravovaný kód tato možnost dříve volala **Pomocníka s výjimkou** .

**Povolit pouze můj kód**: ladicí program se zobrazí pouze v uživatelském kódu ("můj kód"), ignoruje systémový kód a jiný kód, který je optimalizován nebo který nemá symboly ladění.

- **Zobrazit upozornění, pokud při spuštění bez uživatelského kódu (pouze spravované)**: Pokud ladění začíná na pouze můj kód povoleno, tato možnost vás upozorní, pokud není k dispozici žádný uživatelský kód ("můj kód").

**Povolit .NET Frameworkho krokování zdroje**: umožňuje ladicímu programu krokování do .NET Framework zdroje. Povolení této možnosti automaticky zakáže Pouze můj kód. .NET Framework symboly budou staženy do umístění mezipaměti. Změňte umístění mezipaměti pomocí dialogového okna **Možnosti** , kategorie **ladění** , stránka **symboly** .

**Krokovat přes vlastnosti a operátory (pouze spravované)**: brání ladicímu programu v krokování do vlastností a operátorů ve spravovaném kódu.

**Povolit vyhodnocování vlastností a další volání implicitních funkcí**: zapne automatické vyhodnocení vlastností a volání implicitních funkcí v oknech proměnné a v dialogovém okně **QuickWatch** .

- **Funkce pro převod řetězce volání u objektů v oknech proměnných (pouze C# a JavaScript)**: spustí volání implicitního převodu řetězce při vyhodnocování objektů v oknech proměnných. Výsledek se zobrazí jako řetězec namísto názvu typu. Platí pouze při ladění v kódu jazyka C#. Toto nastavení může být přepsáno atributem DebuggerDisplay (viz [použití atributu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)).

**Povolit podporu zdrojového serveru**: instruuje ladicí program sady Visual Studio, aby získal zdrojové soubory ze zdrojových serverů, které implementují protokol SrcSrv ( `srcsrv.dll` ). Team Foundation Server a ladicí nástroje pro Windows jsou dva zdrojové servery, které implementují protokol. Další informace o instalaci SrcSrv najdete v dokumentaci k [srcsrv](/windows-hardware/drivers/debugger/srcsrv) . Kromě toho si přečtěte téma [určení symbolu (. pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

> [!IMPORTANT]
> Vzhledem k tomu, že čtení souborů *. pdb* může spustit libovolný kód v souborech, ujistěte se, že důvěřujete serveru.

- **Vytiskněte diagnostické zprávy zdrojového serveru do okna výstup**: když je povolená podpora zdrojového serveru, toto nastavení zapne diagnostické zobrazení.

- **Povolit zdrojový server pro sestavení částečné důvěryhodnosti (pouze spravované)**: Pokud je povolena podpora zdrojového serveru, toto nastavení přepíše výchozí chování při nenačítání zdrojů pro sestavení s částečnou důvěryhodností.

- **Vždy spouštět nedůvěryhodné příkazy zdrojového serveru bez zobrazení výzvy**: když je povolená podpora zdrojového serveru, toto nastavení přepíše výchozí chování při zobrazování výzev při spuštění nedůvěryhodného příkazu.

**Povolit podporu zdrojového odkazu**: instruuje ladicí program sady Visual Studio, aby stahoval zdrojové soubory pro soubory *. pdb* , které obsahují informace o zdrojovém odkazu. Další informace o zdrojovém odkazu najdete v tématu [specifikace zdrojového odkazu](/dotnet/standard/library-guidance/sourcelink).

> [!IMPORTANT]
> Vzhledem k tomu, že odkaz na zdroj stáhne soubory pomocí protokolu HTTP nebo https, ujistěte se, že důvěřujete souboru *. pdb* .

- **Přejít zpět na ověření správce přihlašovacích údajů Git pro všechny požadavky na zdrojové odkazy**: když je povolená podpora zdrojového odkazu a požadavek na zdrojový odkaz se nezdařil, Visual Studio pak zavolá správce přihlašovacích údajů Git.

**Zvýraznit celý řádek zdroje pro zarážky a aktuální příkaz (pouze C++)**: když ladicí program zvýrazní zarážku nebo aktuální příkaz, zvýrazní celý řádek.

**Vyžadovat, aby se zdrojové soubory přesně shodovaly s původní verzí**: instruuje ladicí program, aby ověřil, že zdrojový soubor odpovídá verzi zdrojového kódu používané k sestavení spustitelného souboru, který ladíte. Pokud se verze neshoduje, budete vyzváni k vyhledání odpovídajícího zdroje. Pokud se nenalezne shodný zdroj, během ladění se nezobrazí zdrojový kód.

**Přesměrovat text z okna výstup do** příkazového okna: pošle všechny zprávy ladicího programu, které by se obvykle zobrazovaly v okně **výstup** , do příkazového **podokna místo** toho.

**Zobrazit nezpracovanou strukturu objektů v oknech proměnných**: vypne všechna přizpůsobení zobrazení struktury objektů. Další informace o úpravách zobrazení najdete v tématu [Vytvoření vlastních zobrazení spravovaných objektů](../debugger/create-custom-views-of-managed-objects.md).

**Potlačit optimalizaci JIT při načtení modulu (pouze spravované)**: ZAKÁŽE optimalizaci JIT spravovaného kódu při načtení modulu a kompilaci JIT při připojení ladicího programu. Zakázáním optimalizace může být snazší ladit některé problémy, i když na úkor výkonu. Pokud používáte Pouze můj kód, potlačení optimalizace JIT může způsobit, že se neuživatelský kód zobrazí jako uživatelský kód ("můj kód"). Další informace najdete v tématu [optimalizace a ladění JIT](../debugger/jit-optimization-and-debugging.md).

**Povolit ladění JavaScriptu pro ASP.NET (Chrome, Microsoft Edge a IE)**: povolí ladicí program skriptu pro aplikace ASP.NET. Při prvním použití v Chrome se možná budete muset přihlásit do prohlížeče a povolit rozšíření Chrome, která jste nainstalovali. Vypnutím této možnosti obnovíte původní chování.

::: moniker range=">= vs-2019"
**Povolení použití ladicího programu jazyka JavaScript s více cíli pro ladění JavaScriptu v příslušných cílech (vyžaduje restart pro ladění)** Umožňuje připojení k prohlížeči a back-endu současně, což vám umožní ladit kód spuštěný v klientovi a na serveru přímo z editoru.
::: moniker-end

**Načíst exporty dll (pouze nativní)**: načte exportní tabulky knihovny DLL. Informace o symbolech z tabulek exportu knihovny DLL mohou být užitečné, pokud pracujete se zprávami systému Windows, postupy systému Windows (WindowProcs), objekty COM nebo zařazování nebo libovolnou knihovnou DLL pro kterou nemáte symboly. Čtení informací o exportu knihovny DLL zahrnuje režii. Proto tato možnost je ve výchozím nastavení vypnuta.

Chcete-li zjistit, jaké symboly jsou k dispozici v exportní tabulce knihovny DLL, použijte `dumpbin /exports` . Symboly jsou k dispozici pro všechny 32y systémové knihovny DLL. Načtením `dumpbin /exports` výstupu můžete zobrazit přesný název funkce, včetně nealfanumerických znaků. To je užitečné pro nastavení zarážky na funkci. Názvy funkcí z tabulky exportu knihovny DLL mohou být v ladicím programu zkráceny jinde. Volání jsou uvedena v pořadí volání s aktuální funkcí (nejhlouběji vnořených) nahoře. Další informace najdete v tématu [DUMPBIN/EXPORTS](/cpp/build/reference/dash-exports).

**Zobrazit diagram paralelních zásobníků zdola nahoru**: Určuje směr, ve kterém jsou balíčky zobrazeny v okně **paralelní zásobníky** .

**Ignorovat výjimky přístupu k paměti GPU, pokud se nezapsaná data nezměnila hodnota**: ignoruje konflikty časování, které byly zjištěny během ladění, pokud se data nezměnila. Další informace najdete v tématu [ladění kódu GPU](../debugger/debugging-gpu-code.md).

**Použít spravovaný režim kompatibility**: nahradí výchozí ladicí stroj starší verzí, aby bylo možné tyto scénáře povolit:

- Používáte jiný jazyk rozhraní .NET než C#, Visual Basic nebo F #, který poskytuje svůj vlastní vyhodnocovací filtr výrazů (zahrnuje C++/CLI).

- Chcete povolit úpravy a pokračování projektů C++ během ladění ve smíšeném režimu.

> [!NOTE]
> Výběr spravovaného režimu kompatibility zakáže některé funkce, které jsou implementované jenom ve výchozím ladicím modulu. Starší ladicí stroj byl nahrazen v aplikaci Visual Studio 2012.

::: moniker range="vs-2017"
**Použít starší verze vyhodnocovacích výrazů v jazyce c# a VB**: ladicí program použije místo vyhodnocovacích Roslyn výrazů založených na jazyce Visual Studio 2015 pro vyhodnocení výrazu Visual Basic vyhodnocení výrazu Visual Studio 2013 C# nebo.
::: moniker-end

**Upozornit při použití vlastních rozhraní pro vizualizaci ladicího programu na potenciálně nebezpečné procesy (pouze spravované)**: aplikace Visual Studio vás upozorní, když používáte vlastní Vizualizér ladicího programu, který spouští kód v laděném procesu, protože by mohlo běžet nezabezpečený kód.

**Povolit přidělování haldy při ladění systému Windows (jenom nativní)**: umožňuje vylepšit diagnostiku haldy v ladicím programu Windows. Povolení této možnosti ovlivní výkon ladění.

**Povolit ladicí nástroje uživatelského rozhraní pro XAML**: živý vizuální strom a vlastnost prozkoumat aktivní se zobrazí při spuštění ladění (**F5**) podporovaného typu projektu. Další informace naleznete v tématu [Kontrola vlastností XAML při ladění](../xaml-tools/inspect-xaml-properties-while-debugging.md).

- **Zobrazit náhled vybraných elementů v živém vizuálním stromu**: element XAML, jehož kontext je vybraný, je také vybrán v okně **živé vizuální stromové struktury** .

- **Zobrazit běhové nástroje v aplikaci**: zobrazí příkazy **živého vizuálního stromu** na panelu nástrojů v hlavním okně aplikace XAML, které je laděno. Tato možnost byla představena v aktualizaci Visual Studio 2015 Update 2.

- **Povolit kódování XAML Hot Loading**: umožňuje používat funkci XAML Hot reload s kódem XAML, když je vaše aplikace spuštěná. (Tato funkce se dřív nazývala "úpravy a pokračování v jazyce XAML")

::: moniker range=">= vs-2019" 
- **Povolit pouze můj kód XAML**: počínaje verzí visual Studio 2019 verze 16,4, **dynamický vizuální strom** ve výchozím nastavení zobrazuje pouze XAML, který je klasifikován jako uživatelský kód. Pokud tuto možnost zakážete, zobrazí se v nástroji celý generovaný kód XAML.

- Vypnout **režim výběru, když je vybrán element** Počínaje verzí Visual Studio 2019 verze 16,4 je tlačítko selektor prvků panelu nástrojů v aplikaci (**Povolit výběr**) vypnuto při výběru prvku. Pokud tuto možnost zakážete, výběr prvků zůstane zapnutý, dokud znovu nekliknete na tlačítko na panelu nástrojů aplikace.

- **Při uložení dokumentu použít Hot reload XAML** Počínaje verzí Visual Studio 2019 verze 16,6 aplikace při ukládání dokumentu použije Hot Load-in XAML.

::: moniker-end

**Povolit diagnostické nástroje při ladění**: během ladění se zobrazí okno **diagnostické nástroje** .

**Zobrazit uplynulý čas PerfTip při ladění**: v okně Code (kód) se zobrazuje uplynulý čas daného volání metody při ladění.

**Povolit funkci upravit a pokračovat**: povolí funkce upravit a pokračovat při ladění.

- **Povolit nativní úpravu a pokračování**: k ladění nativního kódu jazyka C++ můžete použít funkci upravit a pokračovat. Další informace naleznete v tématu [Upravit a pokračovat (C++)](../debugger/edit-and-continue-visual-cpp.md).

- **Použít změny při pokračování (pouze nativní)**: Visual Studio automaticky zkompiluje a použije všechny nedokončené změny v kódu, které jste provedli při pokračování procesu ze stavu přerušení. Pokud není vybrána, můžete použít změny pomocí položky **použít změny kódu** v nabídce **ladění** .

- **Upozornit na starý kód (pouze nativní)**: získání upozornění na zastaralý kód.

Při **ladění zobrazit tlačítko spustit do klikněte v editoru**: když je vybraná tato možnost, při ladění se zobrazí tlačítko [Spustit pro kliknutí](../debugger/debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) .

**Po zastavení ladění automaticky zavřít konzolu**: oznamuje aplikaci Visual Studio, aby uzavřela konzolu na konci ladicí relace.

::: moniker range=">= vs-2019"
**Povolit rychlé vyhodnocení výrazu (pouze spravované)**: umožňuje ladicímu programu pokusit se o rychlejší vyhodnocení simulací spuštění jednoduchých vlastností a metod.

**Načíst symboly ladění v externím procesu (pouze nativní)** Povolí tuto [optimalizaci paměti](https://devblogs.microsoft.com/cppblog/out-of-process-debugger-for-c-in-visual-studio-2019/) při ladění.

**Po přerušení v ladicím programu převést aplikaci Visual Studio na popředí** Přepne Visual Studio do popředí při pozastavení v ladicím programu.
::: moniker-end

## <a name="options-available-in-older-versions-of-visual-studio"></a>Možnosti dostupné ve starších verzích sady Visual Studio

Pokud používáte starší verzi sady Visual Studio, mohou být k dispozici některé další možnosti.

**Povolit Edge vývojářské nástroje pro aplikace JavaScriptu pro UWP (experimentální)**: povolí vývojářské nástroje pro aplikace JAVASCRIPTU pro UWP v Microsoft Edge.

**Povolit starší verzi prohlížeče Chrome JavaScript pro ASP.NET**: povolí pro aplikace ASP.NET starší verzi ladicího programu skriptů pro Chrome JavaScript. Při prvním použití v Chrome se možná budete muset přihlásit do prohlížeče a povolit rozšíření Chrome, která jste nainstalovali.

**Povolit pomocníka pro výjimky**: pro spravovaný kód povolí pomocníka s výjimkou. Od aplikace Visual Studio 2017, Pomocník pro výjimky nahradil pomocníka výjimky.

Vrátit **zásobník volání v neošetřených výjimkách**: způsobí, že okno **zásobník volání** vrátí zpět zásobník volání do bodu před tím, než došlo k neošetřené výjimce.

**Použít experimentální způsob, jak spustit ladění v jazyce Chrome JavaScript při spuštění sady Visual Studio jako správce**: říká aplikaci Visual Studio, aby zkusila nový způsob, jak spustit Chrome během ladění JavaScriptu.

**Upozornit, pokud při spuštění nejsou žádné symboly (pouze nativní)**: při ladění programu, pro který ladicí program neobsahuje žádné informace o symbolech, se zobrazí dialogové okno s upozorněním.

**Upozornit, pokud je při spuštění zakázáno ladění skriptu**: zobrazí dialogové okno s upozorněním, když se ladicí program spustí se zakázaným laděním skriptu.

**Použít nativní režim kompatibility**: Pokud je vybraná tato možnost, ladicí program místo nového nativního ladicího programu použije nativní ladicí program sady Visual Studio 2010.

- Tuto možnost použijte, když ladíte kód .NET C++, protože nový ladicí stroj nepodporuje vyhodnocování výrazů .NET C++. Povolení nativního režimu kompatibility však zakáže mnoho funkcí, které závisí na aktuální implementaci ladicího programu. Starší verze modulu například nemá mnoho vizualizací pro předdefinované typy jako `std::string` v projektech sady Visual Studio 2015.   V těchto případech použijte Visual Studio 2013 projekty pro optimální prostředí ladění.

## <a name="see-also"></a>Viz také

- [Ladění v sadě Visual Studio](../debugger/index.yml)
- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
