---
title: Pouze můj kód | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 62da3a36a34a2111bb139765268fbb0bef9b500d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85531921"
---
# <a name="just-my-code"></a>Pouze můj kód
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vývojáři, kteří používají .NET Framework jazyky, jsou obeznámeni s funkcí Pouze můj kód ladicího programu, která provádí kroky nad systémem, rozhraním a jinými neuživatelskými voláními a sbalí tato volání v oknech zásobník volání. Pouze můj kód bylo rozšířeno na jazyky jazyka C++ a jazyka JavaScript. Toto téma popisuje konkrétní použití Pouze můj kód v projektech .NET Framework, nativních C++ a JavaScript.  
  
## <a name="enable-or-disable-just-my-code"></a><a name="BKMK_Enable_or_disable_Just_My_Code"></a> Povolit nebo zakázat Pouze můj kód  
 Pokud chcete povolit nebo zakázat Pouze můj kód, vyberte **Možnosti a nastavení** v nabídce **ladění** . V uzlu **ladění**  /  **obecně** vyberte nebo zrušte zaškrtnutí **Povolit pouze můj kód**.  
  
 ![Povolení Pouze můj kód v dialogovém okně Možnosti](../debugger/media/dbg-justmycode-options.png "DBG_JustMyCode_Options")  
  
> [!NOTE]
> Nastavení **povolit pouze můj kód** je globální nastavení, které se použije pro všechny projekty sady Visual Studio ve všech jazycích.  
  
### <a name="override-call-stack-filtering"></a><a name="BKMK_Override_call_stack_filtering"></a> Přepsat filtrování zásobníku volání  
 V zobrazení zásobníku volání, například v oknech zásobník volání a úkoly, Pouze můj kód sbalí neuživatelský kód do označeného popisku s poznámkou `[External Code]` . Chcete-li zobrazit sbalené snímky, v místní nabídce zobrazení zásobníku volání vyberte možnost **Zobrazit externí kód** .  
  
> [!NOTE]
> Nastavení **Zobrazit externí kód** je uloženo v profileru aktuálního uživatele. Používá se pro všechny projekty ve všech jazycích, které uživatel otevřel.  
  
## <a name="net-framework-just-my-code"></a><a name="BKMK__NET_Framework_Just_My_Code"></a> .NET Framework Pouze můj kód  
  
### <a name="user-and-non-user-code"></a><a name="BKMK_NET_User_and_non_user_code"></a> Uživatel a jiný kód než uživatel  
 Pro odlišení uživatelského kódu od neuživatelového kódu Pouze můj kód prohlíží soubory symbolů (PDB) a optimalizace programů. Ladicí program považuje kód za neuživatelský kód v případě, že je binární soubor optimalizovaný nebo pokud není k dispozici soubor. pdb.  
  
 Tři atributy ovlivňují také to, co ladicí program považuje za můj kód:  
  
- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> oznamuje ladicímu programu, že kód, na který je použit, není můj kód.  
  
- <xref:System.Diagnostics.DebuggerHiddenAttribute> skryje kód z ladicího programu, a to i v případě, že je vypnutý Pouze můj kód.  
  
- <xref:System.Diagnostics.DebuggerStepThroughAttribute> instruuje ladicí program, aby provedl kód, na který je použit, a ne krok do kódu.  
  
  Veškerý další kód je považován za uživatelský kód.  
  
### <a name="stepping-behavior"></a><a name="BKMK_NET_Stepping_behavior"></a> Chování krokování  
 Při **krokování do** (Klávesová zkratka: F11) neuživatelský kód, ladicí program přesměruje kód na další příkaz uživatele. Při **krokování** (klávesnice: Shift + F11) se ladicí program spustí na další řádek uživatelského kódu. Pokud nedojde k žádnému kódu uživatele, provádění pokračuje, dokud se aplikace neukončí, zarážka je obsazena nebo dojde k výjimce.  
  
### <a name="breakpoint-behavior"></a><a name="BKMK_NET_Breakpoint_behavior"></a> Chování zarážky  
 Pokud je povolená Pouze můj kód, můžete zvolit možnost **přerušit vše** (klávesnice: CTRL + ALT + BREAK) a zastavit provádění na místě, kde není k dispozici žádný uživatelský kód k zobrazení. Pokud k tomu dojde, nezobrazí se žádné okno zdroje. Pokud pak zvolíte příkaz kroku, ladicí program přejde na další řádek uživatelského kódu.  
  
### <a name="exception-behavior"></a><a name="BKMK_NET_Exception_behavior"></a> Chování výjimky  
 Pokud dojde k neošetřené výjimce v neuživatelském kódu, ladicí program se přeruší na řádku v uživatelském kódu, kde byla výjimka vygenerována.  
  
 Pokud jsou pro výjimku povoleny výjimky první, je řádek uživatelského kódu zvýrazněn zeleně. Zásobník volání zobrazuje rámec s poznámkou označený **[externí kód]**.  
  
## <a name="c-just-my-code"></a><a name="BKMK_C___Just_My_Code"></a> Pouze můj kód C++  
  
### <a name="user-and-non-user-code"></a><a name="BKMK_CPP_User_and_non_user_code"></a> Uživatel a jiný kód než uživatel  
 Pouze můj kód jazyka C++ se liší od Pouze můj kód .NET Framework a JavaScriptu, protože chování funkce krokování je nezávislé na chování zásobníku volání.  
  
 **Zásobníky volání**  
  
 Ve výchozím nastavení ladicí program považuje tyto funkce za neuživatelský kód v oknech zásobník volání:  
  
- Funkce s odstraněnými zdrojovými informacemi v souboru symbolů.  
  
- Funkce, kde soubory symbolů označují, že neexistuje zdrojový soubor odpovídající bloku zásobníku.  
  
- Funkce zadané v `*.natjmc` souborech ve `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` složce  
  
  **Pokusný**  
  
  Ve výchozím nastavení jsou pouze funkce, které jsou zadány v `*.natstepfilter` souborech ve `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` složce, považovány za neuživatelský kód.  
  
  Můžete vytvořit vlastní `.natstepfilter` a `.natjmc` přizpůsobit chování okna krokování a zásobníku volání v `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` .  
  
### <a name="stepping-behavior"></a><a name="BKMK_CPP_Stepping_behavior"></a> Chování krokování  
 Při **krokování do** (Klávesová zkratka: F11) neuživatelský kód z uživatelského kódu, ladicí program přesměruje kód na další řádek uživatelského kódu. Při **krokování** (klávesnice: Shift + F11) se ladicí program spustí na další řádek uživatelského kódu. Pokud nedojde k žádnému kódu uživatele, provádění pokračuje, dokud se aplikace neukončí, zarážka je obsazena nebo dojde k výjimce.  
  
 Pokud ladicí program se přeruší v neuživatelském kódu (například v případě, že se příkaz break All zastaví v neuživatelském kódu), krokování pokračuje v neuživatelském kódu.  
  
### <a name="exception-behavior"></a><a name="BKMK_CPP_Exception_behavior"></a> Chování výjimky  
 Pokud ladicí program narazí na výjimku, zastaví se na výjimce bez ohledu na to, zda se jedná o uživatele nebo jiný kód než uživatel. **Uživatelem neošetřené** možnosti v dialogovém okně **výjimky** jsou ignorovány.  
  
### <a name="customize-stepping-behavior"></a><a name="BKMK_CPP_Customize_stepping_behavior"></a> Přizpůsobení chování krokování  
 Můžete určit funkce, které se mají krokovat, jejich uvedením jako neuživatelský kód v `*.natstepfilter` souborech.  
  
- Chcete-li určit neuživatelský kód pro všechny uživatele počítače sady Visual Studio, přidejte soubor. natstepfilter do `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` složky.  
  
- Chcete-li určit neuživatelský kód pro jednotlivé uživatele, přidejte soubor. natstepfilter do `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` složky.  
  
  soubory. natstepfilter jsou soubory XML s touto syntaxí:  
  
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
|Funkce|Povinná hodnota. Určuje jednu nebo více funkcí jako neuživatelské funkce.|  
|`Name`|Povinná hodnota. Formátovaný regulární výraz ECMA-262 určující úplný název funkce, který se má shodovat. Příklad:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> oznamuje ladicímu programu, že všechny metody v `MyNS::MyClass` mají být považovány za neuživatelský kód. Porovnávání rozlišuje velká a malá písmena.|  
|`Module`|Nepovinný parametr. Formátovaný regulární výraz ECMA-262 určující úplnou cestu k modulu, který obsahuje funkci. U porovnávání se nerozlišují malá a velká písmena.|  
|`Action`|Povinná hodnota. Jedna z těchto hodnot citlivých na velká a malá písmena:<br /><br /> -   `NoStepInto`  – instruuje ladicí program, aby se převzal přes odpovídající funkci.<br />-   `StepInto`  – instruuje ladicí program, aby se přihlásil k odpovídajícím funkcím, které potlačuje jiné `NoStepInto` pro odpovídající funkce.|  
  
### <a name="customize-call-stack-behavior"></a><a name="BKMK_CPP_Customize_call_stack_behavior"></a> Přizpůsobení chování zásobníku volání  
 Můžete určit moduly, zdrojové soubory a funkce, které se považují za neuživatelský kód v zásobníkech volání zadáním do `*.natjmc` souborů.  
  
- Chcete-li určit neuživatelský kód pro všechny uživatele počítače sady Visual Studio, přidejte soubor. natjmc do `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` složky.  
  
- Chcete-li určit neuživatelský kód pro jednotlivé uživatele, přidejte soubor. natjmc do `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` složky.  
  
  soubory. natjmc jsou soubory XML s touto syntaxí:  
  
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
|`Name`|Povinná hodnota. Úplná cesta modulu nebo modulů. Můžete použít zástupné znaky systému Windows `?` (nula nebo jeden znak) a `*` (nula nebo více znaků). Příklad:<br /><br /> `<Module Name=”?:\3rdParty\UtilLibs\*” />`<br /><br /> Říká ladicímu programu, aby považoval všechny moduly na `\3rdParty\UtilLibs` jakékoli jednotce jako externí kód.|  
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
  
## <a name="javascript-just-my-code"></a><a name="BKMK_JavaScript_Just_My_Code"></a> Pouze můj kód JavaScriptu  
  
### <a name="user-and-non-user-code"></a><a name="BKMK_JS_User_and_non_user_code"></a> Uživatel a jiný kód než uživatel  
 **Klasifikace kódu**  
  
 JavaScript Pouze můj kód řídí krokování a zobrazování zásobníku volání pomocí kategorizace kódu v jedné z těchto klasifikací:  
  
|Název|Popis|
|-|-|  
|**MyCode**|Uživatelský kód, který vlastníte a ovládáte.|  
|**LibraryCode**|Neuživatelský kód z knihoven, které často používáte, a vaše aplikace spoléhá na správnou funkci (například WinJS nebo jQuery).|  
|**UnrelatedCode**|Neuživatelský kód, který může být spuštěný v aplikaci, ale nevlastníte, a vaše aplikace přímo nespoléhá na správnou funkci (například reklamní sada SDK, která zobrazuje reklamy). V projektech Windows Store se také za UnrelatedCode považuje jakýkoliv kód, který je načten do vaší aplikace z identifikátoru URI protokolu HTTP nebo HTTPS.|  
  
 Ladicí program JavaScriptu automaticky klasifikuje tyto typy kódu:  
  
- Skript, který je spuštěn předáním řetězce do funkce poskytnuté hostitelem, `eval` je klasifikován jako **myCode**.  
  
- Skript, který je spuštěn předáním řetězce konstruktoru, `Function` je klasifikován jako **LibraryCode**.  
  
- Skript obsažený v odkazu na rozhraní, jako je WinJS nebo Azure SDK, je klasifikován jako **LibraryCode**.  
  
- Skript, který je spuštěn předáním řetězce do `setTimeout` , `setImmediate` nebo, `setInterval` jsou klasifikovány jako **UnrelatedCode**.  
  
- `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json`Určuje jiný uživatel a neuživatelský kód pro všechny projekty jazyka JavaScript v aplikaci Visual Studio.  
  
  Můžete upravit výchozí klasifikace a klasifikovat konkrétní soubory a adresy URL přidáním souboru. JSON s názvem `mycode.json` do kořenové složky projektu.  
  
  Všechny ostatní kódy jsou klasifikovány jako **myCode**.  
  
### <a name="stepping-behavior"></a><a name="BKMK_JS_Stepping_behavior"></a> Chování krokování  
  
- Pokud funkce není uživatelem (**myCode**) kód, **Krok do** (Klávesová zkratka: F11) se chová jako **krok za krokem** (klávesnice: F10).  
  
- Pokud krok začíná v kódu, který není uživatel (**LibraryCode** nebo **UnrelatedCode**), krok se dočasně chová, jako by pouze můj kód není povolený. Jakmile se vrátíte k uživatelskému kódu, Pouze můj kód krokování se znovu povolí.  
  
- Když krok ve výsledku uživatelského kódu opustí aktuální kontext spuštění (například krok na posledním řádku obslužné rutiny události), ladicí program se zastaví na dalším spuštěném řádku uživatelského kódu. Například pokud se zpětné volání provede v kódu **LibraryCode** , ladicí program pokračuje, dokud se nespustí další řádek uživatelského kódu.  
  
- **Krok ven** (klávesnice: Shift + F11) zastaví na dalším řádku uživatelského kódu. Pokud nedojde k žádnému kódu uživatele, provádění pokračuje, dokud se aplikace neukončí, zarážka je obsazena nebo dojde k výjimce.  
  
### <a name="breakpoint-behavior"></a><a name="BKMK_JS_Breakpoint_behavior"></a> Chování zarážky  
  
- Zarážky, které byly nastaveny v jakémkoli kódu, budou vždy zasaženy bez ohledu na klasifikaci tohoto kódu.  
  
- Pokud se `debugger` klíčové slovo objevilo v:  
  
  - **LibraryCode** kód, ladicí program se vždycky přeruší.  

  - **UnrelatedCode** kód, ladicí program se nezastaví.  
  
### <a name="exception-behavior"></a><a name="BKMK_JS_Exception_behavior"></a> Chování výjimky  
 Pokud dojde k neošetřené výjimce v:  
  
- Kód **myCode** nebo **LibraryCode** , ladicí program se vždy přeruší.  
  
- Kód **UnrelatedCode** a kód **myCode** nebo **LibraryCode** jsou v zásobníku volání, ladicí program se přeruší.  
  
  Pokud jsou pro výjimku v dialogovém okně výjimky povoleny první výjimky a výjimka je vyvolána v kódu **LibraryCode** nebo **UnrelatedCode** :  
  
- Pokud je výjimka zpracována, ladicí program nebude přerušen.  
  
- Pokud výjimka není zpracována, ladicí program se přeruší.  
  
### <a name="customize-just-my-code"></a><a name="BKMK_JS_Customize_Just_My_Code"></a> Přizpůsobení Pouze můj kód  
 Chcete-li zařadit do kategorií uživatelský a neuživatelský kód pro jeden projekt sady Visual Studio, přidejte soubor. JSON s názvem `mycode.json` do kořenové složky projektu.  
  
 Klasifikace se provádějí v tomto pořadí:  
  
1. Výchozí klasifikace  
  
2. Klasifikace v `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` souboru  
  
3. Klasifikace v `mycode. json` souboru aktuálního projektu.  
  
   Každý krok klasifikace přepíše předchozí kroky. Soubor. JSON není nutné vypsat všechny páry klíč-hodnota a **myCode**, **knihovny**a **nesouvisející** hodnoty můžou být prázdná pole.  
  
   Moje soubory Code. JSON používají tuto syntaxi:  
  
```json  
{  
    "Eval" : "Classification",  
    "Function" : "Classification",  
    "ScriptBlock" : "Classification",  
    "MyCode" : [  
        "UrlOrFileSpec”,  
        . . .  
        "UrlOrFileSpec”  
    ],  
    "Libraries" : [  
        "UrlOrFileSpec”,  
        . .  
        "UrlOrFileSpec”  
    ],  
    "Unrelated" : [  
        "UrlOrFileSpec”,  
        . . .  
        "UrlOrFileSpec”  
    ]  
}  
  
```  
  
 **Eval, Function a ScriptBlock**  
  
 Páry hodnot klíčů **Eval**, **Function**a **ScriptBlock** určují způsob klasifikovaného dynamicky generovaného kódu.  
  
|Název|Popis|
|-|-|  
|**Eval**|Skript, který je spuštěn předáním řetězce do funkce poskytnuté hostitelem `eval` . Ve výchozím nastavení je skript Eval klasifikován jako **myCode**.|  
|**Funkce**|Skript, který je spuštěn předáním řetězce `Function` konstruktoru. Ve výchozím nastavení je skript funkcí klasifikován jako **LibraryCode**.|  
|**ScriptBlock**|Skript, který je spuštěn předáním řetězce do `setTimeout` funkce, `setImmediate` nebo `setInterval` . Ve výchozím nastavení je skript ScriptBlock klasifikován jako **UnrelatedCode**.|  
  
 Můžete změnit hodnotu na jedno z těchto klíčových slov:  
  
- `MyCode`  klasifikuje skript jako **myCode**.  
  
- `Library`  klasifikuje skript jako **LibraryCode**.  
  
- `Unrelated`  klasifikuje skript jako **UnrelatedCode**.  
  
  **MyCode, knihovny a nesouvisející**  
  
  Páry klíč-hodnota **myCode**, **knihovny**a **nesouvisející** hodnoty klíčů určují adresy URL nebo soubory, které chcete zahrnout do klasifikace:  
  
|Název|Popis|
|-|-|  
|**MyCode**|Pole adres URL nebo souborů, které jsou klasifikovány jako **myCode**.|  
|**Knihovny**|Pole adres URL nebo souborů, které jsou klasifikovány jako **LibraryCode**.|  
|**Nesouvisející**|Pole adres URL nebo souborů, které jsou klasifikovány jako **UnrelatedCode**.|  
  
 Adresa URL nebo řetězec souboru může obsahovat jeden nebo více `*` znaků, které neodpovídají žádnému nebo více znakům. `*` je ekvivalentem regulárního výrazu `.*` .
