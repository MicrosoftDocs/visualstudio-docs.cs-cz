---
title: Určení symbolu (PDB) a zdrojových souborů v ladicím programu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: d4d4b02d512480d96c501758f4cf0f1313158942
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74300557"
---
# <a name="specify-symbol-pdb-and-source-files-in-the-visual-studio-debugger"></a>Zadání symbolu (.pdb) a zdrojových souborů v ladicím programu sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Souboru databáze (PDB) program, nazývaný také soubor symbolů, mapuje identifikátory, které vytvoříte ve zdrojových souborech pro třídy, metody a jiný kód, na identifikátory, které jsou použity v kompilovaných spustitelných souborech projektu. Soubor PDB také mapuje příkazy ve zdrojovém kódu k provozním pokynům ve spustitelných souborech. Ladicí program používá tyto informace k určení dvou důležitých informací: zdrojový soubor a číslo řádku, které jsou zobrazeny v prostředí IDE sady Visual Studio a v umístění ve spustitelném souboru, kde je třeba se zastavit při nastavení zarážky. Soubor symbolů obsahuje také původní umístění zdrojových souborů, případně umístění zdrojového serveru, ze kterého lze načíst zdrojové soubory.

 Při ladění projektu v integrovaném vývojovém prostředí sady Visual Studio rozpozná ladicí program výchozí umístění souboru. pdb a zdrojových souborů pro váš kód. Pokud chcete ladit kód mimo váš zdrojový kód projektu, jako je volání systému Windows nebo kódu třetí strany, musíte určit umístění souboru PDB (a volitelně zdrojových souborů z externího kódu) a tyto soubory musí přesně odpovídat spustitelným souborům sestavení.

 Před spuštěním sady Visual Studio 2012 při ladění spravovaného kódu na vzdáleném zařízení, které jste potřebovali k umístění souborů symbolů na vzdáleném počítači. To již neplatí. Všechny soubory symbolů musí být umístěny v místním počítači nebo v umístění zadaném na stránce **Nástroje/možnosti/ladění/symboly** .

## <a name="where-the-debugger-searches-for-pdb-files"></a><a name="BKMK_Find_symbol___pdb__files"></a> Kde ladicí program vyhledává soubory PDB

1. Umístění, které je zadáno uvnitř knihovny DLL nebo spustitelného souboru.

     (Ve výchozím nastavení, pokud máte vytvořenou knihovnu DLL nebo spustitelný soubor ve vašem počítači, linker umístí úplnou cestu a název souboru přidruženého souboru PDB do knihovny DLL nebo spustitelného souboru. Ladicí program nejprve zkontroluje, zda existuje soubor se symboly v umístění, které je zadáno v knihovně DLL nebo spustitelném souboru. To je užitečné, protože budete mít vždy symboly, které jsou k dispozici pro kód, který jste zkompilovali v počítači.)

2. Soubory PDB, které mohou být uloženy ve stejné složce jako knihovna DLL nebo spustitelný soubor.

3. Všechny složky mezipaměti místního symbolu.

4. Všechny zadané servery sítě, Internetu nebo místních symbolů a umístění, například server Microsoft symbol, pokud je povolen.

### <a name="why-do-symbol-files-need-to-exactly-match-the-executable-files"></a><a name="BKMK_Why_do_symbol_files_need_to_exactly_match_the_executable_files_"></a> Proč soubory symbolů musí přesně odpovídat spustitelným souborům?
 Ladicí program načte pouze soubor PDB pro spustitelný soubor, který přesně odpovídá souboru .pdb vytvořeném, když byl sestaven spustitelný soubor (to znamená, že PDB musí být originál nebo kopie původního souboru .pdb). Vzhledem k tomu, že kompilátor je optimalizován pro rychlost kompilace, kromě svého hlavního úkolu vytvoření správného a efektivního kódu, se může změnit rozložení skutečného spustitelného souboru i v případě, že nedošlo ke změně samotného kódu. Další informace najdete v tématu [Proč Visual Studio vyžaduje soubory symbolů ladicího programu, aby přesně odpovídaly binárním souborům, se kterými byly vytvořeny?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/).

### <a name="specify-symbol-locations-and-loading-behavior"></a><a name="BKMK_Specify_symbol_locations_and_loading_behavior"></a> Zadejte umístění symbolu a chování načítání
 Při ladění projektu v integrovaném vývojovém prostředí VS ladicí program automaticky načte soubory symbolů, které jsou umístěny v adresáři projektu. Můžete zadat alternativní cesty hledání a servery symbolů pro Microsoft, Windows nebo komponenty třetích stran v **nabídce Nástroje/možnosti/ladění/symboly**. Můžete také zadat konkrétní moduly, pro které má ladicí program automaticky načíst symboly. A můžete potom změnit tato nastavení ručně při aktivním ladění.

1. V aplikaci Visual Studio otevřete stránku **Nástroje/možnosti/ladění/symboly** .

    ![Nástroje &#45; možnosti &#45; ladění stránky &#45; symboly](../debugger/media/dbg-tools-options-symbols.png "DBG_Tools_Options_Symbols")

2. Vyberte složku ![nástroje&#47; možnosti&#47; ladění ikona složky symboly&#47;symboly](../debugger/media/dbg-tools-options-foldersicon.png "DBG_Tools_Options_FoldersIcon") . Upravitelný text se zobrazí v poli **umístění souborů symbolů (. pdb)** .

3. Zadejte adresu URL nebo cestu k adresáři serveru symbolů nebo umístění symbolu. Doplňování výrazů vám pomůže najít správný formát.

4. Pokud chcete zlepšit výkon při načítání symbolů, zadejte místní adresář, ve kterém se symboly dají zkopírovat pomocí symbolových serverů v poli **symboly mezipaměti v tomto adresáři** do místního adresáře, do kterého se symboly dají zkopírovat.

   > [!NOTE]
   > Neumísťujte mezipaměť symbolu do chráněné složky (například C:\Windows nebo některé z jejích podsložek). Místo toho použijte složku pro čtení i zápis.

   **Určit chování načítání symbolů**

   Můžete určit soubory, které mají být načteny automaticky z umístění pole **umístění souborů symbolů (. pdb)** při spuštění ladění. Soubory se symboly v adresáři projektu jsou vždy načteny.

5. Zvolte **všechny moduly, pokud vyloučené nejsou** pro načtení všech symbolů pro všechny moduly kromě těch, které určíte, když zvolíte odkaz **zadat vyloučené moduly** .

6. Zvolte možnost **pouze zadané moduly** a pak zvolte možnost **zadat moduly** a uveďte moduly, které soubory symbolů, které chcete načíst automaticky. Soubory symbolů pro ostatní moduly jsou ignorovány.

   **Zadat další možnosti symbolu**

   Na stránce **Nástroje/možnosti/ladění/symboly** můžete také nastavit následující možnosti:

   **Upozornit, pokud při spuštění nejsou žádné symboly (jenom nativní)**

   Vyberete-li tuto možnost, zobrazí se dialogové okno upozornění při pokusu o ladění programu, pro které ladicí program neobsahuje žádné symbolické informace.

   **Načtení exportů DLL**

   Při výběru načte exportní tabulky knihovny DLL. Symbolické informace z tabulky exportu knihovny DLL mohou být užitečné, pokud pracujete se zprávami systému Windows, postupy systému Windows (WindowProcs), objekty COM nebo zařazování nebo libovolnou knihovnou DLL pro kterou nemáte symboly. Informace o exportu knihovny DLL pro čtení zahrnují nadměrné zatížení. Proto tato možnost je ve výchozím nastavení vypnuta.

   Chcete-li zjistit, jaké symboly jsou k dispozici v exportní tabulce knihovny DLL, použijte `dumpbin /exports` . Symboly jsou k dispozici pro všechny 32bitové systémové knihovny DLL. Načtením `dumpbin /exports` výstupu můžete zobrazit přesný název funkce, včetně nealfanumerických znaků. To je užitečné pro nastavení zarážky na funkci. Názvy funkcí z tabulky exportu knihovny DLL se mohou jinde v ladícím programu zobrazit ořezané. Volání jsou uvedena v pořadí volání s aktuální funkcí (nejhlouběji vnořených) nahoře. Další informace najdete v tématu [DUMPBIN/EXPORTS](https://msdn.microsoft.com/library/2971ab7e-4ee6-478b-9c85-cda42a4ce1bf).

### <a name="use-symbol-servers-to-find-symbol-files-not-on-your-local-machine"></a><a name="BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine"></a> Servery symbolů použijte k nalezení souborů symbolů, které nejsou na vašem místním počítači.
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] může stáhnout soubory se symboly ladění ze serverů symbolů, které implementují protokol symsrv. [Visual Studio Team Foundation Server](https://msdn.microsoft.com/library/bd6977ca-e30a-491a-a153-671d81222ce6) a [Nástroje pro ladění pro Windows](https://msdn.microsoft.com/library/windows/hardware/ff551063\(v=VS.85\).aspx) jsou dva nástroje, které můžou implementovat servery symbolů. V dialogovém okně **Možnosti** vs určíte, aby se servery symbolů používaly.

 Mezi servery se symboly, které můžete použít, patří:

 **Veřejné servery se symboly Microsoftu**

 Pokud chcete ladit selhání, ke kterému dojde během volání systémové knihovny DLL nebo knihovny třetí strany, budete často potřebovat systémové soubory .pdb, které obsahují symboly pro soubory DLL, EXE a ovladače zařízení v systému Windows. Tyto symboly můžete získat na veřejných serverech symbolů společnosti Microsoft. Veřejné symbolové servery společnosti Microsoft poskytují symboly pro operační systémy Windows kromě MDAC, IIS, ISA a [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .

 Chcete-li použít Microsoft Symbol Servers, zvolte **Možnosti a nastavení** v nabídce **ladění** a potom zvolte **symboly**. Vyberte **Microsoft Symbol Servers**.

 **Servery symbolů v interní síti nebo v místním počítači**

 Váš tým nebo společnost může vytvořit servery symbolů pro vaše vlastní produkty jako mezipaměť pro symboly z externích zdrojů. Symbolový server můžete mít na vlastním počítači. Můžete zadat umístění serverů symbolů jako adresu URL nebo jako cestu na **Debugging** / stránce**symboly** ladění v **dialogovém okně Možnosti**vs.

 **Servery symbolů třetích stran**

 Jiní zprostředkovatelé aplikací a knihoven systému Windows mohou poskytovat přístup k symbolovému serveru na internetu. Adresu URL těchto symbolových serverů zadáte také na stránce **Debugging** / **symboly** ladění.

> [!NOTE]
> Pokud používáte symbolový server jiný než veřejné symbolové servery společnosti Microsoft, přesvědčte se, zda symbolový server a jeho cesty jsou důvěryhodné. Vzhledem k tomu, že soubory se symboly mohou obsahovat libovolný spustitelný kód, můžete se vystavit bezpečnostním hrozbám.

### <a name="find-and-load-symbols-while-debugging"></a><a name="BKMK_Find_and_load_symbols_while_debugging"></a> Najít a načíst symboly při ladění
 V každém okamžiku, kdy je ladicí program v režimu pozastavení, můžete načíst symboly pro modul, který byl dříve vyloučen možnostmi ladicího programu nebo které kompilátor nemůže najít. Symboly můžete načíst z místních nabídek oken Zásobník volání, Moduly, Lokální, Automatické a Všechna kukátka. Pokud ladicí program se přeruší v kódu, který nemá symbol nebo zdrojové soubory k dispozici, zobrazí se okno dokumentu. Zde naleznete informace o chybějících souborech a provedení akcí k jejich vyhledání a načtení.

 **Hledání symbolů se stránkami dokumentu nebyly načteny žádné symboly**

 Existuje několik způsobů jak může ladicí program proniknout do kódu, který nemá k dispozici symboly ladicího programu:

1. Krokování kódu.

2. Rozdělení do kódu od zarážky nebo výjimky.

3. Přepnutí do jiného podprocesu.

4. Změna zásobníku dvojitým kliknutím na snímek v okně Zásobník volání.

   Když dojde k jedné z těchto událostí, ladicí program zobrazí stránku **nejsou načteny žádné symboly** , které vám pomůžou najít a načíst potřebné symboly.

   ![Na stránce nejsou načteny žádné symboly](../debugger/media/dbg-nosymbolsloaded.png "DBG_NoSymbolsLoaded")

- Chcete-li změnit cesty hledání, zvolte nevybranou cestu nebo zvolte možnost **nové** a zadejte novou cestu. Vyberte **načíst** , chcete-li znovu vyhledat cesty a načíst soubor symbolů, pokud je nalezen.

- Klikněte na **Procházet a vyhledejte**_název spustitelného souboru_**...** , abyste popsali všechny možnosti symbolu, a opakujte cesty pro hledání. Pokud je nalezen soubor symbolů, bude načten, nebo se zobrazí Průzkumník souborů, kde můžete soubor symbolu vybrat ručně.

- Vyberte možnost **změnit nastavení symbolů...** , aby **Debugging**se zobrazila  /  Stránka**symboly** ladění v dialogovém okně Možnosti vs.

- Vyberte **Zobrazit zpětný překlad** pro jednorázové zobrazení zpětného překladu v novém okně.

- Chcete-li vždy zobrazit zpětný překlad, pokud nejsou nalezeny zdrojové soubory nebo soubory symbolů, zvolte odkaz **dialogové okno Možnosti** a vyberte možnost **Povolit ladění na úrovni adresy** a **Zobrazit zpětný překlad, pokud není k dispozici zdroj**.

   ![Možnosti &#47; ladění &#47; Obecné možnosti zpětného překladu](../debugger/media/dbg-options-general-disassembly-checkbox.png "DBG_Options_General_disassembly_checkbox")

  **Změna možností symbolu z místní nabídky**

  Při práci v režimu pozastavení můžete najít a načíst symboly pro položky, které jsou zobrazeny v oknech Zásobník volání, Moduly, Lokální, Automatické a všech oknech Kukátka. V okně vyberte položku, otevřete místní nabídku a zvolte jednu z následujících možností:

|Možnost|Popis|
|------------|-----------------|
|**Načíst symboly**|Pokusí se načíst symboly z umístění zadaných na stránce **Debugging**  /  **symboly** ladění v dialogovém okně **Možnosti** . Pokud nelze najít soubor symbolů, spustí se Průzkumník souborů, takže můžete určit nové umístění pro hledání.|
|**Informace o načítání symbolů**|Představuje informace, které vykazují umístění načteného souboru se symbolem nebo prohledávána umístění, pokud ladicí program nemůže najít soubor.|
|**Nastavení symbolu...**|Otevře stránku **ladicí**  /  **symboly** dialogového okna **Možnosti** vs.|
|**Vždy načítat automaticky**|Přidá soubor symbolů do seznamu souborů, které jsou automaticky načteny pomocí ladicího programu.|

### <a name="set-compiler-options-for-symbol-files"></a><a name="BKMK_Set_compiler_options_for_symbol_files"></a> Nastavit možnosti kompilátoru pro soubory symbolů
 Při sestavování projektu z rozhraní IDE VS a použití standardní konfigurace **ladění** sestavení vytvoří jazyk C++ a spravované kompilátory odpovídající soubory symbolů pro váš kód. Můžete také nastavit možnosti kompilátoru na příkazovém řádku k vytvoření souborů symbolů.

 **Možnosti jazyka C++**

 Soubor databáze programu (PDB) uchovává informace o ladění a stavu projektu, které umožňují přírůstkové propojení konfigurace ladění programu. Soubor PDB se vytvoří při sestavení pomocí [/Zi nebo/Zi](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) (pro C/C++).

 V nástroji [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] možnost [/FD](https://msdn.microsoft.com/library/3977a9ed-f0ac-45df-bf06-01cedd2ba85a) pojmenovává soubor. pdb vytvořený kompilátorem. Při vytváření projektu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pomocí průvodců je možnost **/FD** nastavena na vytvoření souboru. pdb s názvem *Project*. pdb.

 Pokud sestavíte aplikaci C/C++ pomocí souboru pravidel a zadáte **/Zi** nebo **/Zi** bez **/FD**, skončíte se dvěma soubory PDB:

- VC*x*. pdb, kde *x* představuje verzi Visual C++, například VC11. pdb. Tento soubor obsahuje všechny informace o ladění pro jednotlivé soubory OBJ a je umístěn ve stejném adresáři jako soubor pravidel projektu.

- Project. pdb tento soubor uchovává všechny informace o ladění pro soubor the.exe. Pro jazyk C/C++ je umístěn v podadresáři \debug.

  Pokaždé, když vytvoří soubor OBJ, kompilátor C/C++ sloučí informace o ladění do VC*x*. pdb. Vložené informace obsahují informace o typu, ale neobsahují informace o symbolu, jako jsou definice funkce. Takže i když každý zdrojový soubor obsahuje společné hlavičkové soubory \<windows.h> , jako je, definice typedef z těchto hlaviček se ukládají pouze jednou, nikoli v každém souboru obj.

  Linker vytvoří project.pdb, který obsahuje informace o ladění souboru EXE v projektu. Soubor Project. pdb obsahuje úplné informace o ladění, včetně prototypů funkcí, nikoli jenom informace o typu nalezené v VC*x*. pdb. Oba soubory PDB umožňují přírůstkové aktualizace. Linker také vloží cestu k souboru .pdb ve vytvořeném souboru .exe nebo .dll.

  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Ladicí program používá cestu k souboru. pdb v souboru exe nebo DLL k vyhledání souboru Project. pdb. Pokud ladicí program nemůže najít soubor PDB na tomto místě nebo je-li cesta neplatná (například pokud byl projekt přesunut do jiného počítače), ladicí program hledá cestu, která obsahuje soubor EXE, cesty symbolů zadané v dialogovém okně **Možnosti** (složka**ladění** , uzel **symboly** ). Ladicí program nenačte soubor .pdb, který neodpovídá laděnému spustitelnému souboru. Pokud ladicí program nemůže najít soubor PDB, zobrazí se dialogové okno **Najít symboly** , které umožňuje hledat symboly nebo přidat další umístění do cesty pro hledání.

  **Volby rozhraní .NET Framework**

  Soubor databáze programu (PDB) uchovává informace o ladění a stavu projektu, které umožňují přírůstkové propojení konfigurace ladění programu. Při sestavování pomocí **/Debug**se vytvoří soubor. pdb. Můžete vytvářet aplikace pomocí **/debug: Full** nebo **/debug: pdbonly**. Sestavování pomocí **/debug: Full** generuje laditelné kódy. Sestavování pomocí **/debug: pdbonly** generuje soubory PDB, ale negeneruje `DebuggableAttribute` , který oznamuje kompilátoru JIT, že jsou k dispozici informace o ladění. Použijte **/debug: pdbonly** , pokud chcete generovat soubory. PDB pro sestavení vydaných verzí, které nechcete ladit. Další informace naleznete v tématu [/Debug (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969) nebo [/Debug (Visual Basic)](https://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).

  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Ladicí program používá cestu k souboru. pdb v souboru exe nebo DLL k vyhledání souboru Project. pdb. Pokud ladicí program nemůže najít soubor PDB na tomto místě nebo je-li cesta neplatná, ladicí program hledá cestu, která obsahuje soubor EXE, a poté cesty symbolů zadané v dialogovém okně **Možnosti** . Tato cesta je obvykle složka **ladění** v uzlu **symboly** . Ladicí program nenačte soubor .pdb, který neodpovídá laděnému spustitelnému souboru. Pokud ladicí program nemůže najít soubor PDB, zobrazí se dialogové okno **Najít symboly** , které umožňuje hledat symboly nebo přidat další umístění do cesty pro hledání.

  **Webové aplikace**

  Konfigurační soubor aplikace (Web.config) musí být nastaven na režim ladění. Režim ladění způsobí, že technologie ASP.NET generuje dynamicky generované soubory a umožňuje ladicímu program připojit k aplikaci technologie ASP.NET. VS tuto hodnotu nastaví automaticky při spuštění ladění, pokud jste vytvořili projekt ze šablony webových projektů.

## <a name="find-source-files"></a><a name="BKMK_Find_source_files"></a> Najít zdrojové soubory

### <a name="where-the-debugger-searches-for-source-files"></a><a name="BKMK_Where_the_debugger_searches_for_source_files"></a> Kde ladicí program vyhledává zdrojové soubory
 Ladicí program vyhledá zdrojové soubory v následujících umístěních:

1. Soubory, které jsou otevřeny v integrovaném vývojovém prostředí Visual Studio instance, které spustilo ladicí program.

2. Soubory v řešení, které jsou otevřeny v instanci sady Visual Studio.

3. Adresáře, které jsou zadány na stránce **Společná nastavení**–  /  **zdrojové soubory ladění** ve vlastnostech řešení. (V **Průzkumník řešení**vyberte uzel řešení, klikněte pravým tlačítkem myši a vyberte **vlastnosti**. )

4. Zdrojové informace o souboru .pdb modulu. To může být umístění zdrojového souboru, když modul byl vytvořen, nebo to může být příkaz na zdrojový server.

### <a name="find-and-load-source-files-with-the-no-source--no-symbols-loaded-pages"></a><a name="BKMK_Find_and_load_source_files_with_the_No_Source___No_Symbols_Loaded_pages"></a> Vyhledání a načtení zdrojových souborů se stránkami žádný zdroj/nebyly načteny žádné symboly
 Pokud ladicí program přeruší provádění v místě, kde není k dispozici zdrojový soubor, zobrazí se stránky **není načten žádný zdroj** nebo **nebyly načteny žádné symboly** , které vám pomohou najít zdrojový soubor. **Nejsou načteny žádné symboly** se zobrazí, pokud ladicí program nemůže najít soubor symbolů (. pdb) pro spustitelný soubor pro dokončení hledání. Stránka Žádné symboly poskytuje možnosti pro vyhledání souboru. Pokud je soubor PDB nalezen po spuštění jedné z možností a ladicí program může načíst zdrojový soubor pomocí informací v souboru symbolů, zobrazí se zdroj. V opačném případě se zobrazí stránka **bez načteného zdroje** , která popisuje problém. Na stránce se zobrazí odkazy s možnostmi, které umožňují provádět akce, které mohou problém vyřešit.

### <a name="add-source-file-search-paths-to-a-solution"></a><a name="BKMK_Add_source_file_search_paths_to_a_solution"></a> Přidat cesty hledání zdrojového souboru do řešení
 Můžete určit síť nebo místní adresáře pro hledání zdrojových souborů.

1. Vyberte řešení v Průzkumník řešení a pak v místní nabídce zvolte **vlastnosti** .

2. V uzlu **společné vlastnosti** vyberte možnost **Ladit zdrojové soubory**.

3. Klikněte na tlačítko složky ![nástroje&#47; možnosti&#47; ladění ikona složky symboly&#47;symboly](../debugger/media/dbg-tools-options-foldersicon.png "DBG_Tools_Options_FoldersIcon") . Upravitelný text se zobrazí v seznamu **adresáře obsahujícího zdrojový kód** .

4. Přidejte cestu, kterou chcete prohledat.

   Všimněte si, že je prohledán pouze zadaný adresář. Je nutné přidat položky pro všechny podadresáře, které chcete prohledávat.

### <a name="use-source-servers"></a><a name="BKMK_Use_source_servers"></a> Použít zdrojové servery
 Pokud neexistuje žádný zdrojový kód v místním počítači nebo soubor PDB neodpovídá zdrojovému kódu, můžete použít zdrojový server k ladění aplikace. Zdrojový server přijímá požadavky na soubory a vrací skutečné soubory. Zdrojový server je spuštěn pomocí souboru knihovny DLL s názvem srcsrv.dll. Zdrojový Server přečte soubor PDB aplikace, který obsahuje odkazy na úložiště zdrojového kódu, jakož i příkazy pro načtení zdrojového kódu z úložiště. Můžete omezit, jaké příkazy mohou být provedeny ze souboru .pdb aplikace uvedením seznamu povolených příkazů v souboru s názvem srcsrv.ini, který musí být umístěn ve stejném adresáři jako soubory srcsrv.dll a devenv.exe.

> [!IMPORTANT]
> Libovolné příkazy lze vložit do souboru v souboru pdb aplikace, takže zkontrolujte, zda umístíte pouze ty, které chcete provést do souboru srcsrv.ini. Pokus o provedení příkazu mimo soubor srcsvr.ini způsobí zobrazení dialogového okna s potvrzením. Další informace najdete v tématu [Upozornění zabezpečení: ladicí program musí spustit nedůvěryhodný příkaz](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Parametry příkazu nejsou ověřovány, proto buďte s důvěryhodnými příkazy opatrní. Například pokud důvěřujete souboru cmd.exe, uživateli se zlými úmysly může zadat parametry, které by z příkazu mohly udělat hrozbu.

 **Povolení použití zdrojového serveru**

1. Ujistěte se, že jsou dodrženy bezpečnostní opatření popsané v předchozí části.

2. V nabídce **nástroje** klikněte na příkaz **Možnosti**.

     Zobrazí se dialogové okno **Možnosti** .

3. V uzlu **ladění** vyberte **Obecné**.

4. Zaškrtněte políčko **Povolit podporu zdrojového serveru** .

     ![Povolit možnosti zdrojového serveru](../debugger/media/dbg-options-general-enablesrcsrvr-checkbox.png "DBG_Options_General_EnableSrcSrvr_checkbox")

5. (Volitelné) Zvolte požadované podřízené možnosti.

     Počítejte s tím, že možnost **Povolení zdrojového serveru pro částečně důvěryhodná sestavení (pouze spravované)** a **vždy spouštět nedůvěryhodné příkazy zdrojového serveru bez zobrazení výzvy** může zvýšit rizika zabezpečení popsaná výše.

## <a name="see-also"></a>Viz také
 [Změny vzdáleného načítání symbolů .NET v prostředí Visual Studio 2012 a 2013](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/)
