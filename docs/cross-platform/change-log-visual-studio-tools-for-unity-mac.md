---
title: Protokol změn (Visual Studio Tools for Unity, Mac) | Microsoft Docs
ms.custom: ''
ms.date: 5/19/2020
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 33a6ac54-d997-4308-b5a0-af7387460849
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 4fa5a68a15dd5b53d5a626ff5c46e9739db504fc
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84184559"
---
# <a name="change-log-visual-studio-tools-for-unity-mac"></a>Protokol změn (Visual Studio Tools for Unity, Mac)

Protokol změn Visual Studio Tools for Unity

## <a name="2610"></a>2.6.1.0
Vydáno 19. května 2020

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Upozorňovat, pokud nemůžeme vytvořit poštovní server na straně Unity.

  - Při zjednodušené kompilaci jsou správně spouštěny analyzátory.

  - Opravená dokumentace k rozhraní API s instalacemi v centru Unity
  
  - Chyby Vizualizér pevného ladicího programu.

## <a name="2600"></a>2.6.0.0
Vydáno 14. dubna 2020

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Přidání [`UNT0012`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/UNT0012.md) diagnostiky Detekovat a zalamovat volání korutin v `StartCoroutine()` .

  - Přidání [`UNT0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/UNT0013.md) diagnostiky Zjištění a odebrání neplatného nebo redundantního `SerializeField` atributu

  - Přidání [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/UNT0014.md) diagnostiky Detekce `GetComponent()` volána s typem bez komponenty nebo bez rozhraní.

  - Přidání [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0009.md) Suppressor pro `IDE0051` . Nepoužívejte příznak s `ContextMenu` atributem nebo odkazem na pole s `ContextMenuItem` atributem nepoužitelné.

  - Přidání [`USP0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0010.md) Suppressor pro `IDE0051` . Neoznačí pole `ContextMenuItem` atributem jako nepoužitou.

  - Přidání [`USP0011`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0011.md) Suppressor pro `IDE0044` . Nevytvářejte pole s `ContextMenuItem` atributem jen pro čtení.

  - [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0004.md)[`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0006.md)a [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0007.md) teď fungují pro `SerializeReference` atributy i `SerializeField` .

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Když je editor schopný komunikovat, odesílají jenom příkazy spustit/zastavit do Unity.

  - Opravená dokumentace QuickInfo s děděnými zprávami.

  - Rozsah pevné zprávy pro `CreateInspectorGUI` zprávu

  - Nevytvářejte sestavy [`UNT0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/UNT0001.md) metod s polymorfními modifikátory.

- **Hodnocení**

  - Pevné zpracování aliasů using.
  
  - Pevné zpracování hodnot null.  

## <a name="2520"></a>2.5.2.0

Vydáno 23. března 2020

### <a name="bug-fixes"></a>Opravy chyb

- **Ladění**

  - Pevná registrace vláken při připojení.

## <a name="2510"></a>2.5.1.0

Vydáno 3. března 2020

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Přidání [`USP0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0008.md) Suppressor pro `IDE0051` . Soukromé metody použité s voláním Invoke, InvokeRepeating, StartCoroutine nebo StopCoroutine by neměly být označeny jako nepoužívané.

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Opravená dokumentace funkci ondrawgizmos implementujte/funkci ondrawgizmosselected implementujte.

- **Hodnocení**

  - Opravená kontrola argumentu lambda.

## <a name="2501"></a>2.5.0.1

Vydáno 19. února 2020

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Opravila se [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/UNT0006.md) Kontrola diagnostiky pro nesprávný podpis zprávy. Při kontrole typů s více úrovněmi dědičnosti může tato diagnostika selhat s následující zprávou: `warning AD0001: Analyzer 'Microsoft.Unity.Analyzers.MessageSignatureAnalyzer' threw an exception of type 'System.ArgumentException' with message 'An item with the same key has already been added` .

## <a name="2500"></a>2.5.0.0

Vydáno 22. ledna 2020

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Přidání podpory pro soubory HLSL
  
  - Přepnuto na uživatelské rozhraní dialogového okna nové složky.
  
  - Přepnuto na novou přístupnou mřížku vlastností pro nastavení.

  - Přidání [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0006.md) Suppressor pro `IDE0051` . Soukromá pole s `SerializeField` atributem by neměla být označena jako nepoužitá.

  - Přidání [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0007.md) Suppressor pro `CS0649` . Pole s `SerializeField` atributem by neměla být označena jako Nepřiřazená.  

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Generování fixního projektu ( `GenerateTargetFrameworkMonikerAttribute` cíl nebyl vždy uložen správně).

- **Hodnocení**

  - Vyhodnocování pevného řetězce (nepoužívá volání ToString ())

## <a name="2420"></a>2.4.2.0

Vydáno 3. prosince 2019

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Pevná Diagnostika s uživatelsky definovanými rozhraními.

  - Opravili jsme rychlé popisy s poškozenými výrazy.
  
## <a name="2410"></a>2.4.1.0

Vydáno 6. listopadu 2019

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Přidala se podpora pro procesy na pozadí Unity. (Ladicí program se může automaticky připojit k hlavnímu procesu místo podřízeného procesu).

  - Přidali jsme rychlý popis pro zprávy Unity a zobrazí se související dokumentace.

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Opravili jsme analyzátor porovnání značek `UNT0002` pomocí pokročilých binárních a volání výrazů.

### <a name="deprecated-features"></a>Zastaralé funkce

- **Spolupráci**

  - Až budete dál, Visual Studio Tools for Unity podporují jenom Visual Studio 2017 +.

## <a name="2400"></a>2.4.0.0

Vydáno 15. října 2019

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Přidání [`USP0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0005.md) Suppressor pro `IDE0060` (nepoužitý parametr) pro všechny zprávy Unity

  - Byl přidán rychlý popis pro pole s příznakem `TooltipAttribute` . (To bude fungovat také pro jednoduché přístupové objekty get pomocí tohoto pole.)

## <a name="2330"></a>2.3.3.0

Vydáno 23. září 2019

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Přidání nového Suppressor pro IDE0060, aby se zabránilo tomu, aby se IDE zobrazovala Rychlá oprava pro odebrání nepoužitých parametrů.
    - `USP0005`pro `IDE0060` : zprávy Unity jsou vyvolány modulem runtime Unity.

## <a name="2320"></a>2.3.2.0

Vydáno 16. září 2019

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Provedli jsme porozumění, že Visual Studio má pro projekty Unity přidat novou diagnostiku specifickou pro Unity. Také jsme zvýšili inteligenci integrovaného vývojového prostředí (IDE) tím, že jsme potlačili obecnou diagnostiku C#, která se nevztahuje na projekty Unity. Například rozhraní IDE nebude zobrazovat rychlou opravu pro změnu proměnné inspektoru, `readonly` která by zabránila v úpravách proměnné v editoru Unity.
    - `UNT0001`: Zprávy Unity jsou volány modulem runtime, i když jsou prázdné, Nedeklarujte je, aby nedocházelo ke zpracování uncesseray modulem runtime Unity.
    - `UNT0002`: Porovnávání značek pomocí rovnosti řetězců je pomalejší než integrovaná metoda CompareTag.
    - `UNT0003`: Použití obecného formuláře pro getComponent je upřednostňováno pro bezpečnost typů.
    - `UNT0004`: Zpráva aktualizace je závislá na frekvenci snímků a měla by místo času. fixedDeltaTime použít Time. deltaTime.
    - `UNT0005`: Zpráva FixedUpdate je nezávislá na snímkovém tempu a měla by místo času. deltaTime používat Time. fixedDeltaTime.
    - `UNT0006`: Pro tuto zprávu Unity byl zjištěn nesprávný podpis metody.
    - `UNT0007`: Unity Přepisuje operátor porovnání s hodnotou null pro objekty Unity, které nejsou kompatibilní s hodnotou null pro slučování.
    - `UNT0008`: Unity přepíše operátor porovnání s hodnotou null pro objekty Unity, které nejsou kompatibilní s rozšířením s hodnotou null.
    - `UNT0009`: Při použití atributu InitializeOnLoad pro třídu je nutné zadat statický konstruktor. Atribut InitializeOnLoad zajistí, že bude volán při spuštění editoru.
    - `UNT0010`: Třídy MonoBehaviour by mělo být vytvořeno pouze pomocí AddComponent (). Objekt MonoBehaviour je komponenta, která musí být připojená k objektu GameObject.
    - `UNT0011`: ScriptableObject by mělo být vytvořeno pouze pomocí metody CreateInstance (). Objekt ScriptableObject musí být vytvořený modulem Unity, aby zpracovával metody zpráv Unity.
    - `USP0001`pro `IDE0029` : objekty Unity by neměly používat slučování s hodnotou null.
    - `USP0002`pro `IDE0031` : objekty Unity by neměly používat šíření hodnoty null.
    - `USP0003`pro `IDE0051` : zprávy Unity jsou vyvolány modulem runtime Unity.
    - `USP0004`for `IDE0044` : pole s atributem SerializeField by neměla být určena jen pro čtení.

## <a name="2310"></a>2.3.1.0

Vydáno 4. září 2019

### <a name="new-features"></a>Nové funkce

- **Hodnocení**

  - Přidání podpory pro lepší zobrazení typu, tj. `List<object>` místo `List'1[[System.Object, <corlib...>]]` .

  - Přidání podpory pro přístup ke členu ukazatele, `p->data->member` tj.

  - Přidání podpory pro implicitní převody v inicializátorech pole, `new byte [] {1,2,3,4}` tj.

  - Byla přidána podpora šestnáctkového editoru při kontrole bajtových polí a řetězců.

## <a name="2300"></a>2.3.0.0

Vydáno 13. srpna 2019

### <a name="bug-fixes"></a>Opravy chyb

- **Hodnocení**

  - Opravili jsme problémy krokování s výjimkami.

  - Pevné vyhodnocení pseudo identifikátorů (například $exception).

  - Zabraňte selhání při přesměrování neplatných adres.  

  - Opravili jsme problém s uvolněnými doménami AppDomain.

## <a name="2200"></a>2.2.0.0

Vydáno 25. července 2019

### <a name="bug-fixes"></a>Opravy chyb

- **Hodnocení**

  - Pevná kontrola s použitím typů IntPtr.

- **Ladění**

  - Pevné zpracování catchpoints a zarážek funkcí.

## <a name="2130"></a>2.1.3.0

Vydáno 9. července 2019

### <a name="new-features"></a>Nové funkce

- **Ladění**

  - Přidání podpory pro zachycení podtříd výjimek.

  - Byla přidána podpora protokolu MDS 2,51.

- **Spolupráci**

  - Přidání podpory pro soubory asmdef

  - Přepne do režimu přejmenování při přidání souboru ze šablony (pro napodobení chování editoru Unity).

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Pevné zpracování poškozených zpráv při komunikaci s přehrávači Unity.

- **Hodnocení**

  - Pevné zpracování oborů názvů ve výrazech.

## <a name="2120"></a>2.1.2.0

Vydáno 2. července 2019

### <a name="bug-fixes"></a>Opravy chyb

- **Hodnocení**

  - Bylo opraveno zasílání zpráv o chybách s neanalyzovanými výrazy.

## <a name="2110"></a>2.1.1.0

Vydáno 27. června 2019

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Rozhraní MonoBehaviour API se aktualizovalo na 2019,1.

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Pevný výkon Průzkumníka projektů Unity.

  - Opravená upozornění a chyby při generování výstupu, když je povolené zjednodušené sestavení.

  - Pevný výkon pro odlehčené sestavení.

## <a name="2100"></a>2.1.0.0

Vydáno 20. června 2019

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Pro projekty Unity se zakázalo úplné sestavení, a to na základě chyb a upozornění technologie IntelliSense. Ve skutečnosti Unity vytvoří řešení sady Visual Studio s projekty knihoven tříd, které reprezentují, co Unity interně dělá. To se říká, výsledek sestavení v sadě Visual Studio se nikdy nepoužívá nebo nezískala v Unity, protože je jejich kanál kompilace uzavřený. Sestavování v aplikaci Visual Studio právě spotřebovává prostředky pro nic. Pokud potřebujete úplné sestavení, protože máte nástroje nebo nastavení, které na něm závisí, můžete tuto optimalizaci zakázat (nastavení/nástroje pro Unity nebo zakázat úplné sestavení projektů).
  
  - Přidala se podpora pro balíčky Unity v UPE. Jsou viditelné pouze odkazované balíčky (používající manifest. JSON ve `Packages` složce) a místní balíčky (vložené do `Packages` složky).

## <a name="2021"></a>2.0.2.1

Vydáno 30. května 2019

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Přidání vlastní ikony pro cíle provádění Unity

## <a name="2020"></a>2.0.2.0

Vydáno 2. dubna 2019

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Přidání podpory pro automatickou aktualizaci databáze assetů v Unity při uložení Tato možnost je ve výchozím nastavení povolená a při ukládání skriptu do sady Visual Studio aktivuje novou kompilaci na straně Unity. Tuto funkci můžete zakázat v Tools\Options\Tools pro AssetDatabase v Unity\Refresh Unity při uložení.

  - Přidání podpory pro nastavení upřednostňované instalace Unity pro offline dokumentaci

  - Přidala se místní nabídka pro nový editor.

### <a name="bug-fixes"></a>Opravy chyb

- **Ladění**

  - Pevné filtrování sestavení a kontrola snímků s prázdnými snímky.

## <a name="2011"></a>2.0.1.1
 
 Vydáno 26. března 2019

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Dočasně nastavte mono výchozí a jenom použitelný ladicí program pro tuto velmi specifickou verzi.

## <a name="2006"></a>2.0.0.6

Vydáno 26. března 2019

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Byla přidána podpora "připojit k Unity a hrát".

## <a name="2005"></a>2.0.0.5

Vydáno 20. března 2019

### <a name="new-features"></a>Nové funkce

- **Generování projektu:**

  - Při zpracování souboru řešení zachovat externí vlastnosti.
  
- **Hodnocení**

  - Byla přidána podpora názvů kvalifikovaných aliasů (pouze globální obor názvů pro nyní). Proto vyhodnocovací filtr výrazů nyní přijímá typy pomocí formuláře Global:: Namespace. Type.

  - Přidání podpory pro `pointer[index]` formulář, která je sémanticky totožná s odkazem na odkazy na ukazatel `*(pointer+index)` .

## <a name="2004"></a>2.0.0.4

Vydáno 5. března 2019

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Rozhraní API se aktualizovalo `ScriptableObject` .

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Z šablon se odebraly obory názvů.

## <a name="2003"></a>2.0.0.3
 
 Vydáno 5. března 2019

### <a name="new-features"></a>Nové funkce

- **Generování projektu:**

  - Veřejná a serializovaná pole už nebudou způsobovat upozornění. Automaticky jsme potlačili `CS0649` `IDE0051` Upozornění kompilátoru a v projektech Unity, která tyto zprávy vytvořila.

- **Spolupráci**

  - Pokud více než jeden proces Unity běží, zobrazí se výzva k připojení ke konkrétní instanci.

- **Hodnocení**

  - Byla přidána podpora místních funkcí.

### <a name="bug-fixes"></a>Opravy chyb

- **Ladění**

  - Bylo vyřešeno čtení vlastního atributu u pojmenovaných argumentů při použití starších verzí protokolu.

## <a name="2002"></a>2.0.0.2

Vydáno 4. února 2019

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Aktualizace rozhraní API MonoBehaviour

### <a name="bug-fixes"></a>Opravy chyb

- **Ladění**

  - Pevné nastavení primitivních hodnot v ladicím programu.

## <a name="2001"></a>2.0.0.1

Vydáno 4. prosince 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Pevný balíček pevného instalačního balíčku.

## <a name="2000"></a>2.0.0.0
 Vydáno 4. prosince 2018

### <a name="new-features"></a>Nové funkce

- **Ladění**

  - Nahradili jsme ladicí program Unity na Macu stejným základním ladicím programem Unity z Windows.

  - Nahradili jsme NRefactory a upřednostňujeme Roslyn pro vyhodnocení výrazu.

  - Přidání podpory pro ukazatele: dereference, přetypování a aritmetické operace (2018.2 Unity + a nový modul runtime jsou pro toto) nutné.

  - Přidání podpory pro zobrazení ukazatele pole (jako v jazyce C++). Ponechejte výraz ukazatele a potom přidejte čárku a počet prvků, které chcete zobrazit.

  - Byla přidána podpora pro asynchronní konstrukce.

  - Přidání podpory pro pseudo Variables (výjimky a identifikátory objektů).

### <a name="bug-fixes"></a>Opravy chyb

- **Ladění**

  - Vyhodnocení výrazu se špatnými nebo nepodporovanými výrazy.

## <a name="1700"></a>1.7.0.0

Vydáno 13. listopadu 2018

### <a name="new-features"></a>Nové funkce

- **Ladění**

  - Do dialogového okna připojit se přidaly Další informace o klientovi (IP adresa, název počítače).

### <a name="bug-fixes"></a>Opravy chyb

- **Ladění**

  - Opravili jsme zablokování v knihovně používané ke komunikaci s modulem ladicího programu Unity, aby se aplikace Visual Studio nebo Unity zablokoval, zejména když jste se připojili k Unity nebo restartujete hru.

- **Spolupráci**

  - Pevná aktivace modulu plug-in Unity, pokud byl vybrán jiný výchozí editor.

  - Pevné vytvoření šablony souboru Unity

## <a name="1602"></a>1.6.0.2

Vydáno 24. července 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Odebrali jsme řešení chyby výkonu Unity, které vyřešila Unity.

## <a name="1601"></a>1.6.0.1

Vydáno 10. července 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Pevná podpora zbarvení kódu shaderu

## <a name="1600"></a>1.6.0.0

Vydáno 26. června 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Průvodc**

  - Opravené překlepy pomocí OnApplicationFocus zprávy.

- **Generování projektu:**

  - Přechodný alternativní postup pro chybu výkonu Unity: mezipaměť MonoIslands při generování projektů.

  - Při použití nového modulu runtime Unity neprovádějte převod přenositelných souborů PDB na MDB.

## <a name="1502"></a>1.5.0.2

Vydáno 18. dubna 2018

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Přidání podpory základního dokončování kódu shaderu

  - Přidání podpory pro přepínání komentářů v souborech shaderu.

## <a name="1501"></a>1.5.0.1

Vydáno 28. března 2018

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Přidání podpory pro další šablony v Průzkumníku projektů Unity.

## <a name="1500"></a>1.5.0.0

Vydáno 21. března 2018

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Přidali jsme podporu pro detekci a připojení k přehrávačům pro Android připojeným přes USB.

## <a name="1403"></a>1.4.0.3

Vydáno 5. března 2018

### <a name="new-features"></a>Nové funkce

- **Generování projektu:**

  - Přidání podpory nového generátoru projektu v Unity 2018,1.

- **Spolupráci**

  - Byl přidán panel možností pro vyhrazená nastavení.

## <a name="1402"></a>1.4.0.2

Vydáno 24. ledna 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Opravená detekce verze mono

- **Spolupráci**

  - Pevné problémy s časováním pomocí 2018,1 a aktivace modulu plug-in.

  - Při zjišťování nového přehrávače se opravila oznámení.

## <a name="1401"></a>1.4.0.1

Vydáno 23. ledna 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Pevné složky pro rozbalení/sbalení při poklikání

## <a name="1400"></a>1.4.0.0

Vydáno 13. prosince 2017

### <a name="new-features"></a>Nové funkce

- **Generování projektu:**

  - Byla přidána podpora pro .NET Standard.

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Opravený automatický převod souboru PDB na soubor MDB pro ladění.

## <a name="1301"></a>1.3.0.1

Vydáno 12. prosince 2017

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Pevné nepřímá volání EditorPrefs. getbool má vliv na inspektora při pokusu o změnu velikosti pole.

- **Průvodc**

  - Aktualizujte kontext Roslyn před vložením metody.

## <a name="1300"></a>1.3.0.0

Vydáno 20. listopadu 2017

### <a name="new-features"></a>Nové funkce

- **Průvodc**

  - Bylo přidáno Průvodce implementací zprávy Unity.

  - Přidání podpory pro nové rozhraní API pro dokončení v VS pro Mac 7,4.

## <a name="1200"></a>1.2.0.0

Vydáno 23. října 2017

### <a name="new-features"></a>Nové funkce

- **Ladění**

  - Přidání podpory pro přenositelné soubory se symboly ladění.

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Opravené rozšíření extra. dll je nesprávně přidáno k názvu souboru sestavení.

  - Nevynuťte si příznak Unity AllowAttachedDebuggingOfEditor, protože výchozí hodnota je nyní true.

## <a name="1103"></a>1.1.0.3

Vydáno 23. října 2017

### <a name="new-features"></a>Nové funkce

- **Generování projektu:**

  - Přidala se podpora pro profil .NET 4,6.

## <a name="1102"></a>1.1.0.2

Vydáno 8. srpna 2017

### <a name="new-features"></a>Nové funkce

- **Ladění**

  - Spusťte dialog připojit k procesu, pokud si nejste jisti, ke které Unity se chcete připojit.

- **Generování projektu:**

  - Vždy povolit nezabezpečený přepínač kompilace při použití Unity 5,6.

## <a name="1101"></a>1.1.0.1

Vydáno 20. července 2017

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Přidání podpory pro lokalizované prostředky.

## <a name="1100"></a>1.1.0.0

Vydáno 12. července 2017

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Přidání podpory pro připojení k přehrávačům a editorům prostřednictvím okna připojit k procesu.

- **Generování projektu:**

  - Pevný název sestavení odkazuje na soubory MCS. rsp.

  - Byla přidána podpora pro kompilační jednotky sestavení. JSON.

  - Fixed definuje s úrovněmi rozhraní API.

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Opravila se chybová zpráva shaderu při kompilaci.

## <a name="1001"></a>1.0.0.1

Vydáno 4. května 2017

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Pevné sledování aktivního dokumentu s hybridními a pravidelnými projekty.

## <a name="1000"></a>adresu

Vydáno 3. května 2017
