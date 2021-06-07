---
title: Protokol změn (Visual Studio Tools for Unity, Windows) | Microsoft Docs
description: Zobrazit protokol změn pro Visual Studio Tools for Unity, Windows. Viz změny od verze 1.0.0.0 až po 4.7.0.0 a vyšší.
ms.custom: ''
ms.date: 6/2/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: ea490b7e-fc0d-44b1-858a-a725ce20e396
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 2ff13b017ffe0d310ddfd1b302c6436e9d708a36
ms.sourcegitcommit: f430d014f912aa7874e1db65026dc72688b973e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2021
ms.locfileid: "111448308"
---
# <a name="change-log-visual-studio-tools-for-unity-windows"></a>Protokol změn (Visual Studio Tools for Unity, Windows)

Protokol změn Visual Studio Tools for Unity

## <a name="41020"></a>4.10.2.0
Vydáno 25. května 2021

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Přidání [`UNT0024`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0024.md) diagnostiky Dává přednost skalárním výpočtům prostřednictvím výpočtů vektoru.

- **Hodnocení**

  - Přidání podpory pro použití přenosných symbolů PDB pro správné filtrování viditelných místních hodnot.

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Stabilita hledání referenčního prostředku pro fixní prostředky

  - Pevný přehrávač oznamuje analýzu s nejnovějšími verzemi Unity.

## <a name="41010"></a>4.10.1.0
Vydáno 11. května 2021

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Pevné problémy se stabilitou [`UNT0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0008.md) QuickFix.

  - Vyřešené problémy s výkonem s vlákny.

## <a name="41000"></a>4.10.0.0
Vydáno 13. dubna 2021

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Přidání [`UNT0019`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0019.md) diagnostiky Nepotřebná nepřímá volání pro `GameObject.gameObject` .

  - Přidání [`UNT0020`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0020.md) diagnostiky `MenuItem` atribut, který se používá pro nestatickou metodu

  - Přidání [`UNT0021`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0021.md) diagnostiky Zpráva Unity by měla být chráněná (výslovný souhlas).

  - Přidání [`UNT0022`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0022.md) diagnostiky Neefektivní metoda pro nastavení pozice a rotace.

  - Přidání [`UNT0023`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0023.md) diagnostiky Přiřazení slučovacích objektů Unity

  - Přidání [`USP0017`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0017.md) Suppressor pro `IDE0074` . Objekty Unity by neměly používat přiřazení slučování.

  - Bylo přidáno zjišťování neurčených projektů C# cílících na Unity.

  - Do CodeLens se přidalo vyhledávání referenčních prostředků Unity.

## <a name="4910"></a>4.9.1.0
Vydáno 2. března 2021

### <a name="new-features"></a>Nové funkce

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

  - Opravili jsme různé problémy uživatelského rozhraní pro jiné než CSYé jazyky.

  - Pevné problémy se stabilitou s [`UNT0018`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0018.md) diagnostikou.
  
- **Tém**

  - Pevné problémy s odpojením virtuálního počítače při použití `Trace` metod.

- **Hodnocení**

  - Pevné Filtrování zastaralých vlastností vyvolává výjimky.

## <a name="4900"></a>4.9.0.0
Vydáno 20. ledna 2021

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Přidání podpory pro `raytrace shaders` `UXML` soubory a `USS` .

  - Byla přidána `.vsconfig` Podpora generování. Visual Studio by nyní mělo detekovat komponenty, které chybí, a zobrazí výzvu k jejich instalaci při použití projektů Unity.

  - Aktualizované rozhraní API pro zprávy Unity (pro všechny metody používané jako korutiny).

  - Bylo aktualizováno zjišťování Android SDK.

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Při použití dialogového okna pro výběr instance se opravila aktualizace procesu.

  - Opravená [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md) Diagnostika, která poskytuje chybná upozornění pro korutiny a `AssetPostprocessor.OnAssignMaterialModel` .

## <a name="4820"></a>4.8.2.0
Vydáno 10. listopadu 2020

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Vylepšená [`UNT0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0010.md) Diagnostika, která se má použít pro všechno, co je děděné z `Component` nejenom `MonoBehaviour` .

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Pevná zpráva o neplatnosti zprávy CodeLens.

## <a name="4810"></a>4.8.1.0
Vydáno 13. října 2020

### <a name="new-features"></a>Nové funkce

- **Hodnocení**

  - Přidání podpory pro implicitní převod s voláními. Dříve vyhodnocovací vyhodnocení vynutilo striktní ověřování typu, což má za následek `Failed to find a match for method([parameters...])` varovné zprávy.

- **Spolupráci**

  - Přidání [`UNT0018`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0018.md) diagnostiky Nepoužívejte `System.Reflection` funkce pro kritické zprávy o výkonu, jako `Update` je,, `FixedUpdate` `LateUpdate` nebo `OnGUI` .

  - Vylepšené [`USP0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0003.md) a [`USP0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0005.md) potlačené objekty s podporou pro všechny `AssetPostprocessor` statické metody.

  - Přidání [`USP0016`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0016.md) Suppressor pro `CS8618` . `C# 8.0` zavádí typy odkazů s možnou hodnotou null a odkazy, které neumožňují hodnotu null. Detekce inicializace typů, které dědí z `UnityEngine.Object` , není podporována a bude mít za následek chyby.

  - Nyní použijte stejný mechanismus pro vytváření projektů a přehrávač asmdef pro Unity 2019. x a 2020. x +.

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Opravilo se neočekávané dokončení zpráv v komentářích.

## <a name="4800"></a>4.8.0.0 
Vydáno 14. září 2020

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opravili jsme generování projektů hráčů pomocí Unity 2019.x.

## <a name="4710"></a>4.7.1.0
Vydáno 5. srpna 2020

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidání podpory oboru názvů do výchozích šablon
  
  - Aktualizace rozhraní API pro zprávy Unity na verzi 2019.4

  - Přidání [`USP0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0013.md) potlačení pro `CA1823` . Soukromá pole s `SerializeField` `SerializeReference` atributy nebo by se neměla označit jako nepoužívané (FxCop).
  
  - Přidání [`USP0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0014.md) potlačení pro `CA1822` . Zprávy Unity by neměly být označeny jako kandidáty `static` na modifikátor (FxCop).

  - Přidání [`USP0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0015.md) potlačení pro `CA1801` . Nepoužívané parametry by neměly být odebrané ze zpráv Unity (FxCop).
  
  - Přidání podpory MenuItem do [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md) potlačovače  

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Oprava [`USP0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0001.md) [`USP0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0002.md) a potlačení nefungují s extra závorkami nebo s argumenty metody.
  
  - Opravili jsme povinnou aktualizaci databáze assetu i v případě, že byla v nastavení Unity zakázaná automatická aktualizace.

## <a name="4700"></a>4.7.0.0
Vydáno 23. června 2020

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidání podpory pro zachování složek řešení při opětovném vygenerování řešení a projektů Unity

  - Přidali [`UNT0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0015.md) jsme diagnostiku. Rozpoznání nesprávné signatury metody `InitializeOnLoadMethod` s `RuntimeInitializeOnLoadMethod` atributem nebo .

  - Přidali [`UNT0016`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0016.md) jsme diagnostiku. Použití `Invoke` , nebo s prvním `InvokeRepeating` `StartCoroutine` `StopCoroutine` argumentem, který je řetězcový literál, není typový bezpečný.

  - Přidali [`UNT0017`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0017.md) jsme diagnostiku. `SetPixels` Volání je pomalé.

  - Přidání podpory pro blokový komentář a odsazení pro soubory Shaderu

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Při filtrování zpráv v průvodci zprávami Unity nenulujte výběr.
  
  - Při otevírání dokumentace k rozhraní Unity API vždy používejte výchozí prohlížeč.
  
  - Oprava , a suppressors s následujícími [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md) pravidly: [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) suppress [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) `IDE0044` (readonly), (unused), (never assigned) pro všechna pole `IDE0051` `CS0649` dekorovaná atributem SerializeField. Potlačit `CS0649` (nikdy nepřiřazeno) pro veřejná pole všech typů, které rozšiřují `Unity.Object`.

  - Oprava kontroly parametrů obecného typu [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md) pro disticii

- **Hodnocení:**

  - Oprava porovnání rovnosti s výčty

## <a name="4610"></a>4.6.1.0
Vydáno 19. května 2020

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Upozornit, pokud se nám nedaří vytvořit server pro zasílání zpráv na straně Unity.
  
  - Analyzátory se správně spouštěly během zjednodušené kompilace.
  
  - Opravili jsme problém, kdy třída MonoBehaviour vytvořená z UPE neodpovídá názvu souboru.

## <a name="4600"></a>4.6.0.0
Vydáno 14. dubna 2020

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidání podpory pro CodeLens (skripty a zprávy Unity)
  
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

## <a name="4510"></a>4.5.1.0

Vydáno 16. března 2020

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidání [`USP0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0008.md) potlačení pro `IDE0051` . Soukromé metody používané s invoke, InvokeRepeating, StartCoroutine nebo StopCoroutine by se neměly označit jako nepoužívané.

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Oprava dokumentace OnDrawGizmos/OnDrawGizmosSelected

- **Hodnocení:**

  - Oprava kontroly argumentu lambda

## <a name="4501"></a>4.5.0.1

Vydáno 19. února 2020

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opravili [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md) jsme diagnostickou kontrolu nesprávného podpisu zprávy. Při kontrole typů s více úrovněmi dědičnosti může tato diagnostika selhat s následující zprávou: `warning AD0001: Analyzer 'Microsoft.Unity.Analyzers.MessageSignatureAnalyzer' threw an exception of type 'System.ArgumentException' with message 'An item with the same key has already been added` .

## <a name="4500"></a>4.5.0.0

Vydáno 22. ledna 2020

### <a name="new-features"></a>Nové funkce

- **Integrace:**

  - Přidání podpory pro soubory HLSL
  
  - Přidání [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) potlačení pro `IDE0051` . Soukromá pole s `SerializeField` atributem by neměla být označena jako nepoužívaná.
  
  - Přidání [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) potlačení pro `CS0649` . Pole s `SerializeField` atributem by neměla být označena jako nepřiřazená.  

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Generování fixního projektu ( `GenerateTargetFrameworkMonikerAttribute` cíl nebyl vždy uložen správně).

## <a name="4420"></a>4.4.2.0

Vydáno 3. prosince 2019

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Pevná Diagnostika s uživatelsky definovanými rozhraními.

  - Opravili jsme rychlé popisy s poškozenými výrazy.

## <a name="4410"></a>4.4.1.0

Vydáno 6. listopadu 2019

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Přidala se podpora pro procesy na pozadí Unity. (Ladicí program se může automaticky připojit k hlavnímu procesu místo podřízeného procesu).
  
  - Přidali jsme rychlý popis pro zprávy Unity a zobrazí se související dokumentace.

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Opravili jsme analyzátor porovnání značek [`UNT0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0002.md) pomocí pokročilých binárních a volání výrazů.

### <a name="deprecated-features"></a>Zastaralé funkce

- **Spolupráci**

  - Až budete dál, Visual Studio Tools for Unity podporují jenom Visual Studio 2017 +.

## <a name="4400"></a>4.4.0.0

Vydáno 15. října 2019

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Přidání [`USP0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0005.md) Suppressor pro `IDE0060` (nepoužitý parametr) pro všechny zprávy Unity
  
  - Byl přidán rychlý popis pro pole s příznakem `TooltipAttribute` . (To bude fungovat také pro jednoduché přístupové objekty get pomocí tohoto pole.)

## <a name="4330"></a>4.3.3.0

Vydáno 23. září 2019

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Opravili jsme chybu a hlášení upozornění pro odlehčená sestavení.

## <a name="4320"></a>4.3.2.0

Vydáno 16. září 2019

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Provedli jsme porozumění, že Visual Studio má pro projekty Unity přidat novou diagnostiku specifickou pro Unity. Také jsme zvýšili inteligenci integrovaného vývojového prostředí (IDE) tím, že jsme potlačili obecnou diagnostiku C#, která se nevztahuje na projekty Unity. Například rozhraní IDE nebude zobrazovat rychlou opravu pro změnu proměnné inspektoru, `readonly` která by zabránila v úpravách proměnné v editoru Unity.
    - [`UNT0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0001.md): Zprávy Unity jsou volány modulem runtime, i když jsou prázdné, Nedeklarujte je, aby nedocházelo ke zpracování uncesseray modulem runtime Unity.
    - [`UNT0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0002.md): Porovnávání značek pomocí rovnosti řetězců je pomalejší než integrovaná metoda CompareTag.
    - [`UNT0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0003.md): Použití obecného formuláře pro getComponent je upřednostňováno pro bezpečnost typů.
    - [`UNT0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0004.md): Zpráva aktualizace je závislá na frekvenci snímků a měla by místo času. fixedDeltaTime použít Time. deltaTime.
    - [`UNT0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0005.md): Zpráva FixedUpdate je nezávislá na snímkovém tempu a měla by místo času. deltaTime používat Time. fixedDeltaTime.
    - [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md): Pro tuto zprávu Unity byl zjištěn nesprávný podpis metody.
    - [`UNT0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0007.md): Unity Přepisuje operátor porovnání s hodnotou null pro objekty Unity, které nejsou kompatibilní s hodnotou null pro slučování.
    - [`UNT0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0008.md): Unity přepíše operátor porovnání s hodnotou null pro objekty Unity, které nejsou kompatibilní s rozšířením s hodnotou null.
    - [`UNT0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0009.md): Při použití atributu InitializeOnLoad pro třídu je nutné zadat statický konstruktor. Atribut InitializeOnLoad zajistí, že bude volán při spuštění editoru.
    - [`UNT0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0010.md): Třídy MonoBehaviour by mělo být vytvořeno pouze pomocí AddComponent (). Objekt MonoBehaviour je komponenta, která musí být připojená k objektu GameObject.
    - [`UNT0011`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0011.md): ScriptableObject by mělo být vytvořeno pouze pomocí metody CreateInstance (). Objekt ScriptableObject musí být vytvořený modulem Unity, aby zpracovával metody zpráv Unity.
    - [`USP0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0001.md) pro `IDE0029` : objekty Unity by neměly používat slučování s hodnotou null.
    - [`USP0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0002.md) pro `IDE0031` : objekty Unity by neměly používat šíření hodnoty null.
    - [`USP0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0003.md) pro `IDE0051` : zprávy Unity jsou vyvolány modulem runtime Unity.
    - [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md) for `IDE0044` : pole s atributem SerializeField by neměla být určena jen pro čtení.

## <a name="4310"></a>4.3.1.0

Vydáno 4. září 2019

### <a name="new-features"></a>Nové funkce

- **Hodnocení**

  - Přidání podpory pro lepší zobrazení typu, tj. `List<object>` místo `List'1[[System.Object, <corlib...>]]` .

  - Přidání podpory pro přístup ke členu ukazatele, `p->data->member` tj.

  - Přidání podpory pro implicitní převody v inicializátorech pole, `new byte [] {1,2,3,4}` tj.

## <a name="4300"></a>4.3.0.0

Vydáno 13. srpna 2019

### <a name="new-features"></a>Nové funkce

- **Ladění**

  - Byla přidána podpora protokolu MDS 2,51.

- **Spolupráci**

  - Vylepšilo se okno připojit k instanci Unity s funkcemi řazení, hledání a aktualizace. PID se teď zobrazuje i pro místní přehrávače (dotazuje se na naslouchající sokety v systému, aby získal vlastnící proces).

  - Přidání podpory pro soubory asmdef

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Pevné zpracování poškozených zpráv při komunikaci s přehrávači Unity.

- **Hodnocení**

  - Pevné zpracování oborů názvů ve výrazech.

  - Pevná kontrola s použitím typů IntPtr.
  
  - Opravili jsme problémy krokování s výjimkami.

  - Pevné vyhodnocení pseudo identifikátorů (například $exception).

  - Zabraňte selhání při přesměrování neplatných adres.  

  - Opravili jsme problém s uvolněnými doménami AppDomain.

## <a name="4201"></a>4.2.0.1

Vydáno 24. července 2019

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Přidání nové možnosti pro vytvoření libovolného typu souboru z Průzkumníka projektů Unity.
  
  - Při použití rychlých buildů pro projekty Unity Vylepšete ukládání do mezipaměti diagnostiky.

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Opravili jsme problém, když Přípona souboru nebyla zpracována žádným známým editorem.

  - Pevná podpora pro vlastní rozšíření v Průzkumníku projektů Unity.

  - Pevné uložení nastavení mimo hlavní dialog.

  - Byla odebrána starší závislost Microsoft. VisualStudio. MPF.

## <a name="4110"></a>4.1.1.0

Vydáno 24. května 2019

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Rozhraní MonoBehaviour API se aktualizovalo na 2019,1.

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Opravená upozornění a chyby při generování výstupu, když je povolené zjednodušené sestavení.

  - Pevný výkon pro odlehčené sestavení.

## <a name="4100"></a>4.1.0.0

Vydáno 21. května 2019

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Přidání podpory nového rozhraní API služby Batch pro rychlejší opětovné načtení projektů.

  - Pro projekty Unity se zakázalo úplné sestavení, a to na základě chyb a upozornění technologie IntelliSense. Ve skutečnosti Unity vytvoří řešení sady Visual Studio s projekty knihoven tříd, které reprezentují, co Unity interně dělá. To se říká, výsledek sestavení v sadě Visual Studio se nikdy nepoužívá nebo nezískala v Unity, protože je jejich kanál kompilace uzavřený. Sestavování v aplikaci Visual Studio právě spotřebovává prostředky pro nic. Pokud potřebujete úplné sestavení, protože máte nástroje nebo nastavení, které na něm závisí, můžete tuto optimalizaci zakázat (nástroje/Možnosti/nástroje pro Unity nebo zakázat kompletní sestavení projektů).

  - Při načtení projektu Unity automaticky zobrazit Průzkumníka projektů Unity (UPE) UPE bude ukotven vedle Průzkumník řešení.

  - Byl aktualizován mechanismus extrakce názvů projektů pomocí Unity 2019. x.

  - Přidala se podpora pro balíčky Unity v UPE. Jsou viditelné pouze odkazované balíčky (pomocí manifest.jsve `Packages` složce) a místní balíčky (vložené do `Packages` složky).

- **Generování projektu:**

  - Při zpracování souboru řešení zachovat externí vlastnosti.

- **Hodnocení**

  - Byla přidána podpora názvů kvalifikovaných aliasů (pouze globální obor názvů pro nyní). Proto vyhodnocovací filtr výrazů nyní přijímá typy pomocí formuláře Global:: Namespace. Type.

  - Přidání podpory pro `pointer[index]` formulář, která je sémanticky totožná s odkazem na odkazy na ukazatel `*(pointer+index)` .

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Opravili jsme problémy s závislostí pomocí Microsoft. VisualStudio. MPF.

  - Pevný aktér pro UWP se připojí bez načtení projektu.

  - Pevná Automatická aktualizace databáze prostředků, když se ještě nepřipojila aplikace Visual Studio

  - Pevné problémy s motivem pomocí popisků a zaškrtávacích políček.

- **Ladění**

  - Pevné krokování se statickými konstruktory.

## <a name="4005"></a>4.0.0.5

Vydáno 27. února 2019

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Opravili jsme detekci verzí sady Visual Studio pomocí instalačního balíčku.

  - Z instalačního balíčku se odebrala nepoužívaná sestavení.

## <a name="4004"></a>4.0.0.4

Vydáno 13. února 2019

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Přidání podpory pro správné detekci procesů Unity během instalace a povolení instalačního modulu pro lepší zpracování zámků souborů.

  - Rozhraní API se aktualizovalo `ScriptableObject` .

## <a name="4003"></a>4.0.0.3

Vydáno 31. ledna 2019

### <a name="new-features"></a>Nové funkce

- **Generování projektu:**

  - Veřejná a serializovaná pole už nebudou způsobovat upozornění. Automaticky jsme potlačili `CS0649` `IDE0051` Upozornění kompilátoru a v projektech Unity, která tyto zprávy vytvořila.

- **Spolupráci**

  - Zlepšilo se uživatelské prostředí pro zobrazování editoru Unity a instancí přehrávače (Windows teď měnitelné velikosti, používejte jednotné okraje a zobrazují úchyt pro změnu velikosti). Přidání informací Process-Id pro editory Unity

  - Rozhraní API se aktualizovalo `MonoBehaviour` .

- **Hodnocení**

  - Byla přidána podpora místních funkcí.

  - Přidání podpory pro pseudo Variables (výjimky a identifikátory objektů).

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Opravili jsme problém s obrázky monikeru a motivy.

  - Zapisovat pouze do okno Výstup při ladění při automatické aktualizaci databáze prostředků.

  - Pevná prodleva uživatelského rozhraní pomocí filtrování Průvodce MonoBehaviour

- **Ladění**

  - Bylo vyřešeno čtení vlastního atributu u pojmenovaných argumentů při použití starších verzí protokolu.

## <a name="4002"></a>4.0.0.2

Vydáno 23. ledna 2019

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Opravilo se generování experimentálního buildu.

  - Pevné zpracování událostí souboru projektu pro minimalizaci zatížení vlákna uživatelského rozhraní.

  - Fixní poskytovatel dokončení se změnami v dávce textu

- **Ladění**

  - Opravili jsme zobrazení zpráv ladění uživatele k připojenému ladicímu programu.

## <a name="4001"></a>4.0.0.1

Vydáno 10. prosince 2018

### <a name="new-features"></a>Nové funkce

- **Hodnocení**

  - Nahradili jsme NRefactory a upřednostňujeme Roslyn pro vyhodnocení výrazu.

  - Přidání podpory pro ukazatele: dereference, přetypování a aritmetické operace (2018.2 Unity + a nový modul runtime jsou pro toto) nutné.

  - Přidání podpory pro zobrazení ukazatele pole (jako v jazyce C++). Ponechejte výraz ukazatele a potom přidejte čárku a počet prvků, které chcete zobrazit.

  - Byla přidána podpora pro asynchronní konstrukce.

- **Spolupráci**

  - Přidání podpory pro automatickou aktualizaci databáze assetů v Unity při uložení Tato možnost je ve výchozím nastavení povolená a při ukládání skriptu do sady Visual Studio aktivuje novou kompilaci na straně Unity. Tuto funkci můžete zakázat v Tools\Options\Tools pro AssetDatabase v Unity\Refresh Unity při uložení.

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Fixní aktivace přemostění, když není vybrána možnost Visual Studio jako preferovaný externí editor.

  - Vyhodnocení výrazu se špatnými nebo nepodporovanými výrazy.

## <a name="4000"></a>4.0.0.0

Vydáno 4. prosince 2018

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Přidání podpory pro Visual Studio 2019 (potřebujete aspoň Unity 2018,3, aby bylo možné použít Visual Studio 2019 jako externí editor skriptu).

  - Přijali jste službu a katalog sady Visual Studio s plnou podporou škálování HDPI, dokonalých obrázků v pixelech a jejich.

### <a name="deprecated-features"></a>Zastaralé funkce:

- **Integrace:**

  - Do budoucna Visual Studio Tools for Unity podporovat pouze Unity 5.2+ (s integrovanou integrací Visual Studio Unity).

  - Do budoucna Visual Studio Tools for Unity podporovat pouze Visual Studio 2015 a více.

  - Odebrali jsme službu starší verze jazyka, seznam chyb a stavový řádek.

  - Odebrali jsme Průvodce rychlým chováním (ve prospěch vyhrazené podpory IntelliSense).

## <a name="3903"></a>3.9.0.3

Vydáno 28. listopadu 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opravili jsme problémy s opětovném načtením projektu a intellisense při přidávání nebo odebírání skriptů umístěných v prvním projektu.

## <a name="3902"></a>3.9.0.2

Vydáno 19. listopadu 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Ladicí program:**

  - Opravili jsme zablokování v knihovně, které se používalo ke komunikaci s ladicím strojem Unity, což nutí Visual Studio nebo Unity blokovat, zejména při pokusu o připojení k Unity nebo restartování hry.

## <a name="3901"></a>3.9.0.1

Vydáno 15. listopadu 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opravili jsme aktivaci modulu plug-in Unity při výběru jiného výchozího editoru.

## <a name="3900"></a>3.9.0.0

Vydáno 13. listopadu 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Vrátili jsme zpět alternativní řešení chyby výkonu Unity, kterou opravila Unity.

## <a name="3807"></a>3.8.0.7

Vydáno 20. září 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Ladicí program:**

  - (Zpětně portované z 3.9.0.2) Opravili jsme zablokování v knihovně, které se používalo ke komunikaci s ladicím strojem Unity, což nutí Visual Studio nebo Unity blokovat, zejména při pokusu o připojení k Unity nebo restartování hry.

## <a name="3806"></a>3.8.0.6

Vydáno 27. srpna 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opravili jsme opětovné načtení projektů a řešení.

## <a name="3805"></a>3.8.0.5

Vydáno 20. srpna 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opravili jsme vyřazení předplatného monitorování projektu.

## <a name="3804"></a>3.8.0.4

Vydáno 14. srpna 2018

### <a name="new-features"></a>Nové funkce

- **Hodnocení:**

  - Přidání podpory pro hodnoty ukazatele

  - Byla přidána podpora obecných metod.

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Inteligentní opětovné načtení s několika změněných projekty

## <a name="3803"></a>3.8.0.3

Vydáno 24. července 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - (Zpětně portované z 3.9.0.0) Vrátili jsme zpět alternativní řešení chyby výkonu Unity, kterou opravila Unity.

## <a name="3802"></a>3.8.0.2

Vydáno 7. července 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Přechodné alternativní řešení chyby výkonu Unity: Při generování projektů se do mezipaměti ukládá MonoIs ve formě mezipaměti.

## <a name="3801"></a>3.8.0.1

Vydáno 26. června 2018

### <a name="new-features"></a>Nové funkce

- **Ladění:**

  - Přidání podpory pro příkazy UserLog a UserBreak

  - Přidání podpory opožděné načítání typů (optimalizace latence odezvy ladicího programu a zatížení sítě)

### <a name="bug-fixes"></a>Opravy chyb

- **Hodnocení:**

  - Vylepšené vyhodnocení výrazu binárního operátoru a vyhledávání metod

## <a name="3800"></a>3.8.0.0

Vydáno 30. května 2018

### <a name="new-features"></a>Nové funkce

- **Ladění:**

  - Přidání podpory pro zobrazení proměnných v asynchronních konstruktorech

  - Byla přidána podpora pro zpracování vnořených typů při nastavování zarážek, aby se zabránilo upozorněním s konstruktory kompilátoru.

- **Integrace:**

  - Přidali jsme podporu gramatik textmate pro shadery (úloha C++ už není nutná pro zabarvení kódu Shaderu).

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Při použití nového modulu runtime Unity už ne převod přenosného souboru pdb na mdb.

## <a name="3701"></a>3.7.0.1

Vydáno 7. května 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Instalační služby:**

  - Opravili jsme problém se závislostmi při používání experimentálních sestavení.

## <a name="3700"></a>3.7.0.0

Vydáno 7. května 2018

### <a name="new-features"></a>Nové funkce

- **Ladění:**

  - Přidání podpory pro orchestrované ladění (ladění více přehrávačů nebo editorů se stejnou Visual Studio relací)

  - Přidali jsme podporu ladění přehrávače Android USB.

  - Přidání podpory pro ladění přehrávače UPW/IL2CPP

- **Hodnocení:**

  - Přidání podpory pro šestnáctkové specifikátory

  - Vylepšené prostředí pro vyhodnocení okna sledování

### <a name="bug-fixes"></a>Opravy chyb

- **Integrace:**

  - Opravili jsme použití nastavení výjimek.

- **Generování projektu:**

  - Vylučte z generování jednotky kompilace správce balíčků.

## <a name="3605"></a>3.6.0.5

Vydáno 13. března 2018

### <a name="new-features"></a>Nové funkce

- **Generování projektu:**

  - Přidání podpory nového generátoru projektu v Unity 2018,1.

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Pevné zpracování poškozených stavů s vlastními projekty.

- **Ladění**

  - Opravení nastavení dalšího příkazu.

## <a name="3604"></a>3.6.0.4

Vydáno 5. března 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Opravená detekce verze mono

- **Spolupráci**

  - Pevné problémy s časováním pomocí 2018,1 a aktivace modulu plug-in.

## <a name="3603"></a>3.6.0.3

Vydáno 23. února 2018

### <a name="new-features"></a>Nové funkce

- **Generování projektu:**

  - Byla přidána podpora pro .NET Standard.

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Opravili jsme detekci cílového rozhraní Unity.

- **Ladění**

  - Pevné přerušení na výjimkách, které jsou vyvolány mimo UserCode.

## <a name="3602"></a>3.6.0.2

Vydáno 7. února 2018

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Aktualizujte plochu rozhraní API UnityMessage pro 2017,3.

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Znovu znovu načíst projekty při externí změně (s omezením).

## <a name="3601"></a>3.6.0.1

Vydáno 24. ledna 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Opravený automatický převod souboru PDB na soubor MDB pro ladění.

  - Pevné nepřímá volání EditorPrefs. getbool má vliv na inspektora při pokusu o změnu velikosti pole.

## <a name="3600"></a>3.6.0.0

Vydáno 10. ledna 2018

### <a name="new-features"></a>Nové funkce

- **Generování projektu:**

  - Přidání podpory pro referenční model 2018,1 MonoIsland

- **Hodnocení**

  - Byla přidána podpora identifikátoru $exception.

- **Ladění**

  - Přidání podpory pro atributy DebuggerHidden/DebuggerStepThrough s novým modulem runtime Unity

- **Průvodc**

  - Zaveďte nejnovější verzi průvodců.

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Pevný výpočet identifikátoru GUID projektu pro projekty přehrávače.

- **Ladění**

  - Opravili časování při zpracovávání přerušujících událostí.

- **Průvodc**

  - Aktualizujte kontext Roslyn před vložením metody.

## <a name="3503"></a>3.5.0.3

Vydáno 9. ledna 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Opravený automatický převod souboru PDB na soubor MDB pro ladění.

## <a name="3502"></a>3.5.0.2

Vydáno 4. prosince 2017

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Projekty Unity se teď při přidání nebo odebrání skriptu z Unity automaticky znovu načítají v sadě Visual Studio.

- **Ladění**

  - Přidání možnosti pro použití ladicího programu mono sdíleného pomocí Xamarin a Visual Studio pro Mac pro ladění editoru Unity

  - Přidání podpory pro přenositelné soubory se symboly ladění.

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Vyřešené problémy s nastavením závislostí.

  - Pevná nabídka Help API pro Unity se nezobrazuje.

- **Generování projektu:**

  - Vytváření projektů s pevným přehrávačem při práci na hře UWP s back-endu IL2CPP/. NET 4,6.

  - Opravené dodatečné rozšíření .dll nesprávně přidáno do souboru názvu sestavení.

  - Pevné použití konkrétní úrovně kompatibility projektového rozhraní API namísto globálního.

  - Nevynuťte si příznak Unity AllowAttachedDebuggingOfEditor, protože výchozí hodnota je nyní true.

## <a name="3402"></a>3.4.0.2

Vydáno 19. září 2017

### <a name="new-features"></a>Nové funkce

- **Generování projektu:**

  - Do kompilačních jednotek byla přidána podpora pro assembly.js.

  - Kopírování sestavení Unity do složky projektu se zastavilo.

- **Ladění**

  - Přidání podpory pro nastavení dalšího příkazu s novým modulem runtime Unity.

  - Přidání podpory pro typ Decimal s novým modulem runtime Unity

  - Přidání podpory pro implicitní nebo explicitní převody.

### <a name="bug-fixes"></a>Opravy chyb

- **Hodnocení**

  - Pevné vytvoření pole s implicitní velikostí.

  - Pevné kompilátory vygenerovaly položky s lokálními.

- **Generování projektu:**

  - Pevný odkaz na úroveň rozhraní API Microsoft. CSharp pro 4,6

## <a name="3302"></a>3.3.0.2

Vydáno 15. srpna 2017

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Opravili jsme Visual Studio řešení v Unity 5.5 a předchozích verzích.

## <a name="3300"></a>3.3.0.0

Vydáno 14. srpna 2017

### <a name="new-features"></a>Nové funkce

- **Hodnocení:**

  - Přidání podpory pro vytváření struktur pomocí nového modulu runtime Unity

  - Přidání podpory pro ukazatele

### <a name="bug-fixes"></a>Opravy chyb

- **Hodnocení:**

  - Oprava vyvolání metody u primitiv

  - Opravili jsme vyhodnocení pole s typy označenými pomocí BeforeFieldInit.

  - Opravili jsme nepodporující volání s binárními operátory (dílčími operátory).

  - Opravili jsme problémy při přidávání položek do Visual Studio Watch.

- **Generování projektu:**

  - Oprava odkazů na název sestavení se soubory mcs.rsp

  - Opravili jsme definice s úrovněmi rozhraní API.

## <a name="3200"></a>3.2.0.0

Vydáno 10. května 2017

### <a name="new-features"></a>Nové funkce

- **Instalační služby:**

  - Přidali jsme podporu čištění mezipaměti MEF.

### <a name="bug-fixes"></a>Opravy chyb

- **Editor kódu:**

  - Oprava klasifikace/dokončování s vlastními atributy

  - Opravili jsme blikání zpráv Unity.

## <a name="3100"></a>3.1.0.0

Vydáno 7. dubna 2017

### <a name="new-features"></a>Nové funkce

- **Ladicí program:**

  - Přidání podpory pro nový modul runtime Unity (s kompatibilitou .NET 4.6 / C# 6)

- **Generování projektu:**

  - Přidání podpory pro profil .NET 4.6

  - Přidání podpory pro soubory mcs.rsp

  - Při použití Unity 5.6 vždy povolte nezabezpečený přepínač kompilace.

  - Přidání podpory pro generování projektů Player při použití platformy Windows Store a back-endu il2cpp

### <a name="bug-fixes"></a>Opravy chyb

- **Editor kódu:**

  - Byla opravena pozice vložení metody s automatickým dokončováním.

- **Generování projektu:**

  - Byla odebrána verze sestavení po zpracování.

## <a name="3001"></a>3.0.0.1

Vydáno 7. března 2017

### <a name="this-version-includes-all-new-features-and-bug-fixes-introduced-with-28x-series"></a>Tato verze zahrnuje všechny nové funkce a opravy chyb představené ve verzi 2.8.x.

## <a name="2820---30-preview-3"></a>2.8.2.0 – 3.0 Preview 3
Vydáno 25. ledna 2017

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Byla opravena regrese, kdy moduly plug-in projektují, kde se odkazuje dvakrát, nejprve jako binární knihovna DLL a pak jako odkaz na projekt.

## <a name="2810---30-preview-2"></a>2.8.1.0 – 3.0 Preview 2
Vydáno 23. ledna 2017

### <a name="bug-fixes"></a>Opravy chyb

- **Editor kódu:**

  - Opravili jsme selhání při spuštění deklarace atributu bez dokončení složených závorek.

- **Ladicí program:**

  - Opravili jsme zarážky funkcí s korutiny v novém kompilátoru/modulu runtime Unity.

  - Přidání upozornění v případě nezabalitelné zarážky (pokud se nenašlo odpovídající umístění zdroje)

- **Generování projektu:**

  - Opravili jsme generování csproj se speciálními/lokalizovanými znaky.

  - Oprava odkazů mimo prostředky, jako je knihovna (například Facebook SDK)

- **Vedlejší:**

  - Přidali jsme kontrolu, která brání spuštění Unity při instalaci nebo odinstalaci.

  - Přepnuli na https a cílí na vzdálenou dokumentaci k Unity.

## <a name="2800---30-preview"></a>2.8.0.0 – 3.0 Preview
Vydáno 17. listopadu 2016

### <a name="new-features"></a>Nové funkce

- **Obecné:**

  - Přidání Visual Studio instalačního programu 2017

  - Přidání Visual Studio rozšíření 2017

  - Přidali jsme podporu lokalizace.

- **Editor kódu:**

  - Přidání C# IntelliSense pro zprávy Unity

  - Přidali jsme barevné zbarvení kódu C# pro zprávy Unity.

- **Ladicí program:**

  - Byla přidána podpora `is` `as` pro výrazy , , přímé přetypování, `default` , `new` .

  - Přidání podpory pro výrazy řetězu řetězců

  - Přidání podpory pro šestnáctkové zobrazení celočíselných hodnot

  - Přidání podpory pro vytváření nových dočasných proměnných (příkazů)

  - Přidání podpory implicitních primitivních převodů

  - Přidali jsme lepší chybové zprávy, když se typ očekává nebo nenašel.

- **Generování projektu:**

  - Z názvů projektů jsme odebrali příponu CSharp.

  - Byl odebrán odkaz na soubor cílů nástroje msbuild v celém systému.

- **Průvodci:**

  - Přidali jsme podporu pro zprávy Unity v jiných typech chování, jako je Editor nebo EditorWindow.

  - Přepnutí na Roslyn pro vložení a formátování zpráv Unity

### <a name="bug-fixes"></a>Opravy chyb

- **Ladicí program:**

  - Opravili jsme chybu s chybou Unity při vyhodnocování obecných typů.

  - Opravili jsme zpracování typů s možnou hodnotou null.

  - Opravili jsme zpracování výčtů.

  - Opravili jsme zpracování vnořených typů členů.

  - Oprava přístupu indexeru kolekce

  - Opravili jsme podporu ladění snímků iterátoru pomocí nového kompilátoru jazyka C#.

- **Generování projektu:**

  - Opravili jsme chybu, která zabránila kompilaci při cílení na webový přehrávač Unity.

  - Opravili jsme chybu, která zabránila kompilaci při kompilaci skriptu s názvem webového zakódovaného souboru.

## <a name="2300"></a>2.3.0.0

Vydáno 14. července 2016

### <a name="new-features"></a>Nové funkce

- **Obecné:**

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

## <a name="2200"></a>2.2.0.0

Vydáno 4. února 2016

### <a name="new-features"></a>Nové funkce

- **Průvodc**

  - V průvodci **implementací MonoBehavior** se přidalo inteligentní vyhledávání.

  - Povědomi jste kontext průvodců; například zprávy NetworkBehavior jsou k dispozici pouze při práci s NetworkBehavior.

  - Do průvodců se přidala podpora pro zprávy NetworkBehavior.

- **ROZHRANÍ**

  - Přidání možnosti pro konfiguraci viditelnosti MonoBehavior zpráv.

  - Byly odebrány stránky vlastností sady Visual Studio, které nejsou relevantní pro projekty Unity.

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

## <a name="2100"></a>2.1.0.0

Vydáno 8. září 2015

### <a name="new-features"></a>Nové funkce

- Podpora pro Unity 5,2

### <a name="bug-fixes"></a>Opravy chyb

- Zobrazení položek nabídky na Unity < 4,2

- Když Visual Studio zamkne soubory XML IntelliSense, chybová zpráva se už nezobrazuje.

- Obsluha <\<When Changed>> podmíněných zarážek, pokud podmíněný argument není logická hodnota.

- Pevné odkazy na sestavení UnityEngine a UnityEditor pro aplikace pro Windows Store.

- Opravená chyba při krokování v ladicím programu: nejde krokovat, obecná výjimka.

- Pevné zarážky počtu volání v aplikaci Visual Studio 2015.

## <a name="2000"></a>2.0.0.0

Vydáno 20. července 2015

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

## <a name="1990---20-preview-2"></a>1.9.9.0 – 2,0 Preview 2
Vydáno 2. dubna 2015

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

## <a name="1980---20-preview"></a>1.9.8.0-2,0 Preview
Vydáno 12. listopadu 2014

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

## <a name="1920"></a>1.9.2.0

Vydáno 9. října 2014

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

## <a name="1910"></a>1.9.1.0

Vydáno 22. září 2014

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

## <a name="1900"></a>1.9.0.0

Vydáno 29. července 2014

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

## <a name="1820"></a>1.8.2.0

Vydáno 7. ledna 2014

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

## <a name="1810"></a>1.8.1.0

Vydáno 21. listopadu 2013

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

## <a name="1800"></a>1.8.0.0

Vydáno 24. září 2013

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

## <a name="1220"></a>1.2.2.0

Vydáno 9. července 2013

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

## <a name="1210"></a>1.2.1.0

Vydáno 9. dubna 2013

### <a name="bug-fixes"></a>Opravy chyb

- Pevné místní nasazení sestavení Unity pro dokončení kódu v případě chyby v/v (například souborů jen pro čtení nebo souborů uzamčených aplikací Visual Studio).

- Opravili jsme regresi, kdy otevření skriptu z Unity se nezaměřuje na soubor, pokud už je otevřený v aplikaci Visual Studio.

- Opravili jsme problém s výkonem nového zpracování výjimek.

- Pevná vazba zarážek v některých externích knihovnách DLL.

## <a name="1200"></a>1.2.0.0

Vydáno 25. března 2013

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

- Oprava chyby UVS-44: Ctrl+SHIFT+Q není ve VS 2012 k dispozici pro rychlé objekty MonoBehaviours.

- Oprava chyby UVS-40: Vybrané položky v Unity Project Exploreru jsou nečitelné, když je okno neaktivní v tmavém motivu VS2012.

- Oprava chyby UVS-39: Problém s tokenizací uvozových řetězců

- Oprava chyby UVS-35: Vyvolání ToString u objektů při kontrole proměnných

- Oprava chyby UVS-27: Ve VS2012 se okno se symbolem goto nekonzistence s tmavým motivem

- Oprava chyby UVS-11: Místní hodnoty v korutínech

## <a name="1100---beta-release"></a>1.1.0.0 – beta verze
Vydáno 9. března 2013

## <a name="10130"></a>1.0.13.0
Vydáno 21. ledna 2013

### <a name="bug-fixes"></a>Opravy chyb

- Opravili jsme Visual Studio, ke které mohlo dojít v případě, že cílová debuggee odesílá neplatné události vlákna. K tomu obvykle dochází při ladění vzdálené unity v OSX.

- Opravili jsme Visual Studio, ke které mohlo dojít, když výjimka vypne ladicí program.

- Opravili jsme naše pomocníky MonoBehavior, když je MonoBehavior jazyka C# v oboru názvů.

- Opravili jsme popisy ladicího programu pro UnityScript Visual Studio 2012.

- Opravili jsme generování projektu, když se z Unity změnily jenom konstanty ladění.

- Opravili jsme navigaci pomocí klávesnice v Unity Project Exploreru.

- Oprava zabarvení UnityScriptu pro řetězce s uvozenou znaky

- Opravili jsme problém se souborem, aby se lépe odhadl název projektu při použití mimo Unity. To je nezbytné, když uživatel použije třetí část souboru v Unity, který deleguje na UnityVS.

- Opravili jsme zpracování dlouhých zpráv odeslaných z Unity do UnityVS. Předtím mohlo dojít k chybové chybě dlouhých zpráv v naší části UnityVS pro zasílání zpráv. V důsledku toho by UnityVS někdy neotevřel soubor z Unity.

## <a name="10120"></a>1.0.12.0
Vydáno 3. ledna 2013

### <a name="bug-fixes"></a>Opravy chyb

- Opravili Visual Studio, ke které mohlo dojít Visual Studio odstranění zarážky.

- Opravili jsme chybu, kdy se po rekompilovaných herních skriptech Unity nepohodly některé zarážky.

- Opravili jsme ladicí program tak, aby správně Visual Studio, když byly zarážky nevázané.

- Opravili jsme problém s registrací, který mohl bránit ladicímu Visual Studio ladění nativních programů.

- Opravili jsme výjimku, ke které mohlo dojít při vyhodnocování výrazů UnityScript a Boo.

- Opravili jsme regresi, kdy změna úrovně rozhraní .NET API v Unity nespouštěl aktualizaci souborů projektu.

- Opravili jsme problém rozhraní API, kdy se uživatelský kód nemohl účastnit obslužné rutiny zpětného volání protokolu.

## <a name="10110"></a>1.0.11.0
Vydáno 28. listopadu 2012

### <a name="new-features"></a>Nové funkce

- Oficiální podpora Unity 4.

- Manipulace se skripty z Průzkumníka projektů Unity

- Integrace Visual Studio okně Přejít na.

- Analýza zprávy konzoly Info, aby se kliknutím na Seznam chyb dostat k prvnímu zásobníku se symboly.

- Přidejte rozhraní API, aby se uživatel mohli účastnit generování projektu.

- Přidejte rozhraní API, které uživateli umožňuje účastnit se LogCallback.

### <a name="bug-fixes"></a>Opravy chyb

- Opravili jsme regresi na pozadí Průzkumníka projektů Unity v Visual Studio 2012.

- Opravili jsme generování projektu pro uživatele plného profilu .NET.

- Opravili jsme generování projektu pro uživatele webového cíle.

- Opravili jsme generování projektu tak, aby zahrnovalo symboly kompilace DEBUG a TRACE jako Unity.

- Opravili jsme problém s chybami při použití speciálních znaků v okně Symbol Goto.

- Opravili jsme problém, kdy do stavového řádku Visual Studio ikonu vložit.

## <a name="10100"></a>1.0.10.0
Vydáno 9. října 2012

### <a name="bug-fixes"></a>Opravy chyb

- Opravili jsme pozadí Průzkumníka projektů Unity v Visual Studio 2010.

- Opravili jsme Visual Studio, ke kterému mohlo dojít v případě, že se UnityVS pokusil připojit ladicí program k Unity, jejíž rozhraní ladicího programu dříve havaruje.

- Opravili jsme Visual Studio, ke kterým mohlo dojít při nastavení zarážky a opětovném načtení appdomain.

- Opravili jsme způsob načítání sestavení z Unity, aby se zabránilo zamykání souborů a zmást proces sestavení Unity.

## <a name="1090"></a>1.0.9.0

Vydáno 3. října 2012

### <a name="bug-fixes"></a>Opravy chyb

- Opravili jsme generování projektu, když projekt Unity obsahuje skutečné prostředky JavaScriptu.

- Opravili jsme zpracování chyb při vyhodnocování výrazů.

- Opravili jsme nastavení nových hodnot na pole hodnotových typů.

- Opravili jsme možné vedlejší účinky při najetí myší na výrazy z editoru kódu.

- Opravili jsme způsob vyhledávání typů v načtených sestaveních pro vyhodnocení výrazu.

- Oprava chyby UVS-21: Vyhodnocení přiřazení u objektů Unity nemá žádný vliv.

- Oprava chyby UVS-21: Neplatný ukazatel při vyhodnocování vyvolání metody do matematického rozhraní API Unity

## <a name="1080"></a>1.0.8.0

Vydáno 26. září 2012

### <a name="bug-fixes"></a>Opravy chyb

- Opravili jsme způsob, jakým skript získal cestu k projektu, aby se ujistil, že dokáže otevřít Visual Studio i skripty.

- Opravili jsme chybu se zarážkami vytvořenými při spuštěné relaci ladění, která Visual Studio uzamkne.

- Opravili jsme způsob registrace UnityVS Visual Studio 2010.

## <a name="1070"></a>1.0.7.0

Vydáno 14. září 2012

### <a name="new-features"></a>Nové funkce

- Visual Studio 2012.

### <a name="bug-fixes"></a>Opravy chyb

- Opravili jsme generování souborů projektu Editor a Plugins tak, aby odpovídaly chování Unity.

- Opravili jsme překlad symbolů .pdb v Unity 4.

> [!IMPORTANT]
> Kvůli podpoře Visual Studio 2012 jsme museli přejmenovat několik souborů a přesunout další. Balíček UnityVS pro import Unity se teď jmenuje UnityVS 2010 nebo UnityVS 2012 pro Visual Studio 2010 a Visual Studio 2012. Tato verze také vyžaduje, aby se soubory projektu UnityVS znovu vygeneroval.

## <a name="1060---internal-build"></a>1.0.6.0 – interní sestavení
Vydáno 12. září 2012

## <a name="1050"></a>1.0.5.0

Vydáno 10. září 2012

### <a name="bug-fixes"></a>Opravy chyb

- Opravili jsme generování souborů projektu, když skripty nebo shadery měly neplatný znak XML.

- Opravili jsme detekci instancí Unity při připojení Unity k serveru prostředků. Tím se aktivoval počet selhání při otevření souborů z Unity a automatické připojení Visual Studio ladicího programu.

## <a name="1040"></a>1.0.4.0

Vydáno 5. září 2012

### <a name="new-features"></a>Nové funkce

- Automatický převod symbolů ladění v Unity

    Pokud máte sestavení .NET .dll s přidruženým souborem .pdb ve složce Asset, jednoduše znovu naimportujte sestavení a UnityVS převede soubor .pdb na soubor symbolů ladění, který skriptovací modul Unity rozumí, a budete moci krokovat do sestavení .NET z UnityVS.

### <a name="bug-fixes"></a>Opravy chyb

- Opravili jsme selhání UnityVS při ladění způsobené výjimkami vyvolané metodami nebo vlastnostmi v Unity.

## <a name="1030"></a>1.0.3.0

Vydáno 4. září 2012

### <a name="new-features"></a>Nové funkce

- Nová možnost konfigurace pro zakázání používání UnityVS k otevření souborů z Unity.

### <a name="bug-fixes"></a>Opravy chyb

- Opravili jsme generování odkazů na UnityEditor pro projekty, které nejsou editorem.

- Opravili jsme definici UNITY_EDITOR pro projekty, které nejsou editorem.

- Opravili jsme náhodné selhání VS způsobené naším vlastním stavový řádek.

## <a name="1020"></a>1.0.2.0

Vydáno 30. srpna 2012

### <a name="bug-fixes"></a>Opravy chyb

- Byl opraven konflikt s ladicím programem PythonTools.

- Opravili jsme odkazy na Mono.Ilail.

- Opravili jsme chybu v načítání skriptování sestavení z Unity s Unity 4 b7.

## <a name="1010"></a>1.0.1.0

Vydáno 28. srpna 2012

### <a name="new-features"></a>Nové funkce

- Podpora verze Preview pro Unity 4.0 Beta

### <a name="bug-fixes"></a>Opravy chyb

- Opravili jsme kontrolu vlastností, které výjimky výjimky řešly.

- Opravili jsme sestupné sestupné zobrazení do základních objektů při kontrole objektů.

- Oprava prázdného rozevíracího seznamu pro kurzor v průvodci MonoBehavior

- Opravili jsme dokončování pro knihovnu DLL ve složce Asset pro UnityScript a Boo.

## <a name="1000---initial-release"></a>1.0.0.0 – počáteční verze
Vydáno 22. srpna 2012
