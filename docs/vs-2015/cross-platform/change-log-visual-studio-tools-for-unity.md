---
title: Protokol změn (Visual Studio Tools for Unity) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: ea490b7e-fc0d-44b1-858a-a725ce20e396
caps.latest.revision: 14
author: conceptdev
ms.author: crdun
manager: jillfra
ms.openlocfilehash: 751faa1d81ca93fce5f8dfa866327cc8787e27ef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825973"
---
# <a name="change-log-visual-studio-tools-for-unity"></a>Protokol změn (Visual Studio Tools for Unity)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Protokol změn Visual Studio Tools for Unity

## <a name="23"></a>2.3

Vydáno 2016-07-14

### <a name="new-features"></a>Nové funkce

- **Všeobecně**

  - Přidání možnosti pro zakázání protokolů konzoly Unity v seznamu chyb sady Visual Studio.

  - Přidání možnosti umožňující úpravu vygenerovaných vlastností projektu.

- **Ladění**

  - Přidaný text, XML, HTML a vizualizace řetězců JSON.

- **Průvodc**

  - Přidání chybějícího MonoBehaviors.

### <a name="bug-fixes"></a>Opravy chyb

- **Všeobecně**

  - Opravili jsme konflikt s reostřejším, který brání zobrazení ovládacích prvků v nastavení sady Visual Studio.

  - Opravili jsme konflikt s Xamarin, který v některých případech zabránil ladění.

- **Ladění**

  - Opravili jsme problém, který způsobil, že se Visual Studio zablokuje při ladění.

  - Opravili jsme problém se zarážkami funkcí v aplikaci Visual Studio 2015.

  - Opravili jsme několik problémů s hodnocením výrazu.

## <a name="22"></a>2,2

Vydáno 2016-02-04

### <a name="new-features"></a>Nové funkce

- **Průvodc**

  - V průvodci **implementací MonoBehavior** se přidalo inteligentní vyhledávání.

  - Povědomi jste kontext průvodců; například zprávy NetworkBehavior jsou k dispozici pouze při práci s NetworkBehavior.

  - Do průvodců se přidala podpora pro zprávy NetworkBehavior.

- **ROZHRANÍ**

  - Přidání možnosti pro konfiguraci viditelnosti MonoBehavior zpráv.

  - Byly odebrány stránky vlastností sady Visual Studio, které nejsou relevent do projektů Unity.

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Pevné odkazy na UnityEngine a UnityEditor v Unity 4,6.

  - V případě, že Unity běží na OSX, je pevná generace souborů projektu.

  - Bylo vyřešeno zpracování názvů projektů obsahujících hashmark (#) znaků.

  - Omezené vygenerované projekty na C# 4.

- **Ladění**

  - Opravili jsme problém s vyhodnocením výrazu při ladění v rámci korutiny Unity.

  - Opravili jsme problém, který způsobil, že se Visual Studio zablokuje při ladění.

- **ROZHRANÍ**

  - Opravili jsme nekompatibilitu s rozšířením sady Visual Studio na [kartách Studio](https://tabsstudio.com/) .

- **Instalační**

  - Podpora instalace VSTU pro celý počítač (instalovat pro všechny uživatele) vytvořením položek registru HKLM.

  - Opravené problémy s odinstalací VSTU, pokud je stejná verze VSTU nainstalovaná pro více různých verzí sady Visual Studio. Například když byly nainstalovány VSTU **2015** 2.1.0.0 a VSTU **2013** 2.1.0.0.

## <a name="21"></a>2.1

Vydáno 2015-09-08

### <a name="new-features"></a>Nové funkce

- Podpora pro Unity 5,2

### <a name="bug-fixes"></a>Opravy chyb

- Zobrazení položek nabídky na Unity < 4,2

- Když Visual Studio zamkne soubory XML IntelliSense, chybová zpráva se už nezobrazuje.

- Obsluha <\<When Changed>> podmíněných zarážek, pokud podmíněný argument není logická hodnota.

- Pevné odkazy na sestavení UnityEngine a UnityEditor pro aplikace pro Windows Store.

- Opravená chyba při krokování v ladicím programu: nejde krokovat, obecná výjimka.

- Pevné zarážky počtu volání v aplikaci Visual Studio 2015.

## <a name="20"></a>2,0

Vydáno 2015-07-20

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace Unity:**

  - Opravili jsme převod symbolů ladění vytvořených pomocí sady Visual Studio 2015 při importu knihovny DLL a jejích symbolů ladění (PDB).

  - Při importu knihoven DLL a symbolů ladění (PDB) vždy generovat soubory MDB s výjimkou případů, kdy je k dispozici také soubor MDB.

  - Pevné znečištění adresáře projektu Unity s adresářem obj

  - Pevná generace odkazů na System.Xml. Link a System. Runtime. Serialization.

  - Přidání podpory pro více předplatitelů k modulům API pro generování souborů projektu.

  - Generování souborů projektu vždy dokončete i v případě, že je jeden ze souborů, který má být vygenerován, uzamčen.

  - Byla přidána podpora * zástupných znaků ve filtru rozšíření při určení souborů, které mají být zahrnuty do projektu C#.

- **Integrace sady Visual Studio:**

  - Opravili jsme problém s kompatibilitou s nástroji pro zvýšení produktivity.

  - Opraveno generování MonoBehaviors kolem událostí a deleguje deklarace.

- **Ladění**

  - Opravili jsme potenciální zablokování při ladění.

  - Opravili jsme problém, kdy se v určitých rámcích zásobníku nezobrazovaly místní hodnoty.

  - Opravila se kontrola prázdných polí.

## <a name="20-preview-2"></a>2,0 Preview 2
Vydáno 2015-04-02

### <a name="new-features"></a>Nové funkce

- **Průzkumník projektů Unity:**

  - Automaticky přejmenovat třídu při přejmenování souboru v Průzkumníku projektů Unity (viz dialogové okno **Možnosti** ).

  - Automaticky vyberte nově vytvořené skripty v Průzkumníku projektů Unity.

  - Sledujte aktivní skript v Průzkumníku projektů Unity (viz dialogové okno **Možnosti** ).

  - Dual-synchronizujte Průzkumník řešení sady Visual Studio (viz dialogové okno **Možnosti** ).

  - V Průzkumníku projektů Unity přijímají ikony sady Visual Studio.

- **Ladění**

  - Umožňuje vybrat cíl aktivního ladění ze seznamu uložených nebo naposledy použitých cílů ladění (viz dialogové okno **Možnosti** ).

  - Vytvořte zarážky funkcí v metodách MonoBehavior a aplikujte je na více tříd MonoBehavior.

  - Podporuje vytvoření ID objektu v ladicím programu.

  - Podpora počtu přístupů zarážek v ladicím programu.

  - Podpora přerušení v ladicím programu (experimentální. Viz **Možnosti** dialogového okna).

  - Podporuje vytváření objektů a polí při vyhodnocování výrazů v ladicím programu.

  - Podporuje porovnání hodnoty null, pokud jsou výrazy vyhodnocení v ladicím programu.

  - Vyfiltrujte zastaralé členy v oknech kukátka ladicího programu.

- **Instalační**

  - Vyoptimalizovaná registrace rozšíření Visual Studio Tools for Unity.

  - Nainstalujte balíček Visual Studio Tools for Unity pro Unity 5.

- **Dokumentace:** Zvyšte výkon generování dokumentace.

- **Průvodci:** Podpora nových metod MonoBehavior pro Unity 4,6 a Unity 5.

- **Unity:** Vyhledávání nebezpečných příznaků a vlastní definice v souborech. rsp během generování souboru projektu.

- **Uživatelské rozhraní:** Přidání dialogového okna **možností** Visual Studio Tools for Unity v aplikaci Visual Studio.

### <a name="bug-fixes"></a>Opravy chyb

- **Průzkumník projektů Unity:**

  - Po přesunutí nebo přejmenování souborů ze sady Visual Studio Průzkumník řešení aktualizujte Průzkumníka projektů Unity.

  - Zachovat výběry při přejmenování souborů v Průzkumníku projektů Unity.

  - Zabraňuje automatickému rozbalení a sbalení při dvojitém kliknutí na soubory v Průzkumníku projektů Unity.

  - Ujistěte se, že nově vybrané soubory jsou viditelné v Průzkumníku projektů Unity.

- **Ladění**

  - Zabraňuje možnému zablokování sady Visual Studio při vyhodnocování výrazů v ladicím programu.

  - Ujistěte se, že vyvolání metod probíhá ve správné doméně v ladicím programu.

- **Jednot**

  - Opravte umístění UnityVS. OpenFile s Unity 5.

  - Opravte umístění pdb2mdb s Unity 5.

  - Zabránit možné výjimce během generování souboru projektu.

  - Zabraňte možnému zablokování při spuštění Unity v OSX.

  - Obsluhovat vnitřní výjimky.

  - Odeslání protokolů konzoly Unity do seznamu chyb VS.

- **Dokumentace:** Opravte generaci dokumentace pro novou dokumentaci k Unity.

- **Projekt:** V případě potřeby přesuňte a přejmenujte soubory Unity. meta, i ve složkách.

- **Průvodci:** Opravte pořadí parametrů metody MonoBehavior při generování kódu.

- **Uživatelské rozhraní:** Podpora motivů sady Visual Studio pro kontextovou nabídku a ikony.

## <a name="20-preview"></a>2,0 Preview
Vydáno 2014-11-12

### <a name="new-features"></a>Nové funkce

- Podpora pro Visual Studio 2015.

- Zbarvení kódu pro shadery Unity v aplikaci Visual Studio 2015.

- Vylepšená vizualizace hodnot při ladění:

  - Lepší vizualizace pro ArrayListy, seznamy, Zatřiďovacími tabulkami a slovníky.

  - Zobrazit neveřejné členy a statické členy jako kategorie v oknech kukátka a místní zobrazení.

  - Vylepšené zobrazení SerializedProperty Unity pouze k vyhodnocení pole hodnoty platné pro vlastnost.

  - Podpora DebuggerDisplayAttribute – pro třídy a struktury.

  - Podpora DebuggerTypeProxyAttribute –

- Zajistěte vložení metod MonoBehaviour pomocí našich průvodců za účelem respektování konvencí psaní kódu pro uživatele.

- Implementujte podporu pro textové šablony času kompilace v projektech generovaných UnityVS.

- Implementujte podporu pro prostředky ResX v projektech generovaných v UnityVS.

- Podpora otevírání shaderů v aplikaci Visual Studio z Unity.

### <a name="bug-fixes"></a>Opravy chyb

- Vyčistěte sokety před zahájením hry v Unity po spuštění připojení a přehrání v aplikaci Visual Studio. To opravuje některé problémy se stabilitou spojení mezi Unity a VS při použití připojení a přehrávání.

- Vyhněte se volání metod v rozhraní ladicího programu skriptovacího stroje Unity, která jsou náchylná k zablokování Unity. Tím se vyřeší zablokování Unity při připojování ladicího programu.

- Oprava zobrazování zásobníky volání, pokud nejsou k dispozici žádné symboly.

- Neregistrujte zpětné volání protokolu, pokud ho nepotřebujeme.

## <a name="192"></a>1.9.2

Vydáno 2014-10-09

### <a name="new-features"></a>Nové funkce

- Zlepšete detekci přehrávačů Unity.

- Při použití našeho souboru Open je třeba použít Unity číslo řádku a také název souboru.

- Pokud není k dispozici žádná místní dokumentace, je výchozí pro online dokumentaci k Unity.

### <a name="bug-fixes"></a>Opravy chyb

- Opravte možnou chybu Unity při stisknutí zarážky po opětovném načtení domény.

- Opravte výjimky zobrazené v konzole Unity při zavírání naší konfigurace nebo systému Windows po opětovném načtení domény.

- Oprava detekce 64bits Unity v místním prostředí.

- Oprava filtrování třídy MonoBehaviour podle verze Unity v průvodcích.

- Oprava chyby, kdy byly všechny prostředky zahrnuty do souborů projektu, pokud byl filtr rozšíření prázdný

## <a name="191"></a>1.9.1

Vydáno 2014-09-22

### <a name="new-features"></a>Nové funkce

- Optimalizuje zarážku vazby na zdrojová umístění.

- Podpora pro přetížené metody ve vyhodnocení výrazu ladicího programu.

- Podpora pro primitivní typy a typy hodnot ve vyhodnocení výrazu ladicího programu.

- Podpora opětovného vytvoření prostředí místních proměnných v jazyce C# při ladění anonymních metod.

- Odstraňte a přejmenujte soubory. meta při odstraňování nebo přejmenování souborů ze sady Visual Studio.

### <a name="bug-fixes"></a>Opravy chyb

- Oprava zpracování motivů sady Visual Studio. Dříve se můžou dialogy v černém motivu zobrazovat jako prázdné.

- Oprava Unity zamrznutí při připojení ladicího programu při opětovné kompilaci Unity.

- Opravovat zarážky při ladění vzdálených editorů nebo přehrávačů kompilovaných v jiném systému.

- Opravte možnou chybu sady Visual Studio, když je dosaženo zarážky.

- Opravit vazbu zarážek, aby se zabránilo zarážekm zobrazeným jako uvolněné.

- Opravte zpracování proměnné s rozsahem v ladicím programu, aby nedocházelo k živým proměnným, které se objeví mimo rozsah.

- Opravte vyhledávání statických členů ve vyhodnocení výrazu ladicího programu.

- Opraví zobrazování typů ve vyhodnocování výrazu ladicího programu pro zobrazení statických polí a vlastností.

- Oprava generování řešení, pokud názvy projektů Unity obsahují speciální znaky, které Visual Studio neumožňuje (připojit problém #948666).

- Opravte Visual Studio Tools balíček Unity tak, aby okamžitě zastavil posílání událostí konzoly, když je možnost nezaškrtnutá (připojit problém #933357).

- Oprava detekce odkazů pro správné opětovné vygenerování odkazů na nová rozhraní API, jako je UnityEngine. UI v projektech generovaných UnityVS.

- Oprava instalačního programu tak, aby vyžadovala ukončení sady Visual Studio před instalací, aby nedocházelo k poškozeným instalacím

- Opravte instalační program a nainstalujte referenční sestavení Unity jako správnou samostatnou součást sdílenou mezi všemi verzemi VSTU.

- Opravte otevírání skriptů pomocí VSTU ve verzích Unity v 64 bitech.

## <a name="19"></a>1,9

Vydáno 2014-07-29

### <a name="new-features"></a>Nové funkce

- V okně připojit ladicí program Unity přidejte možnost zadat vlastní IP adresu a port pro ladění.

- Přidejte možnost konfigurace pro nastavení Unity pro spuštění na pozadí nebo ne.

- Přidejte možnost konfigurace, která generuje soubory řešení a projektu nebo pouze soubory projektu.

- Cíl spuštění: vyberte možnost připojit se k Unity nebo připojit k Unity a hrát.

- Zobrazení multidimenzionálních polí v ladicím programu.

- Zpracujte nové porty ladění přehrávače Unity.

- Zpracování odkazů na nová sestavení Unity, jako jsou například sestavení GUI 4,6.

- Dekonstruuje uzávěry pro správné zobrazení místních proměnných při ladění.

- Dekonstruuje proměnné vygenerované iterátory do argumentů při ladění.

- Zachovat stav Průzkumníka projektů Unity po opětovném načtení projektu

- Přidejte příkaz pro synchronizaci Průzkumníka projektů Unity s aktuálním dokumentem.

### <a name="bug-fixes"></a>Opravy chyb

- Opravte podmíněné zarážky, jejichž podmínky jsou nastaveny před spuštěním ladicího programu.

- Opravte odkazy na UnityEngine, aby se předešlo upozorněním.

- Opravte verze analýzy pro beta verze Unity.

- Opravte problém, kdy se proměnné nezobrazí v okně místní proměnné při povýšení zarážky nebo krokování.

- Opravovat popisy proměnných v Visual Studio 2013.

- Oprava generování dokumentace technologie IntelliSense pro Unity 4,5.

- Opravte komunikaci Unity/Visual Studio po opětovném načtení domény (play/stop v Unity).

- Oprava zpracování částí motivů sady Visual Studio.

> [!IMPORTANT]
> C# je převládající jazyk v ekosystému Unity – nové ukázkové prostředky jsou v jazyce C#, dokumentace Unity ve výchozím nastavení bude C# – odebrali jsme naši základní podporu pro UnityScript a Boo, abyste se lépe zaměřili na prostředí C#. V důsledku toho jsou řešení VSTU nyní jenom C# a je mnohem rychlejší načíst.

## <a name="182"></a>1.8.2

Vydáno 2014-01-07

### <a name="new-features"></a>Nové funkce

- Řešení problému v síťové vrstvě skriptovacího stroje v Unity na Mavericks pro vzdálené zjišťování editorů

- Zpracujte nové porty, aby se zjistily vzdálené přehrávače Unity.

- Odkaz na sestavení UnityEngine specifické pro aktuální cíl sestavení.

- Přidejte nastavení pro filtrování souborů, které se mají zahrnout do vygenerovaných projektů.

- Přidáním nastavení zakážete odesílání protokolů konzoly do seznamu chyb sady Visual Studio. To je užitečné, pokud používáte PlayMaker nebo konzolu pro, protože pro příjem protokolů konzoly může být v Unity k dispozici pouze jedno zpětné volání.

- Přidáním nastavení zakážete generování symbolů ladění MDB. To je užitečné, pokud vytváříte databázi MDB sami.

### <a name="bug-fixes"></a>Opravy chyb

- Opravte regresi, když soubory otevřené v nástroji VS z Unity >= 4,2 ztratí technologii IntelliSense.

- Opravte naše dialogy VS a zpracujte vlastní motivy.

- Opravte zavření kontextové nabídky UPE.

- Zabraňuje selhání v Unity, když je sestavení specifické pro konkrétní verzi, pokud není synchronizováno.

## <a name="181"></a>1.8.1

Vydáno 2013-11-21

### <a name="new-features"></a>Nové funkce

- Upravili jsme průvodce MonoBehaviour pomocí rozhraní API Unity 4,3.

- Průvodci MonoBehaviour filtruje rozhraní API Unity v závislosti na používané verzi.

- Přidejte odkaz na System.Xml. LINQ na projekty pro Unity > 4,1.

- Prettify naše volání ladění. log, aby neobsahovala začátek trasování zásobníku ve zprávě.

### <a name="bug-fixes"></a>Opravy chyb

- Opravili jsme chybu, kdy by došlo ke konfliktu s výchozím zpracováním souborů JavaScriptu v aplikaci Visual Studio.

- Opravili jsme v reálném čase bílý pixel, který se zobrazuje v sadě VS.

- Pevné odstranění sestavení UnityVS. VersionSpecific, pokud je označeno jako jen pro čtení, správcem SCM.

- Při vytváření soketů v balíčku UnityVS byly opraveny výjimky.

- Opravili jsme chybu v aplikaci Visual Studio při načítání burzovních imagí ze sestavení sady Visual Studio.

- Opravili jsme chybu při generování UnityVS. VersionSpecific pro zdrojová sestavení Unity.

- Opravili jsme možné zablokování při otevírání soketu v balíčku Unity.

- Opravili jste zpracování projektu Unity pomlčkou (-) ve svém názvu.

- Pevné otevření skriptů z Unity Nepleťe se s pořadím ALT + TAB pro Unity 4,2 a vyšší.

## <a name="180"></a>1.8.0

Vydáno 2013-09-24

### <a name="new-features"></a>Nové funkce

- Výrazně se vylepšila rychlost připojení ladicího programu.

- Automatické zpracování navigace na soubor a řádek v Unity 4,2 a vyšších.

- Podmíněné zarážky.

- Generátor souborů projektu nyní zpracovává šablony T4.

- Aktualizujte Průvodce MonBehavior novými rozhraními API.

- Dokumentace IntelliSense v jazyce C# pro typy Unity

- Vyhodnocení aritmetických a logických výrazů.

- Lepší zjišťování vzdálených editorů pro vzdálené ladění ve verzi Preview

### <a name="bug-fixes"></a>Opravy chyb

- Opravili jsme chybu, kdy by bylo vlákno v VS. po odpojení ladicího programu navráceno.

- Opravili jsme bílé pixely, které se zobrazují v VS.

- Opravili jste zpracování kliknutí na ikonu stavového řádku.

- Opravila se generování odkazů pomocí sestavení ve složkách modulů plug-in.

- V případě výjimek se opravilo vytváření soketů z balíčku UnityVS.

- Opravili jsme detekci nových verzí UnityVS.

- Opravte výzvu správce licencí po vypršení platnosti licence.

- Opravili jsme chybu, která by mohla vykreslit seznam procesů v okně připojit ladicí program k procesu VS.

- Pevné měnící se hodnoty logických hodnot v místním zobrazení.

## <a name="122"></a>1.2.2

Vydáno 2013-07-09

### <a name="bug-fixes"></a>Opravy chyb

- Zpracujte plně kvalifikované názvy v vyhodnocovacím filtru výrazů.

- Opravili jsme zablokování související s zpracováním výjimek, kde skriptovací modul Unity posílá nesprávná StackFrame data.

- Pevný proces sestavení pro webové cíle.

- Opravili jsme chybu, která by mohla nastat při spuštění sady Visual Studio a odstraněný soubor byl v seznamu souborů, které se mají otevřít při spuštění.

- Opravili UnityVS. OpenFile pro zpracování neskriptových souborů, podobně jako kompilovaných shaderů.

- Nyní odkazujeme na boo. lang a UnityScript. lang ze všech projektů v jazyce C#.

- Pevná generace odkazů v projektech, pokud projekt obsahuje speciální znaky.

- Alternativní řešení problém, kdy volání metody do uvolněných projektů spustí více NullReferenceException MessageBox.

- Vyřešilo se zpracování sestavení beta verze Unity 4,2.

## <a name="121"></a>1.2.1

Vydáno 2013-04-09

### <a name="bug-fixes"></a>Opravy chyb

- Pevné místní nasazení sestavení Unity pro dokončení kódu v případě chyby v/v (například souborů jen pro čtení nebo souborů uzamčených aplikací Visual Studio).

- Opravili jsme regresi, kdy otevření skriptu z Unity se nezaměřuje na soubor, pokud už je otevřený v aplikaci Visual Studio.

- Opravili jsme problém s výkonem nového zpracování výjimek.

- Pevná vazba zarážek v některých externích knihovnách DLL.

## <a name="12"></a>1,2

Vydáno 2013-03-25

### <a name="new-features"></a>Nové funkce

- Výrazně se vylepšila rychlost připojení ladicího programu.

- Optimalizované Průzkumník projektů Unity pro větší projekty.

- Dodržet nastavení sady Visual Studio pro přerušení (nebo ne) na ošetřených a neošetřených výjimkách.

- Dodržet nastavení sady Visual Studio pro volání ToString na lokální proměnné.

- Přidat novou nabídku ladění-> připojit ladicí program Unity, který můžete použít k ladění přehrávačů Unity.

- Zachovejte vlastní projekty přidané do řešení UnityVS při generování souboru řešení.

- Přidat novou klávesovou zkratku CTRL + ALT + M-> CTRL + H k zobrazení dokumentace Unity pro funkci Unity nebo člen na pozici blikajícího kurzoru.

- Při kompilování ze sady Visual Studio Vezměte v úvahu soubory odezvy kompilátoru (RSP).

- Dekonstruovat typy generované kompilátorem pro zobrazení proměnných při ladění metod generátoru.

- Zjednodušte vzdálené ladění tím, že odeberete nutnost konfigurace sdílené složky na Unity. Teď stačí mít přístup k vašemu projektu Unity z Windows.

- Nainstalujte vlastní profil Unity jako standardní cílový profil .NET. Tím se opraví všechny falešně pozitivních hodnot, které může reostřejšíer zobrazit.

- Vypracujte chybu skriptovacího modulu Unity, aby se ladicí program nepřerušil na nesprávně registrovaných vláknech.

- Znovu Pracujte s otevřeným souborem, abyste se vyhnuli konfliktu časování ve VS, kde je to v případě, že je to v případě, že je to v případě, že je možné soubory otevřít, a při selhání

- UnityVS nyní žádá o aktualizaci buildu, když VS sestaví projekt, a ne pro ukládání souboru.

### <a name="bug-fixes"></a>Opravy chyb

- Pevný vlastní profil .NET

- Opravili jsme integraci IT. tím se vyřeší naše problémy s tmavým motivem VS 2012.

- Pevná zkratka rychlého chování ve VS 2012.

- Opravili jsme problém krokování, ke kterému může dojít při ladění a Nehlavní vlákno by mělo zarážku.

- Opravili UnityScript a Boo dokončování typu aliasy, například int.

- Opravila se výjimka při zápisu nového řetězce UnityScript nebo boo.

- Pevné výjimky v nabídkách Unity, pokud nebylo načteno řešení.

- Opravená chyba UVS-48: psaním dvojitých uvozovek se někdy vyprodukuje chyba a přeruší se všechny funkce (dokončování kódu, zvýrazňování syntaxe atd.).

- Opravená chyba UVS-46: duplicitní otevřený soubor skriptu (UnityScript) při kliknutí na Seznam chyb sady Visual Studio.

- Opravená chyba UVS-42: logo konektivity Unity ve stavovém řádku nezpracovává události myši v sadě VS 2012.

- Opravená chyba UVS-44: CTRL + SHIFT + Q není v sadě VS 2012 pro rychlé třídy MonoBehaviour k dispozici.

- Opravená chyba UVS-40: vybrané položky v Průzkumníku projektů Unity jsou nečitelný, pokud je okno neaktivní v motivu VS2012 "tmavého".

- Opravená chyba UVS-39: vydejte řetězce s řídicími řetězci tokenizací.

- Opravená chyba UVS-35: při kontrole proměnných vyvolat ToString pro objekty.

- Opravená chyba UVS-27: příkaz goto symbol Window nekonzistence s motivem "tmavého" v VS2012.

- Opravená chyba UVS-11: národní prostředí v korutinách.

## <a name="11--beta-release"></a>1,1 – beta verze
Vydáno 2014-10-09

## <a name="1013"></a>1.0.13
Vydáno 2013-01-21

### <a name="bug-fixes"></a>Opravy chyb

- Opravili jsme zamrznutí sady Visual Studio, ke kterému může dojít, pokud cílový laděného procesu posílá neplatné události vlákna. K tomu obvykle dochází při ladění vzdálené Unity v OSX.

- Opravili jsme uzamčení sady Visual Studio, které by mohlo nastat, pokud výjimka ukončí ladicí program.

- Opravili jsme naše MonoBehavior pomocníka v případě, že je C# MonoBehavior v oboru názvů.

- Pevné popisy pro ladicí program pro UnityScript v aplikaci Visual Studio 2012.

- Fixní generování projektu, když se z Unity změní jenom konstanty ladění.

- Pevná navigace na klávesnici v Průzkumníku projektů Unity.

- Opravená UnityScript zabarvení pro řetězce s řídicími znaky.

- Opravili jsme náš otevřený soubor k odhadu lepší název projektu, pokud se používá mimo Unity. To je nezbytné v případě, že uživatel používá třetí část souboru Open v Unity, která deleguje UnityVS.

- Bylo vyřešeno zpracování dlouhých zpráv odesílaných z Unity do UnityVS. Než to bude, dlouhé zprávy by mohly způsobit selhání naší části zasílání zpráv v UnityVS. V důsledku toho je někdy UnityVS otevřít soubor z Unity.

## <a name="1012"></a>1.0.12
Vydáno 2013-01-03

### <a name="bug-fixes"></a>Opravy chyb

- Pevné zamrznutí sady Visual Studio, ke kterým může dojít, když aplikace Visual Studio odstranila zarážku.

- Opravili jsme chybu, kdy některé zarážky nedosáhly po rekompilovaných herních skriptech Unity.

- Opravili jste ladicí program o správné informování sady Visual Studio, pokud byly zarážky bez vazby.

- Opravili jsme problém s registrací, který by mohl ladicí program sady Visual Studio zabránit ladění nativních programů.

- Opravili jsme výjimku, která by mohla nastat při vyhodnocování výrazů UnityScript a boo.

- Opravili jsme regresi, kdy změna úrovně rozhraní .NET API v Unity neaktivuje aktualizaci souborů projektu.

- Opravili jsme rozhraní API porucha, kde se v obslužné rutině zpětného volání protokolu nepovedlo zúčastnit kód uživatele.

## <a name="1011"></a>1.0.11
Vydáno 2012-11-28

### <a name="new-features"></a>Nové funkce

- Oficiální podpora Unity 4.

- Manipulace se skripty z Průzkumníka projektů Unity.

- Integrace v aplikaci Visual Studio – přejít na okno.

- Analýza informační zprávy konzoly, aby se kliknutí na Seznam chyb převzala na první stackframe se symboly.

- Přidejte [rozhraní API](../cross-platform/customize-project-files-created-by-vstu.md) , aby se uživatel mohl zúčastnit generování projektu.

- Přidejte [rozhraní API](../cross-platform/share-the-unity-log-callback-with-vstu.md) , aby se uživatel mohl zúčastnit v LogCallback.

### <a name="bug-fixes"></a>Opravy chyb

- Pevná regrese na pozadí Průzkumníka projektů Unity v aplikaci Visual Studio 2012.

- Fixní generování projektů pro uživatele plného profilu .NET.

- Fixní generování projektu pro uživatele cílového webu.

- Pevné generování projektu, které zahrnuje symboly ladění a trasování, jako Unity.

- Pevná Chyba při použití speciálních znaků v našem okně goto symbol.

- Opravená chyba, pokud nemůžeme vložit naši ikonu do stavového řádku sady Visual Studio.

## <a name="1010"></a>1.0.10
Vydáno 2012-10-09

### <a name="bug-fixes"></a>Opravy chyb

- Opravili jsme pozadí Průzkumníka projektů Unity v aplikaci Visual Studio 2010.

- Opravili jsme zablokování sady Visual Studio, ke kterému může dojít, když se UnityVS pokusil připojit ladicí program k Unity, jehož rozhraní ladicího programu předtím selhalo.

- Opravili jsme zablokování sady Visual Studio, ke kterému může dojít, když byla nastavena zarážka a dojde k opětovnému načtení domény AppDomain.

- Opravili jsme, jak jsou sestavení načítána z Unity, aby nedošlo k zamykání souborů a Zaměňujte proces sestavení Unity.

## <a name="109"></a>1.0.9

Vydáno 2012-10-03

### <a name="bug-fixes"></a>Opravy chyb

- Fixní generování projektu, když projekt Unity obsahuje skutečné prostředky JavaScriptu.

- Opravené zpracování chyb ve vyhodnocení výrazu.

- Opravili jsme nastavení nových hodnot na pole hodnotových typů.

- Pevné možné vedlejší účinky při najetí myší na výrazy z editoru kódu

- Opravili jsme, jak se hledají typy v načtených sestaveních pro vyhodnocení výrazu.

- Opravená chyba UVS-21: vyhodnocení přiřazení u objektů Unity nemá žádný vliv.

- Opravená chyba UVS-21: neplatný ukazatel při vyhodnocování volání metody do rozhraní API pro matematiku Unity.

## <a name="108"></a>1.0.8

Vydáno 2012-09-26

### <a name="bug-fixes"></a>Opravy chyb

- Opravili jsme, jak náš otevřený skript získal cestu k projektu, abyste měli jistotu, že je možné otevřít jak Visual Studio, tak i skripty.

- Opravili jsme chybu se zarážkami vytvořenými během spuštěné relace ladění, která by mohla způsobit, že se Visual Studio zamkne.

- Opraveno, jak je UnityVS registrována v aplikaci Visual Studio 2010.

## <a name="107"></a>1.0.7

Vydáno 2012-09-14

### <a name="new-features"></a>Nové funkce

- Podpora sady Visual Studio 2012.

### <a name="bug-fixes"></a>Opravy chyb

- Pevná generace souborů projektů Editor a modulů plug-in, které odpovídají chování Unity.

- Opravili jsme překlad symbolů. pdb na Unity 4.

> [!IMPORTANT]
> Kvůli podpoře sady Visual Studio 2012 jsme museli přejmenovat pár souborů a trochu se přesunout. Balíček UnityVS pro import Unity se teď jmenuje buď UnityVS 2010 nebo UnityVS 2012, pro Visual Studio 2010 a Visual Studio 2012. Tato verze také vyžaduje, aby se soubory projektu UnityVS znovu vygenerovaly.

## <a name="106---internal-build"></a>1.0.6 – interní sestavení
Vydáno 2012-09-12

## <a name="105"></a>1.0.5

Vydáno 2012-09-10

### <a name="bug-fixes"></a>Opravy chyb

- Pevná generace souborů projektu, když skripty nebo shadery měly neplatný znak XML.

- V případě, že byla služba Unity připojena k serveru assetů, byla vyřešena detekce instancí Unity. Aktivované chyby při otevírání souborů z Unity a automatického připojení ladicího programu sady Visual Studio.

## <a name="104"></a>1.0.4

Vydáno 2012-09-05

### <a name="new-features"></a>Nové funkce

- Automatický převod symbolů ladění v Unity

    Pokud máte sestavení .NET. dll s přidruženým souborem. pdb ve složce assets, jednoduše znovu importujte sestavení a UnityVS převede soubor. pdb na soubor symbolů ladění, který skriptovací stroj Unity považuje za a vy budete moci do sestavení .NET krokovat z UnityVS.

### <a name="bug-fixes"></a>Opravy chyb

- Při ladění došlo k UnityVS chybě, která způsobila výjimky vyvolané metodami nebo vlastnostmi v Unity.

## <a name="103"></a>1.0.3

Vydáno 2012-09-04

### <a name="new-features"></a>Nové funkce

- Nová možnost konfigurace, která zakáže použití UnityVS k otevření souborů z Unity.

### <a name="bug-fixes"></a>Opravy chyb

- Pevné generování odkazů na UnityEditor pro needitorované projekty.

- Pevná definice UNITY_EDITOR symbol pro needitorované projekty

- Opravená náhodná chyba oproti chybě způsobená naším vlastním stavovým řádkem.

## <a name="102"></a>1.0.2

Vydáno 2012-08-30

### <a name="bug-fixes"></a>Opravy chyb

- Opravený konflikt s ladicím programem PythonTools

- Pevné odkazy na mono. Cecil.

- Opravili jsme chybu v tom, jak se v Unity načetla sestavení do skriptů s Unity 4 B7.

## <a name="101"></a>1.0.1

Vydáno 2012-08-28

### <a name="new-features"></a>Nové funkce

- Podpora Preview pro Unity 4,0 beta.

### <a name="bug-fixes"></a>Opravy chyb

- Opravili jsme kontrolu vlastností, které vyvolává výjimky.

- Při kontrole objektů je pevně navzestupné na základní objekty.

- Opraven prázdný rozevírací seznam pro kurzor v průvodci MonoBehavior.

- Pevné dokončení pro knihovnu DLL ve složce assetů pro UnityScript a boo.

## <a name="10--initial-release"></a>1,0 – počáteční verze
Vydáno 2012-08-22
