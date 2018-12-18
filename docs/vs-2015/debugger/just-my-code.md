---
title: Pouze můj kód | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b016c8565b3c501c5cc41802512f02b1c10d615
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51798638"
---
# <a name="just-my-code"></a>Pouze můj kód
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vývojáři, kteří používají jazycích rozhraní .NET Framework obeznámeni s jen můj kód, ladicí program funkce kroky systému a rozhraní framework a další neuživatelská volání, která sbalí ty volání v ovládacím prvku windows zásobníku volání. Funkce pouze můj kód rozšířilo a jazyce C++ a JavaScript. Toto téma popisuje, jaké jsou specifikace pomocí volbu pouze vlastní kód v rozhraní .NET Framework, nativní C++ a JavaScript projekty.  
  
##  <a name="BKMK_Enable_or_disable_Just_My_Code"></a> Povolit nebo zakázat pouze můj kód  
 Chcete-li povolit nebo zakázat pouze můj kód, zvolte **možnosti a nastavení** na **ladění** nabídky. V **ladění** / **Obecné** uzlu, vyberte nebo zrušte zaškrtnutí **povolit volbu pouze vlastní kód**.  
  
 ![Povolit volbu pouze vlastní kód v dialogovém okně Možnosti](../debugger/media/dbg-justmycode-options.png "DBG_JustMyCode_Options")  
  
> [!NOTE]
>  **Povolit volbu pouze vlastní kód** nastavení je globální nastavení, které platí pro všechny projekty aplikace Visual Studio ve všech jazycích.  
  
###  <a name="BKMK_Override_call_stack_filtering"></a> Přepsat filtrování zásobníku volání  
 V zobrazení zásobníku volání, jako jsou okna zásobník volání a úlohy funkce pouze můj kód sbalí neuživatelský kód do rámce s poznámkami s popiskem `[External Code]`. Chcete-li zobrazit sbalený rámce, zvolte **zobrazit externí kód** v místní nabídce zásobníku volání zobrazit.  
  
> [!NOTE]
>  **Zobrazit externí kód** nastavení je uložit do aktuálního uživatele profileru. Použije se na všechny projekty ve všech jazycích, které jsou otevřeny uživatelem.  
  
##  <a name="BKMK__NET_Framework_Just_My_Code"></a> Rozhraní .NET framework pouze můj kód  
  
###  <a name="BKMK_NET_User_and_non_user_code"></a> Uživatel a neuživatelský kód  
 Funkce pouze můj kód zjistí k rozlišení uživatelský kód z kódu nepocházejícího od uživatele, soubory symbolů (PDB) a optimalizace programu. Ladicí program bude považovat za kód je kód nepocházející od uživatele při optimalizaci binární soubor, nebo když není k dispozici soubor .pdb.  
  
 Ladicí program považuje na můj kód ovlivňují také tři atributy:  
  
- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> dává pokyn ladicímu programu, že kód, který se použije k není můj kód.  
  
- <xref:System.Diagnostics.DebuggerHiddenAttribute> Skryje kód z ladicího programu, i v případě, že funkce pouze můj kód je vypnutý.  
  
- <xref:System.Diagnostics.DebuggerStepThroughAttribute> sdělí ladicímu programu, chcete-li si kód, který se použije, místo krokování s vnořením do kódu.  
  
  Veškerý kód, se považuje za uživatelského kódu.  
  
###  <a name="BKMK_NET_Stepping_behavior"></a> Chování  
 Když je **Krokovat s vnořením** (Klávesová zkratka: F11) neuživatelský kód, ladicí program přes kód do dalšího příkazu uživatele. Pokud jste **Krokovat s Vystoupením** (klávesnice: Shift + F11), ladicí program se spustí na další řádek kódu uživatele. Pokud nebude nalezen žádný uživatelský kód, provádění pokračuje, dokud aplikace ukončí, dosaženo zarážky nebo dojde k výjimce.  
  
###  <a name="BKMK_NET_Breakpoint_behavior"></a> Chování zarážky  
 Pokud je povolena funkce pouze můj kód, můžete použít **příkaz Pozastavit vše** (klávesnice: Ctrl + Alt + Break) a zastavit provádění v místě, kde neexistuje žádný uživatelský kód pro zobrazení. Pokud k tomu dojde, zobrazí se okno žádný zdroj. Pokud vyberte příkaz kroku ladicí program přejde na další řádek kódu uživatele.  
  
###  <a name="BKMK_NET_Exception_behavior"></a> Výjimka chování  
 Pokud dojde k neošetřené výjimce v neuživatelském kódu, ladicí program přeruší na řádku v uživatelském kódu, ve kterém se vygeneroval výjimku.  
  
 Pokud první příležitosti výjimky jsou povolené pro výjimku, řádku uživatelského kódu je zvýrazněn zeleně. Zásobník volání se zobrazí rámce s poznámkami s popiskem **[externí kód]**.  
  
##  <a name="BKMK_C___Just_My_Code"></a> Pouze můj kód C++  
  
###  <a name="BKMK_CPP_User_and_non_user_code"></a> Uživatel a neuživatelský kód  
 Funkce pouze můj kód C++ se liší od rozhraní .NET Framework a jazyka JavaScript pouze můj kód, protože nezávisí chování chování zásobníku volání.  
  
 **Zásobníky volání**  
  
 Ve výchozím nastavení ladicí program bude považovat za tyto funkce bude neuživatelský kód v zásobníku volání systému windows:  
  
- Funkce s odstraněnými příslušnými daty zdroj informací v jejich soubor symbolů.  
  
- Funkce, kde soubory symbolů znamenat, že neexistuje žádný zdrojový soubor odpovídá rámce zásobníku.  
  
- Funkcí zadaných v `*.natjmc` soubory `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` složky.  
  
  **Krokování**  
  
  Ve výchozím nastavení, podle pouze funkce `*.natstepfilter` soubory `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` složky jsou považovány za neuživatelský kód.  
  
  Můžete vytvořit svoje vlastní `.natstepfilter` a `.natjmc` přizpůsobit posílení a chování okna zásobník volání `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers`.  
  
###  <a name="BKMK_CPP_Stepping_behavior"></a> Chování  
 Když je **Krokovat s vnořením** (Klávesová zkratka: F11) neuživatelský kód z uživatelského kódu, ladicí program při krokování kódu na další řádek kódu uživatele. Pokud jste **Krokovat s Vystoupením** (klávesnice: Shift + F11), ladicí program se spustí na další řádek kódu uživatele. Pokud nebude nalezen žádný uživatelský kód, provádění pokračuje, dokud aplikace ukončí, dosaženo zarážky nebo dojde k výjimce.  
  
 Pokud ladicí program přeruší v neuživatelském kódu (například, pokud příkaz Pozastavit vše zastaví v neuživatelském kódu), krokování pokračuje v neuživatelském kódu.  
  
###  <a name="BKMK_CPP_Exception_behavior"></a> Výjimka chování  
 Pokud ladicí program narazí na výjimku, se zastaví na výjimce bez ohledu na to, jestli má uživatel nebo neuživatelský kód. **Uživatelem neošetřené** možnosti **výjimky** dialogové okno se ignorují.  
  
###  <a name="BKMK_CPP_Customize_stepping_behavior"></a> Přizpůsobení chování  
 Můžete zadat funkce převezme seznam jako neuživatelský kód v kroku `*.natstepfilter` soubory.  
  
- Zadat neuživatelský kód pro všechny uživatele počítače Visual Studio, přidejte soubor .natstepfilter `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` složky.  
  
- Zadat neuživatelském kódu pro jednotlivé uživatele, přidejte soubor .natstepfilter `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` složky.  
  
  .natstepfilter soubory jsou soubory xml touto syntaxí:  
  
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
  
|Prvek|Popis|  
|-------------|-----------------|  
|Funkce|Požadováno. Určuje jednu nebo více funkcí jako funkcí nedefinovaných uživatelem.|  
|`Name`|Požadováno. ECMA 262 ve formátu regulárních výrazů zadáním názvu plná funkčnost tak, aby odpovídaly. Příklad:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> sdělí ladicímu programu, že všechny metody v `MyNS::MyClass` mají být považovány za neuživatelský kód. Shoda rozlišuje velká a malá písmena.|  
|`Module`|Volitelné. ECMA 262 ve formátu regulárních výrazů zadáním úplná cesta k modulu, který obsahuje funkci. Shoda nerozlišuje malá a velká písmena.|  
|`Action`|Požadováno. Jedna z těchto hodnot malá a velká písmena:<br /><br /> -   `NoStepInto`  – sdělí ladicímu programu, aby přešel přes odpovídající funkce.<br />-   `StepInto`  – dává pokyn ladicímu programu vstup do funkce odpovídající přepsání jiného `NoStepInto` pro odpovídající funkce.|  
  
###  <a name="BKMK_CPP_Customize_call_stack_behavior"></a> Přizpůsobení chování zásobníku volání  
 Můžete zadat moduly, zdrojové soubory a funkce považovat za neuživatelský kód v zásobnících volání zadáním v `*.natjmc` soubory.  
  
- Zadat neuživatelský kód pro všechny uživatele počítače Visual Studio, přidejte soubor .natjmc `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` složky.  
  
- Zadat neuživatelském kódu pro jednotlivé uživatele, přidejte soubor .natjmc `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` složky.  
  
  .natjmc soubory jsou soubory xml touto syntaxí:  
  
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
  
 **Atributy modulu**  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Name`|Požadováno. Úplná cesta modulu nebo modulech. Můžete použít zástupné znaky Windows `?` (žádný nebo jeden znak) a `*` (nula nebo více znaků). Například<br /><br /> `<Module Name=”?:\3rdParty\UtilLibs\*” />`<br /><br /> sdělí ladicímu programu, aby považoval všechny moduly v `\3rdParty\UtilLibs` v jakékoli jednotce jako externí kód.|  
|`Company`|Volitelné. Název společnosti, která publikuje modul, který je vložen do spustitelného souboru. Tento atribut slouží k rozlišení moduly.|  
  
 **Atributy souboru**  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Name`|Požadováno. Úplná cesta ke zdrojovému souboru nebo souborů považovat za externí kód. Můžete použít zástupné znaky Windows `?` a `*` při zadání cesty.|  
  
 **Atributy prvků – funkce**  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Name`|Požadováno. Plně kvalifikovaný název funkce, který má zpracovávat jako externí kód.|  
|`Module`|Volitelné. Název nebo úplná cesta k modulu, který obsahuje funkci. Tento atribut slouží k rozlišení funkce se stejným názvem.|  
|`ExceptionImplementation`|Pokud je nastavena na `true`, zásobník volání se zobrazí funkce, která vyvolala výjimku, spíše než tuto funkci.|  
  
##  <a name="BKMK_JavaScript_Just_My_Code"></a> Pouze můj kód jazyka JavaScript  
  
###  <a name="BKMK_JS_User_and_non_user_code"></a> Uživatel a neuživatelský kód  
 **Klasifikacích kódu**  
  
 Funkce pouze můj kód jazyka JavaScript – ovládací prvky krokování a volání Zobrazit zásobník zařazením do testovacích kód v jednom z těchto klasifikací:  
  
|||  
|-|-|  
|**MyCode**|Uživatelský kód, který vlastníte a řídíte vy.|  
|**LibraryCode**|Neuživatelský kód z knihovny, které používáte, pravidelně a vaše aplikace závisí na fungovat správně (třeba WinJS nebo knihovny jQuery).|  
|**UnrelatedCode**|Neuživatelský kód, který mohl být spuštěn v aplikaci, ale není vlastníkem a vaše aplikace nemusí spoléhat přímo na něm fungovala správně (například reklamní sady SDK, která zobrazuje služby Active Directory). V projektech pro Windows Store je jakýkoli kód, který je načten do vaší aplikace z HTTPS URI nebo HTTP také považován za UnrelatedCode.|  
  
 Ladicí program jazyka JavaScript automaticky rozděluje tyto typy kódu:  
  
- Skript, který je proveden předáním řetězce hostitelské `eval` funkce je klasifikován tak **MyCode**.  
  
- Skript, který je proveden tím, že předáte řetězec `Function` konstruktor je klasifikován tak **LibraryCode**.  
  
- Skript, který je součástí odkaz na rozhraní, jako je například WinJS nebo sady Azure SDK, je klasifikován tak **LibraryCode**.  
  
- Skript, který je proveden tím, že předáte řetězec `setTimeout`, `setImmediate`, nebo `setInterval` funkce je klasifikován tak **UnrelatedCode**.  
  
- `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` Určuje jiné uživatele a neuživatelský kód pro všechny projekty jazyka JavaScript Visual Studio.  
  
  Můžete upravit výchozí klasifikace a klasifikovat určité soubory a adresy URL podle přidejte do ní soubor .json `mycode.json` ke kořenové složce projektu.  
  
  Jiný kód je klasifikován tak **MyCode**.  
  
###  <a name="BKMK_JS_Stepping_behavior"></a> Chování  
  
-   Pokud funkce není uživatelem (**MyCode**) kód, **Krokovat s vnořením** (Klávesová zkratka: F11) se chová jako **Krokovat s přeskočením** (klávesnice: F10).  
  
-   Pokud krok v vstoupí v platnost od uživatele (**LibraryCode** nebo **UnrelatedCode**) kód, pak krokování dočasně se chová jako, pokud není povolena funkce pouze můj kód. Poté, co přejdete zpět do uživatelského kódu, funkce pouze můj kód krokování je znovu zapnout.  
  
-   Když některý krok výsledky uživatelského kódu v byste museli opustit aktuální kontext spuštění (jako je vytváření kroku na posledním řádku obslužné rutiny události), ladicí program se zastaví na další spuštěných řádků kódu uživatele. Například, pokud se provede zpětné volání v **LibraryCode** kód, ladicí program bude pokračovat, dokud provede další řádek kódu uživatele.  
  
-   **Krokovat s Vystoupením** (klávesnice: Shift + F11) zastaví na další řádek kódu uživatele. Pokud nebude nalezen žádný uživatelský kód, provádění pokračuje, dokud aplikace ukončí, dosaženo zarážky nebo dojde k výjimce.  
  
###  <a name="BKMK_JS_Breakpoint_behavior"></a> Chování zarážky  
  
-   Které jsou nastavené v jakýkoli kód vždy zarážky se bez ohledu na klasifikaci, že kód  
  
-   Pokud `debugger` – klíčové slovo je zaznamenáno v:  
  
    -   **LibraryCode** kód, ladicí program vždy přeruší.  
  
    -   **UnrelatedCode** kód, ladicí program nelze zastavit.  
  
###  <a name="BKMK_JS_Exception_behavior"></a> Výjimka chování  
 Pokud dojde k neošetřené výjimce v:  
  
- **MyCode** nebo **LibraryCode** kód, ladicí program vždy přeruší.  
  
- **UnrelatedCode** kódu, a **MyCode** nebo **LibraryCode** kódu je v zásobníku volání, přerušení ladicího programu.  
  
  Pokud první příležitosti výjimky jsou povolené pro výjimku v dialogovém okně výjimky a je vyvolána výjimka **LibraryCode** nebo **UnrelatedCode** kódu:  
  
- Pokud je výjimka ošetřena, nedojde k narušení ladicího programu.  
  
- Pokud výjimka není zpracována, ladicí program přeruší.  
  
###  <a name="BKMK_JS_Customize_Just_My_Code"></a> Přizpůsobení pouze můj kód  
 Ke kategorizaci uživatelů a neuživatelský kód pro jeden projekt sady Visual Studio, přidejte do ní soubor .json `mycode.json` ke kořenové složce projektu.  
  
 Klasifikace se provádějí v uvedeném pořadí:  
  
1. Výchozí klasifikace  
  
2. Klasifikacích v `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` souboru  
  
3. Klasifikacích v `mycode. json` souboru aktuálního projektu.  
  
   Každý krok klasifikace přepíše předchozí kroky. Soubor .json není nutné vypsat všechny páry klíč-hodnota a **MyCode**, **knihovny**, a **Unrelated** hodnoty mohou být prázdné pole.  
  
   Soubory .json kódu použijte následující syntaxi:  
  
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
  
 **(V angličtině), funkce tak vlastnost ScriptBlock**  
  
 **Eval**, **funkce**, a **ScriptBlock** páry klíč-hodnota určit, jak dynamicky generovaný kód je klasifikován.  
  
|||  
|-|-|  
|**(V angličtině)**|Skript, který je proveden předáním řetězce hostitelské `eval` funkce. Ve výchozím nastavení, vyhodnocení skriptů klasifikovaný jako **MyCode**.|  
|**– funkce**|Skript, který je proveden tím, že předáte řetězec `Function` konstruktoru. Ve výchozím nastavení, funkce skriptu klasifikovaný jako **LibraryCode**.|  
|**Hodnota ScriptBlock**|Skript, který je proveden tím, že předáte řetězec `setTimeout`, `setImmediate`, nebo `setInterval` funkce. Ve výchozím nastavení, skript ScriptBlock klasifikovaný jako **UnrelatedCode**.|  
  
 Změňte hodnotu na jednu z těchto klíčových slov:  
  
- `MyCode`  klasifikuje skriptu jako **MyCode**.  
  
- `Library`  klasifikuje skriptu jako **LibraryCode**.  
  
- `Unrelated`  klasifikuje skriptu jako **UnrelatedCode**.  
  
  **MyCode, knihovny a nemá vztah**  
  
  **MyCode**, **knihovny**, a **Unrelated** zadejte páry klíč-hodnota adresy URL nebo soubory, které chcete zahrnout do klasifikace:  
  
|||  
|-|-|  
|**MyCode**|Pole adresy URL nebo soubory, které jsou klasifikovány jako **MyCode**.|  
|**Knihovny**|Pole adresy URL nebo soubory, které jsou klasifikovány jako **LibraryCode**.|  
|**Nesouvisejících**|Pole adresy URL nebo soubory, které jsou klasifikovány jako **UnrelatedCode**.|  
  
 Řetězec adresy url nebo soubor může obsahovat jeden nebo více `*` znaků, které odpovídají nula nebo více znaků. `*` odpovídá regulárnímu výrazu `.*`.





