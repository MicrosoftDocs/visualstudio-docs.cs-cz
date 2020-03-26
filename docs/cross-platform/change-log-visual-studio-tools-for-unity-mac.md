---
title: Protokol změn (Nástroje visual ateliéru pro jednotu, Mac) | Dokumenty společnosti Microsoft
ms.custom: ''
ms.date: 12/02/2019
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 33a6ac54-d997-4308-b5a0-af7387460849
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 5599153f79b273249e93c48aaa197214d92f5fe7
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80232923"
---
# <a name="change-log-visual-studio-tools-for-unity-mac"></a>Protokol změn (Visual Studio Tools for Unity, Mac)

Visual Studio Tools for Unity change log.

## <a name="2520"></a>2.5.2.0

Vydáno 23.března 2020

### <a name="bug-fixes"></a>Opravy chyb

- **Ladicí program:**

  - Opravena registrace závitů při připojení.

## <a name="2510"></a>2.5.1.0

Vydáno 3.

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidáno tlumič [`IDE0051`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0008.md)pro . Soukromé metody používané s Invoke, InvokeRepeating, StartCoroutine nebo StopCoroutine by neměly být označeny jako nepoužívané.

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opravena dokumentace OnDrawGizmos/OnDrawGizmosVybraná

- **Hodnocení:**

  - Opravena kontrola argumentů lambda.

## <a name="2501"></a>2.5.0.1

Vydáno 19.února 2020

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opravena [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/UNT0006.md) diagnostická kontrola nesprávného podpisu zprávy. Při kontrole typů s více úrovněmi dědičnosti může tato `warning AD0001: Analyzer 'Microsoft.Unity.Analyzers.MessageSignatureAnalyzer' threw an exception of type 'System.ArgumentException' with message 'An item with the same key has already been added`diagnostika selhat s následující zprávou: .

## <a name="2500"></a>2.5.0.0

Vydáno 22.ledna 2020

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidána podpora pro soubory HLSL.
  
  - Přepnul do nového dialogového okna složky.
  
  - Přepnul do nové mřížky dostupných vlastností pro nastavení.

  - Přidáno tlumič [`IDE0051`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0006.md)pro . Soukromá pole `SerializeField` s atributem by neměla být označena jako nepoužitá.

  - Přidáno tlumič [`CS0649`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0007.md)pro . Pole s `SerializeField` atributem by neměla být označena jako nepřiřazená.  

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opraveno generování`GenerateTargetFrameworkMonikerAttribute` projektu (cíl nebyl vždy správně umístěn)

- **Hodnocení:**

  - Opraveno vyhodnocení řetězce (nepoužití volání ToString()

## <a name="2420"></a>2.4.2.0

Vydáno prosinec 3, 2019

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opravena diagnostika s uživatelsky definovanými rozhraními.

  - Opraveny rychlé popisky s poškozenými výrazy.
  
## <a name="2410"></a>2.4.1.0

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

## <a name="2400"></a>2.4.0.0

Vydáno říjen 15, 2019

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidáno supresorové pro `IDE0060` (nepoužitý parametr) pro všechny zprávy Unity.

  - Byl přidán rychlý popis pro `TooltipAttribute`pole označená písmenem . (To bude fungovat pro jednoduchý get přistupující ho pomocí tohoto pole také).

## <a name="2330"></a>2.3.3.0

Vydáno září 23, 2019

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidánnový supresor pro IDE0060, aby se zabránilo ide z zobrazení rychlé opravy odebrat nepoužívané parametry.
    - `USP0005`for `IDE0060`: Unity zprávy jsou vyvolány unity runtime.

## <a name="2320"></a>2.3.2.0

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

## <a name="2310"></a>2.3.1.0

Vydáno září 4, 2019

### <a name="new-features"></a>Nové funkce

- **Hodnocení:**

  - Přidána podpora pro lepší typ `List<object>` zobrazení, `List'1[[System.Object, <corlib...>]]`tj.

  - Byla přidána podpora přístupu členů `p->data->member`ukazatele, tj.

  - Byla přidána podpora implicitních konverzí v inicializačních polích, tj. `new byte [] {1,2,3,4}`

  - Přidána podpora pro hex editor při kontrole bajtových polí a řetězců.

## <a name="2300"></a>2.3.0.0

Vydáno srpen 13, 2019

### <a name="bug-fixes"></a>Opravy chyb

- **Hodnocení:**

  - Opraveny problémy s krokování s výjimkami.

  - Opraveno vyhodnocení pseudoidentifikátorů (například $exception).

  - Zabránit selhání při dereferencování neplatných adres.  

  - Opraven problém s nezatíženými aplikačními doménami.

## <a name="2200"></a>2.2.0.0

Vydáno červenec 25, 2019

### <a name="bug-fixes"></a>Opravy chyb

- **Hodnocení:**

  - Opravena kontrola s typy IntPtr.

- **Ladicí program:**

  - Opraveno zpracování zarážek a zarážek funkcí.

## <a name="2130"></a>2.1.3.0

Vydáno červenec 9, 2019

### <a name="new-features"></a>Nové funkce

- **Ladicí program:**

  - Přidána podpora pro zachycení podtříd výjimek.

  - Přidána podpora pro protokol MDS 2.51.

- **Integrace:**

  - Přidána podpora pro soubory asmdef.

  - Přepněte do režimu přejmenování při přidání souboru ze šablony (napodobovat chování Editoru jednoty).

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opraveno zpracování poškozených zpráv při komunikaci s Unity Players.

- **Hodnocení:**

  - Opraveno zpracování oborů názvů ve výrazech.

## <a name="2120"></a>2.1.2.0

Vydáno červenec 2, 2019

### <a name="bug-fixes"></a>Opravy chyb

- **Hodnocení:**

  - Opraveno zasílání zpráv o chybách s neoddělitelnými výrazy.

## <a name="2110"></a>2.1.1.0

Vydáno červen 27, 2019

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Aktualizováno Rozhraní API pro monochování na 2019.1.

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opraven výkon aplikace Unity Project Explorer.

  - Opravena upozornění hlášení a chyby pro výstup, když je povoleno zjednodušené sestavení.

  - Opraven análový výkon sestavení.

## <a name="2100"></a>2.1.0.0

Vydáno červen 20, 2019

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Zakázáno úplné sestavení pro projekty Unity, ve prospěch použití chyb a upozornění Technologie IntelliSense. Unity vytvoří řešení visual studio s projekty knihovny tříd, které představují, co Unity dělá interně. Jak již bylo řečeno, výsledek sestavení v sadě Visual Studio se nikdy nepoužívá nebo zvedl Unity jako jejich kompilace kanálu je uzavřena. Vytváření v sadě Visual Studio je jen spotřebovává prostředky pro nic za nic. Pokud potřebujete úplné sestavení, protože máte nástroje nebo nastavení, které na něm závisí, můžete tuto optimalizaci zakázat (Nastavení/Nástroje pro jednotu/Zakázat úplné sestavení projektů).
  
  - Přidána podpora balíčků Unity v UPE. Viditelné jsou pouze odkazované balíčky (pomocí souboru manifest.json ve `Packages` složce) a místní balíčky (vložené do `Packages` složky).

## <a name="2021"></a>2.0.2.1

Vydáno květen 30, 2019

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidána vlastní ikona pro cíle provádění Unity.

## <a name="2020"></a>2.0.2.0

Vydáno duben 2, 2019

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidána podpora pro automatické obnovení databáze datových zdrojů Unity při ukládání. To je ve výchozím nastavení povoleno a při ukládání skriptu v sadě Visual Studio se spustí rekompilace na straně Unity. Tuto funkci můžete zakázat v nástrojích\Možnosti\Nástroje pro Unity\Refresh Unity AssetDatabase při uložení.

  - Přidána podpora pro nastavení preferované instalace jednoty pro dokumentaci offline.

  - Přidáno kontextové menu pro nový editor.

### <a name="bug-fixes"></a>Opravy chyb

- **Ladicí program:**

  - Opraveno filtrování sestav a kontrola rámů s prázdnými rámy.

## <a name="2011"></a>2.0.1.1
 
 Vydáno březen 26, 2019

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Dočasně nastavit Mono výchozí a použitelné ladicí program pro tuto velmi specifickou verzi.

## <a name="2006"></a>2.0.0.6

Vydáno březen 26, 2019

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidána podpora pro "Připojit k Jednotě a play".

## <a name="2005"></a>2.0.0.5

Vydáno březen 20, 2019

### <a name="new-features"></a>Nové funkce

- **Generování projektu:**

  - Při zpracování souboru řešení zachovejte externí vlastnosti.
  
- **Hodnocení:**

  - Přidána podpora pro názvy s kvalifikací aliasů (prozatím pouze globální obor názvů). Vyhodnocení výrazu tedy nyní přijímá typy pomocí formuláře global::namespace.type.

  - Přidána `pointer[index]` podpora formuláře, který je sémanticky identický s formulářem dereference `*(pointer+index)` ukazatele.

## <a name="2004"></a>2.0.0.4

Vydáno březen 5, 2019

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Bylo `ScriptableObject` aktualizováno rozhraní API.

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Byly odebrány obory názvů ze šablon.

## <a name="2003"></a>2.0.0.3
 
 Vydáno březen 5, 2019

### <a name="new-features"></a>Nové funkce

- **Generování projektu:**

  - Veřejná a serializovaná pole již nebudou způsobovat upozornění. Automaticky jsme potlačili `CS0649` upozornění `IDE0051` a kompilátoru v projektech Unity, které tyto zprávy vytvořily.

- **Integrace:**

  - Výzva k připojení k určité instanci, pokud je spuštěn více než jeden proces Unity.

- **Hodnocení:**

  - Přidána podpora pro místní funkce.

### <a name="bug-fixes"></a>Opravy chyb

- **Ladicí program:**

  - Opraveno čtení vlastního atributu u pojmenovaných argumentů při použití starých verzí protokolu.

## <a name="2002"></a>2.0.0.2

Vydáno únor 4, 2019

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Bylo aktualizováno rozhraní API pro monochování.

### <a name="bug-fixes"></a>Opravy chyb

- **Ladicí program:**

  - Opraveno nastavení primitivních hodnot v ladicím programu.

## <a name="2001"></a>2.0.0.1

Vydáno prosinec 4, 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Pevná instalace balíček samostatné hostojánství.

## <a name="2000"></a>2.0.0.0
 Vydáno prosinec 4, 2018

### <a name="new-features"></a>Nové funkce

- **Ladicí program:**

  - Byl nahrazen ladicím programem Unity na Macu stejným ladicím programem Unity ze systému Windows.

  - Nahradil NRefactory ve prospěch Roslyn pro vyhodnocení výrazu.

  - Přidána podpora pro ukazatele: dereference, casting a ukazatel aritmetické (Unity 2018.2+ a nový runtime jsou požadovány pro toto).

  - Přidána podpora pro zobrazení ukazatele pole (například v jazyce C++). Vezměte výraz ukazatele a potom přidejte čárku a počet prvků, které chcete zobrazit.

  - Přidána podpora pro asynchronní konstrukce.

  - Přidána podpora pseudoproměnných (výjimky a identifikátory objektů).

### <a name="bug-fixes"></a>Opravy chyb

- **Ladicí program:**

  - Opraveno vyhodnocení výrazů poškozenými nebo nepodporovanými výrazy.

## <a name="1700"></a>1.7.0.0

Vydáno listopad 13, 2018

### <a name="new-features"></a>Nové funkce

- **Ladicí program:**

  - V dialogovém okně připojit byl přidán o více informací o klientovi (IP, název počítače).

### <a name="bug-fixes"></a>Opravy chyb

- **Ladicí program:**

  - Opravena zablokování v knihovně slouží ke komunikaci s ladicí modul Unity, takže Visual Studio nebo Unity zmrazit, zejména při stisknutí 'Připojit k jednotě' nebo restartování hry.

- **Integrace:**

  - Opravena aktivace pluginu Unity, když byl vybrán jiný výchozí editor.

  - Opraveno vytvoření šablony souboru Unity.

## <a name="1602"></a>1.6.0.2

Vydáno červenec 24, 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Vrácení zpět řešení pro chybu výkonu Unity, která byla opravena Unity.

## <a name="1601"></a>1.6.0.1

Vydáno červenec 10, 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Pevná podpora zbarvení kódu Shader.

## <a name="1600"></a>1.6.0.0

Vydáno červen 26, 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Průvodci:**

  - Opraven překlep se zprávou OnApplicationFocus.

- **Generování projektu:**

  - Přechodné řešení pro chybu výkonu Unity: cache MonoIslands při generování projektů.

  - Při použití nového runtime Unity již nepřevádějí přenosné pdb na mdb.

## <a name="1502"></a>1.5.0.2

Vydáno duben 18, 2018

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidána podpora pro základní dokončení kódu Shader.

  - Přidána podpora pro přepínání komentářů v souborech Shader.

## <a name="1501"></a>1.5.0.1

Vydáno březen 28, 2018

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidána podpora pro další šablony v Průzkumníku projektu Unity.

## <a name="1500"></a>1.5.0.0

Vydáno březen 21, 2018

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidána podpora pro detekci a připojení k přehrávačům Android připojeným přes USB.

## <a name="1403"></a>1.4.0.3

Vydáno březen 5, 2018

### <a name="new-features"></a>Nové funkce

- **Generování projektu:**

  - Přidána podpora pro nový generátor projektu v Unity 2018.1.

- **Integrace:**

  - Přidán panel možností pro vyhrazená nastavení.

## <a name="1402"></a>1.4.0.2

Vydáno leden 24, 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Opravena detekce verze Mono.

- **Integrace:**

  - Opraveny problémy s časováním s aktivací 2018.1 a aktivací pluginů.

  - Opravena oznámení při zjišťování nového hráče.

## <a name="1401"></a>1.4.0.1

Vydáno leden 23, 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opraveny složky Rozbalení/sbalení při poklepání

## <a name="1400"></a>1.4.0.0

Vydáno prosinec 13, 2017

### <a name="new-features"></a>Nové funkce

- **Generování projektu:**

  - Byla přidána podpora pro standard .NET.

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opraven automatický převod symbolu ladění pdb na mdb.

## <a name="1301"></a>1.3.0.1

Vydáno prosinec 12, 2017

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opraveno nepřímé volání EditorPrefs.GetBool, které mělo vliv na inspektora při pokusu o změnu velikosti pole.

- **Průvodci:**

  - Před vložením metody aktualizujte kontext roslyn.

## <a name="1300"></a>1.3.0.0

Vydáno listopad 20, 2017

### <a name="new-features"></a>Nové funkce

- **Průvodci:**

  - Byl přidán průvodce "Implementovat zprávu unity".

  - Přidána podpora pro nové rozhraní API pro dokončení ve VS pro Mac 7.4.

## <a name="1200"></a>1.2.0.0

Vydáno říjen 23, 2017

### <a name="new-features"></a>Nové funkce

- **Ladicí program:**

  - Přidána podpora pro přenosné soubory ladicí symbol.

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Opravena další přípona .dll nesprávně přidaná k názvu souboru sestavení.

  - Nevynucovat AllowAttachedDebuggingOfEditor Unity příznak jako výchozí je nyní 'true'.

## <a name="1103"></a>1.1.0.3

Vydáno říjen 23, 2017

### <a name="new-features"></a>Nové funkce

- **Generování projektu:**

  - Přidána podpora pro profil .NET 4.6.

## <a name="1102"></a>1.1.0.2

Vydáno 8.

### <a name="new-features"></a>Nové funkce

- **Ladicí program:**

  - Spusťte připojit k procesu dialogového okna, pokud si nejste jisti, které Unity připojit k.

- **Generování projektu:**

  - Při použití Unity 5.6 vždy povolte nebezpečný přepínač kompilace.

## <a name="1101"></a>1.1.0.1

Vydáno červenec 20, 2017

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidána podpora lokalizovaných prostředků.

## <a name="1100"></a>1.1.0.0

Vydáno červenec 12, 2017

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidána podpora pro připojení k přehrávačům a editorům prostřednictvím okna Připojit ke procesu.

- **Generování projektu:**

  - Opraveny odkazy na názvy sestavení se soubory mcs.rsp.

  - Přidána podpora pro kompilační jednotky assembly.json.

  - Opravena definice s úrovněmi rozhraní API.

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opravena chybová zpráva shaderu při kompilaci.

## <a name="1001"></a>1.0.0.1

Vydáno květen 4, 2017

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opraveno aktivní sledování dokumentů s hybridními a běžnými projekty.

## <a name="1000"></a>1.0.0.0

Vydáno květen 3, 2017
