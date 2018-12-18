---
title: Nastavení symbolu (.pdb) a zdrojových souborů v ladicím programu
ms.custom: seodec18
ms.date: 10/08/2018
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6ba2f7794b052712d35bbdadb02a0ea8551dc78b
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53060443"
---
# <a name="specify-symbol-pdb-and-source-files-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Zadání symbolu (.pdb) a zdrojových souborů v ladicím programu sady Visual Studio (C#, C++, Visual Basic, F#)

Databáze programu (*PDB*) soubory, soubory symbolů také volat mapování identifikátorů a příkazy ve zdrojovém kódu projektu na odpovídající identifikátory a podle pokynů v kompilaci aplikace. 

Při vytváření projektu v prostředí Visual Studio IDE se standardem konfigurace sestavení pro ladění, kompilátor vytvoří příslušné soubory symbolů. Můžete také [nastavení možností symbol v kódu](#compiler-symbol-options). 

*PDB* soubor uchovává ladění na projekt a informace o stavu, který umožňuje přírůstkové propojení konfigurace ladění vaší aplikace. Ladicí program sady Visual Studio používá *PDB* soubory k určení dvou důležitých informací při ladění:

* Zdrojového souboru název a číslo řádku zobrazíte v integrovaném vývojovém prostředí sady Visual Studio.
* Kam v aplikaci zastavit pro zarážku.

Soubory symbolů také zobrazit umístění zdrojových souborů a volitelně server je z načítat.
  
Ladicí program načte pouze *PDB* soubory, které přesně odpovídají *PDB* souborů vytvoří, když byla aplikace sestavena (to znamená, původní *PDB* soubory nebo kopie). Tato duplikace přesně je nezbytné, protože rozložení aplikace můžete změnit i v případě, že nedošlo ke změně samotného kódu. Další informace najdete v tématu [proč sada Visual Studio vyžaduje soubory symbolů ladicího programu shodovaly binárním souborům, se kterými byly vytvořeny?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/)

> [!TIP]
> Chcete-li ladit kód mimo váš zdrojový kód projektu, jako je kód Windows nebo třetích stran kód volá váš projekt, je nutné zadat umístění z externího kódu *PDB* soubory (a volitelně zdrojových souborů), které se musí přesně shodovat sestavení ve vaší aplikaci. 

## <a name="symbol-file-locations-and-loading-behavior"></a>Umístění souborů se symboly a chování načítání

> [!NOTE]
> Ladění spravovaného kódu na vzdáleném zařízení, všechny soubory symbolů musí být umístěny v místním počítači nebo v umístění [zadaná v možnostech ladicího programu](#BKMK_Specify_symbol_locations_and_loading_behavior).  
  
Při ladění projektu v integrovaném vývojovém prostředí sady Visual Studio, ladicí program automaticky načte soubory symbolů, které jsou umístěny ve složce projektu. 

Ladicí program vyhledává také soubory se symboly v následujících umístěních:

1. Umístění, které je zadáno uvnitř knihovny DLL nebo spustitelného souboru (*.exe*) soubor.  
   
   Ve výchozím nastavení Pokud máte vytvořenou knihovnu DLL nebo s *.exe* souboru na počítači, linker umístí úplnou cestu a název souboru přidruženého *PDB* soubor v knihovně DLL nebo *.exe* souboru. Ladicí program zjistí, pokud existuje soubor se symboly v dané oblasti.  
   
2. Stejné složce jako knihovna DLL nebo *.exe* souboru.
   
3. Žádná umístění zadaná v možnostech ladicího programu pro soubory symbolů. Přidat a povolit umístění symbolů, přečtěte si téma [konfigurovat umístění symbolu a načítání](#BKMK_Specify_symbol_locations_and_loading_behavior). 
   
   - Všechny složky mezipaměti místního symbolu.  
  
   - Zadaný síťový, internet, nebo místní symbolové servery a umístění, jako je například Microsoft Symbol Servers vybrali. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] může stáhnout soubory symbolu ladění ze serverů symbolů, které implementují `symsrv` protokolu. [Visual Studio Team Foundation Server](/azure/devops/pipelines/tasks/build/index-sources-publish-symbols) a [ladění nástroje pro Windows](/windows-hardware/drivers/debugger/index) jsou dva nástroje, které můžete použít servery symbolů.
      
     Servery symbolů, které můžete použít, patří:  
      
     **Veřejné servery symbolů společnosti Microsoft**: K ladění selhání, ke kterému dojde během volání systémové knihovny DLL nebo knihovny třetí strany, budete často potřebovat systémové *PDB* soubory. Systém *PDB* soubory obsahují symboly pro knihovny DLL pro Windows, *.exe* soubory a ovladače zařízení. Můžete získat symboly pro operační systémy Windows, MDAC, IIS, ISA a [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] z veřejné symbolové servery společnosti Microsoft. 
      
     **Servery v interní síti nebo na místním počítači symbolů**: váš tým nebo společnost může vytvořit servery symbolů pro vaše vlastní produkty a jako mezipaměť pro symboly z externích zdrojů. Symbolový server můžete mít na vlastním počítači. 
      
     **Servery symbolů jiných výrobců**: externích poskytovatelů aplikací Windows a knihovny může poskytnout přístup k symbolovému serveru na Internetu. 
    
     > [!WARNING]
     > Pokud používáte symbolový server jiný než veřejné symbolové servery společnosti Microsoft, ujistěte se, že symbol server a jeho cesty jsou důvěryhodné. Protože soubory symbolů může obsahovat libovolný spustitelný kód, můžete zveřejnit na ohrožení zabezpečení.  

<a name="BKMK_Specify_symbol_locations_and_loading_behavior"></a>
### <a name="configure-symbol-locations-and-loading-options"></a>Nakonfigurujte umístění symbolu a možnosti načítání

Na **nástroje** > **možnosti** > **ladění** > **symboly** stránky, můžete:

- Zadejte a vyberte cesty pro hledání a servery symbolů pro společnost Microsoft, Windows nebo komponenty třetích stran.
- Zadejte moduly provést nebo nechcete, aby ladicí program automaticky načíst symboly.
- Tato nastavení změňte, při aktivním ladění. Zobrazit [spravovat symboly při ladění](#manage-symbols-while-debugging). 
  
**Určení umístění symbolu a možnosti načítání:**

1. V sadě Visual Studio, otevřete **nástroje** > **možnosti** > **ladění** > **symboly** (nebo **Ladění** > **možnosti** > **symboly**).  
   
   ![Nástroje &#45; možnosti &#45; ladění &#45; symboly stránky](media/dbg-options-symbols.png "nástroje &#45; možnosti &#45; ladění &#45; symboly stránky")  
   
2. V části **Symbol umístění souborů (.pdb)**,
   - Použít **Microsoft Symbol Servers**, zaškrtněte políčko.  
   
   - Chcete-li přidat nové umístění serveru symbolů
     1. Vyberte **+** symbol v panelu nástrojů. 
     1. V textovém poli zadejte adresu URL nebo složka cestu serveru symbolů nebo umístění symbolu. Doplňování výrazů vám pomůže najít správný formát.
     
     >[!NOTE]
     >Je prohledán pouze určená složky. Je nutné přidat položky pro všechny podsložky, které chcete vyhledávat.  
   
   - Chcete-li přidat nové umístění serveru symbolů služby VSTS 
     1. Vyberte ![nástroje&#47; možnosti&#47; ladění&#47;nová ikona serveru symbolů](media/dbg_tools_options_foldersicon.png "nástroje &#45; možnosti &#45; ladění &#45; nová ikona serveru symbolů") ikonu na panelu nástrojů. 
     1. V **připojit k serveru symbolů služby VSTS** dialogového okna, vyberte jednu z dostupných symbolové servery a vyberte **připojit**.  
   
   - Chcete-li změnit pořadí načítání umístění symbolů, použijte **Ctrl**+**nahoru** a **Ctrl**+**dolů**, nebo **nahoru** a **dolů** ikony šipky. 
   - Upravit adresu URL nebo cestu, poklepejte na položku, nebo ho vyberte a stiskněte klávesu **F2**.  
   - Odebrat položku, vyberte ho a pak vyberte **-** ikonu.
  
3. (Volitelné) Kvůli zvýšení výkonu načítání symbolů, v části **mezipaměti symbolů v tomto adresáři**, zadejte cestu k místní složce, která může kopírovat symbolové servery symbolů k.  
  
   > [!NOTE]
   > Neumísťujte mezipaměti místního symbolu do chráněné složky, například C:\Windows nebo na podsložku. Místo toho použijte složku pro čtení i zápis.  
  
   > [!NOTE]
   > Pro projekty C++, pokud máte `_NT_SYMBOL_PATH` nastavení proměnné prostředí, přepíše hodnoty nastavené v rámci **mezipaměti symbolů v tomto adresáři**.
  
4. Zadejte moduly, které má ladicí program k načtení z **Symbol umístění souborů (.pdb)** při spuštění.  
  
   -  Vyberte **načíst všechny moduly, kromě vyloučených** (výchozí) pro načtení všech symbolů pro všechny moduly v umístění souboru se symboly, s výjimkou výslovně vyloučit moduly. Chcete-li vyloučit některé moduly, vyberte **zadat vyloučené moduly**, vyberte **+** ikonu, zadejte názvy modulů, které chcete vyloučit a vyberte **OK**.  
  
   -  Chcete-li načíst pouze moduly, které zadáte z umístění souborů se symboly, vyberte **zatížení pouze určité moduly**. Vyberte **zadat zahrnuté moduly**, vyberte **+** ikonu, zadejte názvy modulů, které chcete zahrnout a pak vyberte **OK**. Soubory symbolů pro ostatní moduly nejsou načtené.  
  
5. Vyberte **OK**.

## <a name="other-symbol-options-for-debugging"></a>Další možnosti symbolů pro ladění
  
Můžete vybrat další možnosti symbolu v **nástroje** > **možnosti** > **ladění** > **Obecné** (nebo **ladění** > **možnosti** > **Obecné**):  

- **Načtení exportů DLL (pouze nativní)**  
  
  Načtení knihovny DLL exportní tabulky pro C/C++. Podrobnosti najdete v tématu [exportní tabulky knihovny DLL](#use-dumpbin-exports). Informace o exportu knihovny DLL pro čtení zahrnují nadměrné, tak načítání tabulky exportu je ve výchozím nastavení vypnuta. Můžete také použít `dumpbin /exports` v příkazovém řádku sestavení C/C++.  
  
- **Povolit ladění na úrovni adresy** a **zobrazit zpětný překlad, pokud není k dispozici zdroj**  
  
  Vždy zobrazovat rozebrání, když nebyly nalezeny zdrojové soubory nebo soubory symbolu.  
  
  ![Možnosti &#47; ladění &#47; zpětný překlad Obecné možnosti](../debugger/media/dbg_options_general_disassembly_checkbox.png "možnosti &#47; ladění &#47; zpětný překlad Obecné možnosti")  
  <a name="BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine"></a>
- **Povolit podporu zdrojového serveru**  
  
  Zdrojový Server používá pro ladění aplikace, pokud neexistuje žádný zdrojový kód na místním počítači nebo *PDB* souboru se neshoduje s zdrojový kód. Zdrojový Server přijímá požadavky na soubory a vrací skutečné soubory ze správy zdrojového kódu. Zdrojový Server je spuštěn s použitím knihovny DLL s názvem *srcsrv.dll* číst aplikace *PDB* souboru. *PDB* soubor obsahuje odkazy na úložiště zdrojového kódu, jakož i příkazy pro načtení z úložiště zdrojového kódu. 
  
  Můžete omezit příkazy, které *srcsrv.dll* můžete spustit z aplikace *PDB* souboru uvedením povolených příkazů do souboru s názvem *srcsrv.ini*. Místo *srcsrv.ini* ve stejné složce jako soubor *srcsrv.dll* a *devenv.exe*.  
  
  >[!IMPORTANT]
  >Libovolné příkazy lze vložit do vaší aplikace *PDB* souboru, proto ujistěte se, že chcete změnit jenom příkazy, které chcete provést do *srcsrv.ini* souboru. Žádný pokus o provedení příkazu nejsou v *srcsvr.ini* soubor způsobí, že se zobrazí dialog s potvrzení. Další informace najdete v tématu [upozornění zabezpečení: ladicí program musí spustit nedůvěryhodný příkaz](../debugger/security-warning-debugger-must-execute-untrusted-command.md). 
  >
  >Parametry příkazu nejsou ověřovány, proto buďte s důvěryhodnými příkazy opatrní. Například, pokud je uvedená *cmd.exe* ve vašich *srcsrv.ini*, uživatel se zlými úmysly může zadat parametry na *cmd.exe* , který by ji činilo nebezpečné.  
  
  Vyberte tuto položku a podřízené položky, které chcete. **Povolit zdrojový server pro sestavení částečné důvěryhodnosti (pouze spravované)** a **vždy spouštět nedůvěryhodné příkazy ze zdrojového serveru bez zobrazení výzvy** mohou zvýšit možnost bezpečnostního rizika.  
  
  ![Povolit zdrojový server možnosti](../debugger/media/dbg_options_general_enablesrcsrvr_checkbox.png "DBG_Options_General_EnableSrcSrvr_checkbox")  

## <a name="compiler-symbol-options"></a>Možnosti kompilátoru symbol  

Při sestavení projektu v prostředí Visual Studio IDE se standardem **ladění** konfigurace sestavení, C++ a spravované kompilátory vytvořit příslušné soubory symbolů pro váš kód. Můžete také nastavit možnosti kompilátoru v kódu. 

### <a name="cc-options"></a>Možnosti jazyka C/C++ 

- *VC\<x > pdb* a  *\<Projekt > pdb* soubory
  
  A *PDB* soubor pro C/C++ je vytvořen při sestavení s [příznakem/zi nebo /Zi](/cpp/build/reference/z7-zi-zi-debug-information-format). V [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], [/Fd](/cpp/build/reference/fd-program-database-file-name) možnost názvy *PDB* kompilátor vytvoří soubor. Při vytváření projektu v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] využívání rozhraní IDE **/Fd** je možnost nastavená na vytvoření *PDB* soubor s názvem  *\<Projekt > pdb*.  
  
  Pokud vytváříte aplikaci C/C++ pomocí souboru pravidel a zadáte **/zi** nebo **/zi** bez použití **/Fd**, kompilátor vytvoří dva *PDB*soubory:  
  
  - *VC\<x > pdb*, kde  *\<x >* představuje verzi jazyka Visual C++, například *VC11.pdb* 
    
    *VC\<x > pdb* soubor uchovává všechny informace o ladění pro jednotlivé objektových souborů a je umístěn ve stejném adresáři jako soubor pravidel projektu. Pokaždé, když se vytvoří soubor objektu, kompilátor C/C++ sloučí informace o ladění do *VC\<x > pdb*. Ano, i když každý zdrojový soubor obsahuje společné soubory hlaviček, jako  *\<windows.h >*, funkce typedefs z těchto záhlaví jsou uloženy pouze jednou, namísto do každého souboru objektu. Vložené informace obsahují informace o typu, ale neobsahuje informace o symbolech, jako jsou definice funkce.  
  
  - *\<Projekt > .pdb* 
    
     *\<Projekt > pdb* soubor uchovává všechny informace o ladění pro projektu *.exe* souboru a je *\debug* podadresáře.  *\<Projekt > pdb* soubor obsahuje úplné informace o ladění, včetně funkčních prototypů, nejen informace o typu uvedené v *VC\<x > pdb*. 
  
  Oba *VC\<x > pdb* a  *\<Projekt > pdb* soubory umožňují přírůstkové aktualizace. Linker také vloží cestu k *PDB* soubory *.exe* nebo *.dll* soubor, který vytvoří.  
  
- <a name="use-dumpbin-exports"></a>Tabulky exportu knihovny DLL
  
  Použití `dumpbin /exports` zobrazíte symboly k dispozici v exportní tabulce knihovny DLL. Symbolické informace z tabulky exportu knihovny DLL může být užitečné při práci s Windows zprávy, postupů Windows (WindowProcs), COM objekty, zařazování nebo libovolnou knihovnou DLL nemáte symboly. Symboly jsou k dispozici pro všechny 32bitové systémové knihovny DLL. Volání jsou uvedena v pořadí volání s aktuální funkcí (nejhlouběji vnořených) nahoře. 
  
  V článku `dumpbin /exports` výstupu, můžete zobrazit funkce stejné názvy, včetně jiných než alfanumerických znaků. Zobrazuje názvy přesně funkce je užitečná pro nastavení zarážky na funkci, protože názvy funkcí můžete oříznutí jinde v ladicím programu. Další informace najdete v tématu [dumpbin/EXPORTS](/cpp/build/reference/dash-exports).  
  
### <a name="net-framework-options"></a>Volby rozhraní .NET Framework 
  
Sestavení s **/debug** k vytvoření *PDB* souboru. Můžete vytvářet aplikace pomocí **/Debug: Full** nebo **/debug:pdbonly**. Sestavování s **/Debug: Full** generuje laditelný kód. Sestavování s **/debug:pdbonly** generuje *PDB* soubory, ale negeneruje `DebuggableAttribute` , který instruuje kompilátor JIT, že je k dispozici informace o ladění. Použití **/debug:pdbonly** Pokud chcete generovat *PDB* soubory, které verze sestavení, že nechcete být laditelná. Další informace najdete v tématu [/Debug (možnosti kompilátoru C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option) nebo [/Debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug).  
  
### <a name="web-applications"></a>Webové aplikace  
  
Nastavte *web.config* souboru aplikace ASP.NET na režim ladění. Režim ladění způsobí, že technologie ASP.NET generuje dynamicky generované soubory a umožňuje ladicímu program připojit k aplikaci technologie ASP.NET. Visual Studio nastaví automaticky při spuštění ladění, pokud jste vytvořili projekt ze šablony webových projektů.  

##  <a name="manage-symbols-while-debugging"></a>Správa symbolů při ladění 

Můžete použít **moduly**, **zásobník volání**, **lokální**, **automatické hodnoty**, ani na žádného **Watch** okna pro načtení symboly nebo změnit možnosti symbolů při ladění. Další informace najdete v tématu [poznat více do hloubky pomocí jak ladicí program připojí k vaší aplikaci](../debugger/debugger-tips-and-tricks.md#modules_window).

### <a name="use-the-modules-window"></a>Použití okna moduly

Během ladění, **moduly** okno zobrazuje moduly kódu, ladicí program se zpracuje jako uživatelský kód, nebo vlastní kód a jejich načítání stavu symbolů. Můžete také sledovat stav načítání symbolů, načtěte symboly a změňte možnosti symbolu v **moduly** okna.

**K monitorování nebo změnit možnosti nebo umístění symbolů při ladění:**

1. Chcete-li otevřít **moduly** okně během ladění, **ladění** > **Windows** > **moduly**. 
1. V **moduly** okna, klikněte pravým tlačítkem na **Status symbolu** nebo **soubor symbolů** záhlaví nebo jakýkoli modul. 
1. V místní nabídce vyberte jednu z následujících možností:  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Načtení symbolů**|Zobrazí se pro moduly se přeskočila, nebyl nalezen nebo není načtený symboly. Pokusí se načíst symboly z umístění zadaného na **možnosti** > **ladění** > **symboly** stránky. Pokud soubor symbolů se nenašel nebo nenačetl, spustí **Průzkumníka souborů** umožňující vám zadat nové umístění pro hledání.|  
|**Informace o načítání symbolů**|Zobrazuje umístění načteného souboru se symbolem nebo prohledávána umístění, pokud ladicí program nemůže najít soubor.|  
|**Nastavení symbolů**|Otevře **možnosti** > **ladění** > **symboly** stránku, kde můžete upravit a přidat umístění symbolu.|  
|**Vždy načítat automaticky**|Vybraný symbol soubor přidá do seznamu souborů, které jsou automaticky načteny pomocí ladicího programu.|  

### <a name="use-the-no-symbols-loadedno-source-loaded-pages"></a>Použití stránek Loaded/No zdroje nebyly načteny žádné symboly

Aby ladicí program proniknout do kódu, který nemá symbol nebo zdrojové soubory, které jsou k dispozici několika způsoby:  

-  S vnořením do kódu.  
-  Přepnutí do kódu od zarážky nebo výjimky.  
-  Přepnout na jiné vlákno.  
-  Změna zásobníku dvojitým kliknutím na snímek v **zásobník volání** okna.  
   
Pokud k tomu dojde, ladicí program zobrazí **nebyly načteny žádné symboly** nebo **nenačten žádný zdroj** stránky, které pomáhá vyhledat a načíst potřebné symboly nebo zdroje.  
  
 ![Žádné stránky načíst symboly](../debugger/media/dbg-nosymbolsloaded.png "DBG_NoSymbolsLoaded")  
  
**Použití stránky dokumentu nebyly načteny žádné symboly vám pomůže najít a načíst chybějící symboly:**  
  
-   Chcete-li změnit cesty pro hledání, zvolte nevybranou cestu nebo vyberte **novou cestu** nebo **nová cesta VSTS** a zadejte nebo vyberte novou cestu. Vyberte **načíst** hledání cest a načtení souboru symbolů, pokud je nalezen.  
-   Chcete-li přepsání jakékoli volby symbolu a opakujte hledání cesty, vyberte **Procházet a vyhledat \<executable-name >**. Načtení souboru symbolů, je-li nalezeno, nebo **Průzkumníka souborů** otevře, takže můžete ručně vybrat soubor symbolů.  
-   Chcete-li otevřít **možnosti** > **ladění** > **symboly** stránce **zobrazit nastavení symbolů**.  
-   Chcete-li zobrazit rozebrání v novém okně jednou, vyberte **zobrazit zpětný překlad**, nebo vyberte **dialogové okno Možnosti** nastavení možnosti chcete vždy zobrazit rozebrání, když nebyly nalezeny zdrojové soubory nebo soubory symbolu. 
-   Chcete-li zobrazit umístění, prohledávat a výsledek, rozbalte **informace o načítání symbolů**. 

Pokud ladicí program nalezne *PDB* po spuštění jedné z možností a může načíst zdrojový soubor pomocí informací v souboru *PDB* souboru, zobrazí zdroj. V opačném případě se zobrazí **nenačten žádný zdroj** stránka, která popisuje problém s odkazy na akce, které mohou problém vyřešit.

**Chcete-li přidat cesty hledání zdrojového souboru do řešení:**
  
Můžete zadat umístění ladicí program vyhledává zdrojové soubory a vyloučit konkrétní soubory z vyhledávání.

1. Vyberte řešení v **Průzkumníka řešení**a pak vyberte **vlastnosti** ikonu, stiskněte klávesu **Alt**+**Enter**, nebo Klikněte pravým tlačítkem a vyberte **vlastnosti**.
   
1. Vyberte **zdrojové soubory ladění**.
   
1. V části **adresáře obsahujícího zdrojový kód**, zadejte nebo vyberte umístění zdrojového kódu pro hledání. Použití **nový řádek** ikona Přidat další umístění **nahoru** a **dolů** ikony šipky můžete změnit jejich, nebo **X** ikonu k jejich odstranění.
   
   >[!NOTE]
   >Ladicí program vyhledá pouze zadaný adresář. Je nutné přidat položky pro všechny podadresáře, které chcete prohledávat.
   
1. V části **nehledat tyto zdrojové soubory**, zadejte názvy zdrojových souborů, které chcete vyloučit z hledání. 
   
1. Vyberte **OK** nebo **použít**.


## <a name="see-also"></a>Viz také:  
[Vysvětlení nastavení symbolů Visual Studio a soubory symbolů](https://blogs.msdn.microsoft.com/devops/2015/01/05/understanding-symbol-files-and-visual-studios-symbol-settings/)

[.NET změny vzdáleného načítání symbolů v sadě Visual Studio 2012 a 2013](https://blogs.msdn.microsoft.com/devops/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/)
