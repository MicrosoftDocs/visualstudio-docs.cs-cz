---
title: Protokol změn (Nástroje sady Visual Studio pro jednotu, Windows) | Dokumenty společnosti Microsoft
ms.custom: ''
ms.date: 12/02/2019
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: ea490b7e-fc0d-44b1-858a-a725ce20e396
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 0e1810f452f48c95e0c4e8117820be3598b0f139
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74706787"
---
# <a name="change-log-visual-studio-tools-for-unity-windows"></a>Protokol změn (Nástroje visual studia pro jednotu, Windows)

Visual Studio Tools for Unity change log.

## <a name="4420"></a>4.4.2.0

Vydáno prosinec 3, 2019

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opravena diagnostika s uživatelsky definovanými rozhraními.

  - Opraveny rychlé popisky s poškozenými výrazy.

## <a name="4410"></a>4.4.1.0

Vydáno listopad 6, 2019

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidána podpora procesů na pozadí Unity. (Ladicí program je schopen automaticky připojit k hlavnímu procesu namísto podřízeného procesu).
  
  - Byl přidán rychlý popis pro zprávy Unity, který zobrazuje související dokumentaci.

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opraven analyzátor `UNT0002` porovnání tagů s pokročilými binárními a vyvolávacími výrazy.

### <a name="deprecated-features"></a>Zastaralé funkce

- **Integrace:**

  - Do budoucna visual studio nástroje pro jednotu bude podporovat pouze Visual Studio 2017+.

## <a name="4400"></a>4.4.0.0

Vydáno říjen 15, 2019

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidáno supresorové pro `IDE0060` (nepoužitý parametr) pro všechny zprávy Unity.
  
  - Byl přidán rychlý popis pro `TooltipAttribute`pole označená písmenem . (To bude fungovat pro jednoduchý get přistupující ho pomocí tohoto pole také).

## <a name="4330"></a>4.3.3.0

Vydáno září 23, 2019

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opraveno hlášení chyb a upozornění pro zjednodušená sestavení.

## <a name="4320"></a>4.3.2.0

Vydáno září 16, 2019

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Prohloubili jsme pochopení, že Visual Studio má pro unity projekty přidáním nové diagnostiky specifické pro Unity. Také jsme zvýšili inteligenci integrovaného vývojového prostředí (IDE) tím, že jsme potlačili obecnou diagnostiku C#, která se nevztahuje na projekty Unity. Například rozhraní IDE nezobrazí rychlou opravu pro změnu `readonly` proměnné inspektoru, na kterou by se zabránilo úpravě proměnné v Editoru unity.
    - `UNT0001`: Unity zprávy jsou volány za běhu i v případě, že jsou prázdné, nedeklarujte je, aby se zabránilo uncesseray zpracování unity runtime.
    - `UNT0002`: Porovnání značek pomocí rovnosti řetězců je pomalejší než předdefinovaná metoda CompareTag.
    - `UNT0003`: Použití obecné ho formuláře GetComponent je upřednostňováno pro bezpečnost typů.
    - `UNT0004`: Zpráva aktualizace závisí na kratech snímků a měla by místo Time.fixedDeltaTime používat time.deltaTime.
    - `UNT0005`: FixedUpdate zpráva je frame-rate nezávislé a měl by použít Time.fixedDeltaTime místo Time.deltaTime.
    - `UNT0006`: Pro tuto zprávu Unity byl zjištěn nesprávný podpis metody.
    - `UNT0007`: Unity přepíše operátor porovnání null pro Unity objekty, které je nekompatibilní s null coalescing.
    - `UNT0008`: Unity přepíše operátor porovnání null pro Unity objekty, které je nekompatibilní s null šíření.
    - `UNT0009`: Při použití InitializeOnLoad atribut třídy, je třeba zadat statický konstruktor. Atribut InitializeOnLoad zajistí, že bude volán při spuštění editoru.
    - `UNT0010`: MonoBehaviours by měly být vytvořeny pouze pomocí AddComponent(). Objekt MonoBehaviour je komponenta, která musí být připojená k objektu GameObject.
    - `UNT0011`: ScriptableObject by měl být vytvořen pouze pomocí CreateInstance(). Objekt ScriptableObject musí být vytvořený modulem Unity, aby zpracovával metody zpráv Unity.
    - `USP0001`for `IDE0029`: Unity objekty by neměly používat null coalescing.
    - `USP0002`pro `IDE0031`: Unity objekty by neměly používat null šíření.
    - `USP0003`for `IDE0051`: Unity zprávy jsou vyvolány unity runtime.
    - `USP0004`pro `IDE0044`: Pole s atributem SerializeField by neměla být jen pro čtení.

## <a name="4310"></a>4.3.1.0

Vydáno září 4, 2019

### <a name="new-features"></a>Nové funkce

- **Hodnocení:**

  - Přidána podpora pro lepší typ `List<object>` zobrazení, `List'1[[System.Object, <corlib...>]]`tj.

  - Byla přidána podpora přístupu členů `p->data->member`ukazatele, tj.

  - Byla přidána podpora implicitních konverzí v inicializačních polích, tj. `new byte [] {1,2,3,4}`

## <a name="4300"></a>4.3.0.0

Vydáno srpen 13, 2019

### <a name="new-features"></a>Nové funkce

- **Ladicí program:**

  - Přidána podpora pro protokol MDS 2.51.

- **Integrace:**

  - Bylo vylepšeno okno "Připojit k instanci Unity" pomocí funkcí řazení, vyhledávání a aktualizace. PID se nyní zobrazí i pro místní hráče (dotazem na naslouchání sokety v systému k načtení procesu vlastnící).

  - Přidána podpora pro soubory asmdef.

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opraveno zpracování poškozených zpráv při komunikaci s Unity Players.

- **Hodnocení:**

  - Opraveno zpracování oborů názvů ve výrazech.

  - Opravena kontrola s typy IntPtr.
  
  - Opraveny problémy s krokování s výjimkami.

  - Opraveno vyhodnocení pseudoidentifikátorů (například $exception).

  - Zabránit selhání při dereferencování neplatných adres.  

  - Opraven problém s nezatíženými aplikačními doménami.

## <a name="4201"></a>4.2.0.1

Vydáno červenec 24, 2019

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidána nová možnost pro vytvoření libovolného typu souborů z Průzkumníka projektu Unity.
  
  - Zlepšete ukládání do mezipaměti diagnostiky při použití rychlých sestavení pro projekty Unity.

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Byl opraven problém, kdy přípona souboru nebyla zpracována žádným známým editorem.

  - Opravena podpora vlastních rozšíření v Průzkumníku projektu Unity.

  - Opraveno nastavení ukládání mimo hlavní dialog.

  - Byla odebrána starší závislost Microsoft.VisualStudio.MPF.

## <a name="4110"></a>4.1.1.0

Vydáno květen 24, 2019

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Aktualizováno Rozhraní API pro monochování na 2019.1.

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opravena upozornění hlášení a chyby pro výstup, když je povoleno zjednodušené sestavení.

  - Opraven análový výkon sestavení.

## <a name="4100"></a>4.1.0.0

Vydáno květen 21, 2019

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidána podpora pro nové dávkové rozhraní API pro rychlejší opětovné načtení projektů.

  - Zakázáno úplné sestavení pro projekty Unity, ve prospěch použití chyb a upozornění Technologie IntelliSense. Unity vytvoří řešení visual studio s projekty knihovny tříd, které představují, co Unity dělá interně. Jak již bylo řečeno, výsledek sestavení v sadě Visual Studio se nikdy nepoužívá nebo zvedl Unity jako jejich kompilace kanálu je uzavřena. Vytváření v sadě Visual Studio je jen spotřebovává prostředky pro nic za nic. Pokud potřebujete úplné sestavení, protože máte nástroje nebo nastavení, které na něm závisí, můžete tuto optimalizaci zakázat (Nástroje/Možnosti/Nástroje pro jednotu/Zakázat úplné sestavení projektů).

  - Automaticky zobrazit Unity Project Explorer (UPE) při načtení projektu Unity. Upe bude ukotven vedle Průzkumníka řešení.

  - Aktualizovaný mechanismus extrakce názvu projektu pomocí unity 2019.x.

  - Přidána podpora balíčků Unity v UPE. Viditelné jsou pouze odkazované balíčky (pomocí souboru manifest.json ve `Packages` složce) a místní balíčky (vložené do `Packages` složky).

- **Generování projektu:**

  - Při zpracování souboru řešení zachovejte externí vlastnosti.

- **Hodnocení:**

  - Přidána podpora pro názvy s kvalifikací aliasů (prozatím pouze globální obor názvů). Vyhodnocení výrazu tedy nyní přijímá typy pomocí formuláře global::namespace.type.

  - Přidána `pointer[index]` podpora formuláře, který je sémanticky identický s formulářem dereference `*(pointer+index)` ukazatele.

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opraveny problémy se závislostmi na webu Microsoft.VisualStudio.MPF.

  - Opraveno Připojení hráče UPW, bez načtení projektu.

  - Aktualizace databáze dlouhodobého automatického majetku, když visual studio ještě nebylo připojeno.

  - Opraveny problémy s motivy pomocí štítků a zaškrtávacích políček.

- **Ladicí program:**

  - Opraveno krokování se statickými konstruktory.

## <a name="4005"></a>4.0.0.5

Vydáno únor 27, 2019

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opraveno zjišťování verzí sady Visual Studio pomocí instalačního balíčku.

  - Z instalačního balíčku byla odebrána nepoužitá sestavení.

## <a name="4004"></a>4.0.0.4

Vydáno únor 13, 2019

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidána podpora pro správnou detekci procesů Unity během instalace a umožňují instalačnímu modulu lépe zpracovat zámky souborů.

  - Bylo `ScriptableObject` aktualizováno rozhraní API.

## <a name="4003"></a>4.0.0.3

Vydáno leden 31, 2019

### <a name="new-features"></a>Nové funkce

- **Generování projektu:**

  - Veřejná a serializovaná pole již nebudou způsobovat upozornění. Automaticky jsme potlačili `CS0649` upozornění `IDE0051` a kompilátoru v projektech Unity, které tyto zprávy vytvořily.

- **Integrace:**

  - Vylepšeno uživatelské prostředí pro zobrazení editoru Unity a instancí přehrávače (okna jsou nyní nastavitelná, použijte jednotné okraje a zobrazte uzel pro změna velikosti). Přidány informace o Id procesu pro editory Unity.

  - Bylo `MonoBehaviour` aktualizováno rozhraní API.

- **Hodnocení:**

  - Přidána podpora pro místní funkce.

  - Přidána podpora pseudoproměnných (výjimky a identifikátory objektů).

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Byl opraven problém s zástupnými obrázky a motivy.

  - Při automatické aktualizaci databáze datových zdrojů zapisujete do výstupního okna pouze při ladění.

  - Opravena zpoždění ui s filtrováním průvodce MonoBehaviour.

- **Ladicí program:**

  - Opraveno čtení vlastního atributu u pojmenovaných argumentů při použití starých verzí protokolu.

## <a name="4002"></a>4.0.0.2

Vydáno leden 23, 2019

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opravena experimentální generace sestavení.

  - Opraveno zpracování událostí souboru projektu, aby se minimalizoval tlak na vlákno uživatelského rozhraní.

  - Opraven poskytovatel dokončení s dávkovými změnami textu.

- **Ladicí program:**

  - Opraveno zobrazení ladicích zpráv uživatele do připojeného ladicího programu.

## <a name="4001"></a>4.0.0.1

Vydáno prosinec 10, 2018

### <a name="new-features"></a>Nové funkce

- **Hodnocení:**

  - Nahradil NRefactory ve prospěch Roslyn pro vyhodnocení výrazu.

  - Přidána podpora pro ukazatele: dereference, casting a ukazatel aritmetické (Unity 2018.2+ a nový runtime jsou požadovány pro toto).

  - Přidána podpora pro zobrazení ukazatele pole (například v jazyce C++). Vezměte výraz ukazatele a potom přidejte čárku a počet prvků, které chcete zobrazit.

  - Přidána podpora pro asynchronní konstrukce.

- **Integrace:**

  - Přidána podpora pro automatické obnovení databáze datových zdrojů Unity při ukládání. To je ve výchozím nastavení povoleno a při ukládání skriptu v sadě Visual Studio se spustí rekompilace na straně Unity. Tuto funkci můžete zakázat v nástrojích\Možnosti\Nástroje pro Unity\Refresh Unity AssetDatabase při uložení.

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opravena aktivace mostu, pokud visual studio není vybránjako upřednostňovaný externí editor.

  - Opraveno vyhodnocení výrazů poškozenými nebo nepodporovanými výrazy.

## <a name="4000"></a>4.0.0.0

Vydáno prosinec 4, 2018

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidána podpora pro Visual Studio 2019 (potřebujete alespoň Unity 2018.3, abyste mohli používat Visual Studio 2019 jako externí editor skriptů).

  - Přijal visual studio image služby a katalogu, s plnou podporou pro HDPI škálování, pixel dokonalé obrázky a tématikou.

### <a name="deprecated-features"></a>Zastaralé funkce:

- **Integrace:**

  - Do budoucna Visual Studio Tools for Unity bude podporovat pouze Unity 5.2 + (s integrovanou integrací Sady Visual Studio Unity).

  - Do budoucna visual studio nástroje pro jednotu bude podporovat pouze Visual Studio 2015+.

  - Byla odebrána starší jazyková služba, seznam chyb a stavový řádek.

  - Byl odstraněn Průvodce rychlým monochováním (ve prospěch vyhrazené podpory intellisense).

## <a name="3903"></a>3.9.0.3

Vydáno listopad 28, 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opraveny problémy s překládkou a intellisense projektu při přidávání nebo odebírání skriptů umístěných v prvním projektu.

## <a name="3902"></a>3.9.0.2

Vydáno listopad 19, 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Ladicí program:**

  - Opravena zablokování v knihovně slouží ke komunikaci s ladicí modul Unity, takže Visual Studio nebo Unity zmrazit, zejména při stisknutí 'Připojit k jednotě' nebo restartování hry.

## <a name="3901"></a>3.9.0.1

Vydáno listopad 15, 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opravena aktivace pluginu Unity, když byl vybrán jiný výchozí editor.

## <a name="3900"></a>3.9.0.0

Vydáno listopad 13, 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Vrácení zpět řešení pro chybu výkonu Unity, která byla opravena Unity.

## <a name="3807"></a>3.8.0.7

Vydáno září 20, 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Ladicí program:**

  - (Backported od 3.9.0.2) Opravena zablokování v knihovně slouží ke komunikaci s ladicí modul Unity, takže Visual Studio nebo Unity zmrazit, zejména při stisknutí 'Připojit k jednotě' nebo restartování hry.

## <a name="3806"></a>3.8.0.6

Vydáno srpen 27, 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opraveno překládky projektů a řešení.

## <a name="3805"></a>3.8.0.5

Vydáno srpen 20, 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opravena likvidace předplatného monitorování projektu.

## <a name="3804"></a>3.8.0.4

Vydáno srpen 14, 2018

### <a name="new-features"></a>Nové funkce

- **Hodnocení:**

  - Přidána podpora hodnot ukazatele.

  - Přidána podpora pro obecné metody.

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Inteligentní opětovné načtení s více projekty změněny.

## <a name="3803"></a>3.8.0.3

Vydáno červenec 24, 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - (Backported od 3.9.0.0) Vrácení zpět řešení pro chybu výkonu Unity, která byla opravena Unity.

## <a name="3802"></a>3.8.0.2

Vydáno 7.

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Přechodné řešení pro chybu výkonu Unity: cache MonoIslands při generování projektů.

## <a name="3801"></a>3.8.0.1

Vydáno červen 26, 2018

### <a name="new-features"></a>Nové funkce

- **Ladění:**

  - Byla přidána podpora příkazů UserLog a UserBreak.

  - Přidána podpora opožděného načtení typu (optimalizace zatížení sítě a latence odezvy ladicího programu).

### <a name="bug-fixes"></a>Opravy chyb

- **Hodnocení:**

  - Vylepšené vyhodnocení výrazu binárního operátoru a vyhledávání metod.

## <a name="3800"></a>3.8.0.0

Vydáno květen 30, 2018

### <a name="new-features"></a>Nové funkce

- **Ladění:**

  - Přidána podpora pro zobrazování proměnných v asynchronních konstrukcích.

  - Přidána podpora pro zpracování vnořených typů při nastavování zarážek, aby se zabránilo upozornění s konstrukce kompilátoru.

- **Integrace:**

  - Přidána podpora pro gramatiky textmate pro shadery (zatížení Jazyka C++ již není potřeba pro zbarvení kódu Shader).

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Při použití nového runtime Unity již nepřevádějí přenosné pdb na mdb.

## <a name="3701"></a>3.7.0.1

Vydáno květen 7, 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Instalační služby:**

  - Opraven problém se závislostmi při použití experimentálních sestavení.

## <a name="3700"></a>3.7.0.0

Vydáno květen 7, 2018

### <a name="new-features"></a>Nové funkce

- **Ladění:**

  - Přidána podpora pro orchestrované ladění (ladění více přehrávačů nebo editoru se stejnou relací sady Visual Studio).

  - Přidána podpora ladění přehrávače Android USB.

  - Přidána podpora ladění přehrávače UWP/IL2CPP.

- **Hodnocení:**

  - Přidána podpora pro hexadecimální specifikátory.

  - Vylepšené hodnocení okna hodinek.

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opraveno použití nastavení výjimek.

- **Generování projektu:**

  - Vyloučit jednotky kompilace správce balíčků z generace.

## <a name="3605"></a>3.6.0.5

Vydáno březen 13, 2018

### <a name="new-features"></a>Nové funkce

- **Generování projektu:**

  - Přidána podpora pro nový generátor projektu v Unity 2018.1.

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opraveno zpracování poškozených stavů s vlastními projekty.

- **Ladicí program:**

  - Opraveno nastavení dalšího příkazu.

## <a name="3604"></a>3.6.0.4

Vydáno březen 5, 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Opravena detekce verze Mono.

- **Integrace:**

  - Opraveny problémy s časováním s aktivací 2018.1 a aktivací pluginů.

## <a name="3603"></a>3.6.0.3

Vydáno únor 23, 2018

### <a name="new-features"></a>Nové funkce

- **Generování projektu:**

  - Byla přidána podpora pro standard .NET.

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Opraveno zjišťování rozhraní Unity target framework.

- **Ladicí program:**

  - Opraveno rozdělení na výjimky, které jsou vyvolány mimo uživatelský kód.

## <a name="3602"></a>3.6.0.2

Vydáno 7. února 2018

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Aktualizujte povrch rozhraní UNITYMessage API pro 2017.3.

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Pouze znovu načíst projekty na externí změny (s omezením).

## <a name="3601"></a>3.6.0.1

Vydáno leden 24, 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opraven automatický převod symbolu ladění pdb na mdb.

  - Opraveno nepřímé volání EditorPrefs.GetBool, které mělo vliv na inspektora při pokusu o změnu velikosti pole.

## <a name="3600"></a>3.6.0.0

Vydáno leden 10, 2018

### <a name="new-features"></a>Nové funkce

- **Generování projektu:**

  - Přidána podpora pro referenční model 2018.1 MonoIsland.

- **Hodnocení:**

  - Přidána podpora identifikátoru $exception.

- **Ladicí program:**

  - Přidána podpora pro DebuggerHidden/DebuggerStepThrough atributy s novým unity runtime.

- **Průvodci:**

  - Zaváděte nejnovější verzi pro průvodce.

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Opraven výpočty grafického řízení projektu pro projekty hráčů.

- **Ladicí program:**

  - Opraven závod při manipulaci s průlomové události.

- **Průvodci:**

  - Před vložením metody aktualizujte kontext roslyn.

## <a name="3503"></a>3.5.0.3

Vydáno 9.

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opraven automatický převod symbolu ladění pdb na mdb.

## <a name="3502"></a>3.5.0.2

Vydáno prosinec 4, 2017

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Projekty Unity se teď při přidání nebo odebrání skriptu z Unity automaticky znovu načítají v sadě Visual Studio.

- **Ladicí program:**

  - Přidána možnost použít ladicí program Mono sdílený Xamarinem a Visual Studio pro Mac k ladění Editoru unity.

  - Přidána podpora pro přenosné soubory ladicí symbol.

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opraveny problémy se závislostmi instalačního programu.

  - Opravena nabídka nápovědy rozhraní Unity API, která se nezobrazovala.

- **Generování projektu:**

  - Opravena generování projektu hráče při práci na hře UPW s backendem IL2CPP/.NET 4.6.

  - Opravena další přípona .dll nesprávně přidaná k názvu souboru sestavení.

  - Opraveno použití konkrétní úrovně kompatibility rozhraní API projektu namísto globální úrovně.

  - Nevynucovat AllowAttachedDebuggingOfEditor Unity příznak jako výchozí je nyní 'true'.

## <a name="3402"></a>3.4.0.2

Vydáno září 19, 2017

### <a name="new-features"></a>Nové funkce

- **Generování projektu:**

  - Přidána podpora pro kompilační jednotky assembly.json.

  - Ukončení kopírování sestavení Unity do složky projektu.

- **Ladicí program:**

  - Přidána podpora pro nastavení dalšího příkazu s novým runtime Unity.

  - Přidána podpora pro desetinný typ s novým runtime Unity.

  - Přidána podpora pro implicitní/explicitní převody.

### <a name="bug-fixes"></a>Opravy chyb

- **Hodnocení:**

  - Vytvoření pevného pole s implicitní velikostí.

  - Opraveny generované položky kompilátoru s místními obyvateli.

- **Generování projektu:**

  - Opraven odkaz na Microsoft.CSharp pro úroveň rozhraní API 4.6.

## <a name="3302"></a>3.3.0.2

Vydáno srpen 15, 2017

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Opraveno generování řešení Visual Studio na Unity 5.5 a předchozích verzích.

## <a name="3300"></a>3.3.0.0

Vydáno srpen 14, 2017

### <a name="new-features"></a>Nové funkce

- **Hodnocení:**

  - Přidána podpora pro vytváření struktur s novým runtime Unity.

  - Přidána minimalistická podpora pro ukazatele.

### <a name="bug-fixes"></a>Opravy chyb

- **Hodnocení:**

  - Pevná metoda vyvolání na primitivech.

  - Opraveno vyhodnocení pole s typy označenými BeforeFieldInit.

  - Pevná nepodporovaná volání s binárními operátory (substract).

  - Opraveny problémy při přidávání položek do hodinek sady Visual Studio.

- **Generování projektu:**

  - Opraveny odkazy na názvy sestavení se soubory mcs.rsp.

  - Opravena definice s úrovněmi rozhraní API.

## <a name="3200"></a>3.2.0.0

Vydáno květen 10, 2017

### <a name="new-features"></a>Nové funkce

- **Instalační služby:**

  - Přidána podpora pro čištění mezipaměti MEF.

### <a name="bug-fixes"></a>Opravy chyb

- **Editor kódu:**

  - Opravena klasifikace/dokončení s vlastními atributy.

  - Opraveno blikání se zprávami Unity.

## <a name="3100"></a>3.1.0.0

Vydáno duben 7, 2017

### <a name="new-features"></a>Nové funkce

- **Ladicí program:**

  - Přidána podpora nového runtime Unity (s kompatibilitou s rozhraním .NET 4.6 / C# 6).

- **Generování projektu:**

  - Přidána podpora pro profil .NET 4.6.

  - Přidána podpora pro soubory mcs.rsp.

  - Při použití Unity 5.6 vždy povolte nebezpečný přepínač kompilace.

  - Přidána podpora pro generování projektu "Player" při používání platformy Windows Store a backendu il2cpp.

### <a name="bug-fixes"></a>Opravy chyb

- **Editor kódu:**

  - Pevná poloha stříšky po vložení metody s automatickým dokončováním.

- **Generování projektu:**

  - Byla odebrána verze sestavení po zpracování.

## <a name="3001"></a>3.0.0.1

Vydáno březen 7, 2017

### <a name="this-version-includes-all-new-features-and-bug-fixes-introduced-with-28x-series"></a>Tato verze obsahuje všechny nové funkce a opravy chyb zavedené s 2.8.x série.

## <a name="2820---30-preview-3"></a>2.8.2.0 - 3.0 Náhled 3
Vydáno leden 25, 2017

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Opravena regrese, kde pluginy projekty, kde odkazoval dvakrát, nejprve jako binární DLL pak jako odkaz na projekt.

## <a name="2810---30-preview-2"></a>2.8.1.0 - 3.0 Náhled 2
Vydáno leden 23, 2017

### <a name="bug-fixes"></a>Opravy chyb

- **Editor kódu:**

  - Opravena chyba při spuštění deklarace atributu bez dokončení závorky.

- **Ladicí program:**

  - Pevné zarážky funkce s korutiny pod novým kompilátorem Unity/runtime.

  - Přidáno upozornění v případě nezapojovatelné zarážky (pokud není nalezen a lokace odpovídající zdroj).

- **Generování projektu:**

  - Opravena generace csproj se speciálními/lokalizovanými znaky.

  - Opraveny odkazy mimo datové zdroje, například Knihovna (například Facebook SDK).

- **Vedlejší:**

  - Byla přidána kontrola, která má zabránit spuštění Unity při instalaci nebo odinstalaci.

  - Přepnul na https a zaměřil se na vzdálenou dokumentaci Unity.

## <a name="2800---30-preview"></a>2.8.0.0 - 3.0 Náhled
Vydáno listopad 17, 2016

### <a name="new-features"></a>Nové funkce

- **Obecné:**

  - Přidána podpora instalačního programu sady Visual Studio 2017.

  - Přidána podpora rozšíření Visual Studio 2017.

  - Přidána podpora lokalizace.

- **Editor kódu:**

  - Přidány zprávy C# IntelliSense for Unity.

  - Přidáno zbarvení kódu C# pro zprávy Unity.

- **Ladicí program:**

  - Přidána `is`podpora `as`výrazů `default`, `new` , direct cast, .

  - Byla přidána podpora pro výrazy concat řetězce.

  - Přidána podpora šestnáctkového zobrazení hodnot celého čísla.

  - Přidána podpora pro vytváření nových dočasných proměnných (příkazů).

  - Přidána podpora pro implicitní primitivní převody.

  - Přidány lepší chybové zprávy, pokud je typ očekáván nebo nebyl nalezen.

- **Generování projektu:**

  - Byla odebrána přípona CSharp z názvů projektů.

  - Byl odebrán odkaz na soubor cílů msbuild v rámci celého systému.

- **Průvodci:**

  - Přidána podpora pro zprávy Unity v typech bez chování, jako je editor nebo EditorWindow.

  - Přešel na Roslyn pro vkládání a formátování zpráv Unity.

### <a name="bug-fixes"></a>Opravy chyb

- **Ladicí program:**

  - Opravena chyba, která se při vyhodnocování obecných typů zhroutila.

  - Opraveno zpracování typů s možnou hodnotou null.

  - Opraveno zacházení s výčty.

  - Opraveno zpracování vnořených typů členů.

  - Opraven přístup k indexeru kolekce.

  - Pevná podpora pro ladění rámců iterátoru s novým kompilátorem C#.

- **Generování projektu:**

  - Opravena chyba, která bránila kompilaci při cílení na unity webový přehrávač.

  - Opravena chyba, která bránila kompilaci při kompilaci skriptu s názvem souboru kódovaným na webu.

## <a name="2300"></a>2.3.0.0

Vydáno červenec 14, 2016

### <a name="new-features"></a>Nové funkce

- **Obecné:**

  - Byla přidána možnost zakázat protokoly konzoly Unity v seznamu chyb sady Visual Studio.

  - Přidána možnost povolit změny vygenerovaných vlastností projektu.

- **Ladicí program:**

  - Přidány vizualizéry řetězců Text, XML, HTML a JSON.

- **Průvodci:**

  - Přidány chybějící MonoBehaviors.

### <a name="bug-fixes"></a>Opravy chyb

- **Obecné:**

  - Byl opraven konflikt s resharperem, který zabránil zobrazení ovládacích prvků v nastavení sady Visual Studio.

  - Opraven konflikt s Xamarinem, který v některých případech zabránil ladění.

- **Ladicí program:**

  - Byl opraven problém, který způsoboval, že visual studio při ladění zamrzlo.

  - Opraven problém s zarážkymi funkcí v sadě Visual Studio 2015.

  - Opraveno několik problémů s vyhodnocením výrazů.

## <a name="2200"></a>2.2.0.0

Vydáno únor 4, 2016

### <a name="new-features"></a>Nové funkce

- **Průvodci:**

  - Přidáno inteligentní vyhledávání v průvodci **Implementovat monobehavior.**

  - Zjitřili jste si kontext průvodců; Například NetworkBehavior zprávy jsou k dispozici pouze při práci s NetworkBehavior.

  - Byla přidána podpora zpráv NetworkBehavior v průvodcích.

- **Ui:**

  - Přidána možnost konfigurace viditelnosti zpráv MonoBehavior.

  - Odebrány stránky vlastností Visual Studio, které nejsou relevantní pro projekty Unity.

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Opraveny odkazy na UnityEngine a UnityEditor na Unity 4.6.

  - Opraveno generování projektových souborů, když Unity běží na OSX.

  - Opraveno zpracování názvů projektů obsahujících znaky hashmark (#).

  - Omezené generované projekty na C# 4.

- **Ladicí program:**

  - Opraven problém s vyhodnocením výrazu při ladění uvnitř korutiny Unity.

  - Byl opraven problém, který způsoboval, že visual studio při ladění zamrzlo.

- **Ui:**

  - Opravena nekompatibilita s rozšířením [Tabs Studio](https://tabsstudio.com/) Visual Studio.

- **Instalační služby:**

  - Podpora instalace Celého počítače VSTU (instalace pro všechny uživatele) vytvořením položek registru HKLM.

  - Opraveny problémy s odinstalací VSTU při instalaci stejné verze VSTU pro více různých verzí sady Visual Studio. Například při VSTU **2015** 2.1.0.0 a VSTU **2013** 2.1.0.0 byly nainstalovány.

## <a name="2100"></a>2.1.0.0

Vydáno září 8, 2015

### <a name="new-features"></a>Nové funkce

- Podpora jednoty 5.2

### <a name="bug-fixes"></a>Opravy chyb

- Zobrazit položky nabídky na Unity < 4.2

- Při uzamčení souborů xml intellisense se již nezobrazí chybová zpráva.

- Zpracovat \<<při změně>> podmíněných zarážky, pokud podmíněný argument není logická hodnota.

- Opraveny odkazy na sestavení UnityEngine a UnityEditor pro aplikace pro Windows Store.

- Opravena chyba při krokování v ladicím programu: Nelze krokovat, obecná výjimka.

- Opraveny zarážky počtu přístupů ve Visual Studiu 2015.

## <a name="2000"></a>2.0.0.0

Vydáno červenec 20, 2015

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace jednoty:**

  - Opraven převod ladicích symbolů vytvořených pomocí Visual Studia 2015 při importu dll a jejích ladicích symbolů (PDB).

  - Při importu dll a jejích ladicích symbolů (PDB) vždy generujte soubory MDB, s výjimkou případů, kdy je k dispozici také soubor MDB.

  - Opraveno znečištění adresáře projektu Unity s adresářem obj.

  - Opraveno generování odkazů na System.Xml.Link a System.Runtime.Serialization.

  - Přidána podpora pro více odběratelů pro zavěšení rozhraní API generování souborů projektu.

  - Vždy dokončit generování souboru projektu i v případě, že jeden ze souborů, které mají být generovány, je uzamčen.

  - Přidána podpora * zástupných znaků v rozšíření filtru při zadávání souborů, které mají být zahrnuty do projektu C#.

- **Integrace visual studia:**

  - Opraven problém s kompatibilitou s nástroji pro zvýšení produktivity.

  - Opraveno generování MonoBehaviors kolem událostí a delegátů deklarací.

- **Ladicí program:**

  - Opraveno potenciální zmrazení při ladění.

  - Byl opraven problém, kdy místní obyvatelé nebyli zobrazeni v určitých rámech zásobníku.

  - Opravena kontrola prázdných polí.

## <a name="1990---20-preview-2"></a>1.9.9.0 - 2.0 Náhled 2
Vydáno duben 2, 2015

### <a name="new-features"></a>Nové funkce

- **Průzkumník projektu Unity:**

  - Automaticky přejmenovat třídu při přejmenování souboru v Průzkumníku projektu Unity (dialogové okno **Možnosti).**

  - Automaticky vyberte nově vytvořené skripty v Průzkumníku projektu Unity.

  - Sledujte aktivní skript v Průzkumníku projektu Unity (viz dialogové okno **Možnosti).**

  - Duální synchronizace Průzkumníka řešení Visual Studia (dialogové okno **Možnosti).**

  - Přijměte ikony Visual Studia v Průzkumníku projektu Unity.

- **Ladicí program:**

  - Vyberte aktivní cíl ladění ze seznamu uložených nebo naposledy použitých ladicích cílů (dialogové okno **Možnosti).**

  - Vytvořte zarážky funkce na MonoBehavior metody a aplikovat je na více MonoBehavior tříd.

  - Podpora Make Objekt ID v ladicím programu.

  - Podpora počet zásahů zarážky v ladicím programu.

  - Podpora break-on-exception v ladicím programu (Experimental. Viz dialogové **okno Možnosti).**

  - Podpora vytváření objektů a polí při vyhodnocování výrazů v ladicím programu.

  - Podpora null porovnání při vyhodnocení výrazy v ladicím programu.

  - Odfiltrovat zastaralé členy v oknech hodinek ladicího programu.

- **Instalační služby:**

  - Optimalizované nástroje Visual Studio pro registraci rozšíření Unity.

  - Nainstalujte balíček Visual Studio Tools for Unity pro Unity 5.

- **Dokumentace:** Zlepšete výkon generování dokumentace.

- **Průvodci:** Podporujte nové metody MonoBehavior pro Unity 4.6 a Unity 5.

- **Jednota:** Vyhledávání nebezpečných příznaků a vlastní definice v souborech RSP během generování souboru projektu.

- **UI:** V sadě Visual Studio byly přidány nástroje visual studia pro **možnosti jednoty.**

### <a name="bug-fixes"></a>Opravy chyb

- **Průzkumník projektu Unity:**

  - Aktualizujte Průzkumníka projektu Unity po přesunutí nebo přejmenování souborů z Průzkumníka řešení Sady Visual Studio.

  - Při přejmenování souborů v Průzkumníku projektu Unity zachovejte výběry.

  - Zabraňte automatickému rozbalení a sbalení při poklepání souborů v Průzkumníku projektu Unity.

  - Ujistěte se, že nově vybrané soubory jsou viditelné v Průzkumníku projektu Unity.

- **Ladicí program:**

  - Zabránit možné visual studio zmrazit při vyhodnocování výrazů v ladicím programu.

  - Ujistěte se, že volání metody dojít na správné doméně v ladicím programu.

- **Jednoty:**

  - Opravte umístění UnityVS.OpenFile s Unity 5.

  - Opravte umístění pdb2mdb pomocí Unity 5.

  - Zabránit možné výjimce během generování souboru projektu.

  - Zabránit možnému zmrazení při spuštění Unity na OSX.

  - Zpracování vnitřních výjimek.

  - Odešlete protokoly konzoly Unity do seznamu chyb VS.

- **Dokumentace:** Opravte generování dokumentace pro novou dokumentaci unity.

- **Projekt:** V případě potřeby přesuňte a přejmenujte soubory Unity .meta, a to i ve složkách.

- **Průvodci:** Opravte pořadí parametrů metody MonoBehavior při generování kódu.

- **UI:** Podpora motivů sady Visual Studio pro místní nabídku a ikony.

## <a name="1980---20-preview"></a>1.9.8.0 - 2.0 Náhled
Vydáno listopad 12, 2014

### <a name="new-features"></a>Nové funkce

- Podpora pro Visual Studio 2015.

- Kód zbarvení pro unity shaders v Sadě Visual Studio 2015.

- Vylepšená vizualizace hodnot při ladění:

  - Lepší vizualizace pro ArrayLists, Seznamy, Hashtables a slovníky.

  - Zobrazit neveřejné členy a statické členy jako kategorie v sledovaných a místních zobrazeních.

  - Vylepšené zobrazení Unity SerializedProperty pouze vyhodnotit pole hodnoty platné pro vlastnost.

  - Podpora DebuggerDisplayAttribute pro třídy a struktury.

  - Podpora DebuggerTypeProxyAttribute.

- Proveďte vložení monobehaviour metod pomocí našich průvodců respektovat konvence kódování uživatele.

- Implementujte podporu pro šablony textu doby kompilace v projektech generovaných UnityVS.

- Implementujte podporu pro prostředky ResX v UnityVS generované projekty.

- Podporujte otevření stínidla v sadě Visual Studio z unity.

### <a name="bug-fixes"></a>Opravy chyb

- Vyčištění soketů před spuštěním hry v Unity po připojit a play byla spuštěna v sadě Visual Studio. To řeší některé problémy se stabilitou připojení mezi Unity a VS při použití Připojit a play.

- Vyhněte se volání metod v unity skriptovací stroj ladicí rozhraní, které jsou náchylné k zmrazení Unity. To opravuje zmrazení jednoty při připojování ladicího programu.

- Opravte zobrazení zásobníků volání, pokud nejsou k dispozici žádné symboly.

- Neregistrujte zpětné volání protokolu, pokud nemusíme.

## <a name="1920"></a>1.9.2.0

Vydáno 9.října 2014

### <a name="new-features"></a>Nové funkce

- Zlepšete detekci hráčů Unity.

- Při použití našeho otvírače souborů, aby Unity projít číslo řádku, stejně jako název souboru.

- Výchozí online unity dokumentace, pokud neexistuje žádná místní dokumentace.

### <a name="bug-fixes"></a>Opravy chyb

- Opravte potenciální selhání unity při zasažení zarážky po opětovném načtení domény.

- Opravte výjimky zobrazené v konzole Unity při zavírání našich konfiguračních oken nebo o oknech po opětovném načtení domény.

- Opravte detekci 64bits Unity spuštěné místně.

- Oprava filtrování monobehaviours na unity verze v průvodců.

- Opravte chybu, kde byly všechny datové zdroje zahrnuty do souborů projektu, pokud byl filtr rozšíření prázdný.

## <a name="1910"></a>1.9.1.0

Vydáno září 22, 2014

### <a name="new-features"></a>Nové funkce

- Optimalizujte zarážky vazby do zdrojových umístění.

- Podpora přetížených metod v vyhodnocení výrazu ladicího programu.

- Podpora pro zabalení primitiv a typy hodnot v vyhodnocení výrazu ladicího programu.

- Při ladění anonymních metod podporujte opětovné vytváření prostředí místních proměnných jazyka C#.

- Při odstraňování nebo přejmenování souborů z aplikace Visual Studio odstraňte a přejmenujte soubory META.

### <a name="bug-fixes"></a>Opravy chyb

- Opravte zpracování motivů sady Visual Studio. Dříve se dialogová okna s černými motivy mohla jevit jako prázdná.

- Fix Unity zmrazit při připojování ladicího programu při unity je rekompilace.

- Oprava zarážek při ladění vzdálených editorů nebo přehrávačů zkompilovaných v jiném systému.

- Opravte možné selhání sady Visual Studio při zásahu zarážky.

- Opravte zarážky vazba zabránit zarážky zobrazeny jako uvolněna.

- Opravte zpracování oboru proměnných v ladicím programu, abyste se vyhnuli živým proměnným, které se zobrazují mimo rozsah.

- Oprava vyhledávání statických členů v vyhodnocení výrazu ladicího programu.

- Oprava zobrazení typů v vyhodnocení výrazu ladicího programu zobrazíte statická pole a vlastnosti.

- Oprava generování řešení, pokud názvy projektu Unity obsahuje speciální znaky, které Visual Studio zakazuje (Connect problém #948666).

- Opravte balíček Visual Studio Tools Unity, abyste okamžitě přestali odesílat události konzoly poté, co byla možnost nezaškrtnutá (problém připojení #933357).

- Opravte zjišťování odkazů správně obnovit odkazy na nová api, jako je UnityEngine.UI v UnityVS generované projekty.

- Opravte instalační program tak, aby vyžadoval, aby byl visual studio před instalací uzavřen, aby nedošlo k poškození instalací.

- Oprava instalačního programu pro instalaci referenčních sestavení Unity jako správné samostatné součásti sdílené mezi všemi verzemi VSTU.

- Opravte otevírání skriptů pomocí VSTU v 64 bitech verzí Unity.

## <a name="1900"></a>1.9.0.0

Vydáno červenec 29, 2014

### <a name="new-features"></a>Nové funkce

- V okně Připojit jednotu debugger, přidejte možnost zadat vlastní IP a port pro ladění.

- Přidejte možnost konfigurace pro nastavení Unity spustit na pozadí, nebo ne.

- Přidejte možnost konfigurace pro generování pouze souborů řešení a projektů nebo souborů projektu.

- Cíl spuštění: zvolte připojit k jednotě nebo připojit k jednotě a play.

- Zobrazení vícerozměrných polí v ladicím programu.

- Zpracování nové Unity Player ladění porty.

- Zpracování odkazů na nové sestavení Unity, jako je Unity 4.6 GUI sestavení.

- Deconstructs uzávěry správně zobrazit místní proměnné při ladění.

- Deconstructs generované iterátory proměnné do argumentů při ladění.

- Zachovat stav průzkumníka projektu Unity po opětovném načtení projektu.

- Přidejte příkaz pro synchronizaci Průzkumníka projektu Unity s aktuálním dokumentem.

### <a name="bug-fixes"></a>Opravy chyb

- Opravte podmíněné zarážky, jejichž podmínky jsou nastaveny před spuštěním ladicího programu.

- Opravit odkazy na UnityEngine, aby se zabránilo varování.

- Opravte analýzy verzí pro betaverze Unity.

- Opravte problém, kdy by se proměnné nezobrazovaly v okně místních proměnných při zásahu do zarážky nebo krokování.

- Oprava popisů proměnných ve Visual Studiu 2013

- Opravte generování dokumentace Technologie IntelliSense pro Unity 4.5.

- Opravte unity / Visual Studio komunikace po opětovném načtení domény (play/stop v Unity).

- Opravte zpracování částí motivů sady Visual Studio.

> [!IMPORTANT]
> C# převládající jazyk v ekosystému Unity - nové ukázkové prostředky jsou v jazyce C#, dokumentace Unity bude výchozí C# - jsme odstranili naši základní podporu pro UnityScript a Boo lépe zaměřit na c# zkušenosti. V důsledku toho řešení VSTU jsou nyní pouze C# a jsou mnohem rychlejší načíst.

## <a name="1820"></a>1.8.2.0

Vydáno 7.ledna 2014

### <a name="new-features"></a>Nové funkce

- Obejít problém v unity skriptovací homotoru síťové vrstvy na Mavericks pro vzdálené zjišťování editorů.

- Zvládejte nové porty a objevte vzdálené hráče Unity.

- Odkaz unityengine sestavení specifické pro aktuální cíl sestavení.

- Přidání nastavení pro filtrování souborů, které mají být zahrnuty do generovaných projektů.

- Přidáním nastavení zakážete odesílání protokolů konzoly do seznamu chyb sady Visual Studio. To je užitečné, pokud používáte PlayMaker nebo Console Pro, protože v Unity může být registrováno pouze jedno zpětné volání pro příjem protokolů konzoly.

- Přidáním nastavení zakážete generování symbolů ladění mdb. To je užitečné, pokud generujete mdb sami.

### <a name="bug-fixes"></a>Opravy chyb

- Oprava regrese, když soubory otevřené ve VS z Unity >= 4.2 ztratí IntelliSense.

- Opravte naše dialogová okna VS, abyste zvládli vlastní motivy.

- Opravte zavření kontextové nabídky upe.

- Zabránit selhání v Unity při generování sestavení specifické verze, pokud není synchronizováno.

## <a name="1810"></a>1.8.1.0

Vydáno listopad 21, 2013

### <a name="new-features"></a>Nové funkce

- Upraveno Průvodce MonoBehaviour s Unity 4.3 rozhraní API.

- Průvodci MonoBehaviour filtrují rozhraní API Unity v závislosti na verzi, kterou používáte.

- Přidejte odkaz na System.Xml.Linq do projektů unity > 4.1.

- Prettify naše volání Debug.Log nezahrnuje začátek stacktrace ve zprávě.

### <a name="bug-fixes"></a>Opravy chyb

- Opravena chyba, kdy bychom zasahovali do výchozího zpracování souborů JavaScriptu v sadě Visual Studio.

- Opraven bílý pixel, který se objevil ve VS, tentokrát v reálném.

- Opraveno odstranění unityvs.versionspecific sestavení, pokud je označeno jako jen pro čtení SCM.

- Opraveny výjimky při vytváření soketů v balíčku UnityVS.

- Opravena chyba v sadě Visual Studio při načítání obrázků z aplikace Visual Studio.

- Opravena chyba v generování UnityVS.VersionSpecific pro zdrojové sestavení Unity.

- Opraveno možné zmrazení při otevírání soketu v balíčku Unity.

- Opraveno zpracování projektu Unity s pomlčkou (-) v jejich názvu.

- Opraveno otevírání skriptů z Unity, aby nedošlo k záměně pořadí ALT+TAB pro Unity 4.2 a vyšší.

## <a name="1800"></a>1.8.0.0

Vydáno září 24, 2013

### <a name="new-features"></a>Nové funkce

- Výrazně se zlepšila rychlost připojení ladicího programu.

- Automaticky zpracovávat navigaci do souboru a řádku na Unity 4.2 a vyšší.

- Podmíněné zarážky.

- Generátor souborů projektu nyní zpracovává šablony T4.

- Aktualizujte průvodce MonBehavior pomocí nových rozhraní API.

- Dokumentace technologie IntelliSense v c# pro typy Unity.

- Hodnocení aritmetické a logické výrazy.

- Lepší zjišťování vzdálených editorů pro náhled vzdáleného ladění.

### <a name="bug-fixes"></a>Opravy chyb

- Opravena chyba, kdy jsme po odpojení ladicího programu vypustili vlákno do VS.

- Opraven bílý pixel, který se objevil ve VS.

- Opraveno zpracování kliknutí na ikonu stavového řádku.

- Opraveno generování referencí s sestaveními ve složkách Plugins.

- Opraveno vytvoření soketů z balíčku UnityVS v případě výjimek.

- Opravena detekce nových verzí UnityVS.

- Opravena výzva správce licencí po vypršení platnosti licence.

- Opravena chyba, která mohla vykreslit seznam procesů prázdný v detypovém programu pro zpracování okna VS.

- Opravena změna hodnot logických hodnot v místním zobrazení.

## <a name="1220"></a>1.2.2.0

Vydáno 9.července 2013

### <a name="bug-fixes"></a>Opravy chyb

- Zpracování plně kvalifikovaných názvů v vyhodnocení výrazu.

- Opraveno zmrazení související se zpracováním výjimek, kdy nám skriptovací stroj Unity odesílá nesprávná data zásobníku.

- Opraven proces sestavení pro webové cíle.

- Opravena chyba, která se mohla stát, pokud byla spuštěna sada Visual Studio, a že odstraněný soubor byl v seznamu souborů, které se měly otevřít při spuštění.

- Opraven UnityVS.OpenFile pro zpracování souborů bez skriptů, jako jsou kompilované shadery.

- Nyní odkazujeme na Boo.Lang a UnityScript.Lang ze všech projektů Jazyka C#.

- Pevné generování odkazů v projektech, pokud má projekt speciální znaky.

- Řešení: Problém VS, kde volání metody vyřazených projektů by aktivovat více NullReferenceException MessageBox.

- Opraveno zpracování sestav Unity 4.2 Beta.

## <a name="1210"></a>1.2.1.0

Vydáno 9.dubna 2013

### <a name="bug-fixes"></a>Opravy chyb

- Opraveno místní nasazení sestavení Unity pro dokončení kódu v případě chyby vi (například soubory jen pro čtení nebo soubory zamčené visual studio).

- Opravena regrese, kdy otevření skriptu z Unity nezaměřilo soubor, pokud byl již otevřen v sadě Visual Studio.

- Opraven problém s výkonem nového zpracování výjimek.

- Opravena vazba zarážek v některých externích knihovnách DLL.

## <a name="1200"></a>1.2.0.0

Vydáno březen 25, 2013

### <a name="new-features"></a>Nové funkce

- Výrazně se zlepšila rychlost připojení ladicího programu.

- Optimalizované Unity Project Explorer pro větší projekty.

- Ctít nastavení sady Visual Studio přerušit (nebo ne) na zpracované a neošetřené výjimky.

- Honor Visual Studio nastavení volat ToString na místní proměnné.

- Přidejte novou nabídku Ladění -> Připojit Unity ladicí program, který můžete použít k ladění Unity hráčů.

- Zachovat vlastní projekty přidané do řešení UnityVS při generování souboru řešení.

- Přidejte novou klávesovou zkratku CTRL+ALT+M -> CTRL+H, která zobrazí dokumentaci Unity pro funkci Unity nebo člena na pozici stříšky.

- Při kompilaci z aplikace Visual Studio vezměte v úvahu soubory odpovědí kompilátoru (rsp).

- Deconstruct kompilátor generované typy zobrazit proměnné při ladění metody generátoru.

- Zjednodušte vzdálené ladění odebráním nutnosti konfigurovat sdílenou složku na Unity. Nyní stačí mít přístup k projektu Unity z Windows.

- Nainstalujte vlastní profil Unity jako standardní cílový profil .net. To opravuje všechny falešně pozitivní výsledky, které resharper mohl ukázat.

- Obejít chybu skriptovacího modulu Unity, aby se ladicí program nepřerušil v nesprávně registrovaných vláknech.

- Přepracovat otvírač souborů, aby se zabránilo spor ve VS, kde tvrdil, že je schopen otevřít soubory, zatímco shazovat na soubor otevřít požadavek.

- UnityVS nyní žádá o aktualizaci sestavení, když VS vytváří projekt, a ne na ukládání souborů.

### <a name="bug-fixes"></a>Opravy chyb

- Opraven náš vlastní profil .net

- Opravena integrace motivů, která řeší naše problémy s tmavým tématem VS 2012.

- Opravena zkratka rychlého chování ve VS 2012.

- Opraven problém krokování, ke kterému mohlo dojít při ladění a nehlavní vlákno by hit zarážku.

- Opraveno unityscript a boo dokončení aliasů typu, například int.

- Opravena výjimka při psaní nového řetězce UnityScript nebo Boo.

- Opraveny výjimky v nabídkách Unity, když nebylo načteno řešení.

- Opravena chyba UVS-48: psaní dvojité uvozovky někdy způsobuje chybu a přeruší všechny funkce (dokončení kódu, zvýraznění syntaxe atd.).

- Opravena chyba UVS-46: Duplicitní otevřený soubor skriptu (UnityScript) při kliknutí na seznam chyb visual studia.

- Opravena chyba UVS-42: Logo připojení Unity na stavovém řádku nezpracovává události myši ve VS 2012.

- Opravena chyba UVS-44: CTRL+SHIFT+Q není ve VS 2012 k dispozici pro Rychlé monochování.

- Opravena chyba UVS-40: Vybrané položky v Unity Project Explorer jsou nečitelné, když je okno neaktivní v motivu VS2012 "tmavé".

- Opravena chyba UVS-39: Problém tokenizing uvozených řetězců.

- Opravena chyba UVS-35: Vyvolat ToString na objektech při kontrole proměnných.

- Opravena chyba UVS-27: Goto Symbol window nekonzistence s "tmavým" tématem ve VS2012.

- Opravena chyba UVS-11: Locals v korutinách.

## <a name="1100---beta-release"></a>1.1.0.0 - Beta verze
Vydáno březen, 9, 2013

## <a name="10130"></a>1.0.13.0
Vydáno 21.ledna 2013

### <a name="bug-fixes"></a>Opravy chyb

- Opraveno uzamčení sady Visual Studio, ke kterému může dojít, pokud cílové ladění odesílá neplatné události vlákna. To by se obvykle stalo při ladění vzdálené Unity na OSX.

- Opraveno uzamčení sady Visual Studio, ke kterému může dojít, pokud výjimka vypne ladicí program.

- Opravena naše MonoBehavior pomocné soubory, když C# MonoBehavior je v oboru názvů.

- Opraveny popisky popisů pro UnityScript v Visual Studiu 2012.

- Opraveno generování projektu, když jsou změněny pouze ladicí konstanty z Unity.

- Opravena navigace pomocí klávesnice v Průzkumníku projektu Unity.

- Opraveno vybarvení UnityScript u řídicích řetězců.

- Opraven náš otvírač souborů, abychom lépe uhádli název projektu při použití mimo Unity. To je nezbytné, když uživatel používá třetí část otvírače souborů v Unity, který deleguje na UnityVS.

- Opraveno zpracování dlouhých zpráv odeslaných z Unity do UnityVS. Před tím, dlouhé zprávy by mohly dojít k chybě naše zprávy část UnityVS. V důsledku toho někdy UnityVS neotevře soubor z Unity.

## <a name="10120"></a>1.0.12.0
Vydáno 3.ledna 2013

### <a name="bug-fixes"></a>Opravy chyb

- Opraveno uzamčení sady Visual Studio, ke kterému mohlo dojít, když visual studio spouštělo zarážku.

- Opravena chyba, kdy některé zarážky nebyly zasaženy po překompilované maješce Unity.

- Opraven ladicí program, aby bylo správné upozornění sady Visual Studio, když byly zarážky nevázané.

- Byl opraven problém s registrací, který mohl zabránit ladicímu programu sady Visual Studio k ladění nativních programů.

- Opravena výjimka, ke které mohlo dojít při vyhodnocování výrazů UnityScript a Boo.

- Opravena regrese, kdy změna úrovně rozhraní .net API v Unity nespustila aktualizaci souborů projektu.

- Opravena závada rozhraní API, kdy se uživatelský kód nemohl účastnit obslužné rutiny zpětného volání protokolu.

## <a name="10110"></a>1.0.11.0
Vydáno listopad 28, 2012

### <a name="new-features"></a>Nové funkce

- Oficiální podpora Unity 4.

- Manipulace se skripty z Průzkumníka projektu Unity.

- Integrace v okně Navigace na visual studio.

- Analýza zprávy konzoly Info, takže kliknutím na seznam chyb se dostanete na první zásobník se symboly.

- Přidejte [rozhraní API,](../cross-platform/customize-project-files-created-by-vstu.md) které umožní uživateli podílet se na generování projektu.

- Přidejte [rozhraní API,](../cross-platform/share-the-unity-log-callback-with-vstu.md) aby se uživatel mohl účastnit logcallbacku.

### <a name="bug-fixes"></a>Opravy chyb

- Opravena regrese na pozadí Průzkumníka projektu Unity v sadě Visual Studio 2012.

- Opraveno generování projektu pro uživatele úplného profilu .net.

- Opraveno generování projektu pro uživatele webového cíle.

- Opraveno generování projektu tak, aby zahrnovalo symboly kompilace DEBUG a TRACE jako Unity.

- Opravenpád při použití speciálních znaků v našem okně Goto Symbol.

- Opravena chyba, pokud nemůžeme vložit naši ikonu do stavového řádku sady Visual Studio.

## <a name="10100"></a>1.0.10.0
Vydáno 9.října 2012

### <a name="bug-fixes"></a>Opravy chyb

- Opraveno pozadí Průzkumníka projektu Unity v sadě Visual Studio 2010.

- Opraveno zmrazení sady Visual Studio, ke kterému by mohlo dojít, pokud by se UnityVS pokusil připojit ladicí program k unity, jehož rozhraní ladicího programu dříve havarovalo.

- Opraveno zmrazení sady Visual Studio, ke kterému mohlo dojít při nastavení zarážky a došlo k opětovnému načtení domény AppDomain.

- Opraven způsob načítání sestavení z Unity, aby se zabránilo zamykání souborů a zmást proces sestavení Unity.

## <a name="1090"></a>1.0.9.0

Vydáno 3.října 2012

### <a name="bug-fixes"></a>Opravy chyb

- Opraveno generování projektu, když projekt Unity obsahuje skutečné prostředky JavaScriptu.

- Opraveno zpracování chyb při vyhodnocení výrazu.

- Opraveno nastavení nových hodnot pro pole typů hodnot.

- Opraveny možné vedlejší účinky při najetí nad výrazy z editoru kódu.

- Opraven způsob vyhledávání typů v načtených sestaveních pro vyhodnocení výrazů.

- Opravena chyba UVS-21: Vyhodnocení přiřazení objektů Unity nemá žádný vliv.

- Opravena chyba UVS-21: Neplatný ukazatel při vyhodnocování vyvolání metody k unity math api.

## <a name="1080"></a>1.0.8.0

Vydáno září 26, 2012

### <a name="bug-fixes"></a>Opravy chyb

- Opraven způsob, jakým náš skript otvírák získal cestu k projektu, aby se ujistil, že je schopen otevřít visual studio i skripty.

- Opravena chyba s zarážky vytvořenými během relace ladění, která mohla způsobit uzamčení sady Visual Studio.

- Opravenzpůsob registrace UnityVS v sadě Visual Studio 2010.

## <a name="1070"></a>1.0.7.0

Vydáno září 14, 2012

### <a name="new-features"></a>Nové funkce

- Podpora visual studia 2012.

### <a name="bug-fixes"></a>Opravy chyb

- Opraveno generování souborů projektu Editor a Plugins tak, aby odpovídaly chování Unity.

- Opraven překlad symbolů .pdb na Unity 4.

> [!IMPORTANT]
> Kvůli podpoře visual studia 2012 jsme museli přejmenovat několik souborů a přesunout některé další. UnityVS balíček importunity je nyní pojmenovánunityVS 2010 nebo UnityVS 2012, pro příslušně Visual Studio 2010 a Visual Studio 2012. Tato verze také vyžaduje, aby unityvs soubory projektu jsou obnoveny.

## <a name="1060---internal-build"></a>1.0.6.0 - Interní sestavení
Vydáno září 12, 2012

## <a name="1050"></a>1.0.5.0

Vydáno září 10, 2012

### <a name="bug-fixes"></a>Opravy chyb

- Opraveno generování souborů projektu, když skripty nebo shadery měly neplatný znak XML.

- Opraveno zjištění instancí Unity při připojení Unity k serveru Asset. To vyvolalo selhání otevřít soubory z Unity a automatické připojení ladicího programu Visual Studio.

## <a name="1040"></a>1.0.4.0

Vydáno září 5, 2012

### <a name="new-features"></a>Nové funkce

- Automatický převod ladicích symbolů v Unity.

    Pokud máte sestavení .NET .dll s přidruženým .pdb ve složce Asset, jednoduše znovu importujte sestavení a UnityVS převede soubor .pdb do souboru ladicích symbolů, kterému rozumí skriptovací modul Unity, a budete moci vstoupit do sestavení .NET z UnityVS.

### <a name="bug-fixes"></a>Opravy chyb

- Opravena chyba UnityVS při ladění způsobené výjimkami vyzývaným metodami nebo vlastnostmi uvnitř Unity.

## <a name="1030"></a>1.0.3.0

Vydáno září 4, 2012

### <a name="new-features"></a>Nové funkce

- Nová možnost konfigurace zakázat použití UnityVS otevřít soubory z Unity.

### <a name="bug-fixes"></a>Opravy chyb

- Pevné generování odkazů na UnityEditor pro projekty bez editoru.

- Opravena definice UNITY_EDITOR symbolu pro projekty bez editoru.

- Opravena náhodná havárie VS způsobená naším vlastním stavovým panelem.

## <a name="1020"></a>1.0.2.0

Vydáno 30.srpna 2012

### <a name="bug-fixes"></a>Opravy chyb

- Opraven konflikt s ladicím programem PythonTools.

- Opraveny odkazy na Mono.Cecil.

- Opravena chyba v tom, jak byly skriptovací sestavení načteny z Unity s Unity 4 b7.

## <a name="1010"></a>1.0.1.0

Vydáno 28.srpna 2012

### <a name="new-features"></a>Nové funkce

- Podpora náhledu pro Unity 4.0 Beta.

### <a name="bug-fixes"></a>Opravy chyb

- Opravena kontrola vlastností, které vyvolávají výjimky.

- Opravensestup do základních objektů při kontrole objektů.

- Opraven prázdný rozevírací seznam pro kurzor v průvodci MonoBehavior.

- Opraveno dokončení knihovny DLL ve složce Asset pro UnityScript a Boo.

## <a name="1000---initial-release"></a>1.0.0.0 - Počáteční vydání
Vydáno 22.srpna 2012
