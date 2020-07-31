---
title: Protokol změn (Visual Studio Tools for Unity, Windows) | Microsoft Docs
ms.custom: ''
ms.date: 7/30/2020
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: ea490b7e-fc0d-44b1-858a-a725ce20e396
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 2a069753040be65f963c1047ef376bef653bfbc1
ms.sourcegitcommit: 43df639b2cd99200f725a8ebb941477481a6f0ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/31/2020
ms.locfileid: "87471516"
---
# <a name="change-log-visual-studio-tools-for-unity-windows"></a>Protokol změn (Visual Studio Tools for Unity, Windows)

Protokol změn Visual Studio Tools for Unity

## <a name="4710"></a>4.7.1.0
Vydáno 5. srpna 2020

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Přidání podpory oboru názvů do výchozích šablon.
  
  - Rozhraní API pro zprávy Unity se aktualizovalo na 2019,4.

  - Přidání [`USP0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0013.md) Suppressor pro `CA1823` . Soukromá pole s `SerializeField` atributy nebo `SerializeReference` by se neměla označit jako nepoužitá (FxCop).
  
  - Přidání [`USP0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0014.md) Suppressor pro `CA1822` . Zprávy Unity by neměly být označeny jako kandidáti na `static` Modifikátor (FxCop).

  - Přidání [`USP0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0015.md) Suppressor pro `CA1801` . Nepoužité parametry by neměly být odebrány ze zpráv Unity (FxCop).
  
  - Do Suppressor se přidala podpora MenuItem [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md) .  

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Pevné [`USP0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0001.md) a [`USP0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0002.md) potlačené nepracují s dalšími závorkami nebo s argumenty metody.
  
  - Pevná povinná databáze assetu se aktualizuje i v případě, že je v nastavení Unity zakázaná Automatická aktualizace.

## <a name="4700"></a>4.7.0.0
Vydáno 23. června 2020

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Přidání podpory pro uchovávání složek řešení, když Unity znovu generuje řešení a projekty.

  - Přidání [`UNT0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0015.md) diagnostiky Zjistila nesprávný podpis metody pomocí `InitializeOnLoadMethod` `RuntimeInitializeOnLoadMethod` atributu nebo.

  - Přidání [`UNT0016`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0016.md) diagnostiky Použití `Invoke` , `InvokeRepeating` `StartCoroutine` nebo `StopCoroutine` s prvním argumentem pro řetězcový literál není typově bezpečné.

  - Přidání [`UNT0017`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0017.md) diagnostiky `SetPixels`vyvolání je pomalé.

  - Přidání podpory pro komentář k bloku a odsazení pro soubory shaderu

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Při filtrování zpráv v průvodci zprávami Unity neobnovujte výběr.
  
  - Při otevírání dokumentace k rozhraní Unity API vždycky používejte výchozí prohlížeč.
  
  - Pevné [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md) [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) a [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) potlačené následující pravidla: potlačit `IDE0044` (jen pro čtení), `IDE0051` (nepoužívané), `CS0649` (nikdy Nepřiřazeno) pro všechna pole dekorovaná atributem SerializeField. Potlačit `CS0649` (nikdy Nepřiřazeno) pro veřejná pole všech typů, které rozšiřuje `Unity.Object` .

  - Pevná Kontrola parametrů obecného typu pro [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md) diagostic.

- **Hodnocení**

  - Pevné porovnání rovnosti s výčty.

## <a name="4610"></a>4.6.1.0
Vydáno 19. května 2020

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Upozorňovat, pokud nemůžeme vytvořit poštovní server na straně Unity.
  
  - Při zjednodušené kompilaci jsou správně spouštěny analyzátory.
  
  - Opravili jsme problém, kdy třída MonoBehaviour vytvořená z UPE se neshodovala s názvem souboru.

## <a name="4600"></a>4.6.0.0
Vydáno 14. dubna 2020

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Byla přidána podpora pro CodeLens (skripty a zprávy Unity).
  
  - Přidání [`UNT0012`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0012.md) diagnostiky Detekovat a zalamovat volání korutin v `StartCoroutine()` .

  - Přidání [`UNT0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0013.md) diagnostiky Zjištění a odebrání neplatného nebo redundantního `SerializeField` atributu

  - Přidání [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md) diagnostiky Detekce `GetComponent()` volána s typem bez komponenty nebo bez rozhraní.
  
  - Přidání [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md) Suppressor pro `IDE0051` . Nepoužívejte příznak s `ContextMenu` atributem nebo odkazem na pole s `ContextMenuItem` atributem nepoužitelné.

  - Přidání [`USP0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0010.md) Suppressor pro `IDE0051` . Neoznačí pole `ContextMenuItem` atributem jako nepoužitou.
  
  - Přidání [`USP0011`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0011.md) Suppressor pro `IDE0044` . Nevytvářejte pole s `ContextMenuItem` atributem jen pro čtení.
  
  - [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md)[`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md)a [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) teď fungují pro `SerializeReference` atributy i `SerializeField` .
  
### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Když je editor schopný komunikovat, odesílají jenom příkazy spustit/zastavit do Unity.
  
  - Opravená dokumentace QuickInfo s děděnými zprávami.
  
  - Rozsah pevné zprávy pro `CreateInspectorGUI` zprávu

  - Nevytvářejte sestavy [`UNT0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0001.md) metod s polymorfními modifikátory.

- **Hodnocení**

  - Pevné zpracování aliasů using.

## <a name="4510"></a>4.5.1.0

Vydáno 16. března 2020

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Přidání [`USP0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0008.md) Suppressor pro `IDE0051` . Soukromé metody použité s voláním Invoke, InvokeRepeating, StartCoroutine nebo StopCoroutine by neměly být označeny jako nepoužívané.

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Opravená dokumentace funkci ondrawgizmos implementujte/funkci ondrawgizmosselected implementujte.

- **Hodnocení**

  - Opravená kontrola argumentu lambda.

## <a name="4501"></a>4.5.0.1

Vydáno 19. února 2020

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Opravila se [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md) Kontrola diagnostiky pro nesprávný podpis zprávy. Při kontrole typů s více úrovněmi dědičnosti může tato diagnostika selhat s následující zprávou: `warning AD0001: Analyzer 'Microsoft.Unity.Analyzers.MessageSignatureAnalyzer' threw an exception of type 'System.ArgumentException' with message 'An item with the same key has already been added` .

## <a name="4500"></a>4.5.0.0

Vydáno 22. ledna 2020

### <a name="new-features"></a>Nové funkce

- **Spolupráci**

  - Přidání podpory pro soubory HLSL
  
  - Přidání [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) Suppressor pro `IDE0051` . Soukromá pole s `SerializeField` atributem by neměla být označena jako nepoužitá.
  
  - Přidání [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) Suppressor pro `CS0649` . Pole s `SerializeField` atributem by neměla být označena jako Nepřiřazená.  

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
    - [`USP0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0001.md)pro `IDE0029` : objekty Unity by neměly používat slučování s hodnotou null.
    - [`USP0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0002.md)pro `IDE0031` : objekty Unity by neměly používat šíření hodnoty null.
    - [`USP0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0003.md)pro `IDE0051` : zprávy Unity jsou vyvolány modulem runtime Unity.
    - [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md)for `IDE0044` : pole s atributem SerializeField by neměla být určena jen pro čtení.

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

  - Zlepšilo se uživatelské prostředí pro zobrazování editoru Unity a instancí přehrávače (Windows teď měnitelné velikosti, používejte jednotné okraje a zobrazují úchyt pro změnu velikosti). Přidání informací o ID procesu pro editory Unity

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

- **Spolupráci**

  - Po přeposílání Visual Studio Tools for Unity bude podporovat Unity 5.2 + (s integrovanou integrací sady Visual Studio Unity).

  - Až budete dál, Visual Studio Tools for Unity podporují jenom Visual Studio 2015 +.

  - Byla odebrána služba starší verze jazyka, seznam chyb a stavový řádek.

  - Odebral se Průvodce rychlým MonoBehaviour (ve prospěch vyhrazené podpory technologie IntelliSense).

## <a name="3903"></a>3.9.0.3

Vydáno 28. listopadu 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Pevné opětovné načítání projektů a problémy IntelliSense při přidávání nebo odebírání skriptů umístěných v velmi prvním projektu.

## <a name="3902"></a>3.9.0.2

Vydáno 19. listopadu 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Ladění**

  - Opravili jsme zablokování v knihovně používané ke komunikaci s modulem ladicího programu Unity, aby se aplikace Visual Studio nebo Unity zablokoval, zejména když jste se připojili k Unity nebo restartujete hru.

## <a name="3901"></a>3.9.0.1

Vydáno 15. listopadu 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Pevná aktivace modulu plug-in Unity, pokud byl vybrán jiný výchozí editor.

## <a name="3900"></a>3.9.0.0

Vydáno 13. listopadu 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Odebrali jsme řešení chyby výkonu Unity, které vyřešila Unity.

## <a name="3807"></a>3.8.0.7

Vydáno 20. září 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Ladění**

  - (Neportované z 3.9.0.2) Opravili jsme zablokování v knihovně používané ke komunikaci s modulem ladicího programu Unity, aby se aplikace Visual Studio nebo Unity zablokoval, zejména když jste se připojili k Unity nebo restartujete hru.

## <a name="3806"></a>3.8.0.6

Vydáno 27. srpna 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Pevné opětovné načtení projektů a řešení.

## <a name="3805"></a>3.8.0.5

Vydáno 20. srpna 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Pevné vyřazení předplatného monitorování projektu.

## <a name="3804"></a>3.8.0.4

Vydáno 14. srpna 2018

### <a name="new-features"></a>Nové funkce

- **Hodnocení**

  - Přidání podpory pro hodnoty ukazatele

  - Byla přidána podpora pro obecné metody.

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Inteligentní opětovné načtení s více projekty bylo změněno.

## <a name="3803"></a>3.8.0.3

Vydáno 24. července 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - (Neportované z 3.9.0.0) Odebrali jsme řešení chyby výkonu Unity, které vyřešila Unity.

## <a name="3802"></a>3.8.0.2

Vydáno 7. července 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Přechodný alternativní postup pro chybu výkonu Unity: mezipaměť MonoIslands při generování projektů.

## <a name="3801"></a>3.8.0.1

Vydáno 26. června 2018

### <a name="new-features"></a>Nové funkce

- **Tém**

  - Přidání podpory pro příkazy UserLog a UserBreak

  - Přidání podpory opožděného typu (optimalizace zatížení sítě a latence odezvy ladicího programu)

### <a name="bug-fixes"></a>Opravy chyb

- **Hodnocení**

  - Vylepšené vyhodnocení výrazu binárního operátoru a hledání metod.

## <a name="3800"></a>3.8.0.0

Vydáno 30. května 2018

### <a name="new-features"></a>Nové funkce

- **Tém**

  - Přidání podpory pro zobrazení proměnných v asynchronních konstrukcích.

  - Přidání podpory pro zpracování vnořených typů při nastavování zarážek, aby se zabránilo upozornění pomocí konstrukcí kompilátoru.

- **Spolupráci**

  - Přidání podpory pro gramatiky TextMate pro shadery (úlohy C++ již není nutné pro zbarvení kódu shaderu).

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Při použití nového modulu runtime Unity neprovádějte převod přenositelných souborů PDB na MDB.

## <a name="3701"></a>3.7.0.1

Vydáno 7. května 2018

### <a name="bug-fixes"></a>Opravy chyb

- **Instalační**

  - Pevný problém závislosti při použití experimentálních buildů.

## <a name="3700"></a>3.7.0.0

Vydáno 7. května 2018

### <a name="new-features"></a>Nové funkce

- **Tém**

  - Přidali jsme podporu pro orchestraci ladění (ladění více hráčů/Editor se stejnou relací sady Visual Studio).

  - Přidala se podpora pro ladění přehrávače USB Androidu.

  - Přidání podpory pro ladění pro UWP/IL2CPP Player

- **Hodnocení**

  - Byla přidána podpora pro šestnáctkové specifikátory.

  - Vylepšené prostředí pro vyhodnocení sledovacího okna.

### <a name="bug-fixes"></a>Opravy chyb

- **Spolupráci**

  - Pevné použití nastavení výjimek

- **Generování projektu:**

  - Vylučte jednotky kompilace správce balíčků z generace.

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

  - Opravené rozšíření extra. dll je nesprávně přidáno k názvu souboru sestavení.

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

  - Opravili jsme generování řešení sady Visual Studio na Unity 5,5 a předchozích verzích.

## <a name="3300"></a>3.3.0.0

Vydáno 14. srpna 2017

### <a name="new-features"></a>Nové funkce

- **Hodnocení**

  - Přidali jsme podporu pro vytváření struktur s novým modulem runtime Unity.

  - Přidání podpory minimalist pro ukazatele

### <a name="bug-fixes"></a>Opravy chyb

- **Hodnocení**

  - Volání pevné metody na primitivních elementech

  - Pevné vyhodnocení pole s typy označenými pomocí BeforeFieldInit.

  - Pevná Nepodporovaná volání s binárními operátory (substract).

  - Opravené problémy při přidávání položek do kukátka aplikace Visual Studio.

- **Generování projektu:**

  - Pevný název sestavení odkazuje na soubory MCS. rsp.

  - Fixed definuje s úrovněmi rozhraní API.

## <a name="3200"></a>3.2.0.0

Vydáno 10. května 2017

### <a name="new-features"></a>Nové funkce

- **Instalační**

  - Přidání podpory pro čištění mezipaměti MEF.

### <a name="bug-fixes"></a>Opravy chyb

- **Editor kódu:**

  - Pevná klasifikace/dokončování s vlastními atributy.

  - Opravené blikání se zprávami Unity.

## <a name="3100"></a>3.1.0.0

Vydáno 7. dubna 2017

### <a name="new-features"></a>Nové funkce

- **Ladění**

  - Přidání podpory pro nový modul runtime Unity (s kompatibilitou .NET 4,6/C# 6)

- **Generování projektu:**

  - Přidala se podpora pro profil .NET 4,6.

  - Přidání podpory pro soubory MCS. rsp.

  - Vždy povolit nezabezpečený přepínač kompilace při použití Unity 5,6.

  - Přidání podpory pro generování projektu "přehrávač" při použití platformy Windows Store a back-endu il2cpp

### <a name="bug-fixes"></a>Opravy chyb

- **Editor kódu:**

  - Pevná pozice blikajícího kurzoru po vložení metody s automatickým dokončováním

- **Generování projektu:**

  - Následné zpracování verze sestavení se odebralo.

## <a name="3001"></a>3.0.0.1

Vydáno 7. března 2017

### <a name="this-version-includes-all-new-features-and-bug-fixes-introduced-with-28x-series"></a>Tato verze zahrnuje všechny nové funkce a opravy chyb zavedené pomocí řady 2.8. x.

## <a name="2820---30-preview-3"></a>2.8.2.0 – 3,0 Preview 3
Vydáno 25. ledna 2017

### <a name="bug-fixes"></a>Opravy chyb

- **Generování projektu:**

  - Pevná regrese, kde jsou projekty modulů plug-in odkazovány dvakrát, jako binární knihovna DLL, poté jako odkaz na projekt.

## <a name="2810---30-preview-2"></a>2.8.1.0 – 3,0 Preview 2
Vydáno 23. ledna 2017

### <a name="bug-fixes"></a>Opravy chyb

- **Editor kódu:**

  - Při spuštění deklarace atributu bez dokončování závorek došlo k chybě.

- **Ladění**

  - Pevné zarážky funkcí s korutinami v rámci nového kompilátoru Unity/modulu runtime.

  - Přidání upozornění v případě nedostupného bodu přerušení (když není nalezeno odpovídající umístění zdroje).

- **Generování projektu:**

  - Fixní generování csproj pomocí speciálních/lokalizovaných znaků.

  - Pevné odkazy mimo prostředky, jako je například knihovna Facebooku (například Facebook SDK).

- **Vedl**

  - Přidání kontroly, které zabrání spuštění Unity při instalaci nebo odinstalaci.

  - Přepnutím na https zacílíte na vzdálenou dokumentaci Unity.

## <a name="2800---30-preview"></a>2.8.0.0-3,0 Preview
Vydáno 17. listopadu 2016

### <a name="new-features"></a>Nové funkce

- **Všeobecně**

  - Přidala se podpora instalačního programu sady Visual Studio 2017.

  - Přidala se podpora rozšíření sady Visual Studio 2017.

  - Byla přidána podpora lokalizace.

- **Editor kódu:**

  - Byla přidána zpráva jazyka C# technologie IntelliSense pro zprávy Unity.

  - Bylo přidáno zbarvení kódu jazyka C# pro zprávy Unity.

- **Ladění**

  - Přidání podpory pro `is` , `as` , přímé přetypování, `default` , `new` výrazy.

  - Přidání podpory pro výrazy pro řetězce Concat

  - Byla přidána podpora hexadecimálního zobrazení celočíselných hodnot.

  - Přidání podpory pro vytváření nových dočasných proměnných (příkazů).

  - Byla přidána podpora implicitních primitivních převodů.

  - Přidání lepších chybových zpráv, když se očekává nebo nenalezne typ.

- **Generování projektu:**

  - Z názvů projektů byla odebrána přípona CSharp.

  - Odebral se odkaz na soubor cílů MSBuild v rámci systému.

- **Průvodc**

  - Přidání podpory pro zprávy Unity v typech nechování, jako je editor nebo zavření okna editoru.

  - Přepnuto na Roslyn pro vkládání a formátování zpráv Unity.

### <a name="bug-fixes"></a>Opravy chyb

- **Ladění**

  - Opravili jsme chybu při selhání Unity při vyhodnocování generických typů.

  - Pevné zpracování typů s možnou hodnotou null.

  - Pevné zpracování výčtů.

  - Pevné zpracování vnořených typů členů.

  - Přístup k indexeru pevné kolekce.

  - Podporovaná podpora pro ladění snímků iterátorů s novým kompilátorem jazyka C#.

- **Generování projektu:**

  - Opravili jsme chybu, která zabránila kompilaci při cílení na webový přehrávač Unity.

  - Opravila se chyba, která zabránila kompilaci při kompilování skriptu s názvem souboru s kódováním webu.

## <a name="2300"></a>2.3.0.0

Vydáno 14. července 2016

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

- Opravená chyba UVS-44: CTRL + SHIFT + Q není v sadě VS 2012 pro rychlé třídy MonoBehaviour k dispozici.

- Opravená chyba UVS-40: vybrané položky v Průzkumníku projektů Unity jsou nečitelný, pokud je okno neaktivní v motivu VS2012 "tmavého".

- Opravená chyba UVS-39: vydejte řetězce s řídicími řetězci tokenizací.

- Opravená chyba UVS-35: při kontrole proměnných vyvolat ToString pro objekty.

- Opravená chyba UVS-27: příkaz goto symbol Window nekonzistence s motivem "tmavého" v VS2012.

- Opravená chyba UVS-11: národní prostředí v korutinách.

## <a name="1100---beta-release"></a>1.1.0.0 – beta verze
Vydáno v březnu 9. března 2013

## <a name="10130"></a>1.0.13.0
Vydáno 21. ledna 2013

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

## <a name="10120"></a>1.0.12.0
Vydáno 3. ledna 2013

### <a name="bug-fixes"></a>Opravy chyb

- Pevné zamrznutí sady Visual Studio, ke kterým může dojít, když aplikace Visual Studio odstranila zarážku.

- Opravili jsme chybu, kdy některé zarážky nedosáhly po rekompilovaných herních skriptech Unity.

- Opravili jste ladicí program o správné informování sady Visual Studio, pokud byly zarážky bez vazby.

- Opravili jsme problém s registrací, který by mohl ladicí program sady Visual Studio zabránit ladění nativních programů.

- Opravili jsme výjimku, která by mohla nastat při vyhodnocování výrazů UnityScript a boo.

- Opravili jsme regresi, kdy změna úrovně rozhraní .NET API v Unity neaktivuje aktualizaci souborů projektu.

- Opravili jsme rozhraní API porucha, kde se v obslužné rutině zpětného volání protokolu nepovedlo zúčastnit kód uživatele.

## <a name="10110"></a>1.0.11.0
Vydáno 28. listopadu 2012

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

## <a name="10100"></a>1.0.10.0
Vydáno 9. října 2012

### <a name="bug-fixes"></a>Opravy chyb

- Opravili jsme pozadí Průzkumníka projektů Unity v aplikaci Visual Studio 2010.

- Opravili jsme zablokování sady Visual Studio, ke kterému může dojít, když se UnityVS pokusil připojit ladicí program k Unity, jehož rozhraní ladicího programu předtím selhalo.

- Opravili jsme zablokování sady Visual Studio, ke kterému může dojít, když byla nastavena zarážka a dojde k opětovnému načtení domény AppDomain.

- Opravili jsme, jak jsou sestavení načítána z Unity, aby nedošlo k zamykání souborů a Zaměňujte proces sestavení Unity.

## <a name="1090"></a>1.0.9.0

Vydáno 3. října 2012

### <a name="bug-fixes"></a>Opravy chyb

- Fixní generování projektu, když projekt Unity obsahuje skutečné prostředky JavaScriptu.

- Opravené zpracování chyb ve vyhodnocení výrazu.

- Opravili jsme nastavení nových hodnot na pole hodnotových typů.

- Pevné možné vedlejší účinky při najetí myší na výrazy z editoru kódu

- Opravili jsme, jak se hledají typy v načtených sestaveních pro vyhodnocení výrazu.

- Opravená chyba UVS-21: vyhodnocení přiřazení u objektů Unity nemá žádný vliv.

- Opravená chyba UVS-21: neplatný ukazatel při vyhodnocování volání metody do rozhraní API pro matematiku Unity.

## <a name="1080"></a>1.0.8.0

Vydáno 26. září 2012

### <a name="bug-fixes"></a>Opravy chyb

- Opravili jsme, jak náš otevřený skript získal cestu k projektu, abyste měli jistotu, že je možné otevřít jak Visual Studio, tak i skripty.

- Opravili jsme chybu se zarážkami vytvořenými během spuštěné relace ladění, která by mohla způsobit, že se Visual Studio zamkne.

- Opraveno, jak je UnityVS registrována v aplikaci Visual Studio 2010.

## <a name="1070"></a>1.0.7.0

Vydáno 14. září 2012

### <a name="new-features"></a>Nové funkce

- Podpora sady Visual Studio 2012.

### <a name="bug-fixes"></a>Opravy chyb

- Pevná generace souborů projektů Editor a modulů plug-in, které odpovídají chování Unity.

- Opravili jsme překlad symbolů. pdb na Unity 4.

> [!IMPORTANT]
> Kvůli podpoře sady Visual Studio 2012 jsme museli přejmenovat pár souborů a trochu se přesunout. Balíček UnityVS pro import Unity se teď jmenuje buď UnityVS 2010 nebo UnityVS 2012, pro Visual Studio 2010 a Visual Studio 2012. Tato verze také vyžaduje, aby se soubory projektu UnityVS znovu vygenerovaly.

## <a name="1060---internal-build"></a>1.0.6.0 – interní sestavení
Vydáno 12. září 2012

## <a name="1050"></a>1.0.5.0

Vydáno 10. září 2012

### <a name="bug-fixes"></a>Opravy chyb

- Pevná generace souborů projektu, když skripty nebo shadery měly neplatný znak XML.

- V případě, že byla služba Unity připojena k serveru assetů, byla vyřešena detekce instancí Unity. Aktivované chyby při otevírání souborů z Unity a automatického připojení ladicího programu sady Visual Studio.

## <a name="1040"></a>1.0.4.0

Vydáno 5. září 2012

### <a name="new-features"></a>Nové funkce

- Automatický převod symbolů ladění v Unity

    Pokud máte sestavení .NET. dll s přidruženým souborem. pdb ve složce assets, jednoduše znovu importujte sestavení a UnityVS převede soubor. pdb na soubor symbolů ladění, který skriptovací stroj Unity považuje za a vy budete moci do sestavení .NET krokovat z UnityVS.

### <a name="bug-fixes"></a>Opravy chyb

- Při ladění došlo k UnityVS chybě, která způsobila výjimky vyvolané metodami nebo vlastnostmi v Unity.

## <a name="1030"></a>1.0.3.0

Vydáno 4. září 2012

### <a name="new-features"></a>Nové funkce

- Nová možnost konfigurace, která zakáže použití UnityVS k otevření souborů z Unity.

### <a name="bug-fixes"></a>Opravy chyb

- Pevné generování odkazů na UnityEditor pro needitorované projekty.

- Pevná definice UNITY_EDITOR symbol pro needitorované projekty

- Opravená náhodná chyba oproti chybě způsobená naším vlastním stavovým řádkem.

## <a name="1020"></a>1.0.2.0

Vydáno 30. srpna 2012

### <a name="bug-fixes"></a>Opravy chyb

- Opravený konflikt s ladicím programem PythonTools

- Pevné odkazy na mono. Cecil.

- Opravili jsme chybu v tom, jak se v Unity načetla sestavení do skriptů s Unity 4 B7.

## <a name="1010"></a>1.0.1.0

Vydaná 28. srpna 2012

### <a name="new-features"></a>Nové funkce

- Podpora Preview pro Unity 4,0 beta.

### <a name="bug-fixes"></a>Opravy chyb

- Opravili jsme kontrolu vlastností, které vyvolává výjimky.

- Při kontrole objektů je pevně navzestupné na základní objekty.

- Opraven prázdný rozevírací seznam pro kurzor v průvodci MonoBehavior.

- Pevné dokončení pro knihovnu DLL ve složce assetů pro UnityScript a boo.

## <a name="1000---initial-release"></a>1.0.0.0 – počáteční verze
Vydáno 22. srpna 2012
