---
title: Nastavení symbolu (PDB) a zdrojových souborů v ladicím programu
description: Naučte se konfigurovat a spravovat symboly a zdrojové soubory v aplikaci Visual Studio.
ms.custom: ''
ms.date: 10/31/2019
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Debugger.Native
- VS.ToolsOptionsPages.Debugger.Symbols
- vs.debug.options.Native
- vs.debug.nosymbols
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 78440c6da86d49364f7fd9006779166e8c2fb7d3
ms.sourcegitcommit: 686aa3516594ab951d48b192fc60b102eedaf9b7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/06/2021
ms.locfileid: "99628003"
---
# <a name="specify-symbol-pdb-and-source-files-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Určení symbolu (. pdb) a zdrojových souborů v ladicím programu sady Visual Studio (C#, C++, Visual Basic, F #)

Soubory databáze programu (*PDB*), označované také jako soubory symbolů, mapují identifikátory a příkazy ve zdrojovém kódu vašeho projektu na odpovídající identifikátory a pokyny v kompilovaných aplikacích. Tyto mapovací soubory propojí ladicí program s vaším zdrojovým kódem, který umožňuje ladění.

Při sestavování projektu z integrovaného vývojového prostředí sady Visual Studio se standardní konfigurací sestavení ladění vytvoří kompilátor příslušné soubory symbolů. Tento článek popisuje, jak spravovat soubory symbolů v integrovaném vývojovém prostředí (IDE), například jak [určit umístění symbolů v možnostech ladicího programu](#BKMK_Specify_symbol_locations_and_loading_behavior), jak [kontrolovat stav načítání symbolů](#work-with-symbols-in-the-modules-window) během ladění a jak [nastavit možnosti symbolu v kódu](#compiler-symbol-options).

Podrobné vysvětlení souborů symbolů najdete v následujících tématech:

- [Principy souborů symbolů a nastavení symbolů sady Visual Studio](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/)

- [Proč Visual Studio vyžaduje soubory symbolů ladicího programu, aby přesně odpovídaly binárním souborům, se kterými byly vytvořeny?](/archive/blogs/jimgries/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with)

## <a name="how-symbol-files-work"></a>Jak fungují soubory symbolů

Soubor *. pdb* uchovává informace o ladění a stavu projektu, které umožňují přírůstkové propojení konfigurace ladění aplikace. Ladicí program sady Visual Studio používá soubory *. pdb* k určení dvou klíčových částí informací během ladění:

* Název zdrojového souboru a číslo řádku, které se mají zobrazit v integrovaném vývojovém prostředí sady Visual Studio
* Kam se v aplikaci zastaví pro zarážku.

Soubory symbolů také zobrazují umístění zdrojových souborů a případně také server, ze kterého se mají načíst.

Ladicí program načte pouze soubory *. pdb* , které se přesně shodují se soubory *. pdb* vytvořenými při vytvoření aplikace (tj. původní soubory *. pdb* nebo kopie). Tato [Přesná duplikace](/archive/blogs/jimgries/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with) je nezbytná, protože rozložení aplikací se může změnit i v případě, že se samotný kód nezměnil.

> [!TIP]
> Chcete-li ladit kód mimo váš zdrojový kód projektu, jako je například kód systému Windows nebo kód třetí strany pro volání projektu, je nutné zadat umístění souborů *. pdb* externího kódu (a případně zdrojových souborů), které musí přesně odpovídat sestavením ve vaší aplikaci.

## <a name="symbol-file-locations-and-loading-behavior"></a>Umístění souborů symbolů a chování při načítání

Při ladění projektu v integrovaném vývojovém prostředí sady Visual Studio ladicí program automaticky načte soubory symbolů, které jsou umístěny ve složce projektu.

> [!NOTE]
> Při ladění spravovaného kódu na vzdáleném zařízení musí být všechny soubory symbolů umístěny buď na místním počítači, nebo v umístění [zadaném v možnostech ladicího programu](#BKMK_Specify_symbol_locations_and_loading_behavior).

Ladicí program také vyhledává soubory symbolů v následujících umístěních:

1. Umístění, které je zadáno v knihovně DLL nebo spustitelném souboru (*. exe*).

   Ve výchozím nastavení, pokud máte vytvořenou knihovnu DLL nebo soubor *. exe* ve vašem počítači, linker umístí úplnou cestu a název souboru přidruženého souboru *PDB* do souboru DLL nebo *exe* . Ladicí program zkontroluje, zda soubor symbolů v tomto umístění existuje.

2. Stejná složka jako soubor DLL nebo *exe* .

3. Všechna umístění zadaná v možnostech ladicího programu pro soubory symbolů. Chcete-li přidat a povolit umístění symbolů, přečtěte si téma [Konfigurace umístění symbolů a možnosti načítání](#BKMK_Specify_symbol_locations_and_loading_behavior).

   - Libovolná místní složka mezipaměti symbolů.

   - Zadané síťové servery, servery sítě Internet nebo místní symboly a umístění, například servery symbolů společnosti Microsoft, pokud jsou vybrány. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] může stáhnout soubory se symboly ladění ze serverů symbolů, které implementují `symsrv` protokol. [Visual Studio Team Foundation Server](/azure/devops/pipelines/tasks/build/index-sources-publish-symbols) a [ladicí nástroje pro Windows](/windows-hardware/drivers/debugger/index) jsou dva nástroje, které mohou používat servery symbolů.

     Mezi servery se symboly, které můžete použít, patří:

     **Veřejné servery symbolů Microsoftu**: Pokud chcete ladit selhání, ke kterému dojde během volání systémové knihovny DLL nebo knihovny třetí strany, často potřebujete systémové soubory *. pdb* . Systémové soubory *. pdb* obsahují symboly pro knihovny DLL systému Windows, soubory *. exe* a ovladače zařízení. Symboly pro operační systémy Windows, MDAC, IIS, ISA a .NET můžete získat z veřejných serverů Microsoft symbol.

     **Servery symbolů v interní síti nebo v místním počítači**: váš tým nebo společnost může vytvořit servery symbolů pro vaše vlastní produkty a jako mezipaměť pro symboly z externích zdrojů. Symbolový server můžete mít na vlastním počítači.

     **Servery se symboly třetích stran**: Poskytovatelé aplikací a knihoven systému Windows můžou poskytovat přístup k serveru symbolů na internetu.

     > [!WARNING]
     > Pokud používáte symbolový server jiný než veřejné symbolové servery společnosti Microsoft, ujistěte se, že symbol server a jeho cesta jsou důvěryhodné. Vzhledem k tomu, že soubory symbolů mohou obsahovat libovolný spustitelný kód, můžete být vystaveni bezpečnostním hrozbám.

<a name="BKMK_Specify_symbol_locations_and_loading_behavior"></a>
### <a name="configure-symbol-locations-and-loading-options"></a>Konfigurace umístění symbolů a možností načítání

Na   >    >    >  stránce **symboly** ladění možností nástrojů můžete:

- Zadejte a vyberte cesty pro hledání a servery symbolů pro Microsoft, Windows nebo komponenty třetích stran.
- Zadejte moduly, které nechcete, aby ladicí program automaticky načetl symboly pro.
- Tato nastavení můžete změnit při aktivním ladění. Viz [Správa symbolů během ladění](#manage-symbols-while-debugging).

**Určení umístění symbolů a možností načítání:**

1. V aplikaci Visual Studio otevřete   >  **Možnosti** nástrojů  >  **ladění**  >  **symboly** (nebo   >    >  **symboly** možností ladění).

2. V části **umístění souborů symbolů (. pdb)**,
   - Chcete-li použít server symbolů **Microsoft** nebo **symbol serveru NuGet.org**, zaškrtněte políčko.

   - Chcete-li přidat nové umístění serveru symbolů,
     1. Vyberte **+** symbol na panelu nástrojů.
     1. Do textového pole zadejte adresu URL (http), sdílenou síťovou složku nebo místní cestu serveru symbolů nebo umístění symbolu. Doplňování výrazů vám pomůže najít správný formát.

     ![Nástroje &#45; možnosti &#45; ladění stránky &#45; symboly](media/dbg-options-symbols.gif "Nástroje &#45; možnosti &#45; ladění stránky &#45; symboly")

     >[!NOTE]
     >Je prohledána pouze Zadaná složka. Je nutné přidat položky pro všechny podsložky, které chcete prohledávat.

   - Chcete-li přidat nové umístění serveru symbolů VSTS,
     1. Vyberte ![možnosti&#47; nástroje&#47; ladění&#47;symboly ikona ikony serveru](media/dbg_tools_options_foldersicon.png "Nástroje &#45; možnosti &#45; ladění &#45; symboly nový server ikona") na panelu nástrojů.
     1. V dialogovém okně **připojit k serveru symbolů VSTS** vyberte jeden z dostupných serverů symbolů a vyberte **připojit**.

   - Chcete-li změnit pořadí načítání pro umístění symbolů, použijte **kombinaci** + **nahoru** a **CTRL +** + šipka **dolů** nebo ikony šipky **nahoru** a **dolů** .
   - Chcete-li upravit adresu URL nebo cestu, dvakrát klikněte na položku nebo ji vyberte a stiskněte klávesu **F2**.
   - Pokud chcete položku odebrat, vyberte ji a potom vyberte **-** ikonu.

3. Volitelné Chcete-li zlepšit výkon načítání symbolů, zadejte v části **symboly mezipaměti v tomto adresáři** cestu k místní složce, do které budou servery symbolů kopírovat symboly.

   > [!NOTE]
   > Místní mezipaměť symbolů neumísťujte do chráněné složky, jako je například C:\Windows nebo podsložka. Místo toho použijte složku pro čtení i zápis.

   > [!NOTE]
   > V případě projektů v jazyce C++, pokud máte `_NT_SYMBOL_PATH` nastavenou proměnnou prostředí, přepíše hodnotu nastavenou v části **symboly mezipaměti v tomto adresáři**.

4. Určete moduly, které má ladicí program načíst ze **umístění souborů symbolů (. pdb)** při spuštění.

   - Vyberte možnost **načíst všechny moduly, pokud není vyloučena** (výchozí) pro načtení všech symbolů pro všechny moduly v umístění souboru symbolů, s výjimkou modulů, které výslovně vyloučíte. Chcete-li vyloučit určité moduly, vyberte možnost **zadat vyloučené moduly**, vyberte **+** ikonu, zadejte názvy modulů, které mají být vyloučeny, a vyberte **OK**.

   - Chcete-li načíst pouze moduly, které zadáte z umístění souborů symbolů, vyberte možnost **načíst pouze zadané moduly**. Vyberte možnost **zadat zahrnuté moduly**, vyberte **+** ikonu, zadejte názvy modulů, které chcete zahrnout, a pak vyberte **OK**. Soubory symbolů pro ostatní moduly nejsou načteny.

5. Vyberte **OK**.

## <a name="other-symbol-options-for-debugging"></a>Další možnosti symbolu pro ladění

Můžete vybrat další možnosti symbolu v **nabídce nástroje**  >  **Možnosti**  >  **ladění**  >  **Obecné** (nebo   >    >  **Obecné** možnosti ladění):

- **Načíst exporty dll (pouze nativní)**

  Načte exportní tabulky knihovny DLL pro C/C++. Podrobnosti najdete v tématu [exportní tabulky knihovny DLL](#use-dumpbin-exports). Čtení informací o exportu knihovny DLL zahrnuje režii, takže načítání tabulek exportu je ve výchozím nastavení vypnuté. Můžete použít také `dumpbin /exports` v příkazovém řádku sestavení C/C++.

- **Povolit ladění na úrovni adresy** a **Zobrazit zpětný překlad, pokud není k dispozici zdroj**

  Vždy zobrazuje zpětný překlad, pokud nejsou nalezeny zdrojové soubory nebo soubory symbolů.

  ![Možnosti &#47; ladění &#47; Obecné možnosti zpětného překladu](../debugger/media/dbg_options_general_disassembly_checkbox.png "Možnosti &#47; ladění &#47; Obecné možnosti zpětného překladu")
  <a name="BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine"></a>
- **Povolit podporu zdrojového serveru**

  Používá zdrojový server k ladění aplikace v případě, že na místním počítači není žádný zdrojový kód nebo soubor *. pdb* neodpovídá zdrojovému kódu. Zdrojový server přijímá požadavky na soubory a vrací skutečné soubory ze správy zdrojového kódu. Zdrojový server běží pomocí knihovny DLL s názvem *srcsrv.dll* ke čtení souboru *PDB* aplikace. Soubor *. pdb* obsahuje odkazy na úložiště zdrojového kódu a příkazy používané pro načtení zdrojového kódu z úložiště.

  Můžete omezit příkazy, které *srcsrv.dll* lze provést ze souboru *. pdb* aplikace výpisem povolených příkazů v souboru s názvem *srcsrv.ini*. Soubor *srcsrv.ini* umístěte do stejné složky jako *srcsrv.dll* a *devenv.exe*.

  >[!IMPORTANT]
  >Libovolné příkazy mohou být vloženy do souboru *PDB* aplikace, takže nezapomeňte vložit pouze příkazy, které chcete spustit, do souboru *srcsrv.ini* . Při každém pokusu o spuštění příkazu, který není v souboru *srcsvr.ini* , se zobrazí potvrzovací dialogové okno. Další informace najdete v tématu [Upozornění zabezpečení: ladicí program musí spustit nedůvěryhodný příkaz](../debugger/security-warning-debugger-must-execute-untrusted-command.md).
  >
  >Parametry příkazu nejsou ověřovány, proto buďte s důvěryhodnými příkazy opatrní. Pokud jste například v *srcsrv.ini* zadali *cmd.exe* , uživatel se zlými úmysly může zadat parametry *cmd.exe* , které by to mohlo být nebezpečné.

  Vyberte tuto položku a podřízené položky, které chcete. **Povolí zdrojový server pro částečně důvěryhodná sestavení (pouze spravovaná)** a **vždy spouštět nedůvěryhodné příkazy zdrojového serveru bez zobrazení výzvy** . může zvýšit bezpečnostní riziko.

  ![Povolit možnosti zdrojového serveru](../debugger/media/dbg_options_general_enablesrcsrvr_checkbox.png "DBG_Options_General_EnableSrcSrvr_checkbox")

## <a name="compiler-symbol-options"></a>Možnosti symbolu kompilátoru

Při sestavování projektu z integrovaného vývojového prostředí sady Visual Studio se standardní konfigurací sestavení **ladění** vytvoří jazyk C++ a spravované kompilátory odpovídající soubory symbolů pro váš kód. Můžete také nastavit možnosti kompilátoru v kódu.

### <a name="net-options"></a>Možnosti rozhraní .NET

Sestavte pomocí **/Debug** a vytvořte soubor *. pdb* . Můžete vytvářet aplikace pomocí **/debug: Full** nebo **/debug: pdbonly**. Sestavování pomocí **/debug: Full** generuje laditelné kódy. Sestavování pomocí **/debug: pdbonly** generuje soubory *PDB* , ale negeneruje `DebuggableAttribute` , který oznamuje kompilátoru JIT, že jsou k dispozici informace o ladění. Použijte **/debug: pdbonly** , pokud chcete generovat soubory *. pdb* pro sestavení vydaných verzí, které nechcete ladit. Další informace naleznete v tématu [/Debug (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option) nebo [/Debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug).

### <a name="cc-options"></a>Možnosti jazyka C/C++

- Soubory *VC \<x> . pdb* a *\<project> . pdb*

  Soubor *. pdb* pro C/C++ se vytvoří při sestavení pomocí [/Zi nebo/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format). V [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] , možnost [/FD](/cpp/build/reference/fd-program-database-file-name) pojmenuje soubor *. pdb* , který kompilátor vytvoří. Při vytváření projektu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pomocí rozhraní IDE je možnost **/FD** nastavena na vytvoření souboru *. pdb* s názvem *\<project> . pdb*.

  Pokud sestavíte aplikaci C/C++ pomocí souboru pravidel a zadáte **/Zi** nebo **/Zi** bez použití **/FD**, kompilátor vytvoří dva soubory *PDB* :

  - *VC \<x> . pdb*, kde *\<x>* představuje verzi kompilátoru jazyka Microsoft C++, například *VC11. pdb*

    Soubor *VC \<x> . pdb* ukládá všechny informace o ladění pro jednotlivé soubory objektů a je umístěn ve stejném adresáři jako soubor pravidel projektu. Pokaždé, když vytvoří soubor objektu, kompilátor C/C++ sloučí informace o ladění do *VC \<x> . pdb*. Takže i když každý zdrojový soubor obsahuje společné hlavičkové soubory *\<windows.h>* , jako je, definice typedef z těchto hlaviček se ukládají pouze jednou, nikoli v každém souboru objektu. Vložené informace obsahují informace o typu, ale neobsahují informace o symbolech, jako jsou definice funkce.

  - *\<project>soubor. pdb*

    Soubor *\<project> . pdb* uchovává všechny informace o ladění pro soubor *. exe* projektu a je umístěn v podadresáři *\debug.* . Soubor *\<project> . pdb* obsahuje úplné informace o ladění, včetně prototypů funkcí, nikoli jenom informace o typu nalezené v souboru *VC \<x> . pdb*.

  Soubory *VC \<x> . pdb* i *\<project> . pdb* umožňují přírůstkové aktualizace. Linker také vloží cestu k souborům *PDB* v souboru *. exe* nebo *. dll* , který vytvoří.

- <a name="use-dumpbin-exports"></a>Exportní tabulky knihovny DLL

  Použijte `dumpbin /exports` k zobrazení symbolů, které jsou k dispozici v exportní tabulce knihovny DLL. Symbolické informace z tabulek exportu knihovny DLL mohou být užitečné při práci se zprávami systému Windows, postupy systému Windows (WindowProcs), objekty COM, zařazování nebo libovolnou knihovnou DLL, pro kterou nemáte symboly. Symboly jsou k dispozici pro všechny 32bitové systémové knihovny DLL. Volání jsou uvedena v pořadí volání s aktuální funkcí (nejhlouběji vnořených) nahoře.

  Čtením `dumpbin /exports` výstupu můžete zobrazit přesné názvy funkcí, včetně nealfanumerických znaků. Zobrazení přesných názvů funkcí je užitečné pro nastavení zarážky pro funkci, protože názvy funkcí lze zkrátit jinde v ladicím programu. Další informace najdete v tématu [DUMPBIN/EXPORTS](/cpp/build/reference/dash-exports).

### <a name="web-applications"></a>Webové aplikace

Nastavte soubor *web.config* vaší aplikace ASP.NET na režim ladění. Režim ladění způsobí, že technologie ASP.NET generuje dynamicky generované soubory a umožňuje ladicímu program připojit k aplikaci technologie ASP.NET. Sada Visual Studio nastaví tuto automaticky při spuštění ladění, pokud jste vytvořili projekt ze šablony webových projektů.

## <a name="manage-symbols-while-debugging"></a>Správa symbolů během ladění

Můžete použít **moduly**, **zásobník volání**, **místní** hodnoty, **Automatické** hodnoty nebo libovolné okno **kukátka** k načtení symbolů nebo změnu možností symbolu při ladění. Další informace najdete v tématu [o tom, jak se ladicí program připojuje k vaší aplikaci](../debugger/debugger-tips-and-tricks.md#modules_window).

### <a name="work-with-symbols-in-the-modules-window"></a>Práce se symboly v okně moduly

Během ladění se v okně **moduly** zobrazují kódové moduly, které ladicí program zpracovává jako uživatelský kód, nebo můj kód a jejich stav načítání symbolů. Můžete také monitorovat stav načítání symbolů, načítat symboly a měnit možnosti symbolu v okně **moduly** .

**Chcete-li monitorovat nebo měnit umístění symbolů nebo možnosti při ladění:**

1. Chcete-li otevřít okno **moduly** , při ladění vyberte možnost **ladit**  >  **moduly systému Windows**  >   (nebo stiskněte klávesu **CTRL**  +  **ALT**  +  **U**).
1. V okně **moduly** klikněte pravým tlačítkem myši na **stav symbolu** nebo záhlaví **souborů symbolů** nebo na libovolný modul.
1. V místní nabídce vyberte jednu z následujících možností:

|Možnost|Popis|
|------------|-----------------|
|**Načíst symboly**|Zobrazuje se u modulů, které se přeskočily, nenašly, nebo nejsou načtené symboly. Pokusí se načíst symboly z umístění zadaných na   >    >  stránce **symboly** ladění možností. Pokud se soubor symbolů nenajde nebo není načtený, spustí **Průzkumníka souborů** , abyste mohli zadat nové umístění pro hledání.|
|**Informace o načítání symbolů**|Zobrazuje umístění načteného souboru se symboly nebo umístění, která byla prohledána, pokud ladicí program nemůže najít soubor.|
|**Nastavení symbolu**|Otevře stránku s  >    >  **symboly** ladění možností, kde můžete upravit a přidat umístění symbolů.|
|**Vždy načítat automaticky**|Přidá vybraný soubor symbolů do seznamu souborů, které jsou automaticky načteny pomocí ladicího programu.|

### <a name="use-the-no-symbols-loadedno-source-loaded-pages"></a>Použít žádné načtené symboly/Nenačtené stránky zdroje

Existuje několik způsobů, jak ladicí program rozdělit do kódu, který nemá k dispozici symboly nebo zdrojové soubory:

- Krokovat s vnořením do kódu.
- Přerušit do kódu ze zarážky nebo výjimky.
- Přepněte na jiné vlákno.
- Změňte rámeček zásobníku dvojitým kliknutím na rámec v okně **zásobník volání** .

Pokud k tomu dojde, ladicí program zobrazí **Nenačtené symboly** nebo **Nenačtené stránky,** které vám pomůžou najít a načíst potřebné symboly nebo zdroje.

 ![Na stránce nejsou načteny žádné symboly](../debugger/media/dbg-nosymbolsloaded.png "DBG_NoSymbolsLoaded")

**Chcete-li použít stránku dokumentu Nenačtené symboly, které vám pomůžou najít a načíst chybějící symboly:**

- Chcete-li změnit cestu pro hledání, vyberte nevybranou cestu nebo vyberte možnost **Nová cesta** nebo **Nová cesta VSTS** a zadejte nebo vyberte novou cestu. Vyberte **načíst** pro opětovné hledání cest a načtení souboru symbolů, pokud je nalezen.
- Pokud chcete přepsat všechny možnosti symbolu a opakovat cesty hledání, vyberte **Procházet a najít \<executable-name>**. Soubor symbolů se načte, pokud se najde, nebo se otevře **Průzkumník souborů** , abyste mohli ručně vybrat soubor symbolů.
- Chcete-li otevřít  >    >  stránku **symboly** ladění možností, vyberte možnost **změnit nastavení symbolu**.
- Chcete-li znovu zobrazit zpětný překlad v novém okně, vyberte možnost **Zobrazit zpětný překlad**, nebo vyberte možnost **dialog možností** pro nastavení možnosti, aby bylo možné vždy zobrazit zpětný překlad, pokud nejsou nalezeny zdrojové soubory nebo soubory symbolů.
- Chcete-li zobrazit prohledávané umístění a výsledek, rozbalte položku **informace o načtení symbolů**.

Pokud ladicí program nalezne soubor *. pdb* po provedení jedné z možností a může načíst zdrojový soubor pomocí informací v souboru *. pdb* , zobrazí se zdroj. V opačném případě zobrazí stránku **nenačtený zdroj** , která popisuje problém, a odkazy na akce, které mohou problém vyřešit.

**Postup přidání cest pro vyhledávání zdrojového souboru do řešení:**

Můžete určit umístění, ve kterém ladicí program vyhledává zdrojové soubory, a vyloučit konkrétní soubory ze hledání.

1. Vyberte řešení v **Průzkumník řešení** a pak vyberte ikonu **vlastnosti** , stiskněte klávesu **ALT** + **ENTER** nebo klikněte pravým tlačítkem myši a vyberte možnost **vlastnosti**.

1. Vyberte **zdrojové soubory ladění**.

1. V části **adresáře obsahující zdrojový kód** zadejte nebo vyberte umístění zdrojového kódu, který chcete vyhledat. Pomocí ikony **nový řádek** můžete přidat další umístění, ikony šipek **nahoru** a **dolů** pro jejich uspořádání nebo ikonu **X** k jejich odstranění.

   >[!NOTE]
   >Ladicí program vyhledá pouze zadaný adresář. Je nutné přidat položky pro všechny podadresáře, které chcete prohledávat.

1. V části **nehledat tyto zdrojové soubory** zadejte názvy zdrojových souborů, které se mají vyloučit ze služby Search.

1. Vyberte **OK** nebo **použít**.

## <a name="see-also"></a>Viz také
- [Principy souborů symbolů a nastavení symbolů sady Visual Studio](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/)

- [Změny vzdáleného načítání symbolů .NET v prostředí Visual Studio 2012 a 2013](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/)