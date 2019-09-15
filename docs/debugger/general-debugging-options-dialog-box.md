---
title: Obecné, ladění, dialogové okno Možnosti | Microsoft Docs
ms.date: 11/09/2018
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
ms.openlocfilehash: 03634b5a2bd1417e75f843fd9026712313f1923d
ms.sourcegitcommit: 0e482cfc15f809b564c3de61646f29ecd7bfcba6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70987631"
---
# <a name="general-debugging-options"></a>Obecné možnosti ladění

Chcete-li nastavit možnosti ladicího programu sady Visual Studio,**Vyberte možnost** **nástroje** > a v části **ladění** zaškrtněte nebo zrušte zaškrtnutí políček u **obecných** možností. Můžete obnovit všechna výchozí nastavení pomocí **nástrojů** > pro**Import a export nastavení** > **Obnovit všechna nastavení**. Chcete-li obnovit podmnožinu nastavení, uložte nastavení pomocí **Průvodce importem a exportem nastavení** před provedením změn, které chcete otestovat, a pak import uložených nastavení proveďte později.

Můžete nastavit následující **Obecné** možnosti:

**Dotázat se před smazáním všech zarážek**: Vyžaduje potvrzení před dokončením příkazu **Odstranit všechny zarážky** .

**Přerušit všechny procesy při přerušení jednoho procesu**: Současně přeruší všechny procesy, ke kterým je připojen ladicí program, když dojde k přerušení.

**Přerušit při výjimkách mezi doménou AppDomain nebo spravované/nativní hranice**: V případě ladění spravovaného nebo kombinovaného režimu může modul common language runtime zachytit výjimky, které překračují hranice aplikační domény, nebo spravované/nativní hranice, pokud jsou splněné následující podmínky:

1. Když nativní kód volá spravovaný kód pomocí zprostředkovatele komunikace s objekty COM a spravovaný kód vyvolá výjimku. Viz [Úvod do zprostředkovatele komunikace s objekty COM](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).

2. Pokud spravovaný kód spuštěný v doméně aplikace 1 volá spravovaný kód v aplikační doméně 2 a kód v aplikační doméně 2 vyvolá výjimku. Viz téma [programování s aplikačními doménami](/dotnet/articles/framework/app-domains/index).

3. Když kód volá funkci pomocí reflexe a tato funkce vyvolá výjimku. Viz [reflexe](/dotnet/framework/reflection-and-codedom/reflection).

V podmínkách 2 a 3 je výjimka někdy zachycena spravovaným kódem `mscorlib` spíše než modulem CLR (Common Language Runtime). Tato možnost neovlivňuje přerušení u výjimek zachycených `mscorlib`v.

**Povolit ladění na úrovni adresy**: Povoluje rozšířené funkce pro ladění na úrovni adresy (okno **zpětný překlad** , okno **Registry** a zarážky adres).

- **Zobrazit zpětný překlad, pokud není k dispozici zdroj**:   Automaticky zobrazí okno **zpětný překlad** při ladění kódu, pro který není zdroj k dispozici.

**Povolit filtry zarážek**: Umožňuje nastavit filtry na zarážekch, takže budou mít vliv jenom na konkrétní procesy, vlákna nebo počítače.

**Použití nového pomocníka výjimky**: Povolí pomocníka výjimky, který nahradí pomocníka výjimky. (Pomocník s výjimkou je podporován od sady Visual Studio 2017)

> [!NOTE]
> Pro spravovaný kód tato možnost dříve volala **Pomocníka s výjimkou** .

**Povolit pouze můj kód**: Ladicí program zobrazí pouze postup v uživatelském kódu ("můj kód"), ignoruje systémový kód a jiný kód, který je optimalizován nebo který neobsahuje symboly ladění.

- **Zobrazit upozornění, pokud při spuštění žádný uživatelský kód (pouze spravované)** :   Když se ladění spustí s povoleným Pouze můj kód, tato možnost vás upozorní, pokud není k dispozici žádný uživatelský kód ("můj kód").

**Povolit krokování zdroje .NET Framework**: Umožňuje ladicímu programu krokovat se .NET Framework zdroji. Povolení této možnosti automaticky zakáže Pouze můj kód. .NET Framework symboly budou staženy do umístění mezipaměti. Změňte umístění mezipaměti pomocí dialogového okna **Možnosti** , kategorie **ladění** , stránka **symboly** .

**Krokovat přes vlastnosti a operátory (pouze spravované)** : Brání ladicímu programu v krokování do vlastností a operátorů ve spravovaném kódu.

**Povolit vyhodnocování vlastností a další volání implicitních funkcí**: Zapne automatické vyhodnocení vlastností a volání implicitních funkcí v oknech proměnné a v dialogovém okně **QuickWatch** .

- **Funkce pro převod řetězce volání u objektů v oknech proměnnýchC# (a pouze JavaScript)** : Provede volání převodu implicitního řetězce při vyhodnocování objektů v oknech proměnných. Výsledek se zobrazí jako řetězec namísto názvu typu. Platí pouze při ladění v C# kódu. Toto nastavení může být přepsáno atributem DebuggerDisplay (viz [použití atributu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)).

**Povolit podporu zdrojového serveru**: Instruuje ladicí program sady Visual Studio, aby získal zdrojové soubory ze zdrojových serverů, které`srcsrv.dll`implementují protokol SrcSrv (). Team Foundation Server a ladicí nástroje pro Windows jsou dva zdrojové servery, které implementují protokol. Další informace o instalaci SrcSrv najdete v dokumentaci k [srcsrv](/windows-hardware/drivers/debugger/srcsrv) . Kromě toho si přečtěte téma [určení symbolu (. pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

> [!IMPORTANT]
> Vzhledem k tomu, že čtení souborů *. pdb* může spustit libovolný kód v souborech, ujistěte se, že důvěřujete serveru.

- **Vytiskněte diagnostické zprávy zdrojového serveru do okna výstup**:   Pokud je povolená podpora zdrojového serveru, toto nastavení zapne diagnostické zobrazení.

- **Povolí zdrojový server pro částečně důvěryhodná sestavení (pouze spravovaná)** :   Pokud je povolená podpora zdrojového serveru, toto nastavení přepíše výchozí chování při načítání nenačtených zdrojů pro sestavení s částečným vztahem důvěryhodnosti.

- **Vždy spouštět nedůvěryhodné příkazy zdrojového serveru bez zobrazení výzvy**:   Pokud je povolená podpora zdrojového serveru, toto nastavení přepíše výchozí chování při zobrazování výzev při spuštění nedůvěryhodného příkazu.

**Povolit podporu zdrojového odkazu**: Instruuje ladicí program sady Visual Studio, aby stahoval zdrojové soubory pro soubory *. pdb* , které obsahují informace o zdrojovém odkazu. Další informace o zdrojovém odkazu najdete v tématu [specifikace zdrojového odkazu](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/source_link.md).

> [!IMPORTANT]
> Vzhledem k tomu, že odkaz na zdroj stáhne soubory pomocí protokolu HTTP nebo https, ujistěte se, že důvěřujete souboru *. pdb* .

- **Přejít zpět k ověření správce přihlašovacích údajů Git pro všechny požadavky na zdrojové odkazy**:   Pokud je povolená podpora zdrojového odkazu a požadavek na odkaz na zdroj se nezdařil, Visual Studio potom zavolá správce přihlašovacích údajů Git.

**Pro zarážky a aktuální příkaz zvýraznit celý řádek (C++ pouze)** : Když ladicí program zvýrazní zarážku nebo aktuální příkaz, zvýrazní celý řádek.

**Vyžadovat, aby se zdrojové soubory přesně shodovaly s původní verzí**: Instruuje ladicí program, aby ověřil, zda zdrojový soubor odpovídá verzi zdrojového kódu používané k sestavení spustitelného souboru, který ladíte. Pokud se verze neshoduje, budete vyzváni k vyhledání odpovídajícího zdroje. Pokud se nenalezne shodný zdroj, během ladění se nezobrazí zdrojový kód.

**Přesměrovat text z okna výstup do**příkazového podokna: Odesílá všechny zprávy ladicího programu, které by se obvykle zobrazovaly v okně **výstup** , do okna **okamžité** .

**Zobrazit nezpracovanou strukturu objektů v oknech proměnných**: Vypne všechna přizpůsobení zobrazení struktury objektů. Další informace o úpravách zobrazení najdete v tématu [Vytvoření vlastních zobrazení spravovaných objektů](../debugger/create-custom-views-of-dot-managed-objects.md).

**Potlačit optimalizaci JIT při načtení modulu (pouze spravované)** : Zakáže optimalizaci JIT spravovaného kódu při načtení modulu a při připojení ladicího programu je zkompilován kompilátor JIT. Zakázáním optimalizace může být snazší ladit některé problémy, i když na úkor výkonu. Pokud používáte Pouze můj kód, potlačení optimalizace JIT může způsobit, že se neuživatelský kód zobrazí jako uživatelský kód ("můj kód"). Další informace najdete v tématu [optimalizace a ladění JIT](../debugger/jit-optimization-and-debugging.md).

**Povolit ladění JavaScriptu pro ASP.NET (Chrome, Edge a IE)** : Povolí ladicí program skriptu pro aplikace ASP.NET. Při prvním použití v Chrome se možná budete muset přihlásit do prohlížeče a povolit rozšíření Chrome, která jste nainstalovali. Vypnutím této možnosti obnovíte původní chování.

**Povolit Edge vývojářské nástroje pro aplikace JavaScriptu pro UWP (experimentální)** : Povolí vývojové nástroje pro aplikace JavaScriptu pro UWP v Microsoft Edge.

**Povolit starší verzi ladicího programu pro Chrome JavaScript pro ASP.NET**: Povolí pro aplikace ASP.NET starší ladicí program skriptu JavaScriptu pro Chrome. Při prvním použití v Chrome se možná budete muset přihlásit do prohlížeče a povolit rozšíření Chrome, která jste nainstalovali.

**Používejte experimentální způsob, jak spustit ladění aplikace Chrome JavaScript při spuštění sady Visual Studio jako správce**: Oznamuje aplikaci Visual Studio, aby zkusila nový způsob, jak spustit Chrome během ladění JavaScriptu.

**Načíst exporty dll (pouze nativní)** : Načte exportní tabulky knihovny DLL. Informace o symbolech z tabulek exportu knihovny DLL mohou být užitečné, pokud pracujete se zprávami systému Windows, postupy systému Windows (WindowProcs), objekty COM nebo zařazování nebo libovolnou knihovnou DLL pro kterou nemáte symboly. Čtení informací o exportu knihovny DLL zahrnuje režii. Proto tato možnost je ve výchozím nastavení vypnuta.

Chcete-li zjistit, jaké symboly jsou k dispozici v exportní tabulce knihovny `dumpbin /exports`DLL, použijte. Symboly jsou k dispozici pro všechny 32y systémové knihovny DLL. V článku `dumpbin /exports` výstupu uvidíte přesný název funkce, včetně jiných než alfanumerických znaků. To je užitečné pro nastavení zarážky na funkci. Názvy funkcí z tabulky exportu knihovny DLL mohou být v ladicím programu zkráceny jinde. Volání jsou uvedena v pořadí volání s aktuální funkcí (nejhlouběji vnořených) nahoře. Další informace najdete v tématu [dumpbin/EXPORTS](/cpp/build/reference/dash-exports).

**Zobrazit diagram paralelních zásobníků zdola nahoru**: Určuje směr zobrazení zásobníků v okně **paralelní zásobníky** .

**Ignorovat výjimky přístupu k paměti GPU, pokud se nezapsaná data změnila hodnota**: Ignoruje konflikty časování, které byly zjištěny během ladění, pokud se data nezměnila. Další informace najdete v tématu [ladění kódu GPU](../debugger/debugging-gpu-code.md).

**Použít spravovaný režim kompatibility**: Nahradí výchozí ladicí stroj starší verzí, aby bylo možné tyto scénáře povolit:

- Používáte .NET Framework jazyk jiný než C#, Visual Basic nebo F# , který poskytuje svůj vlastní vyhodnocovací filtr výrazů (zahrnuje C++/CLI).

- Chcete povolit možnost upravit a pokračovat pro C++ projekty během ladění ve smíšeném režimu.

> [!NOTE]
> Výběr spravovaného režimu kompatibility zakáže některé funkce, které jsou implementované jenom ve výchozím ladicím modulu. Starší ladicí stroj byl nahrazen v aplikaci Visual Studio 2012.

**Použít starší verze C# a vyhodnocovací filtry výrazů VB**: Ladicí program použije Visual Studio 2013 C# nebo vyhodnocení výrazu Visual Basic namísto vyhodnocovacích vyhodnocení výrazu Roslyn sady Visual Studio 2015.

**Upozorňovat při použití vlastních vizualizací ladicího programu na potenciálně nebezpečné procesy (jenom spravované)** : Visual Studio vás upozorní, když používáte vlastní Vizualizér ladicího programu, který spouští kód v laděném procesu, protože by mohlo běžet nezabezpečený kód.

**Povolit přidělování haldy ladění systému Windows (jenom nativní)** : Povolí haldě ladění systému Windows vylepšení diagnostiky haldy. Povolení této možnosti ovlivní výkon ladění.

**Povolit ladicí nástroje uživatelského rozhraní pro XAML**: Živý vizuální strom a vlastnost prozkoumat v reálném čase se zobrazí při spuštění ladění (**F5**) podporovaného typu projektu. Další informace naleznete v tématu [Kontrola vlastností XAML při ladění](../debugger/inspect-xaml-properties-while-debugging.md).

- **Zobrazit náhled vybraných elementů v živém vizuálním stromu**:   V okně **živého vizuálního stromu** se také vybere element XAML, jehož kontext je vybraný.

- **Zobrazit běhové nástroje v aplikaci**: Zobrazuje příkazy **živého vizuálního stromu** na panelu nástrojů v hlavním okně aplikace XAML, které je laděno. Tato možnost byla představena v aktualizaci Visual Studio 2015 Update 2.

- **Povolit kódování XAML Hot reload**: Umožňuje použít funkci XAML Hot reload s kódem XAML, když je vaše aplikace spuštěná. (Tato funkce se dřív nazývala "úpravy a pokračování v jazyce XAML")

**Povolit diagnostické nástroje při ladění**: Při ladění se zobrazí okno **diagnostické nástroje** .

**Zobrazit uplynulý čas PerfTip při ladění**: V okně Code (kód) se zobrazí uplynulý čas daného volání metody při ladění.

**Povolit úpravy a pokračovat**: Povolí funkci upravit a pokračovat při ladění.

- **Povolit nativní úpravu a pokračování**: Při ladění nativního C++ kódu můžete použít funkci upravit a pokračovat. Další informace najdete v tématu [upravit a pokračovat (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).

- **Použít změny při pokračování (jenom nativní)** : Visual Studio automaticky zkompiluje a použije všechny nedokončené změny v kódu, které jste provedli při pokračování procesu ze stavu přerušení. Pokud není vybrána, můžete použít změny pomocí položky **použít změny kódu** v nabídce **ladění** .

- **Upozornit na starý kód (jenom nativní)** :   Získejte upozornění na zastaralý kód.

**Během ladění zobrazit v editoru tlačítko Spustit jako**: Pokud je vybrána tato možnost, zobrazí se při ladění tlačítko [Spustit pro kliknutí](../debugger/debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) .

**Po zastavení ladění automaticky zavřít konzolu**: Oznamuje aplikaci Visual Studio, aby uzavřela konzolu na konci relace ladění.

::: moniker range=">= vs-2019" 
**Povolit rychlé vyhodnocení výrazu (jenom spravované)** : Umožňuje ladicímu programu pokusit se o rychlejší vyhodnocení simulací spuštění jednoduchých vlastností a metod.
::: moniker-end

## <a name="options-available-in-older-versions-of-visual-studio"></a>Možnosti dostupné ve starších verzích sady Visual Studio

Pokud používáte starší verzi sady Visual Studio, mohou být k dispozici některé další možnosti.

**Povolit pomocníka pro výjimky**: Pro spravovaný kód povolí pomocníka výjimky. Od aplikace Visual Studio 2017, Pomocník pro výjimky nahradil pomocníka výjimky.

**Vrátit zásobník volání v neošetřených výjimkách**: Způsobí, že okno **zásobník volání** vrátí zpět zásobník volání do bodu před tím, než došlo k neošetřené výjimce.

**Upozornit, pokud při spuštění nejsou žádné symboly (pouze nativní)** : Při ladění programu, pro který ladicí program neobsahuje žádné informace o symbolech, se zobrazí dialogové okno s upozorněním.

**Zobrazit upozornění, pokud je při spuštění zakázáno ladění skriptu**: Zobrazí dialogové okno s upozorněním, když se ladicí program spustí se zakázaným laděním skriptu.

**Použít nativní režim kompatibility**: Pokud je vybrána tato možnost, ladicí program použije nativní ladicí program sady Visual Studio 2010 místo nového nativního ladicího programu.

- Tuto možnost použijte při ladění kódu .NET C++ , protože nový ladicí stroj nepodporuje vyhodnocování výrazů .NET. C++ Povolení nativního režimu kompatibility však zakáže mnoho funkcí, které závisí na aktuální implementaci ladicího programu. Starší verze modulu například nemá mnoho vizualizací pro předdefinované typy jako `std::string` v projektech sady Visual Studio 2015.   V těchto případech použijte Visual Studio 2013 projekty pro optimální prostředí ladění.

## <a name="see-also"></a>Viz také:

- [Ladění v sadě Visual Studio](../debugger/index.md)
- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
