---
title: Protokol změn (Visual Studio Tools for Unity) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea490b7e-fc0d-44b1-858a-a725ce20e396
caps.latest.revision: 14
author: conceptdev
ms.author: crdun
manager: ghogen
ms.openlocfilehash: f21a5491d1b0e23bff90ce0105b81eb6291ac7e5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807189"
---
# <a name="change-log-visual-studio-tools-for-unity"></a>Protokol změn (Visual Studio Tools for Unity)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Protokol změn Visual Studio Tools for Unity.

## <a name="23"></a>2.3
 Vydáno 2016-07-14

### <a name="new-features"></a>Nové funkce

-   **Obecné:**

    -   Přidat možnost zakázat Unity konzole protokoly v seznamu chyb sady Visual Studio.

    -   Přidat možnost povolit vlastnosti vygenerované projekt má být upraven.

-   **Ladicí program:**

    -   Přidání textu, XML, HTML a JSON řetězec vizualizéry.

-   **Průvodci:**

    -   Přidat chybějící MonoBehaviors.

### <a name="bug-fixes"></a>Opravy chyb

-   **Obecné:**

    -   Oprava ke konfliktu s ReSharper, který zabránil ovládacích prvků uvnitř sady Visual Studio nastavení zobrazení.

    -   Opravili jsme konflikt s využitím kódu Xamarin, která bránila v některých případech ladění.

-   **Ladicí program:**

    -   Opravili jsme problém, která způsobila zablokování při ladění sady Visual Studio.

    -   Opravili jsme problém s zarážky funkcí v sadě Visual Studio 2015.

    -   Opravili jsme několik výrazů vyhodnocení problémů.

## <a name="22"></a>2.2
 Vydáno 2016-02-04

### <a name="new-features"></a>Nové funkce

-   **Průvodci:**

    -   Přidání inteligentní vyhledávání v **implementace MonoBehavior** průvodce.

    -   Vytvořit průvodce kontextu vědět; například NetworkBehavior zprávy jsou k dispozici pouze při práci s NetworkBehavior.

    -   Přidání podpory pro NetworkBehavior zprávy v průvodci.

-   **UŽIVATELSKÉ ROZHRANÍ:**

    -   Přidat možnost konfigurovat, zda se MonoBehavior zprávy.

    -   Odebrání stránky vlastností sady Visual Studio, které nejsou požadovanou do projektů Unity.

### <a name="bug-fixes"></a>Opravy chyb

-   **Generování projektu:**

    -   Pevné odkazy na UnityEngine a UnityEditor na 4.6 v Unity.

    -   Oprava generování souborů projektu při spuštění Unity na os x.

    -   Oprava zpracování názvy projektů obsahující znaky hashmark (#)

    -   S omezením pomocí specifikátoru generované projekty jazyka C# 4.

-   **Ladicí program:**

    -   Opravili jsme problém s vyhodnocování výrazů při ladění v korutině Unity.

    -   Opravili jsme problém, která způsobila zablokování při ladění sady Visual Studio.

-   **UŽIVATELSKÉ ROZHRANÍ:**

    -   Oprava nekompatibility s [karty Studio](https://tabsstudio.com/) rozšíření sady Visual Studio.

-   **Instalační program:**

    -   Tím, že vytvoříte položky registru HKLM podporují instalaci celý počítač vstu (instalace pro všechny uživatele).

    -   Opravené problémy odinstalaci VSTU při instalaci stejnou verzi VSTU pro několik různých verzí sady Visual Studio. Například když VSTU **2015** 2.1.0.0 a VSTU **2013** 2.1.0.0 oba nainstalovaly.

## <a name="21"></a>2.1
 Vydáno 2015-09-08

### <a name="new-features"></a>Nové funkce

-   Podpora pro Unity 5.2

### <a name="bug-fixes"></a>Opravy chyb

-   Zobrazit položky nabídky na Unity < 4.2

-   Chybová zpráva zmizí při uzamčení soubory intellisense XML sady Visual Studio.

-   Zpracování <\<při změně >> podmíněné zarážky, pokud podmíněné argument není logická hodnota.

-   Pevné odkazy na sestavení UnityEngine a UnityEditor pro aplikace Windows Store.

-   Oprava chyby při krokování v ladicím programu: nelze krokovat obecnou výjimku.

-   Pevný počet průchodů zarážky v sadě Visual Studio 2015.

## <a name="20"></a>2.0
 Vydáno 2015-07-20

### <a name="bug-fixes"></a>Opravy chyb

-   **Integrace Unity:**

    -   Opravili jsme převod symboly ladění, které jsou vytvořené pomocí sady Visual Studio 2015, při importu knihovny DLL a jeho ladění symbolů (PDB).

    -   Vždy generovat soubory MDB při importu knihovny DLL a jeho ladění symbolů (PDB), s výjimkou případů, kdy se soubor MDB také poskytuje.

    -   Oprava znečištění adresáře Unity projektů s adresářem obj.

    -   Oprava generování odkazů na System.Xml.Link a System.Runtime.Serialization.

    -   Přidání podpory pro několik předplatitelů do generování souboru projektu rozhraní API zavěšení.

    -   Generování souboru vždy dokončený projekt i v případě, že jeden ze souborů, které chcete vygenerovat je.

    -   Přidání podpory pro * zástupné znaky v rozšíření filtrování při určování souborů, které mají být zahrnuty v projektu C#.

-   **Integrace se sadou Visual Studio:**

    -   Opravili jsme potíže s kompatibilitou se nástrojů Productivity Power Tools.

    -   Opravili jsme generování MonoBehaviors kolem deklarace události a delegáti.

-   **Ladicí program:**

    -   Opravili jsme potenciální zablokování při ladění.

    -   Opravili jsme problém, kde by lokální proměnné zobrazí v některých rámců zásobníku.

    -   Oprava kontroly prázdné pole.

## <a name="20-preview-2"></a>2.0 preview 2
 Vydáno 2015-04-02

### <a name="new-features"></a>Nové funkce

-   **Unity Project Exploreru:**

    -   Automatické přejmenování tříd při přejmenování souboru v Průzkumníku projektů Unity (viz **možnosti** dialogového okna).

    -   Automatický výběr nově vytvořený skripty v Průzkumníku projektů Unity.

    -   Sledování aktivních skriptů v Průzkumníku projektů Unity (viz **možnosti** dialogového okna).

    -   Duální synchronizovat Průzkumníku řešení sady Visual Studio (viz **možnosti** dialogového okna).

    -   Osvojte si ikony sady Visual Studio v Průzkumníku projektů Unity.

-   **Ladicí program:**

    -   Vyberte cíl active ladění ze seznamu cílů ladění uložené nebo naposledy použitých (viz **možnosti** dialogového okna).

    -   Vytvořit zarážky funkcí na MonoBehavior metody a použít je u více MonoBehavior tříd.

    -   Ujistěte se, ID objektu se podporují v ladicím programu.

    -   Podpora v ladicím programu počet průchodů zarážky.

    -   Podpora přerušení na výjimky v ladicím programu (experimentální. Zobrazit **možnosti** dialogového okna).

    -   Podporuje vytváření objekty a pole při vyhodnocení výrazů v ladicím programu.

    -   Podporuje porovnání null při vyhodnocování výrazů v ladicím programu.

    -   Zastaralé členy v oknech ladicího programu Sledování filtru

-   **Instalační program:**

    -   Optimalizované Visual Studio Tools for Unity registrace rozšíření.

    -   Instalace Visual Studio Tools pro Unity balíček pro Unity 5.

-   **Dokumentace ke službě:** zlepšení výkonu při generování dokumentace.

-   **Průvodce:** podporu nových MonoBehavior metod 4.6 v Unity a Unity 5.

-   **Unity:** nebezpečné příznaků vyhledávání a vlastních definuje v soubory .rsp při generování souboru projektu.

-   **Uživatelské rozhraní:** přidali Visual Studio Tools for Unity **možnosti** dialogového okna v sadě Visual Studio.

### <a name="bug-fixes"></a>Opravy chyb

-   **Unity Project Exploreru:**

    -   Aktualizujte Průzkumníka projektů Unity po soubory se přesunout nebo přejmenovat v Průzkumníku řešení sady Visual Studio.

    -   Zachovat výběr při přejmenování souborů v Průzkumníku projektů Unity.

    -   Zakázat automatické rozbalovat a sbalovat se soubory dvojité kliknutí v Průzkumníku projektů Unity.

    -   Ujistěte se, že nově vybrané soubory jsou viditelné v Průzkumníku projektů Unity.

-   **Ladicí program:**

    -   Zabraňte možný výskyt sady Visual Studio zablokovat při vyhodnocení výrazů v ladicím programu.

    -   Ujistěte se, že volání metod provádělo na správné domény v ladicím programu.

-   **Unity:**

    -   Opravte umístění UnityVS.OpenFile pomocí Unity 5.

    -   Opravte umístění pdb2mdb pomocí Unity 5.

    -   Zabraňte možnou výjimkou při generování souboru projektu.

    -   Zabránit možný zablokování při spuštění Unity na os x.

    -   Zpracování interních výjimek.

    -   Odeslat protokoly konzoly s Unity v seznamu chyb VS.

-   **Dokumentace ke službě:** opravte generování dokumentace pro nové dokumentace k unity.

-   **Projekt:** přesunutí a přejmenování souborů .meta Unity v případě potřeby i ve složkách.

-   **Průvodce:** opravte pořadí parametrů metody MonoBehavior při generování kódu.

-   **Uživatelské rozhraní:** motivů aplikace Visual Studio podporu pro místní nabídky a ikony.

## <a name="20-preview"></a>2.0 preview
 Vydáno 2014-11-12

### <a name="new-features"></a>Nové funkce

-   Podpora pro sadu Visual Studio 2015.

-   Zabarvení kódu pro shadery Unity v sadě Visual Studio 2015.

-   Lepší vizualizace hodnot při ladění:

    -   Lepší vizualizace pro instance třídy ArrayList, seznamy, zatřiďovacích tabulkách a slovníky.

    -   Zobrazit jako kategorií v kukátka a místních zobrazeních neveřejné členy a statické členy.

    -   Vylepšené zobrazení SerializedProperty Unity a pouze vyhodnotit pole hodnotu pro vlastnost platná.

    -   Debuggerdisplayattribute – podpora pro třídy a struktury.

    -   Debuggertypeproxyattribute – podpora.

-   Ujistěte se, vložení metody třídy MonoBehaviour. pomocí naší průvodců dodržovat konvence psaní kódu uživatele.

-   Implementovat podporu pro kompilaci textové šablony v projektech UnityVS vygenerována.

-   Podpora prostředků ResX implementovat v projektech UnityVS vygenerována.

-   Podpora otevírání shadery v sadě Visual Studio z Unity.

### <a name="bug-fixes"></a>Opravy chyb

-   Vyčištění sockets před zahájením hry v Unity po připojení a Play se aktivovalo v sadě Visual Studio. To řeší některé problémy se stabilitou připojení mezi Unity a VS při použití připojení a Play.

-   Vyhněte se volání metody v Unity a skriptovací stroj rozhraní ladicího programu, které jsou náchylné k zablokování Unity. To řeší Unity zablokování při připojování ladicího programu.

-   Opravte, když není k dispozici žádné symboly zobrazení zásobníky volání.

-   Pokud nemusíme neregistrujte zpětné volání protokolu.

## <a name="192"></a>1.9.2
 Vydáno 2014-10-09

### <a name="new-features"></a>Nové funkce

-   Vylepšení detekce hráči Unity.

-   Při používání našich otevírající soubor, ujistěte se, Unity předat číslo řádku, jakož i název souboru.

-   Pokud neexistuje žádná místní dokumentace výchozí si online dokumentaci k Unity.

### <a name="bug-fixes"></a>Opravy chyb

-   Při dosažení zarážky po znovu načíst domény byla opravena chyba vyskytující potenciální Unity.

-   Oprava výjimky uvedené v konzole nástroje Unity při uzavření naše konfigurace nebo o časových obdobích, po domény znovu načíst.

-   Opravte detekce 64bitový Unity spuštěná místně.

-   Oprava na Unity verze v průvodcích závislé filtrování toho třídy Monobehaviour.

-   Oprava chyby, kde všechny prostředky byly obsaženy v souborech projektu Pokud filtr přípon byla prázdná.

## <a name="191"></a>1.9.1
 Vydáno 2014-09-22

### <a name="new-features"></a>Nové funkce

-   Optimalizujte vazby zarážku do zdrojového umístění.

-   Podpora pro přetížené metody v pořadí vyhodnocování výrazů ladicího programu.

-   Podpora zabalení primitivních elementů a typů hodnot v pořadí vyhodnocování výrazů ladicího programu.

-   Podpora opětovného vytvoření lokálních proměnných prostředí jazyka C#, při ladění anonymní metody.

-   Odstranění a přejmenování .meta souborů, když se odstranění nebo přejmenování souborů ze sady Visual Studio.

### <a name="bug-fixes"></a>Opravy chyb

-   Opravte zpracování motivů aplikace Visual Studio. Dialogová okna na černé motivy dříve, může zobrazovat prázdný.

-   Zablokování Unity stanovit při připojování ladicího programu během rekompilace Unity.

-   Oprava zarážky při ladění vzdáleného editory nebo hráči zkompilovány v jiném systému.

-   Opravte možné chybovému ukončení sady Visual Studio při dosažení zarážky.

-   Oprava zarážky vazby zarážky zobrazuje jako, aby byla uvolněna.

-   Opravte zpracování obor proměnné v ladicím programu, aby se zabránilo živé proměnné, které se zobrazují mimo rozsah.

-   Opravte vyhledávání statické členy v pořadí vyhodnocování výrazů ladicího programu.

-   Opravte zobrazení typů v pořadí vyhodnocování výrazů ladicího programu k zobrazení statická pole a vlastnosti.

-   Oprava generování řešení, když názvy projektů Unity zahrnuje speciální znaky, že Visual Studio zakazuje (problém připojit #948666).

-   Oprava aplikace Visual Studio nástroje Unity balíček okamžitě zastavit odesílání událostí konzole po nezaškrtnuto (připojit problém #933357) možnost.

-   Opravte detekce odkazy se správně obnovit odkazy na nová rozhraní API jako UnityEngine.UI v projektech UnityVS vygenerována.

-   Opravte instalační program tak, aby vyžadovala, že Visual Studio zavřená před instalací, aby se zabránilo poškozená instalace.

-   Opravte instalační program jako součást správné samostatné, sdílet mezi všechny verze VSTU referenční sestavení Unity.

-   Oprava otevření skripty ve verzích 64 bitů v Unity s VSTU.

## <a name="19"></a>1.9
 Vydáno 2014-07-29

### <a name="new-features"></a>Nové funkce

-   V okně připojit ladicí program Unity verze podporují možnost zadat vlastní IP a portu pro ladění.

-   Přidáte konfigurační možnost nastavit Unity běžet na pozadí nebo ne.

-   Přidáte konfigurační možnost Generovat soubory řešení a projektu nebo jenom soubory projektu.

-   Při spuštění cílového: připojit k Unity nebo připojit k Unity a hrát.

-   Zobrazení vícerozměrných polí v ladicím programu.

-   Zpracujte nové Unity Playeru ladění porty.

-   Popisovač odkazy na nové sestavení Unity, jako je Unity a 4.6 grafickým uživatelským rozhraním sestavení.

-   Deconstructs uzávěry ke správnému zobrazení místní proměnné při ladění.

-   Deconstructs generované iterátory proměnné do argumenty při ladění.

-   Zachovat stav Průzkumník projektů Unity po znovu načíst projekt.

-   Přidáte příkaz Synchronizovat Průzkumník projektů Unity s aktuální dokument.

### <a name="bug-fixes"></a>Opravy chyb

-   Opravte podmíněné zarážky, jejíž podmínky jsou nastavit před spuštěním ladicí program.

-   Opravte odkazy na UnityEngine, aby se zabránilo upozornění.

-   Oprava analýzy verze pro Unity beta verze.

-   Tento problém vyřešit, kde by proměnné zobrazí v okně místních proměnných při dosažení zarážky a krokování.

-   Opravte proměnné popisy v sadě Visual Studio 2013.

-   Oprava generování dokumentace technologie IntelliSense pro Unity 4.5.

-   Opravit v Unity a sady Visual Studio komunikace po domény znovu načíst (Přehrát a zastavit v Unity).

-   Opravte zpracování částí motivů aplikace Visual Studio.

> [!IMPORTANT]
>  C# se převládající jazyk v ekosystému Unity – nové ukázkové prostředky jsou v jazyce C#, dokumentace k Unity budou ve výchozím nastavení jazyka C# – odebrali jsme naše základní podporu UnityScript a poč lépe zaměřit se na prostředí jazyka C#. V důsledku toho VSTU řešení jsou nyní C# pouze a je mnohem rychlejší načíst.

## <a name="182"></a>1.8.2
 Vydáno 2014-01-07

### <a name="new-features"></a>Nové funkce

-   Vyřešit problém v Unity a skriptovací stroj síťovou vrstvou na Mavericks vzdálené zjišťování editory.

-   Zpracujte nové porty ke zjištění vzdáleného hráči Unity.

-   Odkaz na konkrétní UnityEngine sestavení do aktuální sestavení cíl.

-   Přidáte nastavení k filtrování souborů, které mají být zahrnuty generované projekty.

-   Přidáte nastavení zakázat odesílání protokoly konzoly do seznamu chyb sady Visual Studio. To je užitečné, pokud používáte PlayMaker nebo konzoly Pro jako může být jen jedno zpětné volání, které jsou zaregistrované v Unity přijímat protokoly konzoly.

-   Přidejte nastavení zakáže generování symbolů pro ladění mdb. To je užitečné, pokud jste mdb generuje sami.

### <a name="bug-fixes"></a>Opravy chyb

-   Oprava regrese, když soubory otevřít v sadě Visual Studio z Unity > = 4.2 ztratí technologie IntelliSense.

-   Opravte naši VS dialogová okna pro zpracování vlastní motivy.

-   Oprava zavření kontextovou nabídku UPE.

-   Bránící zhroucení v Unity, když konkrétní verze generovaného sestavení, pokud je synchronizovaný.

## <a name="181"></a>1.8.1
 Vydáno 2013-11-21

### <a name="new-features"></a>Nové funkce

-   Upravit třídy MonoBehaviour průvodců s rozhraními API Unity 4.3.

-   Třída MonoBehaviour průvodců jsou filtrování rozhraní API Unity v závislosti na verzi, kterou používáte.

-   K projektům přidat odkaz na System.Xml.Linq pro Unity > 4.1.

-   Prettify naše volání Debug.Log tak, aby nezahrnovala začátku stacktrace ve zprávě.

### <a name="bug-fixes"></a>Opravy chyb

-   Je opravená chyba, kde jsme by mohly narušit výchozí zpracování souborů JavaScript v sadě Visual Studio.

-   Oprava povolí, v sadě Visual Studio, pro skutečné tentokrát bílé pixel.

-   Oprava odstranění UnityVS.VersionSpecific sestavení, pokud je označena jako jen pro čtení pomocí Správce řízení služeb.

-   Oprava výjimky při vytváření balíčku UnityVS sokety.

-   Oprava chyby v sadě Visual Studio při načítání uložené obrázky ze sestavení sady Visual Studio.

-   Oprava chyby při generování UnityVS.VersionSpecific pro zdrojové sestavení Unity.

-   Oprava možné zablokování při otevřeme soket v balíčku Unity.

-   Vyřešilo se zpracování Unity projektu s pomlčkou (-) v názvu.

-   Opravili jsme otevření skriptů z Unity nelze zaměňovat pořadí ALT + TAB pro Unity 4.2 a novější.

## <a name="180"></a>1.8.0
 Vydáno 2013-09-24

### <a name="new-features"></a>Nové funkce

-   Výrazně zlepšit rychlost připojení ladicího programu.

-   Automaticky zpracovává navigace k souboru a řádku v Unity 4.2 a vyšší.

-   Podmíněné zarážky.

-   Generátor souboru projektu nyní zpracovává šablony T4.

-   Aktualizujte MonBehavior průvodců pomocí nových rozhraní API.

-   Dokumentace technologie IntelliSense v jazyce C# pro typy Unity.

-   Aritmetické a logické výrazy hodnocení.

-   Lepší zjišťování vzdálené editory pro vzdálené ladění ve verzi preview.

### <a name="bug-fixes"></a>Opravy chyb

-   Opravená chyba, kde jsme by způsobit únik těchto vlákno v sadě Visual Studio po odpojení ladicí program.

-   Opravili jsme bílé pixel povolí, v sadě Visual Studio.

-   Vyřešilo se zpracování kliknutí na ikonu panelu stavu.

-   Opravili jsme generování odkazů se sestavení ve složkách moduly plug-in.

-   Oprava vytvoření soketů z balíčku UnityVS v případě výjimky.

-   Opravili jsme zjišťování nových verzí UnityVS.

-   Opravili jsme řádku správce licencí, když platnost licence vypršela.

-   Je opravená chyba, která může vykreslit seznam procesů v ladicím programu připojit k procesu okno VS prázdný.

-   Oprava změny hodnot logických výrazů v místním okně.

## <a name="122"></a>1.2.2
 Vydáno 2013-07-09

### <a name="bug-fixes"></a>Opravy chyb

-   Zpracování plně kvalifikované názvy ve vyhodnocovací filtr výrazů.

-   Oprava zablokování související se zpracování výjimek, kde Unity skriptovací stroj je odeslání stackframe nesprávná data.

-   Opravili jsme proces sestavení pro Web cíle.

-   Opravili jsme chybu, která se může stát, pokud byl spuštěn Visual Studio a který byl odstraněný soubor v seznamu souborů, které se otevře při spuštění.

-   Oprava UnityVS.OpenFile ke zpracování souborů bez skriptů, jako je zkompilován shadery.

-   Nyní odkazujeme Boo.Lang a UnityScript.Lang ze všech projekty jazyka C#.

-   Oprava generování odkazů v projektech, pokud projekt obsahuje speciální znaky.

-   Alternativní řešení VS problém, pokud volání metody uvolnění projektů se aktivuje více NullReferenceException MessageBox.

-   Oprava zpracování sestavení, beta verze 4.2 Unity.

## <a name="121"></a>1.2.1
 Vydáno 2013-04-09

### <a name="bug-fixes"></a>Opravy chyb

-   Oprava místní nasazení sestavení Unity pro doplňování kódu v případě chyby vstupně-výstupní operace (jako jsou soubory jen pro čtení, nebo soubory uzamčené sady Visual Studio).

-   Oprava regrese, kde otevřením skriptu z Unity by zaměřit soubor pokud již byl otevřen v sadě Visual Studio.

-   Oprava potíží s výkonem nové zpracování výjimky.

-   Pevné vazby zarážky v některé externí knihovny DLL.

## <a name="12"></a>1.2
 Vydáno 2013-03-25

### <a name="new-features"></a>Nové funkce

-   Výrazně zlepšit rychlost připojení ladicího programu.

-   Optimalizované Unity Project Exploreru pro větší projekty.

-   Bude respektovat nastavení sady Visual Studio pro přerušení (nebo nemusíte) na ošetřené i neošetřené výjimky.

-   Respektovat nastavení sady Visual Studio pro volání ToString na lokální proměnné.

-   Přidat nové nabídky Ladění -> ladicí program připojit Unity, který můžete použít k ladění Unity přehrávače.

-   Zachovat vlastní projekty do řešení UnityVS při generování souboru řešení.

-   Přidat nové klávesové zkratky CTRL + ALT + M -> CTRL + H k zobrazení dokumentace k Unity pro Unity funkce nebo člen na pozici blikajícího kurzoru.

-   Při kompilaci ze sady Visual Studio, vezměte v úvahu kompilátoru soubory odpovědí (rsp).

-   Dekonstruovat typů generovaný kompilátorem, který chcete zobrazit proměnné při ladění generátor metody.

-   Zjednodušení, vzdálené ladění odstraňují potřebu nakonfigurovat sdílenou složku a Unity. Teď stačí mít přístup ke svým projektem Unity z Windows.

-   Instalace vlastního profilu Unity jako standardní profil cílového rozhraní .net. To řeší všechny počet falešně pozitivních výsledků, které se může zobrazit ReSharper.

-   Alternativní Unity skriptování chyby modulu, aby ladicí program nebude správně přerušit na jiných zaregistrovaný vlákna.

-   Přepracujte otevírající soubor tak, aby se zabránilo časování v sadě Visual Studio, ve kterém se vydával za nebudou moct otevřít soubory, při k chybě při požadavku na otevření souboru.

-   UnityVS se nyní chce aktualizovat sestavení při sestavení projektu VS a už není v souboru uložte.

### <a name="bug-fixes"></a>Opravy chyb

-   Opravili naše vlastní profil .net

-   Oprava integrace motivy, to řeší naše problémy s tmavým motivem VS 2012.

-   Rychlá oprava chování zástupce ve VS 2012.

-   Opravili jsme krokování problém, který se může stát při ladění a mimo hlavní vlákno byste dostali na zarážku.

-   Oprava UnityScript a poč dokončení aliasy typů, jako je například int.

-   Oprava výjimky při zápisu nový UnityScript nebo poč řetězec.

-   Oprava výjimky v nabídkách Unity při řešení nebyl načten.

-   Oprava chyby UVS 48: zadáním dvojité uvozovky někdy chybě a přerušení všech – funkce (dokončování kódu, zvýraznění syntaxe atd).

-   Oprava chyby UVS 46: Duplicitní soubor otevřen skriptu (UnityScript), když kliknou na chyby seznam sady Visual Studio.

-   Oprava chyby UVS 42: logo připojení k Unity ve stavovém řádku nezpracuje události myši ve VS 2012.

-   Oprava chyby UVS 44: CTRL + SHIFT + Q není k dispozici v sadě VS 2012 pro rychlé třídy Monobehaviour.

-   Oprava chyby UVS 40: vybrané položky v Průzkumníku projektů Unity jsou nejde přečíst, pokud je okno v VS2012 "" tmavé neaktivní.

-   Oprava chyby UVS 39: tokenizaci problém uvozeny řídicími znaky řetězce.

-   Oprava chyby UVS 35: vyvolat ToString u objektů při kontrole proměnných.

-   Oprava chyby UVS 27: Goto Symbol okno nesoulad s "" tmavé v VS2012.

-   Oprava chyby UVS-11: místní hodnoty v korutinách.

## <a name="11--beta-release"></a>1.1 – beta verze
 Vydáno 2014-10-09

## <a name="1013"></a>1.0.13
 Vydáno 2013-01-21

### <a name="bug-fixes"></a>Opravy chyb

-   Oprava sady Visual Studio uzamkne, který se může stát, pokud cíl laděný proces je odesílání událostí neplatné vlákno. Která by obvykle stát při ladění vzdáleného Unity na os x.

-   Opravili jsme sady Visual Studio se uzamkne, který se může stát, pokud výjimka ukončí ladicí program.

-   Oprava naše MonoBehavior pomocné rutiny při MonoBehavior C# je v oboru názvů.

-   Opravili jsme popisky ladicího programu pro UnityScript v sadě Visual Studio 2012.

-   Opravili jsme generování projektu, když se změní pouze konstanty ladění z Unity.

-   Oprava navigaci pomocí klávesnice v Průzkumníku projektů Unity.

-   Oprava UnityScript obarvení uvozovacími znaky řetězce.

-   Opravili jsme naše otevírající soubor uhodnutelné lepší název projektu při použití mimo Unity. Který je nezbytné, pokud uživatel použije v Unity, který se delegoval UnityVS třetí otevírající soubor část.

-   Oprava zpracování dlouhé zprávy odeslané z Unity UnityVS. Před tímto dlouhých zpráv mohlo dojít k selhání naše zasílání zpráv součástí UnityVS. V důsledku toho někdy UnityVS nepůjde dokument otevřít soubor z Unity.

## <a name="1012"></a>1.0.12
 Vydáno 2013-01-03

### <a name="bug-fixes"></a>Opravy chyb

-   Oprava sady Visual Studio se uzamkne, může dojít v případě sady Visual Studio bylo odstranění zarážky.

-   Je opravená chyba, kdy některé by zarážky po Unity překompilovány herní skripty.

-   Opravili jsme ladicí program správně upozornit sady Visual Studio nevázaná zarážky.

-   Oprava potíží registrace, které by mohlo ohrozit ladicího programu sady Visual Studio k ladění nativní aplikace.

-   Oprava výjimky, které může dojít v případě, že vaše rozhodnutí vyzkoušet UnityScript a rezervace výrazy.

-   Oprava regrese, kde by změna úrovně rozhraní API .net v Unity aktivovat aktualizaci souborů projektu.

-   Opravili jsme poruchu rozhraní API, kde uživatelský kód nelze účastnit obslužná metoda zpětného volání protokolu.

## <a name="1011"></a>1.0.11
 Vydáno 2012-11-28

### <a name="new-features"></a>Nové funkce

-   Oficiální podpora 4 Unity.

-   Manipulace s skriptů z Průzkumníku projektů Unity.

-   Integrace v sadě Visual Studio přejděte do okna.

-   Analýza zprávu s informacemi o konzolu, tak, aby kliknutím na položku v seznamu chyb můžete přejít k první stackframe se symboly.

-   Přidat [API](../cross-platform/customize-project-files-created-by-vstu.md) aby mohl uživatel součástí generování projektu.

-   Přidat [API](../cross-platform/share-the-unity-log-callback-with-vstu.md) aby mohl uživatel účastnit LogCallback.

### <a name="bug-fixes"></a>Opravy chyb

-   Oprava regrese na pozadí Průzkumník projektů Unity v sadě Visual Studio 2012.

-   Opravili jsme generování projektu pro uživatele celého profilu .net.

-   Opravili jsme generování projektu pro uživatele webový cíl.

-   Generování pevné projektu zahrnout ladění a trasování kompilace symboly jako Unity nemá.

-   Oprava chyb při použití speciálních znaků v našich Goto Symbol okna.

-   Oprava chyb, pokud jsme nedá se dosadit naše ikonu na stavovém řádku v sadě Visual Studio.

## <a name="1010"></a>1.0.10
 Vydáno 2012-10-09

### <a name="bug-fixes"></a>Opravy chyb

-   Oprava na pozadí v Průzkumníku projektů Unity v sadě Visual Studio 2010.

-   Opravili jsme zablokování sady Visual Studio, který se může stát, pokud UnityVS pokusili připojit ladicí modul k Unity, jehož rozhraní ladicího programu dříve došlo k chybě aplikace.

-   Oprava, která může dojít v případě, že byla nastavena zarážka a opětovné načtení domény aplikace by dojít k zablokování sady Visual Studio.

-   Opravili jsme, jak se načítají sestavení z Unity vyhnout zamykání souborů a obcházení proces sestavení Unity.

## <a name="109"></a>1.0.9
 Vydáno 2012-10-03

### <a name="bug-fixes"></a>Opravy chyb

-   Opravili jsme generování projektu, pokud obsahuje skutečné prostředky jazyka JavaScript Unity projektu.

-   Oprava chyby ve vyhodnocení výrazu.

-   Opravili jsme nastavení nových hodnot pro pole typů hodnot.

-   Oprava možné vedlejší efekty při přechodu myši nad výrazy z editoru kódu.

-   Opravili jsme, jak jsou typy prohledaný načtená sestavení pro vyhodnocení výrazu.

-   Oprava chyby UVS – 21: hodnocení přiřazení na objektech Unity nemá žádný vliv.

-   Oprava chyby UVS – 21: neplatný ukazatel při vyhodnocení volání metody matematické API Unity.

## <a name="108"></a>1.0.8
 Vydáno 2012-09-26

### <a name="bug-fixes"></a>Opravy chyb

-   Dlouhodobý způsob, jak naše skript otevírající získat cestu k projektu se ujistěte, zda je možné otevřít Visual Studio a skripty.

-   Oprava chyby se zarážkami vytvořené během relace ladění byla spuštěna, který může způsobit sady Visual Studio k uzamčení.

-   Opravili jsme, jak je UnityVS zaregistrovaná na Visual Studio 2010.

## <a name="107"></a>1.0.7
 Vydáno 2012-09-14

### <a name="new-features"></a>Nové funkce

-   Podpora v sadě Visual Studio 2012.

### <a name="bug-fixes"></a>Opravy chyb

-   Oprava generování editoru a moduly plug-in projektových souborů tak, aby odpovídaly Unity a chování.

-   Opravili jsme překlad symbolů .pdb v Unity 4.

> [!IMPORTANT]
>  Z důvodu podpory Visual Studio 2012 museli jsme přejmenovat několik souborů a některých dalších pohybovat. UnityVS balíčku k importu Unity teď jmenuje UnityVS 2010 nebo UnityVS 2012, respektive Visual Studio 2010 a Visual Studio 2012. Tato verze také vyžaduje, že UnityVS soubory projektu jsou znovu vygenerovány.

## <a name="106---internal-build"></a>1.0.6 – interní sestavení
 Vydáno 2012-09-12

## <a name="105"></a>1.0.5
 Vydáno 2012-09-10

### <a name="bug-fixes"></a>Opravy chyb

-   Oprava generování souborů projektu, kdy skripty nebo shadery znak neplatný kód xml.

-   Oprava zjišťování instancí Unity Unity bylo připojení k serveru Asset. Aktivuje toto selhání k otevírání souborů z Unity a automatické připojení ladicího programu sady Visual Studio.

## <a name="104"></a>1.0.4
 Vydáno 2012-09-05

### <a name="new-features"></a>Nové funkce

-   Automatický převod symbolů pro ladění v Unity.

     Pokud máte .dll sestavení .NET s jeho přidružené .pdb ve složce Asset, jednoduše znovu importujte sestavení a UnityVS převede na soubor symbolů ladění, Unity a skriptovací stroj rozumí a budete mít ke kroku do vašeho sestavení .NET z pdb UnityVS.

### <a name="bug-fixes"></a>Opravy chyb

-   Oprava chyb UnityVS během ladění způsobeno výjimky vyvolané z metody nebo vlastnosti v Unity.

## <a name="103"></a>verze 1.0.3
 Vydáno 2012-09-04

### <a name="new-features"></a>Nové funkce

-   Nová možnost konfigurace zakázat použití UnityVS pro otevření souborů z Unity.

### <a name="bug-fixes"></a>Opravy chyb

-   Oprava generování odkazů na UnityEditor pro projekty mimo editor.

-   Oprava definice symbolu UNITY_EDITOR pro projekty mimo editor.

-   Oprava náhodné VS případ chyby způsobené naše vlastní stavový řádek.

## <a name="102"></a>1.0.2
 Vydáno 2012-08-30

### <a name="bug-fixes"></a>Opravy chyb

-   Oprava konflikt s ladicím programem PythonTools.

-   Pevné odkazy na Mono.Cecil.

-   Oprava chyby v sestaveních jak skriptovací byly načteny z Unity s b7 Unity 4.

## <a name="101"></a>1.0.1
 Vydáno 2012-08-28

### <a name="new-features"></a>Nové funkce

-   Podpora pro Unity 4.0 beta verze Preview.

### <a name="bug-fixes"></a>Opravy chyb

-   Oprava kontroly vlastnosti vyvolávání výjimek.

-   Opravili jsme sestupně do základní objekty při kontrole objekty.

-   Oprava prázdný rozevírací seznam pro kurzor v Průvodci MonoBehavior.

-   Oprava dokončování pro knihovny dll ve složce Asset UnityScript a poč.

## <a name="10--initial-release"></a>Verzi 1.0 – počáteční
 Vydáno 2012-08-22

