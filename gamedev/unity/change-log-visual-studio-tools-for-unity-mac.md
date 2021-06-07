---
title: Protokol změn (Visual Studio Tools for Unity, Mac) | Microsoft Docs
description: Zobrazit protokol změn pro Visual Studio Tools for Unity, Mac. Viz změny od verze 1.0.0.0 až po 2.7.0.0 a vyšší.
ms.custom: ''
ms.date: 6/3/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: 33a6ac54-d997-4308-b5a0-af7387460849
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 2d3faf8e5231ca5d2e99bcf80dc18b6d4f4607cd
ms.sourcegitcommit: f430d014f912aa7874e1db65026dc72688b973e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2021
ms.locfileid: "111448295"
---
# <a name="change-log-visual-studio-tools-for-unity-mac"></a>Protokol změn (Visual Studio Tools for Unity, Mac)

Protokol změn Visual Studio Tools for Unity

## <a name="21020"></a>2.10.2.0
Vydáno 2. června 2021

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Přidání [`UNT0024`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0024.md) diagnostiky Dává přednost skalárním výpočtům prostřednictvím výpočtů vektoru.

- **Hodnocení**

  - Přidání podpory pro použití přenosných symbolů PDB pro správné filtrování viditelných místních hodnot.

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Pevný přehrávač oznamuje analýzu s nejnovějšími verzemi Unity.

## <a name="21010"></a>2.10.1.0
Vydáno 11. května 2021

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Pevné problémy se stabilitou [`UNT0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0008.md) QuickFix.

  - Vyřešené problémy s výkonem s vlákny.

  - Pevné filtrování potlačených upozornění a chyb v seznam chyb.

  - Pevné filtrování procesů na pozadí Unity

## <a name="21000"></a>2.10.0.0
Vydáno 13. dubna 2021

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Přidání [`UNT0019`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0019.md) diagnostiky Nepotřebná nepřímá volání pro `GameObject.gameObject` .

  - Přidání [`UNT0020`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0020.md) diagnostiky `MenuItem` atribut, který se používá pro nestatickou metodu

  - Přidání [`UNT0021`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0021.md) diagnostiky Zpráva Unity by měla být chráněná (výslovný souhlas).

  - Přidání [`UNT0022`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0022.md) diagnostiky Neefektivní metoda pro nastavení pozice a rotace.

  - Přidání [`UNT0023`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0023.md) diagnostiky Přiřazení slučovacích objektů Unity

  - Přidání [`USP0017`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0017.md) Suppressor pro `IDE0074` . Objekty Unity by neměly používat přiřazení slučování.

## <a name="2940"></a>2.9.4.0
Vydáno 6. dubna 2021

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Oprava problémů s výčtem testů

## <a name="2930"></a>2.9.3.0
Vydáno 30. března 2021

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Oprava problémů pomocí nástroje Test Runner 

## <a name="2920"></a>2.9.2.0
Vydáno 2. března 2021

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Opravili jsme zvýrazňování hledání v dialogu zprávy Unity.

  - Pevné problémy se stabilitou pomocí prvku TreeView projektu Unity.

- **Tém**

  - Pevné zpracování podmíněných zarážek.

## <a name="2910"></a>2.9.1.0
Vydáno 9. února 2021

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Přidání podpory pro spouštění a ladění testů Unity z integrovaného vývojového prostředí

- **Hodnocení**

  - Přidáno `Active Scene` do místních hodnot, kde se zobrazují kořenové herní objekty.

  - Přidáno `this.gameObject` do místních hodnot, pokud je v nich široce používáme v projektech Unity.

  - Přidány `Children` a `Components` seskupují všechny `GameObject` instance, abyste mohli snadno zobrazit celou hierarchii objektů.

  - Přidáno `Scene Path` do všech `GameObject` instancí, aby se zobrazilo umístění ve scéně.

  - Přidání podpory pro `JobEntityBatch` /Lambdas při použití entit se zdrojovými generátory

  - Vylepšená podpora pro zobrazování velkých polí (pomocí kontejnerů indexů).

  - Pro rozhraní API 2019,4 se přidaly chybějící zprávy Unity.

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Pevné problémy se stabilitou pomocí dialogu zprávy Unity

  - Opravili jsme různé problémy uživatelského rozhraní pro jiné než CSYé jazyky.

  - Pevné problémy se stabilitou s [`UNT0018`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0018.md) diagnostikou.

- **Tém**

  - Pevné problémy s odpojením virtuálního počítače při použití `Trace` metod.

- **Hodnocení**

  - Pevné Filtrování zastaralých vlastností vyvolává výjimky.

## <a name="2900"></a>2.9.0.0
Vydáno 20. ledna 2021

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Přidání podpory pro `raytrace shaders` `UXML` soubory a `USS` .

  - Aktualizované rozhraní API pro zprávy Unity (pro všechny metody používané jako korutiny).

  - Bylo aktualizováno zjišťování Android SDK.

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Opravená [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md) Diagnostika, která poskytuje chybná upozornění pro korutiny a `AssetPostprocessor.OnAssignMaterialModel` .

## <a name="2840"></a>2.8.4.0
Vydáno 15. prosince 2020

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Opravili jsme problém se spolehlivostí při zavírání Průvodce vytvořením události Unity.

## <a name="2830"></a>2.8.3.0
Vydáno 10. listopadu 2020

### <a name="bug-fixes"></a>Opravy chyb

- **Ladění**

  - Pevně se připojuje k Unity i v případě, že v řešení není žádný projekt VSTU.

## <a name="2820"></a>2.8.2.0
Vydáno 27. října 2020

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - [`UNT0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0010.md)Vylepšili jsme diagnostiku tak, aby se aplikuje na všechno, co `Component` dědí z , a ne jenom `MonoBehaviour` na .

## <a name="2810"></a>2.8.1.0
Vydáno 13. října 2020

### <a name="new-features"></a>Nové funkce

- **Hodnocení:**

  - Přidání podpory implicitního převodu s vyvoláními Vyhodnocovač dříve vynucoval striktní kontrolu typů, což vedlo k `Failed to find a match for method([parameters...])` upozorněním.

- **Integrace:**

  - Přidali [`UNT0018`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0018.md) jsme diagnostiku. Funkce ve zprávách `System.Reflection` kritických pro výkon, jako jsou , , nebo , byste neměli `Update` `FixedUpdate` `LateUpdate` `OnGUI` používat.

  - Vylepšené [`USP0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0003.md) [`USP0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0005.md) potlačení a s podporou všech `AssetPostprocessor` statických metod.

  - Přidání [`USP0016`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0016.md) potlačení pro `CS8618` . `C# 8.0` zavádí odkazové typy s možnou hodnotou null a odkazové typy s možnou hodnotou null. Detekce inicializace typů zděděných `UnityEngine.Object` z není podporována a bude mít za následek chyby.

  - Teď používáte stejný přehrávač a mechanismus generování projektů asmdef pro Unity 2019.x i 2020.x+.
  
  - Vylepšené uživatelské prostředí při generování zpráv Unity pomocí průvodce

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opravili jsme neočekávané dokončování zpráv v komentářích.

## <a name="2800"></a>2.8.0.0 
Vydáno 14. září 2020

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opravili jsme generování projektů hráčů pomocí Unity 2019.x.

## <a name="2710"></a>2.7.1.0
Vydáno 5. srpna 2020

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Aktualizace rozhraní API pro zprávy Unity na verzi 2019.4

  - Přidání [`USP0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0013.md) potlačení pro `CA1823` . Soukromá pole s `SerializeField` `SerializeReference` atributy nebo by se neměla označit jako nepoužívané (FxCop).
  
  - Přidání [`USP0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0014.md) potlačení pro `CA1822` . Zprávy Unity by neměly být označeny jako kandidáty `static` na modifikátor (FxCop).

  - Přidání [`USP0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0015.md) potlačení pro `CA1801` . Nepoužívané parametry by neměly být odebrané ze zpráv Unity (FxCop).
  
  - Přidání `MenuItem` podpory do [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md) potlačovače  

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Oprava [`USP0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0001.md) [`USP0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0002.md) a potlačení nefungují s extra závorkami nebo s argumenty metody.
  
  - Opravili jsme povinnou aktualizaci databáze assetu i v případě, že byla v nastavení Unity zakázaná automatická aktualizace.

## <a name="2700"></a>2.7.0.0
Vydáno 23. června 2020

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidání podpory pro zachování složek řešení při opětovném vygenerování řešení a projektů Unity

  - Přidali [`UNT0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0015.md) jsme diagnostiku. Rozpoznání nesprávné signatury metody `InitializeOnLoadMethod` s `RuntimeInitializeOnLoadMethod` atributem nebo .

  - Přidali [`UNT0016`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0016.md) jsme diagnostiku. Použití `Invoke` , nebo s prvním `InvokeRepeating` `StartCoroutine` `StopCoroutine` argumentem, který je řetězcový literál, není typový bezpečný.

  - Přidali [`UNT0017`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0017.md) jsme diagnostiku. `SetPixels` Volání je pomalé.

### <a name="bug-fixes"></a>Opravy chyb

- **Ladicí program:**

  - Opravili jsme vytváření zarážek, když hra běží na staré Mono runtime (pokus o vytvoření zarážky při pokusu o vytvoření). 
  
- **Integrace:**

  - Při filtrování zpráv v průvodci zprávami Unity nenulujte výběr.
  
  - Oprava , a suppressors s následujícími [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md) pravidly: [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) suppress [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) `IDE0044` (readonly), (unused), (never assigned) pro všechna pole `IDE0051` `CS0649` dekorovaná atributem SerializeField. Potlačit `CS0649` (nikdy nepřiřazeno) pro veřejná pole všech typů, které rozšiřují `Unity.Object`.

  - Oprava kontroly parametrů obecného typu pro [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md) .

- **Hodnocení:**

  - Oprava porovnání rovnosti s výčty

## <a name="2610"></a>2.6.1.0
Vydáno 19. května 2020

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Upozornit, pokud se nám nedaří vytvořit server pro zasílání zpráv na straně Unity.

  - Analyzátory se správně spouštěly během zjednodušené kompilace.

  - Opravili jsme dokumentaci k rozhraní API s instalacemi Unity Hubu.
  
  - Opravili jsme selhání vizualizéru ladicího programu.

## <a name="2600"></a>2.6.0.0
Vydáno 14. dubna 2020

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidali [`UNT0012`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0012.md) jsme diagnostiku. Rozpoznání a zabalení volání korutiny v `StartCoroutine()` .

  - Přidali [`UNT0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0013.md) jsme diagnostiku. Rozpoznání a odebrání neplatného nebo redundantního `SerializeField` atributu

  - Přidali [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md) jsme diagnostiku. Rozpoznání `GetComponent()` s typem bez komponenty nebo bez rozhraní

  - Přidání [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md) potlačení pro `IDE0051` . Ne flagujte metody s `ContextMenu` atributem nebo odkazované polem s `ContextMenuItem` atributem jako nepoužívané.

  - Přidání [`USP0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0010.md) potlačení pro `IDE0051` . Neo označení polí s `ContextMenuItem` atributem jako nepoužívaných

  - Přidání [`USP0011`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0011.md) potlačení pro `IDE0044` . Nevyděláte pole s `ContextMenuItem` atributem jen pro čtení.

  - [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md)A [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) teď fungují pro atributy `SerializeReference` `SerializeField` i .

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Příkazy pro spuštění/zastavení odešlete Unity jenom v případě, že editor dokáže komunikovat.

  - Opravili jsme dokumentaci QuickInfo se zděděnou zprávou.

  - Oprava oboru zpráv `CreateInspectorGUI` pro zprávu

  - Nehlásit metody [`UNT0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0001.md) s polymorfním modifikátory.

- **Hodnocení:**

  - Opravili jsme zpracování aliasů using.
  
  - Opravili jsme zpracování hodnot null.  

## <a name="2520"></a>2.5.2.0

Vydáno 23. března 2020

### <a name="bug-fixes"></a>Opravy chyb

- **Ladění**

  - Pevná registrace vláken při připojení.

## <a name="2510"></a>2.5.1.0

Vydáno 3. března 2020

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Přidání [`USP0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0008.md) Suppressor pro `IDE0051` . Soukromé metody použité s voláním Invoke, InvokeRepeating, StartCoroutine nebo StopCoroutine by neměly být označeny jako nepoužívané.

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Opravená dokumentace funkci ondrawgizmos implementujte/funkci ondrawgizmosselected implementujte.

- **Hodnocení**

  - Opravená kontrola argumentu lambda.

## <a name="2501"></a>2.5.0.1

Vydáno 19. února 2020

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Opravila se [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md) Kontrola diagnostiky pro nesprávný podpis zprávy. Při kontrole typů s více úrovněmi dědičnosti může tato diagnostika selhat s následující zprávou: `warning AD0001: Analyzer 'Microsoft.Unity.Analyzers.MessageSignatureAnalyzer' threw an exception of type 'System.ArgumentException' with message 'An item with the same key has already been added` .

## <a name="2500"></a>2.5.0.0

Vydáno 22. ledna 2020

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Přidání podpory pro soubory HLSL
  
  - Přepnuto na uživatelské rozhraní dialogového okna nové složky.
  
  - Přepnuto na novou přístupnou mřížku vlastností pro nastavení.

  - Přidání [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) Suppressor pro `IDE0051` . Soukromá pole s `SerializeField` atributem by neměla být označena jako nepoužitá.

  - Přidání [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) Suppressor pro `CS0649` . Pole s `SerializeField` atributem by neměla být označena jako Nepřiřazená.  

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

  - Přidání [`USP0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0005.md) Suppressor pro `IDE0060` (nepoužitý parametr) pro všechny zprávy Unity

  - Byl přidán rychlý popis pro pole s příznakem `TooltipAttribute` . (To bude fungovat také pro jednoduché přístupové objekty get pomocí tohoto pole.)

## <a name="2330"></a>2.3.3.0

Vydáno 23. září 2019

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Přidání nového Suppressor pro IDE0060, aby se zabránilo tomu, aby se IDE zobrazovala Rychlá oprava pro odebrání nepoužitých parametrů.
    - `USP0005` pro `IDE0060` : zprávy Unity jsou vyvolány modulem runtime Unity.

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
    - `USP0001` pro `IDE0029` : objekty Unity by neměly používat slučování s hodnotou null.
    - `USP0002` pro `IDE0031` : objekty Unity by neměly používat šíření hodnoty null.
    - `USP0003` pro `IDE0051` : zprávy Unity jsou vyvolány modulem runtime Unity.
    - `USP0004` for `IDE0044` : pole s atributem SerializeField by neměla být určena jen pro čtení.

## <a name="2310"></a>2.3.1.0

Vydáno 4. září 2019

### <a name="new-features"></a>Nové funkce

- **Hodnocení**

  - Přidání podpory pro lepší zobrazení typu, tj. `List<object>` místo `List'1[[System.Object, <corlib...>]]` .

  - Přidání podpory pro přístup ke členu ukazatele, `p->data->member` tj.

  - Byla přidána podpora implicitních převodů v inicializátorech polí, tj. `new byte [] {1,2,3,4}` .

  - Byla přidána podpora šestnáctkového editoru při kontrole polí bajtů a řetězců.

## <a name="2300"></a>2.3.0.0

Vydáno 13. srpna 2019

### <a name="bug-fixes"></a>Opravy chyb

- **Hodnocení:**

  - Opravili jsme problémy s krokováním s výjimkami.

  - Opravili jsme vyhodnocení pseudo identifikátorů (například $exception).

  - Zabránit selhání při derefererování neplatných adres.  

  - Opravili jsme problém s uvolněnou doménou appdomain.

## <a name="2200"></a>2.2.0.0

Vydáno 25. července 2019

### <a name="bug-fixes"></a>Opravy chyb

- **Hodnocení:**

  - Oprava kontroly s typy IntPtr

- **Ladicí program:**

  - Opravili jsme zpracování zachytáků a zarážek funkcí.

## <a name="2130"></a>2.1.3.0

Vydáno 9. července 2019

### <a name="new-features"></a>Nové funkce

- **Ladicí program:**

  - Přidání podpory pro zachytání podtříd výjimek

  - Byla přidána podpora pro protokol MDS 2.51.

- **Integrace:**

  - Přidání podpory pro soubory asmdef

  - Při přidání souboru ze šablony přepněte do režimu přejmenování (napodobte chování editoru Unity).

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opravili jsme zpracování poškozených zpráv při komunikaci s hráči Unity.

- **Hodnocení:**

  - Opravili jsme zpracování oborů názvů ve výrazech.

## <a name="2120"></a>2.1.2.0

Vydáno 2. července 2019

### <a name="bug-fixes"></a>Opravy chyb

- **Hodnocení:**

  - Opravili jsme hlášení chyb s neparseovatelnými výrazy.

## <a name="2110"></a>2.1.1.0

Vydáno 27. června 2019

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Aktualizace rozhraní MonoBehaviour API na verzi 2019.1

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opravili jsme výkon Unity Project Exploreru.

  - Opravili jsme upozornění a chyby generování sestav pro výstup při povoleném zjednodušeném sestavení.

  - Byl opraven jednoduchý výkon sestavení.

## <a name="2100"></a>2.1.0.0

Vydáno 20. června 2019

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Zakázali jsme úplné sestavení pro projekty Unity a ve prospěch použití chyb a upozornění IntelliSense. Unity ve skutečnosti vytvoří Visual Studio s projekty knihoven tříd, které představují, co Unity interně dělá. Je však třeba říct, že Unity při zavírání kanálu kompilace Visual Studio sestavení ve výchozím nastavení ho nikdy nevyuží ani nepřebírá. Sestavování v Visual Studio jen spotřebovává prostředky za nic. Pokud potřebujete úplné sestavení, protože máte nástroje nebo nastavení, které na něm závisí, můžete tuto optimalizaci zakázat (Nastavení/Nástroje pro Unity/Zakázat úplné sestavení projektů).
  
  - Přidání podpory pro balíčky Unity v UPE Viditelné jsou pouze odkazované balíčky (pomocí manifest.jsve složce ) a místní `Packages` balíčky (vložené ve `Packages` složce).

## <a name="2021"></a>2.0.2.1

Vydáno 30. května 2019

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidání vlastní ikony pro cíle provádění Unity

## <a name="2020"></a>2.0.2.0

Vydáno 2. dubna 2019

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidání podpory pro automatickou aktualizaci databáze prostředků Unity při uložení Tato možnost je ve výchozím nastavení povolená a aktivuje rekompilaci na straně Unity při ukládání skriptu do Visual Studio. Tuto funkci můžete při uložení zakázat ve složce Tools\Options\Tools for Unity\Refresh Unity's AssetDatabase.

  - Přidali jsme podporu nastavení preferované instalace unity pro offline dokumentaci.

  - Přidali jsme místní nabídku pro nový editor.

### <a name="bug-fixes"></a>Opravy chyb

- **Ladicí program:**

  - Opravili jsme filtrování sestavení a kontrolu rámců s prázdnými snímky.

## <a name="2011"></a>2.0.1.1
 
 Vydáno 26. března 2019

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Dočasné nastavení mono jako výchozího a pouze použitelného ladicího programu pro tuto velmi specifickou verzi

## <a name="2006"></a>2.0.0.6

Vydáno 26. března 2019

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidání podpory pro Attach to Unity and Play (Připojit k Unity a Play)

## <a name="2005"></a>2.0.0.5

Vydáno 20. března 2019

### <a name="new-features"></a>Nové funkce

- **Generování projektu:**

  - Zachování externích vlastností při zpracování souboru řešení
  
- **Hodnocení:**

  - Přidání podpory pro názvy kvalifikované pro aliasy (pro tuto dobu pouze globální obor názvů) Vyhodnocovač výrazů teď přijímá typy pomocí formuláře global::namespace.type.

  - Byla přidána podpora `pointer[index]` pro formulář, který je sémanticky identický s formulářem s odkazem `*(pointer+index)` ukazatele.

## <a name="2004"></a>2.0.0.4

Vydáno 5. března 2019

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Aktualizovali jsme `ScriptableObject` rozhraní API.

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

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

  - Opravili jsme oznámení při detekci nového přehrávače.

## <a name="1401"></a>1.4.0.1

Vydáno 23. ledna 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Oprava rozbalení/sbalení složek poklikaní

## <a name="1400"></a>1.4.0.0

Vydáno 13. prosince 2017

### <a name="new-features"></a>Nové funkce

- **Generování projektu:**

  - Přidání podpory pro .NET Standard

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Oprava automatického převodu pdb na symbol ladění mdb

## <a name="1301"></a>1.3.0.1

Vydáno 12. prosince 2017

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opravili jsme nepřímé volání EditorPrefs.GetBool, které při pokusu o změnu velikosti pole ovlivnilo inspektor.

- **Průvodci:**

  - Aktualizujte kontext roslyn před vložením metody .

## <a name="1300"></a>1.3.0.0

Vydáno 20. listopadu 2017

### <a name="new-features"></a>Nové funkce

- **Průvodci:**

  - Přidání průvodce Implement Unity message (Implementace zprávy Unity)

  - Přidání podpory pro nové rozhraní API pro dokončování ve VS pro Mac 7.4

## <a name="1200"></a>1.2.0.0

Vydáno 23. října 2017

### <a name="new-features"></a>Nové funkce

- **Ladicí program:**

  - Byla přidána podpora přenosných souborů symbolů ladění.

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Opravili jsme .dll příponu nesprávně přidané do názvu souboru sestavení.

  - Nevynutí příznak AllowAttachedDebuggingOfEditor Unity, protože výchozí hodnota je teď true.

## <a name="1103"></a>1.1.0.3

Vydáno 23. října 2017

### <a name="new-features"></a>Nové funkce

- **Generování projektu:**

  - Přidání podpory pro profil .NET 4.6

## <a name="1102"></a>1.1.0.2

Vydáno 8. srpna 2017

### <a name="new-features"></a>Nové funkce

- **Ladicí program:**

  - Pokud si nejste jistí, ke které Unity se má připojit, spusťte dialogové okno Připojit ke zpracování.

- **Generování projektu:**

  - Při použití Unity 5.6 vždy povolte nezabezpečený přepínač kompilace.

## <a name="1101"></a>1.1.0.1

Vydáno 20. července 2017

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidání podpory pro lokalizované prostředky

## <a name="1100"></a>1.1.0.0

Vydáno 12. července 2017

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidání podpory pro připojení k přehrávačům a editorům prostřednictvím okna Připojit k procesu

- **Generování projektu:**

  - Oprava odkazů na název sestavení se soubory mcs.rsp

  - Byla přidána podpora assembly.jspro jednotky kompilace.

  - Opravili jsme definice s úrovněmi rozhraní API.

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Oprava chybové zprávy shaderu při kompilaci

## <a name="1001"></a>1.0.0.1

Vydáno 4. května 2017

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opravili jsme aktivní sledování dokumentů pomocí hybridních a běžných projektů.

## <a name="1000"></a>1.0.0.0

Vydáno 3. května 2017
