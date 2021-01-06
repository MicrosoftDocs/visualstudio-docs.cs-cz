---
title: Ladění uživatelského kódu pomocí Pouze můj kód | Microsoft Docs
description: Pouze můj kód je funkce ladění, která automaticky provede kroky volání do neuživatelského kódu. Naučte se, jak tuto funkci povolit, zakázat a používat.
ms.custom: SEO-VS-2020
ms.date: 02/13/2019
ms.topic: how-to
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c902147bd1b7761bb6fdab1bc577af6a1990bed
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903880"
---
# <a name="debug-only-user-code-with-just-my-code"></a>Ladit pouze uživatelský kód pomocí Pouze můj kód

*Pouze můj kód* je funkce ladění sady Visual Studio, která automaticky provede kroky pro volání do systému, rozhraní a dalšího neuživatelského kódu. V okně **zásobník volání** pouze můj kód sbalí tato volání do snímků **[External Code]** .

Pouze můj kód funguje jinak v projektech .NET, C++ a JavaScript.

## <a name="enable-or-disable-just-my-code"></a><a name="BKMK_Enable_or_disable_Just_My_Code"></a> Povolit nebo zakázat Pouze můj kód

Pro většinu programovacích jazyků je Pouze můj kód ve výchozím nastavení povolený.

- Chcete-li povolit nebo zakázat pouze můj kód v aplikaci Visual Studio, v nabídce  >  **Možnosti** nástrojů (nebo   >  **Možnosti** ladění) > **ladění**  >  **obecně** vyberte nebo zrušte zaškrtnutí políčka **Povolit pouze můj kód**.

![Povolení Pouze můj kód v dialogovém okně Možnosti](../debugger/media/dbg_justmycode_options.png "Povolit Pouze můj kód")

> [!NOTE]
> **Možnost povolit pouze můj kód** je globální nastavení, které platí pro všechny projekty sady Visual Studio ve všech jazycích.

## <a name="just-my-code-debugging"></a>ladění s možností Pouze můj kód

Během relace ladění zobrazuje okno **moduly** , které kódové moduly ladicí program zpracovává jako můj kód (kód uživatele), spolu s jejich stavem načítání symbolů. Další informace najdete v tématu [o tom, jak se ladicí program připojuje k vaší aplikaci](../debugger/debugger-tips-and-tricks.md#modules_window).

![Uživatelský kód v okně moduly](../debugger/media/dbg_justmycode_module.png "Uživatelský kód v okně moduly")

V okně **zásobník volání** nebo **úlohy** pouze můj kód sbalí neuživatelský kód na označený blok kódu s poznámkou `[External Code]` .

![Rámec externího kódu v okně zásobník volání](../debugger/media/dbg_justmycode_externalcode.png "Rámec externího kódu")

>[!TIP]
>Chcete-li otevřít **moduly**, **zásobník volání**, **úlohy** nebo většinu dalších oken ladění, musíte být v relaci ladění. Při ladění vyberte v části **ladit**  >  **okna** okna, které chcete otevřít.

<a name="BKMK_Override_call_stack_filtering"></a> Chcete-li zobrazit kód ve sbaleném bloku **[External Code]** , klikněte pravým tlačítkem myši do **zásobníku volání** nebo okna **úlohy** a v místní nabídce vyberte možnost **Zobrazit externí kód** . Rozšířené řádky externího kódu nahradí rámec **[External Code**].

![Zobrazit externí kód v okně zásobník volání](../debugger/media/dbg_justmycode_showexternalcode.png "Zobrazit externí kód")

> [!NOTE]
> **Zobrazit externí kód** je aktuální uživatelské nastavení profileru, které platí pro všechny projekty ve všech jazycích, které uživatel otevřel.

Dvojím kliknutím na rozbalený externí řádek kódu v okně **zásobník volání** se zvýrazní řádek kódu, který je zelený ve zdrojovém kódu. Pro knihovny DLL nebo jiné moduly, které nebyly nalezeny nebo načteny, se může otevřít stránka symbol nebo zdroj nebyl nalezen.

## <a name="net-just-my-code"></a><a name="BKMK__NET_Framework_Just_My_Code"></a>Pouze můj kód .NET

V projektech .NET Pouze můj kód používá soubory symbolů (*PDB*) a optimalizace programu pro klasifikaci uživatele a neuživatelského kódu. Ladicí program .NET považuje optimalizované binární soubory a Nenačtené soubory *. pdb* za neuživatelský kód.

Tři atributy kompilátoru mají vliv i na to, co ladicí program .NET považuje za uživatelský kód:

- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> oznamuje ladicímu programu, že kód, na který se aplikuje, není uživatelský kód.
- <xref:System.Diagnostics.DebuggerHiddenAttribute> skryje kód z ladicího programu, a to i v případě, že je vypnutý Pouze můj kód.
- <xref:System.Diagnostics.DebuggerStepThroughAttribute> instruuje ladicí program, aby provedl kód, na který je aplikován, nikoli krok do kódu.

Ladicí program .NET považuje veškerý další kód za uživatelský kód.

Během ladění .NET:

- **Ladit**  >  **Krok dovnitř** (nebo **F11**) v krocích nesouvisejících s uživatelem v kódu na další řádek uživatelského kódu.
- **Ladit**  >  **Krok ven** (nebo **SHIFT** + **F11**) na neuživatelský kód se spustí na další řádek uživatelského kódu.

Pokud není k dispozici více uživatelských kódů, ladění pokračuje, dokud nebude ukončeno, narazí na jinou zarážku nebo vyvolá chybu.

<a name="BKMK_NET_Breakpoint_behavior"></a>Pokud ladicí program se přeruší v kódu, který není uživatelem (například použijete příkaz **Debug**  >  **Break All** a Pause on-user Code), nezobrazí se **žádné zdrojové** okno. Pak můžete pomocí příkazu **ladit**  >  **Krok** přejít na další řádek uživatelského kódu.

Pokud dojde k neošetřené výjimce v neuživatelském kódu, ladicí program se přeruší na řádku uživatelského kódu, kde byla výjimka vygenerována.

Pokud jsou pro výjimku povoleny výjimky první pravděpodobnosti, je volání řádku uživatelského kódu zvýrazněno zeleně ve zdrojovém kódu. V okně **zásobník volání** se zobrazí rámec s poznámkami označený **[externí kód]**.

## <a name="c-just-my-code"></a><a name="BKMK_C___Just_My_Code"></a> Pouze můj kód C++

Počínaje verzí Visual Studio 2017 15,8 je také podporováno Pouze můj kód pro krokování kódu. Tato funkce také vyžaduje použití přepínače kompilátoru [/JMC (pouze ladění kódu)](/cpp/build/reference/jmc) . Přepínač je ve výchozím nastavení povolen v projektech C++. V okně **zásobník volání** a podpora zásobníku volání v pouze můj kód není přepínač/JMC povinný.

<a name="BKMK_CPP_User_and_non_user_code"></a> Aby bylo možné klasifikovat jako uživatelský kód, musí být PDB pro binární soubor obsahující uživatelský kód načten ladicím programem (k jeho kontrole použijte okno **moduly** ).

V případě chování zásobníku volání, například v okně **zásobník volání** , pouze můj kód v jazyce C++ považují pouze tyto funkce za *neuživatelský kód*:

- Funkce s odstraněnými zdrojovými informacemi v souboru symbolů.
- Funkce, kde soubory symbolů označují, že neexistuje zdrojový soubor odpovídající bloku zásobníku.
- Funkce zadané v souborech *\* . natjmc* ve složce *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers*

Pro chování při krokování kódu Pouze můj kód v jazyce C++ považují pouze tyto funkce za kód, který *není uživatelem*:

- Funkce pro které nebyl načten odpovídající soubor PDB do ladicího programu.
- Funkce zadané v souborech *\* . natjmc* ve složce *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers*

> [!NOTE]
> Pro podporu kódu v Pouze můj kód musí být kód C++ kompilován pomocí kompilátorů MSVC v aplikaci Visual Studio 15,8 Preview 3 nebo vyšší a musí být povolen přepínač kompilátoru/JMC (ve výchozím nastavení je povolený). Další podrobnosti najdete v tématech [přizpůsobení zásobníku volání C++ a chování krokování kódu](#BKMK_CPP_Customize_call_stack_behavior)) a tohoto [blogového příspěvku](https://devblogs.microsoft.com/cppblog/announcing-jmc-stepping-in-visual-studio/). Pro kód kompilovaný pomocí staršího kompilátoru jsou soubory *. natstepfilter* jediným způsobem, jak přizpůsobit kód krokování, což je nezávisle na pouze můj kód. Viz [přizpůsobení chování krokování v C++](#BKMK_CPP_Customize_stepping_behavior).

<a name="BKMK_CPP_Stepping_behavior"></a> Během ladění jazyka C++:

- **Ladit**  >  **Krok dovnitř** (nebo **F11**) v krocích nesouvisejících s uživatelem v kódu na další řádek uživatelského kódu.
- **Ladit**  >  **Krok ven** (nebo **SHIFT** + **F11**) na neuživatelský kód se spustí na další řádek uživatelského kódu.

Pokud není k dispozici více uživatelských kódů, ladění pokračuje, dokud nebude ukončeno, narazí na jinou zarážku nebo vyvolá chybu.

Pokud ladicí program se přeruší v kódu, který není uživatelem (například použijete příkaz **Debug**  >  **Break All** a Pause in on-user Code), krokování pokračuje v neuživatelském kódu.

Pokud ladicí program narazí na výjimku, zastaví se na výjimce bez ohledu na to, zda je v uživatelském nebo neuživatelský kód. **Uživatelem neošetřené** možnosti v dialogovém okně **nastavení výjimky** jsou ignorovány.

### <a name="customize-c-call-stack-and-code-stepping-behavior"></a><a name="BKMK_CPP_Customize_call_stack_behavior"></a> Přizpůsobení zásobníku volání C++ a chování krokování kódu

V případě projektů v jazyce C++ lze určit moduly, zdrojové soubory a funkce, které okno **zásobník volání** zpracovává jako neuživatelský kód jejich zadáním do souborů *\* . natjmc* . Toto přizpůsobení se vztahuje také na krokování kódu, pokud používáte nejnovější kompilátor (viz [C++ pouze můj kód](#BKMK_CPP_User_and_non_user_code)).

- Chcete-li určit neuživatelský kód pro všechny uživatele počítače sady Visual Studio, přidejte soubor *. natjmc* do složky *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* .
- Chcete-li určit neuživatelský kód pro jednotlivé uživatele, přidejte soubor *. natjmc* do *dokumentů%USERPROFILE%\My<složce sady \\ Visual Studio verze \> \Visualizers* .

Soubor *. natjmc* je soubor XML s touto syntaxí:

```xml
<?xml version="1.0" encoding="utf-8"?>
<NonUserCode xmlns="http://schemas.microsoft.com/vstudio/debugger/jmc/2015">

  <!-- Modules -->
  <Module Name="ModuleSpec" />
  <Module Name="ModuleSpec" Company="CompanyName" />

  <!-- Files -->
  <File Name="FileSpec"/>

  <!-- Functions -->
  <Function Name="FunctionSpec" />
  <Function Name="FunctionSpec" Module ="ModuleSpec" />
  <Function Name="FunctionSpec" Module ="ModuleSpec" ExceptionImplementation="true" />

</NonUserCode>

```

 **Atributy elementu modulu**

|Atribut|Popis|
|---------------|-----------------|
|`Name`|Povinná hodnota. Úplná cesta modulu nebo modulů. Můžete použít zástupné znaky systému Windows `?` (nula nebo jeden znak) a `*` (nula nebo více znaků). Příklad:<br /><br /> `<Module Name="?:\3rdParty\UtilLibs\*" />`<br /><br /> Říká ladicímu programu, aby považoval všechny moduly v *\3rdParty\UtilLibs* na jakékoli jednotce jako externí kód.|
|`Company`|Nepovinný parametr. Název společnosti, která publikuje modul, který je vložený ve spustitelném souboru. Pomocí tohoto atributu lze odstranit nejednoznačnost modulů.|

 **Atributy elementu souboru**

|Atribut|Popis|
|---------------|-----------------|
|`Name`|Povinná hodnota. Úplná cesta ke zdrojovému souboru nebo souborům, které mají být považovány za externí kód. Můžete použít zástupné znaky systému Windows `?` a `*` zadat cestu.|

 **Atributy elementu funkce**

|Atribut|Popis|
|---------------|-----------------|
|`Name`|Povinná hodnota. Plně kvalifikovaný název funkce, která má být považována za externí kód.|
|`Module`|Nepovinný parametr. Název nebo úplná cesta k modulu, který obsahuje funkci. Tento atribut lze použít k nejednoznačnosti funkcí se stejným názvem.|
|`ExceptionImplementation`|Když je nastavena na `true` , zásobník volání zobrazí funkci, která výjimku vyvolala místo této funkce.|

### <a name="customize-c-stepping-behavior-independent-of-just-my-code-settings"></a><a name="BKMK_CPP_Customize_stepping_behavior"></a> Přizpůsobení chování krokování C++ nezávisle na nastavení Pouze můj kód

V projektech v jazyce C++ můžete zadat funkce pro krokování jejich uvedením jako neuživatelský kód v souborech *\* . natstepfilter* . Funkce uvedené v souborech *\* . natstepfilter* nejsou závislé na nastavení pouze můj kód.

- Chcete-li určit neuživatelský kód pro všechny místní uživatele sady Visual Studio, přidejte soubor *. natstepfilter* do složky *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* .
- Chcete-li určit neuživatelský kód pro jednotlivé uživatele, přidejte soubor *. natstepfilter* do *dokumentů%USERPROFILE%\My<složce sady \\ Visual Studio verze \> \Visualizers* .

Soubor *. natstepfilter* je soubor XML s touto syntaxí:

```xml
<?xml version="1.0" encoding="utf-8"?>
<StepFilter xmlns="http://schemas.microsoft.com/vstudio/debugger/natstepfilter/2010">
    <Function>
        <Name>FunctionSpec</Name>
        <Action>StepAction</Action>
    </Function>
    <Function>
        <Name>FunctionSpec</Name>
        <Module>ModuleSpec</Module>
        <Action>StepAction</Action>
    </Function>
</StepFilter>

```

|Element|Popis|
|-------------|-----------------|
|`Function`|Povinná hodnota. Určuje jednu nebo více funkcí jako neuživatelské funkce.|
|`Name`|Povinná hodnota. Formátovaný regulární výraz ECMA-262 určující úplný název funkce, který se má shodovat. Například:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> oznamuje ladicímu programu, že všechny metody v `MyNS::MyClass` mají být považovány za neuživatelský kód. Porovnávání rozlišuje velká a malá písmena.|
|`Module`|Nepovinný parametr. Formátovaný regulární výraz ECMA-262 určující úplnou cestu k modulu, který obsahuje funkci. U porovnávání se nerozlišují malá a velká písmena.|
|`Action`|Povinná hodnota. Jedna z těchto hodnot citlivých na velká a malá písmena:<br /><br /> `NoStepInto`  – instruuje ladicí program, aby převzal funkci.<br /> `StepInto`  – instruuje ladicí program, aby se přepsal do funkce a přepsaly se jiné `NoStepInto` pro odpovídající funkci.|

## <a name="javascript-just-my-code"></a><a name="BKMK_JavaScript_Just_My_Code"></a> Pouze můj kód JavaScriptu

<a name="BKMK_JS_User_and_non_user_code"></a> JavaScript Pouze můj kód řídí krokování a zobrazování zásobníku volání pomocí kategorizace kódu v jedné z těchto klasifikací:

|Klasifikace|Popis|
|-|-|
|**MyCode**|Uživatelský kód, který vlastníte a ovládáte.|
|**LibraryCode**|Neuživatelský kód z knihoven, které často používáte, a vaše aplikace spoléhá na správné fungování (například WinJS nebo jQuery).|
|**UnrelatedCode**|Neuživatelský kód v aplikaci, který nevlastníte, a vaše aplikace nespoléhá na správné fungování. Například reklamní sada SDK, která zobrazuje reklamy, by mohla být UnrelatedCode. V projektech UWP se jako UnrelatedCode považuje také jakýkoli kód, který je načten do vaší aplikace z identifikátoru URI protokolu HTTP nebo HTTPS.|

Ladicí program JavaScriptu klasifikuje kód jako uživatele nebo neuživatel v tomto pořadí:

1. Výchozí klasifikace.
   - Skript spuštěný předáním řetězce do funkce poskytnuté hostitelem `eval` je **myCode**.
   - Skript spuštěný předáním řetězce do `Function` konstruktoru je **LibraryCode**.
   - Skript v odkazu na rozhraní, jako je WinJS nebo Azure SDK, je **LibraryCode**.
   - Skript spuštěný předáním řetězce do `setTimeout` , `setImmediate` nebo `setInterval` funkce je **UnrelatedCode**.

2. Klasifikace zadané pro všechny projekty JavaScriptu sady Visual Studio v souboru *% VSInstallDirectory% \JavaScript\JustMyCode\mycode.default.wwa.js* .

3. Klasifikace v *mycode.jsv* souboru aktuálního projektu.

Každý krok klasifikace přepíše předchozí kroky.

Všechny ostatní kódy jsou klasifikovány jako **myCode**.

Můžete upravit výchozí klasifikace a klasifikovat konkrétní soubory a adresy URL jako uživatel nebo neuživatelský kód přidáním souboru *. JSON* s názvem *mycode.js* do kořenové složky projektu JavaScriptu. Viz [přizpůsobení pouze můj kód JavaScriptu](#BKMK_JS_Customize_Just_My_Code).

<a name="BKMK_JS_Stepping_behavior"></a> Během ladění JavaScriptu:

- Pokud je funkce neuživatelský kód, krok **ladění**  >   (nebo klávesa **F11**) se chová stejně jako krok **ladění**  >   (nebo **F10**).
- Pokud krok začíná v kódu, který není uživatel (**LibraryCode** nebo **UnrelatedCode**), krok se dočasně chová, jako by pouze můj kód není povolená. Až se vrátíte k uživatelskému kódu, Pouze můj kód krokování se znovu povolí.
- Když krok uživatelského kódu vede k ukončení aktuálního kontextu spuštění, ladicí program se zastaví na následujícím řádku kódu spouštěného uživatelem. Například pokud se zpětné volání provede v kódu **LibraryCode** , ladicí program pokračuje, dokud se nespustí další řádek uživatelského kódu.
- **Krok ven** (nebo **SHIFT** + **F11**) se zastaví na dalším řádku uživatelského kódu.

Pokud není k dispozici více uživatelských kódů, ladění pokračuje, dokud nebude ukončeno, narazí na jinou zarážku nebo vyvolá chybu.

Zarážky nastavené v kódu jsou vždycky stejné, ale kód je klasifikovaný.

- Pokud se `debugger` klíčové slovo vyskytuje v **LibraryCode**, ladicí program se vždy přeruší.
- Pokud se `debugger` klíčové slovo vyskytuje v **UnrelatedCode**, ladicí program se nezastaví.

<a name="BKMK_JS_Exception_behavior"></a> Pokud dojde k neošetřené výjimce v kódu **myCode** nebo **LibraryCode** , ladicí program se vždy přeruší.

Pokud v **UnrelatedCode** dojde k neošetřené výjimce a v zásobníku volání je **myCode** nebo **LibraryCode** , ladicí program se přeruší.

Pokud jsou pro výjimku povoleny výjimky s první pravděpodobností a k výjimce dojde v **LibraryCode** nebo **UnrelatedCode**:

- Pokud je výjimka zpracována, ladicí program nebude přerušen.
- Pokud výjimka není zpracována, ladicí program se přeruší.

### <a name="customize-javascript-just-my-code"></a><a name="BKMK_JS_Customize_Just_My_Code"></a> Přizpůsobení Pouze můj kód JavaScriptu

Pro kategorizaci uživatelského a neuživatelského kódu pro jeden projekt JavaScriptu můžete přidat soubor *. JSON* s názvem *mycode.js* do kořenové složky projektu.

Specifikace v tomto souboru přepisují výchozí klasifikace a *mycode.default.wwa.jsv* souboru. *mycode.jsv* souboru nemusí vypisovat všechny páry klíč-hodnota. **MyCode**, **knihovny** a **nesouvisející** hodnoty mohou být prázdná pole.

*Mycode.js* soubory používají tuto syntaxi:

```json
{
    "Eval" : "Classification",
    "Function" : "Classification",
    "ScriptBlock" : "Classification",
    "MyCode" : [
        "UrlOrFileSpec",
        . . .
        "UrlOrFileSpec"
    ],
    "Libraries" : [
        "UrlOrFileSpec",
        . .
        "UrlOrFileSpec"
    ],
    "Unrelated" : [
        "UrlOrFileSpec",
        . . .
        "UrlOrFileSpec"
    ]
}

```

**Eval, Function a ScriptBlock**

Páry hodnot klíčů **Eval**, **Function** a **ScriptBlock** určují způsob klasifikace dynamicky generovaného kódu:

|Název|Popis|
|-|-|
|**Eval**|Skript, který je spuštěn předáním řetězce do funkce poskytnuté hostitelem `eval` . Ve výchozím nastavení je skript Eval klasifikován jako **myCode**.|
|**Funkce**|Skript, který je spuštěn předáním řetězce `Function` konstruktoru. Ve výchozím nastavení je skript funkcí klasifikován jako **LibraryCode**.|
|**ScriptBlock**|Skript, který je spuštěn předáním řetězce do `setTimeout` funkce, `setImmediate` nebo `setInterval` . Ve výchozím nastavení je skript ScriptBlock klasifikován jako **UnrelatedCode**.|

Můžete změnit hodnotu na jedno z těchto klíčových slov:

- `MyCode` klasifikuje skript jako **myCode**.
- `Library` klasifikuje skript jako **LibraryCode**.
- `Unrelated` klasifikuje skript jako **UnrelatedCode**.

**MyCode, knihovny a nesouvisející**

Páry klíč-hodnota **myCode**, **knihovny** a **nesouvisející** hodnoty klíčů určují adresy URL nebo soubory, které chcete zahrnout do klasifikace:

|Název|Popis|
|-|-|
|**MyCode**|Pole adres URL nebo souborů, které jsou klasifikovány jako **myCode**.|
|**Knihovny**|Pole adres URL nebo souborů, které jsou klasifikovány jako **LibraryCode**.|
|**Nesouvisející**|Pole adres URL nebo souborů, které jsou klasifikovány jako **UnrelatedCode**.|

Adresa URL nebo řetězec souboru může obsahovat jeden nebo více `*` znaků, které se shodují s žádným nebo více znaky. `*` je stejný jako regulární výraz `.*` .
