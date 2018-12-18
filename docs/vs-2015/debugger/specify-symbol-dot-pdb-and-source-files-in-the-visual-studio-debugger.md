---
title: Zadání symbolu (.pdb) a zdrojové soubory v ladicím programu | Dokumentace Microsoftu
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
- VS.ToolsOptionsPages.Debugger.Native
- VS.ToolsOptionsPages.Debugger.Symbols
- vs.debug.options.Native
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- source code
- .dbg files
- source code, managing
- symbols, managing
- .pdb files
- dbg files
- pdb files
- debugger
ms.assetid: 1105e169-5272-4e7c-b3e7-cda1b7798a6b
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f716bb50d04b7bb3e961325136c118d6dcc4a9db
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062752"
---
# <a name="specify-symbol-pdb-and-source-files-in-the-visual-studio-debugger"></a>Zadání symbolu (.pdb) a zdrojových souborů v ladicím programu sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Souboru databáze (PDB) program, nazývaný také soubor symbolů, mapuje identifikátory, které vytvoříte ve zdrojových souborech pro třídy, metody a jiný kód, na identifikátory, které jsou použity v kompilovaných spustitelných souborech projektu. Soubor PDB také mapuje příkazy ve zdrojovém kódu k provozním pokynům ve spustitelných souborech. Ladicí program používá tyto informace k určení dvou důležitých informací: zdrojový soubor a číslo řádku, které jsou zobrazeny v prostředí IDE sady Visual Studio a v umístění ve spustitelném souboru, kde je třeba se zastavit při nastavení zarážky. Soubor symbolů obsahuje také původní umístění zdrojových souborů, případně umístění zdrojového serveru, ze kterého lze načíst zdrojové soubory.

 Při ladění projektu v integrovaném vývojovém prostředí sady Visual Studio ví ladicí program výchozí umístění pro soubory .pdb a zdrojové pro váš kód. Pokud chcete ladit kód mimo váš zdrojový kód projektu, jako je volání systému Windows nebo kódu třetí strany, musíte určit umístění souboru PDB (a volitelně zdrojových souborů z externího kódu) a tyto soubory musí přesně odpovídat spustitelným souborům sestavení.

 Před Visual Studio 2012 při ladění spravovaného kódu na vzdáleném zařízení nutné vložit soubory symbolů ve vzdáleném počítači. To již neplatí. Všechny soubory symbolů musí být umístěny v místním počítači nebo v umístění zadaném **nástroje / Možnosti / ladění / symboly** stránky.

##  <a name="BKMK_Find_symbol___pdb__files"></a> Pokud ladicí program vyhledává soubory PDB

1.  Umístění, které je zadáno uvnitř knihovny DLL nebo spustitelného souboru.

     (Ve výchozím nastavení, pokud máte vytvořenou knihovnu DLL nebo spustitelný soubor ve vašem počítači, linker umístí úplnou cestu a název souboru přidruženého souboru PDB do knihovny DLL nebo spustitelného souboru. Ladicí program nejprve zkontroluje, zda existuje soubor se symboly v umístění, které je zadáno v knihovně DLL nebo spustitelném souboru. To je užitečné, protože budete mít vždy symboly, které jsou k dispozici pro kód, který jste zkompilovali v počítači.)

2.  Soubory PDB, které mohou být uloženy ve stejné složce jako knihovna DLL nebo spustitelný soubor.

3.  Všechny složky mezipaměti místního symbolu.

4.  Všechny zadané servery sítě, Internetu nebo místních symbolů a umístění, například server Microsoft symbol, pokud je povolen.

###  <a name="BKMK_Why_do_symbol_files_need_to_exactly_match_the_executable_files_"></a> Proč soubory symbolů musí přesně odpovídat spustitelným souborům?
 Ladicí program načte pouze soubor PDB pro spustitelný soubor, který přesně odpovídá souboru .pdb vytvořeném, když byl sestaven spustitelný soubor (to znamená, že PDB musí být originál nebo kopie původního souboru .pdb). Vzhledem k tomu, že kompilátor je optimalizován pro rychlost kompilace, kromě svého hlavního úkolu vytvoření správného a efektivního kódu, se může změnit rozložení skutečného spustitelného souboru i v případě, že nedošlo ke změně samotného kódu. Další informace najdete v části [proč sada Visual Studio vyžaduje soubory symbolů ladicího programu shodovaly binárním souborům, se kterými byly vytvořeny?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/).

###  <a name="BKMK_Specify_symbol_locations_and_loading_behavior"></a> Zadejte umístění symbolu a chování načítání
 Při ladění projektu v integrovaném vývojovém prostředí VS ladicí program automaticky načte soubory symbolů, které jsou umístěny v adresáři projektu. Můžete zadat alternativní cesty hledání a servery symbolů pro společnost Microsoft, Windows nebo komponenty třetích stran v **nástroje / Možnosti / ladění / symboly**. Můžete také určit konkrétní moduly, které má ladicí program automaticky načíst symboly pro. A můžete potom změnit tato nastavení ručně při aktivním ladění.

1. V sadě Visual Studio, otevřete **nástroje / Možnosti / ladění / symboly** stránky.

    ![Nástroje &#45; možnosti &#45; ladění &#45; symboly stránky](../debugger/media/dbg-tools-options-symbols.png "DBG_Tools_Options_Symbols")

2. Vyberte složku ![nástroje&#47; možnosti&#47; ladění&#47;ikonu složky symboly](../debugger/media/dbg-tools-options-foldersicon.png "DBG_Tools_Options_FoldersIcon") ikonu. Upravitelný text se zobrazí v **Symbol umístění souborů (.pdb)** pole.

3. Zadejte adresu URL nebo cestu k adresáři serveru symbolů nebo umístění symbolu. Doplňování výrazů vám pomůže najít správný formát.

4. Chcete-li zlepšit výkon při načítání zadejte cestu k místnímu adresáři, kam lze zkopírovat symboly podle serverů symbolů v **mezipaměti symbolů v tomto adresáři** místní adresář, do něhož lze symboly zkopírovat.

   > [!NOTE]
   >  Neumísťujte mezipaměť symbolu do chráněné složky (například C:\Windows nebo některé z jejích podsložek). Místo toho použijte složku pro čtení i zápis.

   **Zadejte chování načítání symbolu**

   Můžete určit soubory, které mají být načteny automaticky z **Symbol umístění souborů (.pdb)** umístění pole při zahájení ladění. Soubory se symboly v adresáři projektu jsou vždy načteny.

5. Zvolte **všechny moduly, kromě vyloučených** k načtení všech symbolů pro všechny moduly, kromě těch, které určíte při výběru možnosti **zadat vyloučené moduly** odkaz.

6. Zvolte **pouze určité moduly** možnost a klikněte na tlačítko **určit moduly** pro uvedení seznamu modulů, které soubory, které chcete načíst automaticky symbolů. Soubory symbolů pro ostatní moduly jsou ignorovány.

   **Zadejte další možnosti symbolu.**

   Můžete také nastavit následující možnosti na **nástroje / Možnosti / ladění / symboly** stránky:

   **Varovat, pokud žádné symboly při spuštění (pouze nativní)**

   Vyberete-li tuto možnost, zobrazí se dialogové okno upozornění při pokusu o ladění programu, pro které ladicí program neobsahuje žádné symbolické informace.

   **Načtení exportů DLL**

   Při výběru načte exportní tabulky knihovny DLL. Symbolické informace z tabulky exportu knihovny DLL mohou být užitečné, pokud pracujete se zprávami systému Windows, postupy systému Windows (WindowProcs), objekty COM nebo zařazování nebo libovolnou knihovnou DLL pro kterou nemáte symboly. Informace o exportu knihovny DLL pro čtení zahrnují nadměrné zatížení. Proto tato možnost je ve výchozím nastavení vypnuta.

   Chcete-li zjistit, jaké symboly jsou k dispozici v exportní tabulce knihovny DLL, použijte `dumpbin /exports`. Symboly jsou k dispozici pro všechny 32bitové systémové knihovny DLL. V článku `dumpbin /exports` výstupu uvidíte přesný název funkce, včetně jiných než alfanumerických znaků. To je užitečné pro nastavení zarážky na funkci. Názvy funkcí z tabulky exportu knihovny DLL se mohou jinde v ladícím programu zobrazit ořezané. Volání jsou uvedena v pořadí volání s aktuální funkcí (nejhlouběji vnořených) nahoře. Další informace najdete v tématu [dumpbin/EXPORTS](http://msdn.microsoft.com/library/2971ab7e-4ee6-478b-9c85-cda42a4ce1bf).

###  <a name="BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine"></a> Použít servery symbolů ke hledání souborů symbolů nenainstalovaných v místním počítači
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] může stáhnout soubory symbolu ladění ze serverů symbolů, které implementují protokol symsrv. [Visual Studio Team Foundation Server](http://msdn.microsoft.com/library/bd6977ca-e30a-491a-a153-671d81222ce6) a [ladění nástroje pro Windows](http://msdn.microsoft.com/library/windows/hardware/ff551063\(v=VS.85\).aspx) jsou dva nástroje, které implementují servery symbolů. Zadejte symbolové servery k použitím v VS **možnosti** dialogové okno.

 Mezi servery se symboly, které můžete použít, patří:

 **Veřejné symbolové servery společnosti Microsoft**

 Pokud chcete ladit selhání, ke kterému dojde během volání systémové knihovny DLL nebo knihovny třetí strany, budete často potřebovat systémové soubory .pdb, které obsahují symboly pro soubory DLL, EXE a ovladače zařízení v systému Windows. Tyto symboly můžete získat na veřejných serverech symbolů společnosti Microsoft. Veřejné symbolové servery společnosti Microsoft poskytuje symboly pro operační systémy Windows společně s MDAC, IIS, ISA a [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

 Pokud chcete použít servery symbolů společnosti Microsoft, zvolte **možnosti a nastavení** na **ladění** nabídky a klikněte na tlačítko **symboly**. Vyberte **Microsoft Symbol Servers**.

 **Servery se symboly v interní síti nebo na místním počítači**

 Váš tým nebo společnost může vytvořit servery symbolů pro vaše vlastní produkty jako mezipaměť pro symboly z externích zdrojů. Symbolový server můžete mít na vlastním počítači. Můžete zadat umístění serverů symbolů jako adresu URL nebo cestu na **ladění**/**symboly** stránku **dialogové okno Možnosti**.

 **Servery symbolů jiných výrobců**

 Jiní zprostředkovatelé aplikací a knihoven systému Windows mohou poskytovat přístup k symbolovému serveru na internetu. Také zadejte adresu URL těchto serverů symbolů **ladění**/**symboly** stránky,

> [!NOTE]
>  Pokud používáte symbolový server jiný než veřejné symbolové servery společnosti Microsoft, přesvědčte se, zda symbolový server a jeho cesty jsou důvěryhodné. Vzhledem k tomu, že soubory se symboly mohou obsahovat libovolný spustitelný kód, můžete se vystavit bezpečnostním hrozbám.

###  <a name="BKMK_Find_and_load_symbols_while_debugging"></a> Najít a načíst symboly při ladění
 V každém okamžiku, kdy je ladicí program v režimu pozastavení, můžete načíst symboly pro modul, který byl dříve vyloučen možnostmi ladicího programu nebo které kompilátor nemůže najít. Symboly můžete načíst z místních nabídek oken Zásobník volání, Moduly, Lokální, Automatické a Všechna kukátka. Pokud ladicí program se přeruší v kódu, který nemá symbol nebo zdrojové soubory k dispozici, zobrazí se okno dokumentu. Zde naleznete informace o chybějících souborech a provedení akcí k jejich vyhledání a načtení.

 **Hledání symbolů se stránkami dokumentu nebyly načteny žádné symboly**

 Existuje několik způsobů jak může ladicí program proniknout do kódu, který nemá k dispozici symboly ladicího programu:

1. Krokování kódu.

2. Rozdělení do kódu od zarážky nebo výjimky.

3. Přepnutí do jiného podprocesu.

4. Změna zásobníku dvojitým kliknutím na snímek v okně Zásobník volání.

   Při jedné z těchto událostí ladicí program zobrazí **nebyly načteny žádné symboly** stránka může pomoci najít a načíst potřebné symboly.

   ![Žádné stránky načíst symboly](../debugger/media/dbg-nosymbolsloaded.png "DBG_NoSymbolsLoaded")

- Chcete-li změnit cesty hledání, zvolte nevybranou cestu nebo vyberte **nový** a zadejte novou cestu. Zvolte **načíst** hledání cest a načtení souboru symbolů, pokud je nalezen.

- Zvolte **Procházet a vyhledat**_název spustitelného souboru_**...**  pro přepsání jakékoli volby symbolu a opakujte hledání cesty. Pokud je nalezen soubor symbolů, bude načten, nebo se zobrazí Průzkumník souborů, kde můžete soubor symbolu vybrat ručně.

- Zvolte **změnit nastavení symbolů...**  zobrazíte **ladění** / **symboly** stránky v dialogovém okně Možnosti VS.

- Zvolte **zobrazit zpětný překlad** chcete zobrazit rozebrání v novém okně jednou.

- Pokud chcete vždy zobrazit rozebrání, když nejsou nalezeny zdrojové soubory nebo soubory symbolu, zvolte **dialogové okno Možnosti** propojit a vyberte možnost **povolit ladění na úrovni adresy** a **zobrazit zpětný překlad, pokud není k dispozici zdroj**.

   ![Možnosti &#47; ladění &#47; zpětný překlad Obecné možnosti](../debugger/media/dbg-options-general-disassembly-checkbox.png "DBG_Options_General_disassembly_checkbox")

  **Změňte možnosti symbolu z místní nabídky**

  Při práci v režimu pozastavení můžete najít a načíst symboly pro položky, které jsou zobrazeny v oknech Zásobník volání, Moduly, Lokální, Automatické a všech oknech Kukátka. V okně vyberte položku, otevřete místní nabídku a zvolte jednu z následujících možností:

|Možnost|Popis|
|------------|-----------------|
|**Načtení symbolů**|Pokusí se načíst symboly z umístění zadaného na **ladění** / **symboly** stránku **možnosti** dialogové okno. Pokud nelze najít soubor symbolů, spustí se Průzkumník souborů, takže můžete určit nové umístění pro hledání.|
|**Informace o načítání symbolů**|Představuje informace, které vykazují umístění načteného souboru se symbolem nebo prohledávána umístění, pokud ladicí program nemůže najít soubor.|
|**Nastavení symbolů...**|Otevře **ladění** / **symboly** stránku **možnosti** dialogové okno.|
|**Vždy načítat automaticky**|Přidá soubor symbolů do seznamu souborů, které jsou automaticky načteny pomocí ladicího programu.|

###  <a name="BKMK_Set_compiler_options_for_symbol_files"></a> Nastavit možnosti kompilátoru pro soubory symbolů
 Při sestavení projektu z rozhraní IDE VS a použití standardní **ladění** konfigurace sestavení, C++ a spravované kompilátory odpovídající soubory symbolů pro váš kód vytvořit. Můžete také nastavit možnosti kompilátoru na příkazovém řádku k vytvoření souborů symbolů.

 **Možnosti jazyka C++**

 Soubor databáze programu (PDB) uchovává informace o ladění a stavu projektu, které umožňují přírůstkové propojení konfigurace ladění programu. Soubor PDB je vytvořen při sestavení s [příznakem/zi nebo /Zi](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) (pro C/C++).

 V [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], [/Fd](http://msdn.microsoft.com/library/3977a9ed-f0ac-45df-bf06-01cedd2ba85a) možnost pojmenuje soubor .pdb vytvořený kompilátorem. Při vytváření projektu v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pomocí průvodců **/Fd** je možnost nastavená na vytvoření souboru .pdb s názvem *projektu*.pdb.

 Pokud vytváříte aplikaci C/C++ pomocí souboru pravidel a zadáte **/zi** nebo **/zi** bez **/Fd**, skončíte se dvěma soubory PDB:

- VC*x*.pdb, kde *x* představuje verzi jazyka Visual C++, například VC11.pdb. Tento soubor obsahuje všechny informace o ladění pro jednotlivé soubory OBJ a je umístěn ve stejném adresáři jako soubor pravidel projektu.

- Project.pdb tento soubor uchovává všechny informace o ladění pro soubor the.exe. Pro jazyk C/C++ je umístěn v podadresáři \debug.

  Pokaždé, když se vytvoří soubor s příponou OBJ, kompilátor C/C++ sloučí informace o ladění do VC*x*.pdb. Vložené informace obsahují informace o typu, ale neobsahují informace o symbolu, jako jsou definice funkce. Ano, i když každý zdrojový soubor obsahuje společné soubory hlaviček, jako \<windows.h >, funkce typedefs z těchto záhlaví jsou uloženy pouze jednou, namísto do každého souboru OBJ.

  Linker vytvoří project.pdb, který obsahuje informace o ladění souboru EXE v projektu. Soubor project.pdb obsahuje úplné informace o ladění, včetně funkčních prototypů, nejen informace o typu uvedené v VC*x*.pdb. Oba soubory PDB umožňují přírůstkové aktualizace. Linker také vloží cestu k souboru .pdb ve vytvořeném souboru .exe nebo .dll.

  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Ladicí program používá cestu k souboru .pdb v souboru EXE nebo DLL k vyhledání souboru project.pdb. Pokud ladicí program nemůže najít soubor PDB na tomto místě nebo je-li cesta neplatná (například, pokud byl projekt přesunut do jiného počítače), ladicí program hledá cestu, která obsahuje soubor EXE, cesty symbolů zadané v **možnosti** Dialogové okno (**ladění** složce **symboly** uzlu). Ladicí program nenačte soubor .pdb, který neodpovídá laděnému spustitelnému souboru. Pokud ladicí program nemůže najít soubor .pdb **najít symboly** se zobrazí dialogové okno, které umožňuje hledat symboly nebo přidat další umístění pro cestu hledání.

  **Možnosti rozhraní .NET framework**

  Soubor databáze programu (PDB) uchovává informace o ladění a stavu projektu, které umožňují přírůstkové propojení konfigurace ladění programu. Soubor PDB je vytvořen při sestavení s **/debug**. Můžete vytvářet aplikace pomocí **/Debug: Full** nebo **/debug:pdbonly**. Sestavování s **/Debug: Full** generuje laditelný kód. Sestavování s **/debug:pdbonly** generuje soubory PDB ale negeneruje `DebuggableAttribute` , který instruuje kompilátor JIT, že je k dispozici informace o ladění. Použití **/debug:pdbonly** Pokud chcete generovat soubory .pdb pro sestavení pro vydání, které nemá být laditelná. Další informace najdete v tématu [/Debug (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969) nebo [/Debug (Visual Basic)](http://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).

  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Ladicí program používá cestu k souboru .pdb v souboru EXE nebo DLL k vyhledání souboru project.pdb. Pokud ladicí program nemůže najít soubor PDB na tomto místě nebo je-li cesta neplatná, ladicí program hledá cestu, která obsahuje soubor EXE, a poté cesty symbolů zadané v **možnosti** dialogové okno. Tato cesta je obvykle **ladění** složky **symboly** uzlu. Ladicí program nenačte soubor .pdb, který neodpovídá laděnému spustitelnému souboru. Pokud ladicí program nemůže najít soubor .pdb **najít symboly** se zobrazí dialogové okno, které umožňuje hledat symboly nebo přidat další umístění pro cestu hledání.

  **Webové aplikace**

  Konfigurační soubor aplikace (Web.config) musí být nastaven na režim ladění. Režim ladění způsobí, že technologie ASP.NET generuje dynamicky generované soubory a umožňuje ladicímu program připojit k aplikaci technologie ASP.NET. VS tuto hodnotu nastaví automaticky při spuštění ladění, pokud jste vytvořili projekt ze šablony webových projektů.

##  <a name="BKMK_Find_source_files"></a> Najít zdrojové soubory

###  <a name="BKMK_Where_the_debugger_searches_for_source_files"></a> Pokud ladicí program vyhledává zdrojové soubory
 Ladicí program vyhledá zdrojové soubory v následujících umístěních:

1.  Soubory, které jsou otevřeny v integrovaném vývojovém prostředí Visual Studio instance, které spustilo ladicí program.

2.  Soubory v řešení, která je otevřená v instanci aplikace Visual Studio.

3.  Adresáře, které jsou určené v **společné vlastnosti** / **zdrojové soubory ladění** stránku vlastností řešení. (V **Průzkumníka řešení**, vyberte uzel řešení, klikněte pravým tlačítkem a vyberte **vlastnosti**. )

4.  Zdrojové informace o souboru .pdb modulu. To může být umístění zdrojového souboru, když modul byl vytvořen, nebo to může být příkaz na zdrojový server.

###  <a name="BKMK_Find_and_load_source_files_with_the_No_Source___No_Symbols_Loaded_pages"></a> Najít a načíst zdrojové soubory s žádný zdrojový / nebyly načteny žádné symboly stránky
 Pokud ladicí program přeruší provádění v místě, kde není k dispozici zdrojový soubor, zobrazí **nenačten žádný zdroj** nebo **nebyly načteny žádné symboly** stránek, které vám mohou pomoci najít zdrojový soubor. **Nebyly načteny žádné symboly** se zobrazí, když ladicí program nemůže najít soubor symbolů (PDB) pro spustitelný soubor a dokončit tak hledání. Stránka Žádné symboly poskytuje možnosti pro vyhledání souboru. Pokud je soubor PDB nalezen po spuštění jedné z možností a ladicí program může načíst zdrojový soubor pomocí informací v souboru symbolů, zobrazí se zdroj. V opačném případě **nenačten žádný zdroj** se zobrazí stránka s popisem problému. Na stránce se zobrazí odkazy s možnostmi, které umožňují provádět akce, které mohou problém vyřešit.

###  <a name="BKMK_Add_source_file_search_paths_to_a_solution"></a> Přidat cesty hledání zdrojového souboru do řešení
 Můžete určit síť nebo místní adresáře pro hledání zdrojových souborů.

1. V Průzkumníku řešení vyberte řešení a klikněte na tlačítko **vlastnosti** z místní nabídky.

2. V části **společné vlastnosti** uzlu, vyberte **zdrojové soubory ladění**.

3. Klikněte na složku ![nástroje&#47; možnosti&#47; ladění&#47;ikonu složky symboly](../debugger/media/dbg-tools-options-foldersicon.png "DBG_Tools_Options_FoldersIcon") ikonu. Upravitelný text se zobrazí v **adresáře obsahujícího zdrojový kód** seznamu.

4. Přidejte cestu, kterou chcete prohledat.

   Všimněte si, že je prohledán pouze zadaný adresář. Je nutné přidat položky pro všechny podadresáře, které chcete prohledávat.

###  <a name="BKMK_Use_source_servers"></a> Použití zdrojových serverů
 Pokud neexistuje žádný zdrojový kód v místním počítači nebo soubor PDB neodpovídá zdrojovému kódu, můžete použít zdrojový server k ladění aplikace. Zdrojový server přijímá požadavky na soubory a vrací skutečné soubory. Zdrojový server je spuštěn pomocí souboru knihovny DLL s názvem srcsrv.dll. Zdrojový Server přečte soubor PDB aplikace, který obsahuje odkazy na úložiště zdrojového kódu, jakož i příkazy pro načtení zdrojového kódu z úložiště. Můžete omezit, jaké příkazy mohou být provedeny ze souboru .pdb aplikace uvedením seznamu povolených příkazů v souboru s názvem srcsrv.ini, který musí být umístěn ve stejném adresáři jako soubory srcsrv.dll a devenv.exe.

> [!IMPORTANT]
>  Libovolné příkazy lze vložit do souboru v souboru pdb aplikace, takže zkontrolujte, zda umístíte pouze ty, které chcete provést do souboru srcsrv.ini. Pokus o provedení příkazu mimo soubor srcsvr.ini způsobí zobrazení dialogového okna s potvrzením. Další informace najdete v tématu [upozornění zabezpečení: ladicí program musí spustit nedůvěryhodný příkaz](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Parametry příkazu nejsou ověřovány, proto buďte s důvěryhodnými příkazy opatrní. Například pokud důvěřujete souboru cmd.exe, uživateli se zlými úmysly může zadat parametry, které by z příkazu mohly udělat hrozbu.

 **Chcete-li povolit použití zdrojového serveru**

1.  Ujistěte se, že jsou dodrženy bezpečnostní opatření popsané v předchozí části.

2.  Na **nástroje** nabídce zvolte **možnosti**.

     **Možnosti** zobrazí se dialogové okno.

3.  V **ladění** uzlu, vyberte **Obecné**.

4.  Vyberte **povolit podporu zdrojového serveru** zaškrtávací políčko.

     ![Povolit zdrojový server možnosti](../debugger/media/dbg-options-general-enablesrcsrvr-checkbox.png "DBG_Options_General_EnableSrcSrvr_checkbox")

5.  (Volitelné) Zvolte požadované podřízené možnosti.

     Všimněte si, že oba **povolit zdrojový server pro sestavení částečné důvěryhodnosti (pouze spravované)** a **vždy spouštět nedůvěryhodné příkazy ze zdrojového serveru bez zobrazení výzvy** mohou zvýšit možnost bezpečnostního rizika, které bylo uvedeno výše.

## <a name="see-also"></a>Viz také
 [.NET změny vzdáleného načítání symbolů v sadě Visual Studio 2012 a 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013.aspx)
