---
title: Obecné, ladění, dialogové okno Možnosti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.options.General
- VS.ToolsOptionsPages.Debugger.General
- VS.ToolsOptionsPages.Debugger.ENC
- vs.debug.options.ENC
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- Options dialog box, debugging
ms.assetid: b33aee0b-43c3-4c26-8ed4-bc673f491503
caps.latest.revision: 50
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6c53af4a8e0f42708ab94d7206a9c0cc54819798
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573542"
---
# <a name="general-debugging-options-dialog-box"></a>Obecné, ladění, dialogové okno Možnosti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Na stránce**Nástroje/možnosti/ladění/obecné** lze nastavit následující možnosti:  
  
 **Dotázat se před smazáním všech zarážek**  
 Vyžaduje potvrzení před dokončením příkazu **Odstranit všechny zarážky** .  
  
 **Přerušit všechny procesy při přerušení jednoho procesu**  
 Současně přeruší všechny procesy, ke kterým je připojen ladicí program, když dojde k přerušení.  
  
 **Přerušit při výjimkách mezi doménou AppDomain nebo spravované/nativní hranice**  
 V případě ladění spravovaného nebo kombinovaného režimu může modul common language runtime zachytit výjimky, které překračují hranice aplikační domény, nebo spravované/nativní hranice, pokud jsou splněné následující podmínky:  
  
 1 \), když nativní kód volá spravovaný kód pomocí zprostředkovatele komunikace s objekty COM a spravovaný kód vyvolá výjimku. Viz [Úvod do zprostředkovatele komunikace s objekty COM](https://msdn.microsoft.com/library/8bd62e68-383d-407f-998b-29aa0ce0fd67).  
  
 2 \) Pokud spravovaný kód spuštěný v aplikační doméně 1 volá spravovaný kód v aplikační doméně 2 a kód v aplikační doméně 2 vyvolá výjimku. Viz téma [programování s aplikačními doménami](https://msdn.microsoft.com/bd36055b-56bd-43eb-b4d8-820c37172131).  
  
 3 \), když kód volá funkci pomocí reflexe a funkce vyvolá výjimku. Viz [reflexe](https://msdn.microsoft.com/library/d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775).  
  
 V 2) a 3) je výjimka někdy zachycena spravovaným kódem v `mscorlib` namísto modulu CLR (Common Language Runtime). Tato možnost neovlivňuje přerušení u výjimek zachycených `mscorlib`.  
  
 **Povolit ladění na úrovni adres**  
 Povoluje rozšířené funkce pro ladění na úrovni adresy (okno **zpětný překlad** , okno **Registry** a zarážky adres).  
  
 **Zobrazit zpětný překlad, pokud není k dispozici zdroj**  
 Automaticky zobrazí okno **zpětný překlad** při pokusu o ladění kódu, pro který není k dispozici zdroj.  
  
 **Povolit filtry zarážek**  
 Umožňuje nastavit filtry na zarážekch, aby ovlivnily pouze konkrétní procesy, vlákna nebo počítače.  
  
 **Povolit pomocníka pro výjimky**  
 Pouze pro spravovaný kód. Spravované výjimky otevřete dialogové okno Pomocník pro výjimky.  Viz [Pomocník pro výjimky](https://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb).  
  
 **Vrátit zásobník volání v neošetřených výjimkách**  
 Způsobí, že okno **zásobník volání** vrátí zpět zásobník volání do bodu před tím, než došlo k neošetřené výjimce.  
  
 **Povolit Pouze můj kód**  
 Ladicí program zobrazí pouze postup v uživatelském kódu ("můj kód"), ignoruje systémový kód a jiný kód, který je optimalizován nebo který neobsahuje symboly ladění.  
  
 **Zobrazit všechny členy pro objekty, které nejsou uživatelem, v oknech proměnných (jenom Visual Basic)**  
 Zapne zobrazení neveřejných členů v objektech, které jsou v neuživatelském kódu (nikoli "můj kód").  
  
 **Upozornit, pokud při spuštění žádný uživatelský kód**  
 Když se ladění spustí s povoleným Pouze můj kód, tato možnost vás upozorní, pokud není k dispozici žádný uživatelský kód ("můj kód").  
  
 **Povolit krokování zdroje .NET Framework**  
 Umožňuje ladicímu programu krokovat se .NET Framework zdroji. Když se tato možnost povolí automaticky, zakáže se Pouze můj kód .NET Framework symboly se stáhnou do umístění mezipaměti. Umístění mezipaměti můžete změnit v dialogovém okně **Možnosti** , kategorie **ladění** , stránka **symboly** .  
  
 **Krokovat přes vlastnosti a operátory (pouze spravované)**  
 Brání ladicímu programu v krokování do vlastností a operátorů ve spravovaném kódu.  
  
 **Povolit vyhodnocování vlastností a další volání implicitních funkcí**  
 Zapne automatické vyhodnocení vlastností a volání implicitních funkcí v oknech proměnné a v dialogovém okně **QuickWatch** .  
  
 **Funkce pro převod řetězce volání u objektů v oknech proměnnýchC# (a jenom JavaScript)**  
 Provede volání převodu implicitního řetězce při vyhodnocování objektů v oknech proměnných. Proto je výsledek zobrazen jako řetězec namísto názvu typu. Platí pouze při ladění v C# kódu. Toto nastavení může být přepsáno atributem DebuggerDisplay (viz [použití atributu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)).  
  
 **Povolit podporu zdrojového serveru**  
 Instruuje ladicí program sady Visual Studio, aby získal zdrojové soubory ze zdrojových serverů, které implementují protokol SrcSrv (`srcsrv.dll`). Team Foundation Server a ladicí nástroje pro Windows jsou dva zdrojové servery, které implementují protokol. Další informace o instalaci SrcSrv najdete v dokumentaci k ladicím nástrojům pro systém Windows. Kromě toho si přečtěte téma [určení symbolu (. pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
> [!IMPORTANT]
> Vzhledem k tomu, že čtení souborů. pdb může spustit libovolný kód v souborech, ujistěte se, že důvěřujete serveru.  
  
 **Vytiskne diagnostické zprávy zdrojového serveru do okna výstup.**  
 Pokud je povolená podpora zdrojového serveru, toto nastavení zapne diagnostické zobrazení.  
  
 **Povolí zdrojový server pro sestavení částečné důvěryhodnosti (pouze spravované).**  
 Pokud je povolená podpora zdrojového serveru, toto nastavení přepíše výchozí chování při načítání nenačtených zdrojů pro sestavení s částečným vztahem důvěryhodnosti.  
  
 **Pro zarážky a aktuální příkaz zvýraznit celý řádek**  
 Když ladicí program zvýrazní zarážku nebo aktuální příkaz, zvýrazní celý řádek.  
  
 **Vyžadovat, aby se zdrojové soubory přesně shodovaly s původní verzí**  
 Instruuje ladicí program, aby ověřil, zda zdrojový soubor odpovídá verzi zdrojového kódu používané k sestavení spustitelného souboru, který ladíte. Pokud se verze neshoduje, zobrazí se výzva k vyhledání odpovídajícího zdroje. Pokud se nenalezne shodný zdroj, během ladění se nezobrazí zdrojový kód.  
  
 **Přesměrovat text z okna výstup do příkazového podokna**  
 Odesílá všechny zprávy ladicího programu, které by se obvykle zobrazovaly v okně **výstup** , do okna **okamžité** .  
  
 **Zobrazit nezpracovanou strukturu objektů v oknech proměnných**  
 Vypne všechna přizpůsobení zobrazení struktury objektů. Další informace o úpravách zobrazení najdete v tématu [Vytvoření vlastních zobrazení spravovaných objektů](../debugger/create-custom-views-of-managed-objects.md).  
  
 **Potlačit optimalizaci JIT při načtení modulu (pouze spravované)**  
 Zakáže optimalizaci JIT spravovaného kódu při načtení modulu a při připojení ladicího programu je zkompilován kompilátor JIT. Zakázáním optimalizace může být snazší ladit některé problémy, i když na úkor výkonu. Pokud používáte Pouze můj kód, potlačení optimalizace JIT může způsobit, že se neuživatelský kód zobrazí jako uživatelský kód ("můj kód").  
  
 **Upozornit, pokud při spuštění nejsou žádné symboly (jenom nativní)**  
 Při pokusu o ladění programu, pro který ladicí program neobsahuje žádné informace o symbolech, se zobrazí dialogové okno s upozorněním.  
  
 **Zobrazit upozornění, pokud je při spuštění zakázáno ladění skriptu**  
 Zobrazí dialogové okno s upozorněním, když se ladicí program spustí se zakázaným laděním skriptu.  
  
 **Načtení exportů DLL**  
 Načte exportní tabulky knihovny DLL. Informace o symbolech z tabulek exportu knihovny DLL mohou být užitečné, pokud pracujete se zprávami systému Windows, postupy systému Windows (WindowProcs), objekty COM nebo zařazování nebo libovolnou knihovnou DLL pro kterou nemáte symboly. Čtení informací o exportu knihovny DLL zahrnuje režii. Proto tato možnost je ve výchozím nastavení vypnuta.  
  
 Chcete-li zjistit, jaké symboly jsou k dispozici v exportní tabulce knihovny DLL, použijte `dumpbin /exports`. Symboly jsou k dispozici pro všechny 32y systémové knihovny DLL. Načtením výstupu `dumpbin /exports` můžete zobrazit přesný název funkce, včetně jiných než alfanumerických znaků. To je užitečné pro nastavení zarážky na funkci. Názvy funkcí z tabulky exportu knihovny DLL mohou být v ladicím programu zkráceny jinde. Volání jsou uvedena v pořadí volání s aktuální funkcí (nejhlouběji vnořených) nahoře. Další informace najdete v tématu [Výpis paměti bin/EXPORTS](https://msdn.microsoft.com/library/2971ab7e-4ee6-478b-9c85-cda42a4ce1bf).  
  
 **Zobrazit diagram paralelních zásobníků zdola nahoru**  
 Určuje směr zobrazení zásobníků v okně **paralelní zásobníky** .  
  
 **Ignorovat výjimky přístupu k paměti GPU, pokud nezapsaná data nezměnila hodnotu**  
 Ignoruje konflikty časování, které byly zjištěny během ladění, pokud se data nezměnila. Další informace najdete v tématu [ladění kódu GPU](../debugger/debugging-gpu-code.md).  
  
 **Použít spravovaný režim kompatibility**  
 Nahradí výchozí ladicí stroj starší verzí, aby bylo možné tyto scénáře povolit:  
  
- Používáte .NET Framework jazyk jiný než C#, vb nebo F# , který poskytuje svůj vlastní vyhodnocovací filtr výrazů (zahrnuje C++/CLI).  
  
- V případě ladění ve smíšeném režimu chcete povolit C++ možnost upravit a pokračovat pro projekty.  
  
  Všimněte si, že volba spravovaného režimu kompatibility zakáže některé funkce, které jsou implementované jenom ve výchozím ladicím modulu.  
  
  **Použít nativní režim kompatibility**  
  Pokud je vybrána tato možnost, ladicí program použije nativní ladicí program sady Visual Studio 2010 místo nového nativního ladicího programu.  
  
  Tuto možnost byste měli použít při ladění kódu .NET C++ , protože nový ladicí stroj nepodporuje vyhodnocování výrazů .NET. C++ Povolení nativního režimu kompatibility však zakáže mnoho funkcí, které závisí na aktuální implementaci ladicího programu. Starší verze modulu například nemá mnoho vizualizací pro předdefinované typy, jako je `std::string` v projektech sady Visual Studio 2015.  V těchto případech použijte Visual Studio 2013 projekty pro optimální prostředí ladění.  
  
  **Použít starší verze C# a vyhodnocovací filtry výrazů VB**  
  Ladicí program použije filtry výrazů Visual Studio 2013 C#/VB místo vyhodnocovacích vyhodnocení výrazu založeného na Roslyn sady Visual Studio 2015.  
  
  **Upozornit, když se používají vlastní vizualizace ladicího programu pro potenciálně nebezpečné procesy (jenom spravované)**  
  Visual Studio vás upozorní, když používáte vlastní Vizualizér ladicího programu, který spouští kód v procesu laděného procesu, protože by mohl běžet nezabezpečený kód.  
  
  **Povolit přidělování haldy ladění systému Windows (jenom nativní)**  
  Povolí haldě ladění systému Windows vylepšení diagnostiky haldy. Povolení této možnosti ovlivní výkon ladění.  
  
  **Povolit ladicí nástroje uživatelského rozhraní pro XAML**  
  Živý vizuální strom a vlastnost prozkoumat v reálném čase se zobrazí při spuštění ladění (F5) podporovaného typu projektu. Další informace naleznete v tématu [Kontrola vlastností XAML při ladění](../debugger/inspect-xaml-properties-while-debugging.md).  
  
  **Zobrazit náhled vybraných elementů v živém vizuálním stromu**  
  V okně **živého vizuálního stromu** se také vybere element XAML, jehož kontext je vybraný.  
  
  **Zobrazit běhové nástroje v aplikaci**  
  Zobrazuje příkazy **živého vizuálního stromu** na panelu nástrojů v hlavním okně aplikace XAML, které je laděno. Tato možnost byla představena v aktualizaci Visual Studio 2015 Update 2.  
  
  **Povolit Diagnostické nástroje při ladění**  
  Při ladění se zobrazí okno **diagnostické nástroje** . Další informace najdete v tématu [profilování integrované v ladicím programu](/visualstudio/profiling/running-profiling-tools-with-or-without-the-debugger).  
  
  **Zobrazit uplynulý čas PerfTip při ladění**  
  V okně Code (kód) se zobrazí uplynulý čas daného volání metody při ladění.  
  
  **Povolit úpravy a pokračovat**  
  Během ladění můžete použít funkci upravit a pokračovat.  
  
  **Povolit nativní úpravu a pokračování**  
  Při ladění nativního C++ kódu můžete použít funkci upravit a pokračovat. Další informace najdete v tématu [Úpravy a pokračování (vizuál C++)](../debugger/edit-and-continue-visual-cpp.md).  
  
  **Použít změny při pokračování (jenom nativní)**  
  Visual Studio automaticky zkompiluje a použije všechny nedokončené změny v kódu, které jste provedli při pokračování procesu ze stavu přerušení. Pokud není vybrána, můžete použít změny pomocí položky použít změny kódu v nabídce ladění.  
  
  **Upozornit na starý kód (jenom nativní)**  
  Získejte upozornění na zastaralý kód.  
  
  **Povolení předkompilování (pouze nativní)**  
  Předkompilace je povolena.  
  
## <a name="see-also"></a>Viz také  
 [Ladění v sadě Visual Studio](../debugger/debugging-in-visual-studio.md)
