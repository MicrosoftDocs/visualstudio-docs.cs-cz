---
title: Protokol změn (Visual Studio Tools for Unity, Windows) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/18/2019
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: ea490b7e-fc0d-44b1-858a-a725ce20e396
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 713535bb11b4bd9cab4ef1b31507b96fe1c9897a
ms.sourcegitcommit: 88f576ac32af31613c1a10c1548275e1ce029f4f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71185989"
---
# <a name="change-log-visual-studio-tools-for-unity-windows"></a>Protokol změn (Visual Studio Tools for Unity, Windows)

Protokol změn Visual Studio Tools for Unity.

## <a name="4330"></a>4.3.3.0

Vydáno 23. září 2019

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opravili jsme chybu a hlášení upozornění pro odlehčená sestavení.

## <a name="4320"></a>4.3.2.0

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

## <a name="4310"></a>4.3.1.0

vydáno 4. září 2019

### <a name="new-features"></a>Nové funkce

- **Vyhodnocení:**

  - Přidání podpory pro lepší zobrazení typu, tj. `List<object>` `List'1[[System.Object, <corlib...>]]`místo.

  - Přidání podpory pro přístup ke členu ukazatele, `p->data->member`tj.

  - Přidání podpory pro implicitní převody v inicializátorech pole, tj. `new byte [] {1,2,3,4}`

## <a name="4300"></a>4.3.0.0

vydáno 13. srpna 2019

### <a name="new-features"></a>Nové funkce

- **Ladicí program:**

  - Byla přidána podpora protokolu MDS 2,51.

- **Integrace:**

  - Vylepšilo se okno připojit k instanci Unity s funkcemi řazení, hledání a aktualizace. PID se teď zobrazuje i pro místní přehrávače (dotazuje se na naslouchající sokety v systému, aby získal vlastnící proces).

  - Přidání podpory pro soubory asmdef

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Pevné zpracování poškozených zpráv při komunikaci s přehrávači Unity.

- **Vyhodnocení:**

  - Pevné zpracování oborů názvů ve výrazech.

  - Pevná kontrola s použitím typů IntPtr.
  
  - Opravili jsme problémy krokování s výjimkami.

  - Pevné vyhodnocení pseudo identifikátorů (například $exception).

  - Zabraňte selhání při přesměrování neplatných adres.  

  - Opravili jsme problém s uvolněnými doménami AppDomain.

## <a name="4201"></a>4.2.0.1

vydáno 24. července 2019

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidání nové možnosti pro vytvoření libovolného typu souboru z Průzkumníka projektů Unity.
  
  - Při použití rychlých buildů pro projekty Unity Vylepšete ukládání do mezipaměti diagnostiky.

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opravili jsme problém, když Přípona souboru nebyla zpracována žádným známým editorem.

  - Pevná podpora pro vlastní rozšíření v Průzkumníku projektů Unity.

  - Pevné uložení nastavení mimo hlavní dialog.

  - Byla odebrána starší závislost Microsoft. VisualStudio. MPF.

## <a name="4110"></a>4.1.1.0

Vydáno 24. května 2019

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Rozhraní MonoBehaviour API se aktualizovalo na 2019,1.

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opravená upozornění a chyby při generování výstupu, když je povolené zjednodušené sestavení.

  - Pevný výkon pro odlehčené sestavení.

## <a name="4100"></a>4.1.0.0

Vydáno 21. května 2019

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidání podpory nového rozhraní API služby Batch pro rychlejší opětovné načtení projektů.

  - Pro projekty Unity se zakázalo úplné sestavení, a to na základě chyb a upozornění technologie IntelliSense. Ve skutečnosti Unity vytvoří řešení sady Visual Studio s projekty knihoven tříd, které reprezentují, co Unity interně dělá. To se říká, výsledek sestavení v sadě Visual Studio se nikdy nepoužívá nebo nezískala v Unity, protože je jejich kanál kompilace uzavřený. Sestavování v aplikaci Visual Studio právě spotřebovává prostředky pro nic. Pokud potřebujete úplné sestavení, protože máte nástroje nebo nastavení, které na něm závisí, můžete tuto optimalizaci zakázat (nástroje/Možnosti/nástroje pro Unity nebo zakázat kompletní sestavení projektů).

  - Při načtení projektu Unity automaticky zobrazit Průzkumníka projektů Unity (UPE) UPE bude ukotven vedle Průzkumník řešení.

  - Byl aktualizován mechanismus extrakce názvů projektů pomocí Unity 2019. x.

  - Přidala se podpora pro balíčky Unity v UPE. Jsou viditelné pouze odkazované balíčky (používající manifest. JSON `Packages` ve složce) a místní balíčky (vložené `Packages` do složky).

- **Generování projektu:**

  - Při zpracování souboru řešení zachovat externí vlastnosti.

- **Vyhodnocení:**

  - Byla přidána podpora názvů kvalifikovaných aliasů (pouze globální obor názvů pro nyní). Proto vyhodnocovací filtr výrazů nyní přijímá typy pomocí formuláře Global:: Namespace. Type.

  - Přidání podpory pro `pointer[index]` formulář, která je sémanticky totožná s odkazem `*(pointer+index)` na odkazy na ukazatel.

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opravili jsme problémy s závislostí pomocí Microsoft. VisualStudio. MPF.

  - Pevný aktér pro UWP se připojí bez načtení projektu.

  - Pevná Automatická aktualizace databáze prostředků, když se ještě nepřipojila aplikace Visual Studio

  - Pevné problémy s motivem pomocí popisků a zaškrtávacích políček.

- **Ladicí program:**

  - Pevné krokování se statickými konstruktory.

## <a name="4005"></a>4.0.0.5

Vydáno 27. února 2019

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opravili jsme detekci verzí sady Visual Studio pomocí instalačního balíčku.

  - Z instalačního balíčku se odebrala nepoužívaná sestavení.

## <a name="4004"></a>4.0.0.4

Vydáno 13. února 2019

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidání podpory pro správné detekci procesů Unity během instalace a povolení instalačního modulu pro lepší zpracování zámků souborů.

  - Rozhraní API `ScriptableObject` se aktualizovalo.

## <a name="4003"></a>4.0.0.3

Vydáno 31. ledna 2019

### <a name="new-features"></a>Nové funkce

- **Generování projektu:**

  - Veřejná a serializovaná pole už nebudou způsobovat upozornění. Automaticky jsme potlačili `CS0649` upozornění kompilátoru a `IDE0051` v projektech Unity, která tyto zprávy vytvořila.

- **Integrace:**

  - Zlepšilo se uživatelské prostředí pro zobrazování editoru Unity a instancí přehrávače (Windows teď měnitelné velikosti, používejte jednotné okraje a zobrazují úchyt pro změnu velikosti). Přidání informací o ID procesu pro editory Unity

  - Rozhraní API `MonoBehaviour` se aktualizovalo.

- **Vyhodnocení:**

  - Byla přidána podpora místních funkcí.

  - Přidání podpory pro pseudo Variables (výjimky a identifikátory objektů).

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opravili jsme problém s obrázky monikeru a motivy.

  - Zapisovat pouze do okno Výstup při ladění při automatické aktualizaci databáze prostředků.

  - Pevná prodleva uživatelského rozhraní pomocí filtrování Průvodce MonoBehaviour

- **Ladicí program:**

  - Bylo vyřešeno čtení vlastního atributu u pojmenovaných argumentů při použití starších verzí protokolu.

## <a name="4002"></a>4.0.0.2

Vydáno 23. ledna 2019

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opravilo se generování experimentálního buildu.

  - Pevné zpracování událostí souboru projektu pro minimalizaci zatížení vlákna uživatelského rozhraní.

  - Fixní poskytovatel dokončení se změnami v dávce textu

- **Ladicí program:**

  - Opravili jsme zobrazení zpráv ladění uživatele k připojenému ladicímu programu.

## <a name="4001"></a>4.0.0.1

Vydáno 10. prosince 2018

### <a name="new-features"></a>Nové funkce

- **Vyhodnocení:**

  - Nahradili jsme NRefactory a upřednostňujeme Roslyn pro vyhodnocení výrazu.

  - Přidání podpory pro ukazatele: dereference, přetypování a aritmetické operace (2018.2 Unity + a nový modul runtime jsou pro toto) nutné.

  - Přidání podpory pro zobrazení ukazatele pole (jako v C++) Ponechejte výraz ukazatele a potom přidejte čárku a počet prvků, které chcete zobrazit.

  - Byla přidána podpora pro asynchronní konstrukce.

- **Integrace:**

  - Přidání podpory pro automatickou aktualizaci databáze assetů v Unity při uložení Tato možnost je ve výchozím nastavení povolená a při ukládání skriptu do sady Visual Studio aktivuje novou kompilaci na straně Unity. Tuto funkci můžete zakázat v Tools\Options\Tools pro AssetDatabase v Unity\Refresh Unity při uložení.

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Fixní aktivace přemostění, když není vybrána možnost Visual Studio jako preferovaný externí editor.

  - Vyhodnocení výrazu se špatnými nebo nepodporovanými výrazy.

## <a name="4000"></a>4.0.0.0

Vydáno 4. prosince 2018

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidání podpory pro Visual Studio 2019 (potřebujete aspoň Unity 2018,3, aby bylo možné použít Visual Studio 2019 jako externí editor skriptu).

  - Přijali jste službu a katalog sady Visual Studio s plnou podporou škálování HDPI, dokonalých obrázků v pixelech a jejich.

### <a name="deprecated-features"></a>Zastaralé funkce

- **Integrace:**

  - Po přeposílání Visual Studio Tools for Unity bude podporovat Unity 5.2 + (s integrovanou integrací sady Visual Studio Unity).

  - Až budete dál, Visual Studio Tools for Unity podporují jenom Visual Studio 2015 +.

  - Byla odebrána služba starší verze jazyka, seznam chyb a stavový řádek.

  - Odebral se Průvodce rychlým MonoBehaviour (ve prospěch vyhrazené podpory technologie IntelliSense).

## <a name="3903"></a>3.9.0.3

vydáno 28. listopadu 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Pevné opětovné načítání projektů a problémy IntelliSense při přidávání nebo odebírání skriptů umístěných v velmi prvním projektu.

## <a name="3902"></a>3.9.0.2

vydáno 19. listopadu 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Ladicí program:**

  - Oprava vzájemné zablokování v knihovně používaný ke komunikaci s modulem Unity a ladicí program, nastavení sady Visual Studio nebo Unity ukotvit, zejména v případě dosažení "Připojit k Unity" nebo restartování hry.

## <a name="3901"></a>3.9.0.1

Vydáno 15. listopadu 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Oprava Unity modulu plug-in aktivace byla vyberete jiný výchozí editor.

## <a name="3900"></a>3.9.0.0

Vydáno 13. listopadu 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Alternativní řešení pro chybu Unity výkonu, která byla opravena Unity vrácena zpět.

## <a name="3807"></a>3.8.0.7

Vydáno 20. září 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Ladicí program:**

  - (Přeneseny zpět z 3.9.0.2) Oprava vzájemné zablokování v knihovně používaný ke komunikaci s modulem Unity a ladicí program, nastavení sady Visual Studio nebo Unity ukotvit, zejména v případě dosažení "Připojit k Unity" nebo restartování hry.

## <a name="3806"></a>3.8.0.6

Vydáno 27. srpna 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opravili jsme opětovném načtení projektů a řešení.

## <a name="3805"></a>3.8.0.5

vydáno 20. srpna 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Oprava projektu monitorování integrity předplatného.

## <a name="3804"></a>3.8.0.4

Vydáno 14. srpna 2018

### <a name="new-features"></a>Nové funkce

- **Vyhodnocení:**

  - Přidání podpory pro hodnoty ukazatele.

  - Přidání podpory pro obecné metody.

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Inteligentní načíst znovu s více projekty změnit.

## <a name="3803"></a>3.8.0.3

Vydáno 24. července 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - (Přeneseny zpět z 3.9.0.0) Alternativní řešení pro chybu Unity výkonu, která byla opravena Unity vrácena zpět.

## <a name="3802"></a>3.8.0.2

Vydáno 7. července 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Přechodné alternativní řešení pro chyby výkonu Unity: při vytváření projektů do mezipaměti MonoIslands.

## <a name="3801"></a>3.8.0.1

Vydáno 26. června 2018

### <a name="new-features"></a>Nové funkce

- **Ladění:**

  - Přidání podpory pro příkazy UserLog a UserBreak.

  - Podpora přidání opožděné načtení typu (optimalizace síťová latence odezvy zatížení a ladicí program).

### <a name="bug-fixes"></a>Opravy chyb

- **Vyhodnocení:**

  - Vylepšené vyhodnocení výrazu binární operátor a metoda vyhledávání.

## <a name="3800"></a>3.8.0.0

Vydáno 30. května 2018

### <a name="new-features"></a>Nové funkce

- **Ladění:**

  - Přidání podpory pro zobrazení proměnné v asynchronní konstrukce.

  - Přidání podpory pro vnořené typy zpracování, při nastavení zarážek, aby se zabránilo upozornění s kompilátoru konstrukce.

- **Integrace:**

  - Přidání podpory pro gramatik textmate shadery (úlohy pro C++ je už je nepotřebujete pro zabarvení kódu shaderu).

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Nelze převést souboru PDB typu portable mdb zobrazovat při používání nového modulu runtime Unity.

## <a name="3701"></a>3.7.0.1

Vydáno 7. května 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Instalační program:**

  - Oprava závislostí problém při používání experimentální sestavení.

## <a name="3700"></a>3.7.0.0

Vydáno 7. května 2018

### <a name="new-features"></a>Nové funkce

- **Ladění:**

  - Přidání podpory pro iniciovat organizovaně, což ladění (ladění více hráči nebo editoru pomocí stejné relaci sady Visual Studio).

  - Přidání podpory pro Android USB player ladění.

  - Přidání podpory pro UPW/endem IL2CPP player ladění.

- **Vyhodnocení:**

  - Přidání podpory pro šestnáctkové specifikátorů.

  - Vylepšené sledování okno hodnocení.

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Oprava využití nastavení výjimek.

- **Generování projektu:**

  - Vyloučíte z generování balíčku správce kompilačních jednotek.

## <a name="3605"></a>3.6.0.5

Vydáno 13. března 2018

### <a name="new-features"></a>Nové funkce

- **Generování projektu:**

  - Přidání podpory pro nový generátor projektu v Unity 2018.1.

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opravili jsme zpracování poškozená státy, s vlastní projekty.

- **Ladicí program:**

  - Oprava, nastavení dalšího příkazu.

## <a name="3604"></a>3.6.0.4

Vydané 5. března 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Detekce Mono opravenou verzi.

- **Integrace:**

  - Oprava problémy načasování s 2018.1 a aktivace modulu plug-in.

## <a name="3603"></a>3.6.0.3

Vydáno 23. února 2018

### <a name="new-features"></a>Nové funkce

- **Generování projektu:**

  - Přidání podpory pro .NET Standard.

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Oprava Unity cílové rozhraní framework zjišťování.

- **Ladicí program:**

  - Oprava přerušení při výjimkách, které jsou zahozeny mimo usercode.

## <a name="3602"></a>3.6.0.2

Vydáno 7. února 2018

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Aktualizujte rovinu rozhraní API UnityMessage pro 2017.3.

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Jenom znovu načte projekty na externí změně (omezení využití sítě).

## <a name="3601"></a>3.6.0.1

Vydáno 24. ledna 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Oprava automatické pdb do mdb ladicí symbol převodu.

  - Oprava nepřímé volání EditorPrefs.GetBool vliv na okně Inspektor. při pokusu o změnu velikosti pole.

## <a name="3600"></a>3.6.0.0

Vydáno 10. ledna 2018

### <a name="new-features"></a>Nové funkce

- **Generování projektu:**

  - Přidání podpory pro 2018.1 MonoIsland referenční model.

- **Vyhodnocení:**

  - Přidání podpory pro identifikátor $exception.

- **Ladicí program:**

  - Přidání podpory pro atributy DebuggerHidden/DebuggerStepThrough se nový modul runtime Unity.

- **Průvodci:**

  - Zavést ' nejnovější ' pro průvodce.

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Opravili jsme výpočet identifikátoru guid projektu pro projekty přehrávače.

- **Ladicí program:**

  - Opravili jsme soupeření při zpracování události zásadní.

- **Průvodci:**

  - Před vložením metoda aktualizujte roslyn kontextu.

## <a name="3503"></a>3.5.0.3

Vydáno 9. ledna 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Oprava automatické pdb do mdb ladicí symbol převodu.

## <a name="3502"></a>3.5.0.2

Vydáno 4. prosince 2017

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Projekty Unity se teď při přidání nebo odebrání skriptu z Unity automaticky znovu načítají v sadě Visual Studio.

- **Ladicí program:**

  - Přidat možnost použít ladicí program Mono, sdílený produkty Xamarin a Visual Studio for Mac k ladění nástroje Unity Editor.

  - Přidání podpory pro soubory symbolů ladění přenosné.

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opravili jsme potíže s instalací závislosti.

  - Oprava rozhraní API Unity Nápověda není zobrazen.

- **Generování projektu:**

  - Oprava player generování projektu při práci na hře pro UPW s back-endem IL2CPP/.NET 4.6 end.

  - Opravili jsme navíc DLL rozšíření chybně přidá k názvu souboru sestavení.

  - Oprava využití určitého projektu, API úroveň kompatibility místo globální.

  - Nesnažte se vynutit příznak AllowAttachedDebuggingOfEditor Unity jako výchozí hodnota je "true".

## <a name="3402"></a>3.4.0.2

Vydáno 19. září 2017

### <a name="new-features"></a>Nové funkce

- **Generování projektu:**

  - Přidání podpory pro assembly.json kompilačních jednotek.

  - Zastavit kopírování Unity sestavení do složky projektu.

- **Ladicí program:**

  - Přidání podpory pro nastavení dalšího příkazu pomocí nového modulu runtime Unity.

  - Přidání podpory pro typ desetinné se nový modul runtime Unity.

  - Přidání podpory pro implicitní a explicitní převody.

### <a name="bug-fixes"></a>Opravy chyb

- **Vyhodnocení:**

  - Oprava vytvoření pole s implicitní velikostí.

  - Generovaný kompilátorem opravené položky, místní hodnoty.

- **Generování projektu:**

  - Pevný odkaz na Microsoft.CSharp obsahují třídy pro 4.6 úroveň rozhraní API.

## <a name="3302"></a>3.3.0.2

Vydáno: 15. srpna 2017

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Opravili jsme generování řešení sady Visual Studio na Unity 5.5 a předchozích verzích.

## <a name="3300"></a>3.3.0.0

Vydáno 14. srpna 2017

### <a name="new-features"></a>Nové funkce

- **Vyhodnocení:**

  - Přidání podpory pro vytváření struktury se nový modul runtime Unity.

  - Přidání podpory minimalist pro ukazatele.

### <a name="bug-fixes"></a>Opravy chyb

- **Vyhodnocení:**

  - Opravili jsme volání metody na primitiv.

  - Pole pevné hodnocení s typy označené BeforeFieldInit.

  - Oprava nepodporovaném volání s binárními operátory (odečíst).

  - Opravené problémy při přidávání položek do Visual Studio Watch.

- **Generování projektu:**

  - Pevné odkazy na název sestavení se mcs.rsp soubory.

  - Oprava definuje s úrovní rozhraní API.

## <a name="3200"></a>3.2.0.0

Vydáno 10. května 2017

### <a name="new-features"></a>Nové funkce

- **Instalační program:**

  - Přidání podpory pro čištění mezipaměť MEF.

### <a name="bug-fixes"></a>Opravy chyb

- **Editor kódu:**

  - Oprava klasifikace/dokončení s vlastními atributy.

  - Opravili jsme blikání s zprávy Unity.

## <a name="3100"></a>3.1.0.0

Vydáno 7. dubna 2017

### <a name="new-features"></a>Nové funkce

- **Ladicí program:**

  - Přidali jsme podporu pro nový modul runtime Unity (s .NET 4.6 / kompatibilita C# 6).

- **Generování projektu:**

  - Přidání podpory pro profil .NET 4.6.

  - Přidání podpory pro mcs.rsp soubory.

  - Vždy povolte přepínač nebezpečné kompilace při použití Unity 5.6.

  - Přidali jsme podporu pro generování projektu "Player" při použití Windows Store platformy a endem il2cpp back-endu.

### <a name="bug-fixes"></a>Opravy chyb

- **Editor kódu:**

  - Opravili jsme pozici blikajícího kurzoru po vložení metody s automatickým dokončováním.

- **Generování projektu:**

  - Odebrané sestavení verze následné zpracování.

## <a name="3001"></a>3.0.0.1

Vydáno 7. března 2017

### <a name="this-version-includes-all-new-features-and-bug-fixes-introduced-with-28x-series"></a>Tato verze zahrnuje všechny nové funkce a opravy chyb nepředchází 2.8.x řady.

## <a name="2820---30-preview-3"></a>2.8.2.0 - 3.0 ve verzi preview 3
Vydáno 25. ledna 2017

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Oprava regrese, kde moduly plug-in projekty tam, kde odkazováno dvakrát, nejprve jako binární knihovnu DLL jako projekt odkázat na.

## <a name="2810---30-preview-2"></a>2.8.1.0 - 3.0 ve verzi preview 2
Vydáno 23. ledna 2017

### <a name="bug-fixes"></a>Opravy chyb

- **Editor kódu:**

  - Oprava chyby při počáteční deklaraci atributu bez uzavírání hranatých závorek.

- **Ladicí program:**

  - Fixed – funkce zarážky u korutin v rámci nového Unity kompilátoru a modulu runtime.

  - Přidání upozornění v případě unbindable bod přerušení (když je nalezena žádná odpovídající umístění zdroje).

- **Generování projektu:**

  - Opravili jsme generování souboru csproj pomocí speciální/lokalizované znaky.

  - Pevné odkazy mimo prostředky, jako jsou knihovny (jako je Facebook SDK).

- **Různé:**

  - Přidání kontroly pro Unity Zabraňte jejich spuštění při instalaci nebo odinstalaci.

  - Přepnout na https cílit na vzdálené dokumentace k Unity.

## <a name="2800---30-preview"></a>2.8.0.0 - 3.0 ve verzi preview
Vydáno 17. listopadu 2016

### <a name="new-features"></a>Nové funkce

- **Obecné:**

  - Přidání podpory instalačního programu sady Visual Studio 2017.

  - Byla přidána podpora rozšíření sady Visual Studio 2017.

  - Podpora přidání lokalizace.

- **Editor kódu:**

  - Přidání C# IntelliSense pro zprávy Unity.

  - Přidání C# kód zabarvení pro zprávy Unity.

- **Ladicí program:**

  - Přidání podpory pro `is`, `as`přímé přetypování, `default`, `new` výrazy.

  - Přidání podpory pro řetězec concat výrazy.

  - Přidání podpory pro hexadecimální zobrazení celočíselných hodnot.

  - Přidání podpory pro vytváření nové dočasné proměnné (příkazů).

  - Přidání podpory pro primitivní implicitní převody.

  - Přidání lepší chybové zprávy při typ je očekáván nebo nebyl nalezen.

- **Generování projektu:**

  - Přípona CSharp odebrán názvy projektů.

  - Odebrán odkaz na soubor cílů široké msbuild systému.

- **Průvodci:**

  - Přidání podpory pro zprávy Unity v jiné chování typy, například Editor nebo okna editoru.

  - Přepnout na platformě Roslyn vložit a formátovat zprávy Unity.

### <a name="bug-fixes"></a>Opravy chyb

- **Ladicí program:**

  - Je opravená chyba při vyhodnocování obecných typů chyb Unity.

  - Oprava zpracování typů s povolenou hodnotou Null.

  - Oprava zpracování výčtů.

  - Oprava zpracování typů vnořeného člena.

  - Opravili jsme kolekci přístup indexeru.

  - Oprava podpory ladění snímků iterátor s nový kompilátor jazyka C#.

- **Generování projektu:**

  - Oprava chyby, který zabránil kompilace při cílení na Unity Web Playeru.

  - Oprava chyby, který zabránil kompilace při kompilaci skriptu s webovým kódovaný název souboru.

## <a name="2300"></a>2.3.0.0

Vydáno 14. července 2016

### <a name="new-features"></a>Nové funkce

- **Obecné:**

  - Přidat možnost zakázat Unity konzole protokoly v seznamu chyb sady Visual Studio.

  - Přidat možnost povolit vlastnosti vygenerované projekt má být upraven.

- **Ladicí program:**

  - Přidání textu, XML, HTML a JSON řetězec vizualizéry.

- **Průvodci:**

  - Přidat chybějící MonoBehaviors.

### <a name="bug-fixes"></a>Opravy chyb

- **Obecné:**

  - Oprava ke konfliktu s ReSharper, který zabránil ovládacích prvků uvnitř sady Visual Studio nastavení zobrazení.

  - Opravili jsme konflikt s využitím kódu Xamarin, která bránila v některých případech ladění.

- **Ladicí program:**

  - Opravili jsme problém, která způsobila zablokování při ladění sady Visual Studio.

  - Opravili jsme problém s zarážky funkcí v sadě Visual Studio 2015.

  - Opravili jsme několik výrazů vyhodnocení problémů.

## <a name="2200"></a>2.2.0.0

Vydáno 4. února 2016

### <a name="new-features"></a>Nové funkce

- **Průvodci:**

  - Přidání inteligentní vyhledávání v **implementace MonoBehavior** průvodce.

  - Vytvořit průvodce kontextu vědět; například NetworkBehavior zprávy jsou k dispozici pouze při práci s NetworkBehavior.

  - Přidání podpory pro NetworkBehavior zprávy v průvodci.

- **UŽIVATELSKÉ ROZHRANÍ:**

  - Přidat možnost konfigurovat, zda se MonoBehavior zprávy.

  - Odebrání stránky vlastností sady Visual Studio, které nejsou relevantní pro projekty Unity.

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Pevné odkazy na UnityEngine a UnityEditor na 4.6 v Unity.

  - Oprava generování souborů projektu při spuštění Unity na os x.

  - Oprava zpracování názvy projektů obsahující znaky hashmark (#)

  - S omezením pomocí specifikátoru generované projekty jazyka C# 4.

- **Ladicí program:**

  - Opravili jsme problém s vyhodnocování výrazů při ladění v korutině Unity.

  - Opravili jsme problém, která způsobila zablokování při ladění sady Visual Studio.

- **UŽIVATELSKÉ ROZHRANÍ:**

  - Oprava nekompatibility s [karty Studio](https://tabsstudio.com/) rozšíření sady Visual Studio.

- **Instalační program:**

  - Tím, že vytvoříte položky registru HKLM podporují instalaci celý počítač vstu (instalace pro všechny uživatele).

  - Opravené problémy odinstalaci VSTU při instalaci stejnou verzi VSTU pro několik různých verzí sady Visual Studio. Například když VSTU **2015** 2.1.0.0 a VSTU **2013** 2.1.0.0 oba nainstalovaly.

## <a name="2100"></a>2.1.0.0

Vydáno 8. září 2015

### <a name="new-features"></a>Nové funkce

- Podpora pro Unity 5.2

### <a name="bug-fixes"></a>Opravy chyb

- Zobrazit položky nabídky na Unity < 4.2

- Chybová zpráva zmizí při uzamčení soubory intellisense XML sady Visual Studio.

- Zpracování <\<při změně >> podmíněné zarážky, pokud podmíněné argument není logická hodnota.

- Pevné odkazy na sestavení UnityEngine a UnityEditor pro aplikace Windows Store.

- Opravená chyba při krokování v ladicím programu: Nepovedlo se krokovat, obecná výjimka.

- Pevný počet průchodů zarážky v sadě Visual Studio 2015.

## <a name="2000"></a>2.0.0.0

Vydáno 20. července 2015

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace Unity:**

  - Opravili jsme převod symboly ladění, které jsou vytvořené pomocí sady Visual Studio 2015, při importu knihovny DLL a jeho ladění symbolů (PDB).

  - Vždy generovat soubory MDB při importu knihovny DLL a jeho ladění symbolů (PDB), s výjimkou případů, kdy se soubor MDB také poskytuje.

  - Oprava znečištění adresáře Unity projektů s adresářem obj.

  - Oprava generování odkazů na System.Xml.Link a System.Runtime.Serialization.

  - Přidání podpory pro několik předplatitelů do generování souboru projektu rozhraní API zavěšení.

  - Generování souboru vždy dokončený projekt i v případě, že jeden ze souborů, které chcete vygenerovat je.

  - Přidání podpory pro * zástupné znaky v rozšíření filtrování při určování souborů, které mají být zahrnuty v projektu C#.

- **Integrace se sadou Visual Studio:**

  - Opravili jsme potíže s kompatibilitou se nástrojů Productivity Power Tools.

  - Opravili jsme generování MonoBehaviors kolem deklarace události a delegáti.

- **Ladicí program:**

  - Opravili jsme potenciální zablokování při ladění.

  - Opravili jsme problém, kde by lokální proměnné zobrazí v některých rámců zásobníku.

  - Oprava kontroly prázdné pole.

## <a name="1990---20-preview-2"></a>1.9.9.0 - 2.0 preview 2
Vydáno 2. dubna 2015

### <a name="new-features"></a>Nové funkce

- **Unity Project Exploreru:**

  - Automatické přejmenování tříd při přejmenování souboru v Průzkumníku projektů Unity (viz **možnosti** dialogového okna).

  - Automatický výběr nově vytvořený skripty v Průzkumníku projektů Unity.

  - Sledování aktivních skriptů v Průzkumníku projektů Unity (viz **možnosti** dialogového okna).

  - Duální synchronizovat Průzkumníku řešení sady Visual Studio (viz **možnosti** dialogového okna).

  - Osvojte si ikony sady Visual Studio v Průzkumníku projektů Unity.

- **Ladicí program:**

  - Vyberte cíl active ladění ze seznamu cílů ladění uložené nebo naposledy použitých (viz **možnosti** dialogového okna).

  - Vytvořit zarážky funkcí na MonoBehavior metody a použít je u více MonoBehavior tříd.

  - Ujistěte se, ID objektu se podporují v ladicím programu.

  - Podpora v ladicím programu počet průchodů zarážky.

  - Podpora přerušení na výjimky v ladicím programu (experimentální. Zobrazit **možnosti** dialogového okna).

  - Podporuje vytváření objekty a pole při vyhodnocení výrazů v ladicím programu.

  - Podporuje porovnání null při vyhodnocování výrazů v ladicím programu.

  - Zastaralé členy v oknech ladicího programu Sledování filtru

- **Instalační program:**

  - Optimalizované Visual Studio Tools for Unity registrace rozšíření.

  - Instalace Visual Studio Tools pro Unity balíček pro Unity 5.

- **Nápovědě** Zvyšte výkon generování dokumentace.

- **Průvodci:** Podpora nových metod MonoBehavior pro Unity 4,6 a Unity 5.

- **Unity:** Vyhledávání nebezpečných příznaků a vlastní definice v souborech. rsp během generování souboru projektu.

- **UŽIVATELSKÉ ROZHRANÍ:** Přidání dialogového okna **možností** Visual Studio Tools for Unity v aplikaci Visual Studio.

### <a name="bug-fixes"></a>Opravy chyb

- **Unity Project Exploreru:**

  - Aktualizujte Průzkumníka projektů Unity po soubory se přesunout nebo přejmenovat v Průzkumníku řešení sady Visual Studio.

  - Zachovat výběr při přejmenování souborů v Průzkumníku projektů Unity.

  - Zakázat automatické rozbalovat a sbalovat se soubory dvojité kliknutí v Průzkumníku projektů Unity.

  - Ujistěte se, že nově vybrané soubory jsou viditelné v Průzkumníku projektů Unity.

- **Ladicí program:**

  - Zabraňte možný výskyt sady Visual Studio zablokovat při vyhodnocení výrazů v ladicím programu.

  - Ujistěte se, že volání metod provádělo na správné domény v ladicím programu.

- **Unity:**

  - Opravte umístění UnityVS.OpenFile pomocí Unity 5.

  - Opravte umístění pdb2mdb pomocí Unity 5.

  - Zabraňte možnou výjimkou při generování souboru projektu.

  - Zabránit možný zablokování při spuštění Unity na os x.

  - Zpracování interních výjimek.

  - Odeslat protokoly konzoly s Unity v seznamu chyb VS.

- **Nápovědě** Opravte generaci dokumentace pro novou dokumentaci k Unity.

- **Projektem** V případě potřeby přesuňte a přejmenujte soubory Unity. meta, i ve složkách.

- **Průvodci:** Opravte pořadí parametrů metody MonoBehavior při generování kódu.

- **UŽIVATELSKÉ ROZHRANÍ:** Podpora motivů sady Visual Studio pro kontextovou nabídku a ikony.

## <a name="1980---20-preview"></a>1.9.8.0 - 2.0 preview
Vydáno 12. listopadu 2014

### <a name="new-features"></a>Nové funkce

- Podpora pro sadu Visual Studio 2015.

- Zabarvení kódu pro shadery Unity v sadě Visual Studio 2015.

- Lepší vizualizace hodnot při ladění:

  - Lepší vizualizace pro instance třídy ArrayList, seznamy, zatřiďovacích tabulkách a slovníky.

  - Zobrazit jako kategorií v kukátka a místních zobrazeních neveřejné členy a statické členy.

  - Vylepšené zobrazení SerializedProperty Unity a pouze vyhodnotit pole hodnotu pro vlastnost platná.

  - Debuggerdisplayattribute – podpora pro třídy a struktury.

  - Debuggertypeproxyattribute – podpora.

- Ujistěte se, vložení metody třídy MonoBehaviour. pomocí naší průvodců dodržovat konvence psaní kódu uživatele.

- Implementovat podporu pro kompilaci textové šablony v projektech UnityVS vygenerována.

- Podpora prostředků ResX implementovat v projektech UnityVS vygenerována.

- Podpora otevírání shadery v sadě Visual Studio z Unity.

### <a name="bug-fixes"></a>Opravy chyb

- Vyčištění sockets před zahájením hry v Unity po připojení a Play se aktivovalo v sadě Visual Studio. To řeší některé problémy se stabilitou připojení mezi Unity a VS při použití připojení a Play.

- Vyhněte se volání metody v Unity a skriptovací stroj rozhraní ladicího programu, které jsou náchylné k zablokování Unity. To řeší Unity zablokování při připojování ladicího programu.

- Opravte, když není k dispozici žádné symboly zobrazení zásobníky volání.

- Pokud nemusíme neregistrujte zpětné volání protokolu.

## <a name="1920"></a>1.9.2.0

Vydáno 9. října 2014

### <a name="new-features"></a>Nové funkce

- Vylepšení detekce hráči Unity.

- Při používání našich otevírající soubor, ujistěte se, Unity předat číslo řádku, jakož i název souboru.

- Pokud neexistuje žádná místní dokumentace výchozí si online dokumentaci k Unity.

### <a name="bug-fixes"></a>Opravy chyb

- Při dosažení zarážky po znovu načíst domény byla opravena chyba vyskytující potenciální Unity.

- Oprava výjimky uvedené v konzole nástroje Unity při uzavření naše konfigurace nebo o časových obdobích, po domény znovu načíst.

- Opravte detekce 64bitový Unity spuštěná místně.

- Oprava na Unity verze v průvodcích závislé filtrování toho třídy Monobehaviour.

- Oprava chyby, kde všechny prostředky byly obsaženy v souborech projektu Pokud filtr přípon byla prázdná.

## <a name="1910"></a>1.9.1.0

Vydáno 22. září 2014

### <a name="new-features"></a>Nové funkce

- Optimalizujte vazby zarážku do zdrojového umístění.

- Podpora pro přetížené metody v pořadí vyhodnocování výrazů ladicího programu.

- Podpora zabalení primitivních elementů a typů hodnot v pořadí vyhodnocování výrazů ladicího programu.

- Podpora opětovného vytvoření lokálních proměnných prostředí jazyka C#, při ladění anonymní metody.

- Odstranění a přejmenování .meta souborů, když se odstranění nebo přejmenování souborů ze sady Visual Studio.

### <a name="bug-fixes"></a>Opravy chyb

- Opravte zpracování motivů aplikace Visual Studio. Dialogová okna na černé motivy dříve, může zobrazovat prázdný.

- Zablokování Unity stanovit při připojování ladicího programu během rekompilace Unity.

- Oprava zarážky při ladění vzdáleného editory nebo hráči zkompilovány v jiném systému.

- Opravte možné chybovému ukončení sady Visual Studio při dosažení zarážky.

- Oprava zarážky vazby zarážky zobrazuje jako, aby byla uvolněna.

- Opravte zpracování obor proměnné v ladicím programu, aby se zabránilo živé proměnné, které se zobrazují mimo rozsah.

- Opravte vyhledávání statické členy v pořadí vyhodnocování výrazů ladicího programu.

- Opravte zobrazení typů v pořadí vyhodnocování výrazů ladicího programu k zobrazení statická pole a vlastnosti.

- Oprava generování řešení, když názvy projektů Unity zahrnuje speciální znaky, že Visual Studio zakazuje (problém připojit #948666).

- Oprava aplikace Visual Studio nástroje Unity balíček okamžitě zastavit odesílání událostí konzole po nezaškrtnuto (připojit problém #933357) možnost.

- Opravte detekce odkazy se správně obnovit odkazy na nová rozhraní API jako UnityEngine.UI v projektech UnityVS vygenerována.

- Opravte instalační program tak, aby vyžadovala, že Visual Studio zavřená před instalací, aby se zabránilo poškozená instalace.

- Opravte instalační program jako součást správné samostatné, sdílet mezi všechny verze VSTU referenční sestavení Unity.

- Oprava otevření skripty ve verzích 64 bitů v Unity s VSTU.

## <a name="1900"></a>1.9.0.0

Vydáno 29. července 2014

### <a name="new-features"></a>Nové funkce

- V okně připojit ladicí program Unity verze podporují možnost zadat vlastní IP a portu pro ladění.

- Přidáte konfigurační možnost nastavit Unity běžet na pozadí nebo ne.

- Přidáte konfigurační možnost Generovat soubory řešení a projektu nebo jenom soubory projektu.

- Při spuštění cílového: připojit k Unity nebo připojit k Unity a hrát.

- Zobrazení vícerozměrných polí v ladicím programu.

- Zpracujte nové Unity Playeru ladění porty.

- Popisovač odkazy na nové sestavení Unity, jako je Unity a 4.6 grafickým uživatelským rozhraním sestavení.

- Deconstructs uzávěry ke správnému zobrazení místní proměnné při ladění.

- Deconstructs generované iterátory proměnné do argumenty při ladění.

- Zachovat stav Průzkumník projektů Unity po znovu načíst projekt.

- Přidáte příkaz Synchronizovat Průzkumník projektů Unity s aktuální dokument.

### <a name="bug-fixes"></a>Opravy chyb

- Opravte podmíněné zarážky, jejíž podmínky jsou nastavit před spuštěním ladicí program.

- Opravte odkazy na UnityEngine, aby se zabránilo upozornění.

- Oprava analýzy verze pro Unity beta verze.

- Tento problém vyřešit, kde by proměnné zobrazí v okně místních proměnných při dosažení zarážky a krokování.

- Opravte proměnné popisy v sadě Visual Studio 2013.

- Oprava generování dokumentace technologie IntelliSense pro Unity 4.5.

- Opravit v Unity a sady Visual Studio komunikace po domény znovu načíst (Přehrát a zastavit v Unity).

- Opravte zpracování částí motivů aplikace Visual Studio.

> [!IMPORTANT]
> C# se převládající jazyk v ekosystému Unity – nové ukázkové prostředky jsou v jazyce C#, dokumentace k Unity budou ve výchozím nastavení jazyka C# – odebrali jsme naše základní podporu UnityScript a poč lépe zaměřit se na prostředí jazyka C#. V důsledku toho VSTU řešení jsou nyní C# pouze a je mnohem rychlejší načíst.

## <a name="1820"></a>1.8.2.0

Vydáno 7. ledna 2014

### <a name="new-features"></a>Nové funkce

- Vyřešit problém v Unity a skriptovací stroj síťovou vrstvou na Mavericks vzdálené zjišťování editory.

- Zpracujte nové porty ke zjištění vzdáleného hráči Unity.

- Odkaz na konkrétní UnityEngine sestavení do aktuální sestavení cíl.

- Přidáte nastavení k filtrování souborů, které mají být zahrnuty generované projekty.

- Přidáte nastavení zakázat odesílání protokoly konzoly do seznamu chyb sady Visual Studio. To je užitečné, pokud používáte PlayMaker nebo konzoly Pro jako může být jen jedno zpětné volání, které jsou zaregistrované v Unity přijímat protokoly konzoly.

- Přidejte nastavení zakáže generování symbolů pro ladění mdb. To je užitečné, pokud jste mdb generuje sami.

### <a name="bug-fixes"></a>Opravy chyb

- Oprava regrese, když soubory otevřít v sadě Visual Studio z Unity > = 4.2 ztratí technologie IntelliSense.

- Opravte naši VS dialogová okna pro zpracování vlastní motivy.

- Oprava zavření kontextovou nabídku UPE.

- Bránící zhroucení v Unity, když konkrétní verze generovaného sestavení, pokud je synchronizovaný.

## <a name="1810"></a>1.8.1.0

Vydáno 21. listopadu 2013

### <a name="new-features"></a>Nové funkce

- Upravit třídy MonoBehaviour průvodců s rozhraními API Unity 4.3.

- Třída MonoBehaviour průvodců jsou filtrování rozhraní API Unity v závislosti na verzi, kterou používáte.

- K projektům přidat odkaz na System.Xml.Linq pro Unity > 4.1.

- Prettify naše volání Debug.Log tak, aby nezahrnovala začátku stacktrace ve zprávě.

### <a name="bug-fixes"></a>Opravy chyb

- Je opravená chyba, kde jsme by mohly narušit výchozí zpracování souborů JavaScript v sadě Visual Studio.

- Oprava povolí, v sadě Visual Studio, pro skutečné tentokrát bílé pixel.

- Oprava odstranění UnityVS.VersionSpecific sestavení, pokud je označena jako jen pro čtení pomocí Správce řízení služeb.

- Oprava výjimky při vytváření balíčku UnityVS sokety.

- Oprava chyby v sadě Visual Studio při načítání uložené obrázky ze sestavení sady Visual Studio.

- Oprava chyby při generování UnityVS.VersionSpecific pro zdrojové sestavení Unity.

- Oprava možné zablokování při otevřeme soket v balíčku Unity.

- Vyřešilo se zpracování Unity projektu s pomlčkou (-) v názvu.

- Opravili jsme otevření skriptů z Unity nelze zaměňovat pořadí ALT + TAB pro Unity 4.2 a novější.

## <a name="1800"></a>1.8.0.0

Vydáno 24. září 2013

### <a name="new-features"></a>Nové funkce

- Výrazně zlepšit rychlost připojení ladicího programu.

- Automaticky zpracovává navigace k souboru a řádku v Unity 4.2 a vyšší.

- Podmíněné zarážky.

- Generátor souboru projektu nyní zpracovává šablony T4.

- Aktualizujte MonBehavior průvodců pomocí nových rozhraní API.

- Dokumentace technologie IntelliSense v jazyce C# pro typy Unity.

- Aritmetické a logické výrazy hodnocení.

- Lepší zjišťování vzdálené editory pro vzdálené ladění ve verzi preview.

### <a name="bug-fixes"></a>Opravy chyb

- Opravená chyba, kde jsme by způsobit únik těchto vlákno v sadě Visual Studio po odpojení ladicí program.

- Opravili jsme bílé pixel povolí, v sadě Visual Studio.

- Vyřešilo se zpracování kliknutí na ikonu panelu stavu.

- Opravili jsme generování odkazů se sestavení ve složkách moduly plug-in.

- Oprava vytvoření soketů z balíčku UnityVS v případě výjimky.

- Opravili jsme zjišťování nových verzí UnityVS.

- Opravili jsme řádku správce licencí, když platnost licence vypršela.

- Je opravená chyba, která může vykreslit seznam procesů v ladicím programu připojit k procesu okno VS prázdný.

- Oprava změny hodnot logických výrazů v místním okně.

## <a name="1220"></a>1.2.2.0

Vydáno 9. července 2013

### <a name="bug-fixes"></a>Opravy chyb

- Zpracování plně kvalifikované názvy ve vyhodnocovací filtr výrazů.

- Oprava zablokování související se zpracování výjimek, kde Unity skriptovací stroj je odeslání stackframe nesprávná data.

- Opravili jsme proces sestavení pro Web cíle.

- Opravili jsme chybu, která se může stát, pokud byl spuštěn Visual Studio a který byl odstraněný soubor v seznamu souborů, které se otevře při spuštění.

- Oprava UnityVS.OpenFile ke zpracování souborů bez skriptů, jako je zkompilován shadery.

- Nyní odkazujeme Boo.Lang a UnityScript.Lang ze všech projekty jazyka C#.

- Oprava generování odkazů v projektech, pokud projekt obsahuje speciální znaky.

- Alternativní řešení VS problém, pokud volání metody uvolnění projektů se aktivuje více NullReferenceException MessageBox.

- Oprava zpracování sestavení, beta verze 4.2 Unity.

## <a name="1210"></a>1.2.1.0

Vydáno 9. dubna 2013

### <a name="bug-fixes"></a>Opravy chyb

- Oprava místní nasazení sestavení Unity pro doplňování kódu v případě chyby vstupně-výstupní operace (jako jsou soubory jen pro čtení, nebo soubory uzamčené sady Visual Studio).

- Oprava regrese, kde otevřením skriptu z Unity by zaměřit soubor pokud již byl otevřen v sadě Visual Studio.

- Oprava potíží s výkonem nové zpracování výjimky.

- Pevné vazby zarážky v některé externí knihovny DLL.

## <a name="1200"></a>1.2.0.0

Vydáno 25. března 2013

### <a name="new-features"></a>Nové funkce

- Výrazně zlepšit rychlost připojení ladicího programu.

- Optimalizované Unity Project Exploreru pro větší projekty.

- Bude respektovat nastavení sady Visual Studio pro přerušení (nebo nemusíte) na ošetřené i neošetřené výjimky.

- Respektovat nastavení sady Visual Studio pro volání ToString na lokální proměnné.

- Přidat nové nabídky Ladění -> ladicí program připojit Unity, který můžete použít k ladění Unity přehrávače.

- Zachovat vlastní projekty do řešení UnityVS při generování souboru řešení.

- Přidat nové klávesové zkratky CTRL + ALT + M -> CTRL + H k zobrazení dokumentace k Unity pro Unity funkce nebo člen na pozici blikajícího kurzoru.

- Při kompilaci ze sady Visual Studio, vezměte v úvahu kompilátoru soubory odpovědí (rsp).

- Dekonstruovat typů generovaný kompilátorem, který chcete zobrazit proměnné při ladění generátor metody.

- Zjednodušení, vzdálené ladění odstraňují potřebu nakonfigurovat sdílenou složku a Unity. Teď stačí mít přístup ke svým projektem Unity z Windows.

- Instalace vlastního profilu Unity jako standardní profil cílového rozhraní .net. To řeší všechny počet falešně pozitivních výsledků, které se může zobrazit ReSharper.

- Alternativní Unity skriptování chyby modulu, aby ladicí program nebude správně přerušit na jiných zaregistrovaný vlákna.

- Přepracujte otevírající soubor tak, aby se zabránilo časování v sadě Visual Studio, ve kterém se vydával za nebudou moct otevřít soubory, při k chybě při požadavku na otevření souboru.

- UnityVS se nyní chce aktualizovat sestavení při sestavení projektu VS a už není v souboru uložte.

### <a name="bug-fixes"></a>Opravy chyb

- Opravili naše vlastní profil .net

- Oprava integrace motivy, to řeší naše problémy s tmavým motivem VS 2012.

- Rychlá oprava chování zástupce ve VS 2012.

- Opravili jsme krokování problém, který se může stát při ladění a mimo hlavní vlákno byste dostali na zarážku.

- Oprava UnityScript a poč dokončení aliasy typů, jako je například int.

- Oprava výjimky při zápisu nový UnityScript nebo poč řetězec.

- Oprava výjimky v nabídkách Unity při řešení nebyl načten.

- Oprava chyby UVS 48: zadáním dvojité uvozovky někdy chybě a přerušení všech – funkce (dokončování kódu, zvýraznění syntaxe atd).

- Opravená chyba UVS-46: Po kliknutí na Seznam chyb sady Visual Studio byl duplikován otevřený soubor skriptu (UnityScript).

- Opravená chyba UVS-42: Logo konektivity Unity ve stavovém řádku nezpracovává události myši v sadě VS 2012.

- Opravená chyba UVS-44: CTRL + SHIFT + Q není v sadě VS 2012 pro rychlé třídy MonoBehaviour k dispozici.

- Opravená chyba UVS-40: Vybrané položky v Průzkumníku projektů Unity jsou nečitelný, pokud je okno neaktivní v VS2012 "tmavého" motivu.

- Opravená chyba UVS-39: Vystavení tokenizacích řídicích řetězců

- Opravená chyba UVS-35: Při kontrole proměnných vyvolat ToString na objekty.

- Opravená chyba UVS-27: Přejít na okno symbolů nekonzistence s "tmavým" motivem v VS2012.

- Opravená chyba UVS-11: Lokální hodnoty v korutinách.

## <a name="1100---beta-release"></a>1.1.0.0 – beta verze
Vydáno 9. března, 2013

## <a name="10130"></a>1.0.13.0
Vydáno 21. ledna 2013

### <a name="bug-fixes"></a>Opravy chyb

- Oprava sady Visual Studio uzamkne, který se může stát, pokud cíl laděný proces je odesílání událostí neplatné vlákno. Která by obvykle stát při ladění vzdáleného Unity na os x.

- Opravili jsme sady Visual Studio se uzamkne, který se může stát, pokud výjimka ukončí ladicí program.

- Oprava naše MonoBehavior pomocné rutiny při MonoBehavior C# je v oboru názvů.

- Opravili jsme popisky ladicího programu pro UnityScript v sadě Visual Studio 2012.

- Opravili jsme generování projektu, když se změní pouze konstanty ladění z Unity.

- Oprava navigaci pomocí klávesnice v Průzkumníku projektů Unity.

- Oprava UnityScript obarvení uvozovacími znaky řetězce.

- Opravili jsme naše otevírající soubor uhodnutelné lepší název projektu při použití mimo Unity. Který je nezbytné, pokud uživatel použije v Unity, který se delegoval UnityVS třetí otevírající soubor část.

- Oprava zpracování dlouhé zprávy odeslané z Unity UnityVS. Před tímto dlouhých zpráv mohlo dojít k selhání naše zasílání zpráv součástí UnityVS. V důsledku toho někdy UnityVS nepůjde dokument otevřít soubor z Unity.

## <a name="10120"></a>1.0.12.0
Vydáno 3. lednu 2013

### <a name="bug-fixes"></a>Opravy chyb

- Oprava sady Visual Studio se uzamkne, může dojít v případě sady Visual Studio bylo odstranění zarážky.

- Je opravená chyba, kdy některé by zarážky po Unity překompilovány herní skripty.

- Opravili jsme ladicí program správně upozornit sady Visual Studio nevázaná zarážky.

- Oprava potíží registrace, které by mohlo ohrozit ladicího programu sady Visual Studio k ladění nativní aplikace.

- Oprava výjimky, které může dojít v případě, že vaše rozhodnutí vyzkoušet UnityScript a rezervace výrazy.

- Oprava regrese, kde by změna úrovně rozhraní API .net v Unity aktivovat aktualizaci souborů projektu.

- Opravili jsme poruchu rozhraní API, kde uživatelský kód nelze účastnit obslužná metoda zpětného volání protokolu.

## <a name="10110"></a>1.0.11.0
Vydáno 28. listopadu 2012

### <a name="new-features"></a>Nové funkce

- Oficiální podpora 4 Unity.

- Manipulace s skriptů z Průzkumníku projektů Unity.

- Integrace v sadě Visual Studio přejděte do okna.

- Analýza zprávu s informacemi o konzolu, tak, aby kliknutím na položku v seznamu chyb můžete přejít k první stackframe se symboly.

- Přidat [API](../cross-platform/customize-project-files-created-by-vstu.md) aby mohl uživatel součástí generování projektu.

- Přidat [API](../cross-platform/share-the-unity-log-callback-with-vstu.md) aby mohl uživatel účastnit LogCallback.

### <a name="bug-fixes"></a>Opravy chyb

- Oprava regrese na pozadí Průzkumník projektů Unity v sadě Visual Studio 2012.

- Opravili jsme generování projektu pro uživatele celého profilu .net.

- Opravili jsme generování projektu pro uživatele webový cíl.

- Generování pevné projektu zahrnout ladění a trasování kompilace symboly jako Unity nemá.

- Oprava chyb při použití speciálních znaků v našich Goto Symbol okna.

- Oprava chyb, pokud jsme nedá se dosadit naše ikonu na stavovém řádku v sadě Visual Studio.

## <a name="10100"></a>1.0.10.0
Vydáno 9. října 2012

### <a name="bug-fixes"></a>Opravy chyb

- Oprava na pozadí v Průzkumníku projektů Unity v sadě Visual Studio 2010.

- Opravili jsme zablokování sady Visual Studio, který se může stát, pokud UnityVS pokusili připojit ladicí modul k Unity, jehož rozhraní ladicího programu dříve došlo k chybě aplikace.

- Oprava, která může dojít v případě, že byla nastavena zarážka a opětovné načtení domény aplikace by dojít k zablokování sady Visual Studio.

- Opravili jsme, jak se načítají sestavení z Unity vyhnout zamykání souborů a obcházení proces sestavení Unity.

## <a name="1090"></a>1.0.9.0

Vydáno 3 říjen 2012

### <a name="bug-fixes"></a>Opravy chyb

- Opravili jsme generování projektu, pokud obsahuje skutečné prostředky jazyka JavaScript Unity projektu.

- Oprava chyby ve vyhodnocení výrazu.

- Opravili jsme nastavení nových hodnot pro pole typů hodnot.

- Oprava možné vedlejší efekty při přechodu myši nad výrazy z editoru kódu.

- Opravili jsme, jak jsou typy prohledaný načtená sestavení pro vyhodnocení výrazu.

- Opravená chyba UVS-21: Vyhodnocení přiřazení u objektů Unity nemá žádný vliv.

- Opravená chyba UVS-21: Neplatný ukazatel při vyhodnocování volání metody do rozhraní API pro matematiku Unity

## <a name="1080"></a>1.0.8.0

Vydáno 26. září 2012

### <a name="bug-fixes"></a>Opravy chyb

- Dlouhodobý způsob, jak naše skript otevírající získat cestu k projektu se ujistěte, zda je možné otevřít Visual Studio a skripty.

- Oprava chyby se zarážkami vytvořené během relace ladění byla spuštěna, který může způsobit sady Visual Studio k uzamčení.

- Opravili jsme, jak je UnityVS zaregistrovaná na Visual Studio 2010.

## <a name="1070"></a>1.0.7.0

Vydáno 14. září 2012

### <a name="new-features"></a>Nové funkce

- Podpora v sadě Visual Studio 2012.

### <a name="bug-fixes"></a>Opravy chyb

- Oprava generování editoru a moduly plug-in projektových souborů tak, aby odpovídaly Unity a chování.

- Opravili jsme překlad symbolů .pdb v Unity 4.

> [!IMPORTANT]
> Z důvodu podpory Visual Studio 2012 museli jsme přejmenovat několik souborů a některých dalších pohybovat. UnityVS balíčku k importu Unity teď jmenuje UnityVS 2010 nebo UnityVS 2012, respektive Visual Studio 2010 a Visual Studio 2012. Tato verze také vyžaduje, že UnityVS soubory projektu jsou znovu vygenerovány.

## <a name="1060---internal-build"></a>1.0.6.0 – interní sestavení
Vydáno 12. září 2012

## <a name="1050"></a>1.0.5.0

Vydáno 10. září 2012

### <a name="bug-fixes"></a>Opravy chyb

- Oprava generování souborů projektu, kdy skripty nebo shadery znak neplatný kód xml.

- Oprava zjišťování instancí Unity Unity bylo připojení k serveru Asset. Aktivuje toto selhání k otevírání souborů z Unity a automatické připojení ladicího programu sady Visual Studio.

## <a name="1040"></a>1.0.4.0

Vydané 5. září 2012

### <a name="new-features"></a>Nové funkce

- Automatický převod symbolů pro ladění v Unity.

    Pokud máte .dll sestavení .NET s jeho přidružené .pdb ve složce Asset, jednoduše znovu importujte sestavení a UnityVS převede na soubor symbolů ladění, Unity a skriptovací stroj rozumí a budete mít ke kroku do vašeho sestavení .NET z pdb UnityVS.

### <a name="bug-fixes"></a>Opravy chyb

- Oprava chyb UnityVS během ladění způsobeno výjimky vyvolané z metody nebo vlastnosti v Unity.

## <a name="1030"></a>1.0.3.0

Vydáno 4. září 2012

### <a name="new-features"></a>Nové funkce

- Nová možnost konfigurace zakázat použití UnityVS pro otevření souborů z Unity.

### <a name="bug-fixes"></a>Opravy chyb

- Oprava generování odkazů na UnityEditor pro projekty mimo editor.

- Oprava definice symbolu UNITY_EDITOR pro projekty mimo editor.

- Oprava náhodné VS případ chyby způsobené naše vlastní stavový řádek.

## <a name="1020"></a>1.0.2.0

Vydáno 30. srpna 2012

### <a name="bug-fixes"></a>Opravy chyb

- Oprava konflikt s ladicím programem PythonTools.

- Pevné odkazy na Mono.Cecil.

- Oprava chyby v sestaveních jak skriptovací byly načteny z Unity s b7 Unity 4.

## <a name="1010"></a>1.0.1.0

Vydáno 28. srpna 2012

### <a name="new-features"></a>Nové funkce

- Podpora pro Unity 4.0 beta verze Preview.

### <a name="bug-fixes"></a>Opravy chyb

- Oprava kontroly vlastnosti vyvolávání výjimek.

- Opravili jsme sestupně do základní objekty při kontrole objekty.

- Oprava prázdný rozevírací seznam pro kurzor v Průvodci MonoBehavior.

- Oprava dokončování pro knihovny dll ve složce Asset UnityScript a poč.

## <a name="1000---initial-release"></a>1.0.0.0 – počáteční verze
Vydáno 22. srpna 2012
