---
title: Protokol změn (Visual Studio Tools for Unity, Mac) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/18/2019
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 33a6ac54-d997-4308-b5a0-af7387460849
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 897851055bd2eacc10edea9fdff2ab3ecd61b963
ms.sourcegitcommit: 88f576ac32af31613c1a10c1548275e1ce029f4f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71185963"
---
# <a name="change-log-visual-studio-tools-for-unity-mac"></a>Protokol změn (Visual Studio Tools for Unity, Mac)

Protokol změn Visual Studio Tools for Unity.

## <a name="2330"></a>2.3.3.0

Vydáno 23. září 2019

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidání nového Suppressor pro IDE0060, aby se zabránilo tomu, aby se IDE zobrazovala Rychlá oprava pro odebrání nepoužitých parametrů.
    - `USP0005`pro `IDE0060`: Zprávy Unity jsou vyvolány modulem runtime Unity.

## <a name="2320"></a>2.3.2.0

Vydáno 16. září 2019

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Provedli jsme porozumění, že Visual Studio má pro projekty Unity přidat novou diagnostiku specifickou pro Unity. Také jsme zvýšili inteligenci integrovaného vývojového prostředí (IDE) tím, že jsme potlačili obecnou diagnostiku C#, která se nevztahuje na projekty Unity. Například rozhraní IDE nebude zobrazovat rychlou opravu pro změnu proměnné inspektoru, `readonly` která by zabránila v úpravách proměnné v editoru Unity.
    - `UNT0001`: Zprávy Unity jsou volány modulem runtime, i když jsou prázdné, proto je nedeklarujte, aby nedocházelo ke zbytečnému zpracování modulem runtime Unity.
    - `UNT0002`: Porovnávání značek pomocí rovnosti řetězců je pomalejší než integrovaná metoda CompareTag.
    - `UNT0003`: Kvůli bezpečnosti typů se upřednostňuje použití obecné formy getComponent.
    - `UNT0004`: Zpráva Update je závislá na snímkové frekvenci a měla by místo Time.fixedDeltaTime používat Time.deltaTime.
    - `UNT0005`: Zpráva FixedUpdate je nezávislá na snímkové frekvenci a měla by místo Time.deltaTime používat Time.fixedDeltaTime.
    - `UNT0006`: Pro tuto zprávu Unity byl zjištěn nesprávný podpis metody.
    - `UNT0007`: Unity přepisuje operátor porovnání s hodnotou null pro objekty Unity, které nejsou kompatibilní se sloučením s hodnotou null.
    - `UNT0008`: Unity přepisuje operátor porovnání s hodnotou null pro objekty Unity, které nejsou kompatibilní s šířením hodnoty null.
    - `UNT0009`: Při použití atributu InitializeOnLoad pro třídu musíte poskytnout statický konstruktor. Atribut InitializeOnLoad zajistí, že bude volán při spuštění editoru.
    - `UNT0010`: Objekty MonoBehaviour by se měly vytvářet jen pomocí metody AddComponent(). Objekt MonoBehaviour je komponenta, která musí být připojená k objektu GameObject.
    - `UNT0011`: Objekt ScriptableObject by se měl vytvářet jen pomocí metody CreateInstance(). Objekt ScriptableObject musí být vytvořený modulem Unity, aby zpracovával metody zpráv Unity.
    - `USP0001`pro `IDE0029`: Objekty Unity by neměly používat slučování s hodnotou null.
    - `USP0002`pro `IDE0031`: Objekty Unity by neměly používat šíření hodnoty null.
    - `USP0003`pro `IDE0051`: Zprávy Unity jsou vyvolány modulem runtime Unity.
    - `USP0004`pro `IDE0044`: Pole s atributem SerializeField by neměla být určena jen pro čtení.

## <a name="2310"></a>2.3.1.0

vydáno 4. září 2019

### <a name="new-features"></a>Nové funkce

- **Vyhodnocení:**

  - Přidání podpory pro lepší zobrazení typu, tj. `List<object>` `List'1[[System.Object, <corlib...>]]`místo.

  - Přidání podpory pro přístup ke členu ukazatele, `p->data->member`tj.

  - Přidání podpory pro implicitní převody v inicializátorech pole, tj. `new byte [] {1,2,3,4}`

  - Byla přidána podpora šestnáctkového editoru při kontrole bajtových polí a řetězců.

## <a name="2300"></a>2.3.0.0

vydáno 13. srpna 2019

### <a name="bug-fixes"></a>Opravy chyb

- **Vyhodnocení:**

  - Opravili jsme problémy krokování s výjimkami.

  - Pevné vyhodnocení pseudo identifikátorů (například $exception).

  - Zabraňte selhání při přesměrování neplatných adres.  

  - Opravili jsme problém s uvolněnými doménami AppDomain.

## <a name="2200"></a>2.2.0.0

Vydáno 25. července 2019

### <a name="bug-fixes"></a>Opravy chyb

- **Vyhodnocení:**

  - Pevná kontrola s použitím typů IntPtr.

- **Ladicí program:**

  - Pevné zpracování catchpoints a zarážek funkcí.

## <a name="2130"></a>2.1.3.0

vydáno 9. července 2019

### <a name="new-features"></a>Nové funkce

- **Ladicí program:**

  - Přidání podpory pro zachycení podtříd výjimek.

  - Byla přidána podpora protokolu MDS 2,51.

- **Integrace:**

  - Přidání podpory pro soubory asmdef

  - Přepne do režimu přejmenování při přidání souboru ze šablony (pro napodobení chování editoru Unity).

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Pevné zpracování poškozených zpráv při komunikaci s přehrávači Unity.

- **Vyhodnocení:**

  - Pevné zpracování oborů názvů ve výrazech.

## <a name="2120"></a>2.1.2.0

vydáno 2. července 2019

### <a name="bug-fixes"></a>Opravy chyb

- **Vyhodnocení:**

  - Bylo opraveno zasílání zpráv o chybách s neanalyzovanými výrazy.

## <a name="2110"></a>2.1.1.0

Vydáno 27. června 2019

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Rozhraní MonoBehaviour API se aktualizovalo na 2019,1.

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Pevný výkon Průzkumníka projektů Unity.

  - Opravená upozornění a chyby při generování výstupu, když je povolené zjednodušené sestavení.

  - Pevný výkon pro odlehčené sestavení.

## <a name="2100"></a>2.1.0.0

Vydáno 20. června 2019

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Pro projekty Unity se zakázalo úplné sestavení, a to na základě chyb a upozornění technologie IntelliSense. Ve skutečnosti Unity vytvoří řešení sady Visual Studio s projekty knihoven tříd, které reprezentují, co Unity interně dělá. To se říká, výsledek sestavení v sadě Visual Studio se nikdy nepoužívá nebo nezískala v Unity, protože je jejich kanál kompilace uzavřený. Sestavování v aplikaci Visual Studio právě spotřebovává prostředky pro nic. Pokud potřebujete úplné sestavení, protože máte nástroje nebo nastavení, které na něm závisí, můžete tuto optimalizaci zakázat (nastavení/nástroje pro Unity nebo zakázat úplné sestavení projektů).
  
  - Přidala se podpora pro balíčky Unity v UPE. Jsou viditelné pouze odkazované balíčky (používající manifest. JSON `Packages` ve složce) a místní balíčky (vložené `Packages` do složky).

## <a name="2021"></a>2.0.2.1

Vydáno 30. května 2019

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidání vlastní ikony pro cíle provádění Unity

## <a name="2020"></a>2.0.2.0

Vydáno 2. dubna 2019

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidání podpory pro automatickou aktualizaci databáze assetů v Unity při uložení Tato možnost je ve výchozím nastavení povolená a při ukládání skriptu do sady Visual Studio aktivuje novou kompilaci na straně Unity. Tuto funkci můžete zakázat v Tools\Options\Tools pro AssetDatabase v Unity\Refresh Unity při uložení.

  - Přidání podpory pro nastavení upřednostňované instalace Unity pro offline dokumentaci

  - Přidala se místní nabídka pro nový editor.

### <a name="bug-fixes"></a>Opravy chyb

- **Ladicí program:**

  - Pevné filtrování sestavení a kontrola snímků s prázdnými snímky.

## <a name="2011"></a>2.0.1.1
 
 Vydáno 26. března 2019

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Dočasně nastavte mono výchozí a jenom použitelný ladicí program pro tuto velmi specifickou verzi.

## <a name="2006"></a>2.0.0.6

Vydáno 26. března 2019

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Byla přidána podpora "připojit k Unity a hrát".

## <a name="2005"></a>2.0.0.5

Vydáno 20. března 2019

### <a name="new-features"></a>Nové funkce

- **Generování projektu:**

  - Při zpracování souboru řešení zachovat externí vlastnosti.
  
- **Vyhodnocení:**

  - Byla přidána podpora názvů kvalifikovaných aliasů (pouze globální obor názvů pro nyní). Proto vyhodnocovací filtr výrazů nyní přijímá typy pomocí formuláře Global:: Namespace. Type.

  - Přidání podpory pro `pointer[index]` formulář, která je sémanticky totožná s odkazem `*(pointer+index)` na odkazy na ukazatel.

## <a name="2004"></a>2.0.0.4

Vydáno 5. března 2019

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Rozhraní API `ScriptableObject` se aktualizovalo.

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Z šablon se odebraly obory názvů.

## <a name="2003"></a>2.0.0.3
 
 Vydáno 5. března 2019

### <a name="new-features"></a>Nové funkce

- **Generování projektu:**

  - Veřejná a serializovaná pole už nebudou způsobovat upozornění. Automaticky jsme potlačili `CS0649` upozornění kompilátoru a `IDE0051` v projektech Unity, která tyto zprávy vytvořila.

- **Integrace:**

  - Pokud více než jeden proces Unity běží, zobrazí se výzva k připojení ke konkrétní instanci.

- **Vyhodnocení:**

  - Byla přidána podpora místních funkcí.

### <a name="bug-fixes"></a>Opravy chyb

- **Ladicí program:**

  - Bylo vyřešeno čtení vlastního atributu u pojmenovaných argumentů při použití starších verzí protokolu.

## <a name="2002"></a>2.0.0.2

Vydáno 4. února 2019

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Aktualizace rozhraní API MonoBehaviour

### <a name="bug-fixes"></a>Opravy chyb

- **Ladicí program:**

  - Pevné nastavení primitivních hodnot v ladicím programu.

## <a name="2001"></a>2.0.0.1

Vydáno 4. prosince 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Pevný balíček pevného instalačního balíčku.

## <a name="2000"></a>2.0.0.0
 Vydáno 4. prosince 2018

### <a name="new-features"></a>Nové funkce

- **Ladicí program:**

  - Nahradili jsme ladicí program Unity na Macu stejným základním ladicím programem Unity z Windows.

  - Nahradili jsme NRefactory a upřednostňujeme Roslyn pro vyhodnocení výrazu.

  - Přidání podpory pro ukazatele: dereference, přetypování a aritmetické operace (2018.2 Unity + a nový modul runtime jsou pro toto) nutné.

  - Přidání podpory pro zobrazení ukazatele pole (jako v C++) Ponechejte výraz ukazatele a potom přidejte čárku a počet prvků, které chcete zobrazit.

  - Byla přidána podpora pro asynchronní konstrukce.

  - Přidání podpory pro pseudo Variables (výjimky a identifikátory objektů).

### <a name="bug-fixes"></a>Opravy chyb

- **Ladicí program:**

  - Vyhodnocení výrazu se špatnými nebo nepodporovanými výrazy.

## <a name="1700"></a>1.7.0.0

Vydáno 13. listopadu 2018

### <a name="new-features"></a>Nové funkce

- **Ladicí program:**

  - Přidat další informace o klientech (IP, název počítače) v dialogovém okně připojit.

### <a name="bug-fixes"></a>Opravy chyb

- **Ladicí program:**

  - Oprava vzájemné zablokování v knihovně používaný ke komunikaci s modulem Unity a ladicí program, nastavení sady Visual Studio nebo Unity ukotvit, zejména v případě dosažení "Připojit k Unity" nebo restartování hry.

- **Integrace:**

  - Oprava Unity modulu plug-in aktivace byla vyberete jiný výchozí editor.

  - Oprava vytvoření šablony souboru Unity.

## <a name="1602"></a>1.6.0.2

Vydáno 24. července 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Alternativní řešení pro chybu Unity výkonu, která byla opravena Unity vrácena zpět.

## <a name="1601"></a>1.6.0.1

Vydáno 10. července 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Oprava zabarvení kódu shaderu podporovat.

## <a name="1600"></a>1.6.0.0

Vydáno 26. června 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Průvodci:**

  - Oprava překlep OnApplicationFocus zpráva.

- **Generování projektu:**

  - Přechodné alternativní řešení pro chyby výkonu Unity: při vytváření projektů do mezipaměti MonoIslands.

  - Nelze převést souboru PDB typu portable mdb zobrazovat při používání nového modulu runtime Unity.

## <a name="1502"></a>1.5.0.2

Vydáno 18. dubna 2018

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidání podpory pro základní doplňování kódu shaderu.

  - Přidání podpory pro přepínání komentáře v souborech shaderu.

## <a name="1501"></a>1.5.0.1

Vydáno 28. března 2018

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidání podpory pro další šablony v Průzkumníku projektů Unity.

## <a name="1500"></a>1.5.0.0

Vydáno 21. březnem 2018

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidání podpory pro zjišťování a připojování k aktérů Androidu prostřednictvím USB připojená.

## <a name="1403"></a>1.4.0.3

Vydané 5. března 2018

### <a name="new-features"></a>Nové funkce

- **Generování projektu:**

  - Přidání podpory pro nový generátor projektu v Unity 2018.1.

- **Integrace:**

  - Možnost přidání panelu pro vyhrazené nastavení.

## <a name="1402"></a>1.4.0.2

Vydáno 24. ledna 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Detekce Mono opravenou verzi.

- **Integrace:**

  - Oprava problémy načasování s 2018.1 a aktivace modulu plug-in.

  - Oprava upozornění při zjištění nového hráče.

## <a name="1401"></a>1.4.0.1

Vydáno 23. ledna 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Klikněte dvakrát na pevnou Rozbalit/sbalit složky na

## <a name="1400"></a>1.4.0.0

Vydáno 13. prosince 2017

### <a name="new-features"></a>Nové funkce

- **Generování projektu:**

  - Přidání podpory pro .NET Standard.

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Oprava automatické pdb do mdb ladicí symbol převodu.

## <a name="1301"></a>1.3.0.1

Vydáno 12. prosince 2017

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Oprava nepřímé volání EditorPrefs.GetBool vliv na okně Inspektor. při pokusu o změnu velikosti pole.

- **Průvodci:**

  - Před vložením metoda aktualizujte roslyn kontextu.

## <a name="1300"></a>1.3.0.0

Vydáno 20. listopadu 2017

### <a name="new-features"></a>Nové funkce

- **Průvodci:**

  - Přidání průvodce "Unity implementujte zprávu".

  - Přidání podpory pro nové dokončení rozhraní API v sadě Visual Studio pro Mac 7.4.

## <a name="1200"></a>1.2.0.0

Vydáno 23. října 2017

### <a name="new-features"></a>Nové funkce

- **Ladicí program:**

  - Přidání podpory pro soubory symbolů ladění přenosné.

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Opravili jsme navíc DLL rozšíření chybně přidá k názvu souboru sestavení.

  - Nesnažte se vynutit příznak AllowAttachedDebuggingOfEditor Unity jako výchozí hodnota je "true".

## <a name="1103"></a>1.1.0.3

Vydáno 23. října 2017

### <a name="new-features"></a>Nové funkce

- **Generování projektu:**

  - Přidání podpory pro profil .NET 4.6.

## <a name="1102"></a>1.1.0.2

Vydáno 8. srpna 2017

### <a name="new-features"></a>Nové funkce

- **Ladicí program:**

  - Spustit dialogu připojit k procesu, pokud nejste si jisti, jaké Unity pro připojení k.

- **Generování projektu:**

  - Vždy povolte přepínač nebezpečné kompilace při použití Unity 5.6.

## <a name="1101"></a>1.1.0.1

Vydáno 20. července 2017

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidání podpory pro lokalizované prostředky.

## <a name="1100"></a>1.1.0.0

Vydáno 12. července 2017

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidání podpory pro připojení k hráčům a editory prostřednictvím připojit k procesu okno.

- **Generování projektu:**

  - Pevné odkazy na název sestavení se mcs.rsp soubory.

  - Přidání podpory pro assembly.json kompilačních jednotek.

  - Oprava definuje s úrovní rozhraní API.

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Oprava shaderu chybová zpráva při kompilaci.

## <a name="1001"></a>1.0.0.1

Vydáno 4. května 2017

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Oprava aktivní sledování dokumentů s hybridní a běžných projektů.

## <a name="1000"></a>1.0.0.0

Vydáno 3. května 2017
