---
title: Ladění kódu uživatele pomocí funkce pouze můj kód | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/22/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 01e36c528b71bb49b29265890ca6c48863f01be9
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389024"
---
# <a name="debug-only-user-code-with-just-my-code"></a>Ladit jenom uživatelský kód pomocí funkce pouze můj kód 

*Funkce pouze můj kód* je funkce ladění sady Visual Studio, která automaticky kroky prostřednictvím volání do systému, rozhraní a jiného kódu od uživatele. V **zásobník volání** sbalí tato volání do okna pouze můj kód **[externí kód]** snímků. 

Funkce pouze můj kód funguje jinak v projektech .NET Framework, C++ a JavaScript.

##  <a name="BKMK_Enable_or_disable_Just_My_Code"></a> Povolit nebo zakázat pouze můj kód  

Pro většinu programovacích jazyků ve výchozím nastavení zapnutá funkce pouze můj kód. 

- Chcete-li povolit nebo zakázat volbu pouze vlastní kód v sadě Visual Studio v nabídce **nástroje** > **možnosti** (nebo **ladění** > **možnosti**) > **Ladění** > **Obecné**zaškrtněte nebo zrušte zaškrtnutí možnosti **povolit volbu pouze vlastní kód**.
  
 ![Povolit volbu pouze vlastní kód v dialogovém okně Možnosti](../debugger/media/dbg_justmycode_options.png "povolit volbu pouze vlastní kód")  
  
> [!NOTE]
> **Povolit volbu pouze vlastní kód** je globální nastavení, které se vztahují na všechny projekty sady Visual Studio ve všech jazycích.  
  
##  <a name="just-my-code-debugging"></a>ladění s možností Pouze můj kód

Během relace ladění **moduly** zobrazí okno, které kód modulů ladicí program se zpracuje jako můj kód (uživatel), spolu s jejich načítání stavu symbolů. Další informace najdete v tématu [poznat více do hloubky pomocí jak ladicí program připojí k vaší aplikaci](../debugger/debugger-tips-and-tricks.md#modules_window).

 ![Uživatelský kód v okně moduly](../debugger/media/dbg_justmycode_module.png "uživatelského kódu v okně moduly")
  
V **zásobník volání** nebo **úlohy** okně volbu pouze vlastní kód sbalí neuživatelský kód do rámečku kódu s poznámkami šedě označený `[External Code]`.

 ![Externí rámec kódu v okně zásobník volání](../debugger/media/dbg_justmycode_externalcode.png "rámce externího kódu")
  
>[!TIP]
>Chcete-li otevřít **moduly**, **zásobník volání**, **úlohy**, nebo většinu dalších ladění systému windows, musí být v relaci ladění. Při ladění, v části **ladění** > **Windows**, vyberte systému windows, který chcete spustit. 

<a name="BKMK_Override_call_stack_filtering"></a> Chcete-li zobrazit kód v sbaleném **[externí kód]** frame, klikněte pravým tlačítkem **zásobník volání** nebo **úloh** okna a vyberte **zobrazit externí kód**v místní nabídce. Nahraďte řádky rozšířené externí kód **[externí kód**] rámce. 

 ![Zobrazit externí kód v okně zásobník volání](../debugger/media/dbg_justmycode_showexternalcode.png "zobrazit externí kód")
  
> [!NOTE]
> **Zobrazit externí kód** je aktuální uživatel profiler nastavení, která se vztahuje na všechny projekty ve všech jazycích, které jsou otevřeny uživatelem.

Dvojitým kliknutím řádku rozšířené externí kód v **zásobník volání** okno zvýrazní volající kód řádek zeleně ve zdrojovém kódu. Pro knihovny DLL nebo jiných modulů nebyl nalezen nebo načten symbol nebo zdrojové nebyl nalezen, že mohou otevřít stránku.

##  <a name="BKMK__NET_Framework_Just_My_Code"></a>Rozhraní .NET framework pouze můj kód 

Funkce pouze můj kód v projektech .NET Framework používá symbol (*PDB*) soubory a optimalizace programu ke klasifikaci uživatele a neuživatelský kód. Ladicí program rozhraní .NET Framework považuje za optimalizovaný binární soubory a zkušebně načtených *PDB* soubory za neuživatelský kód.
  
Tři atributy kompilátoru také ovlivnit ladicí program .NET považuje na uživatelském kódu:  

- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> dává pokyn ladicímu programu, že kód, který se použije k není uživatelský kód.  
- <xref:System.Diagnostics.DebuggerHiddenAttribute> Skryje kód z ladicího programu, i v případě, že funkce pouze můj kód je vypnutý.  
- <xref:System.Diagnostics.DebuggerStepThroughAttribute> sdělí ladicímu programu, chcete-li si kód, který se použije, místo krokování s vnořením do kódu.  

Ladicí program rozhraní .NET Framework považuje veškerý kód bude uživatelský kód.  

Během ladění v rozhraní .NET Framework:

- **Ladění** > **Krokovat s vnořením** (nebo **F11**) v neuživatelském kódu překročí kód na další řádek kódu uživatele. 
- **Ladění** > **Krokovat s Vystoupením** (nebo **Shift**+**F11**) na jiný než uživatelský kód běží na další řádek kódu uživatele. 

Pokud není žádný další kód uživatele, ladění pokračuje, dokud ho ukončí, narazí na další zarážku nebo vyvolá chybu. 

<a name="BKMK_NET_Breakpoint_behavior"></a> Pokud ladicí program přeruší v neuživatelském kódu (například použít **ladění** > **příkaz Pozastavit vše** a pozastavení v neuživatelském kódu), **žádný zdrojový** zobrazí se okno. Pak můžete použít **ladění** > **krok** příkazu Přejít na další řádek kódu uživatele.

Pokud dojde k neošetřené výjimce v neuživatelském kódu, ladicí program přeruší na řádek kódu uživatele, ve kterém se vygeneroval výjimku.  
  
Pokud první příležitosti výjimky jsou povolené pro výjimku, řádku volání uživatelského kódu je zvýrazněn zeleně ve zdrojovém kódu. **Zásobník volání** zobrazí okno rámce s poznámkami, které jsou označené jako **[externí kód]**.  

##  <a name="BKMK_C___Just_My_Code"></a> Pouze můj kód C++  
  
V jazyce C++ povolením funkce pouze můj kód je stejné jako při použití [/JMC (pouze můj kód ladění)](/cpp/build/reference/jmc) přepínač kompilátoru.

<a name="BKMK_CPP_User_and_non_user_code"></a> Funkce pouze můj kód se liší v jazyce C++ než v rozhraní .NET Framework a jazyka JavaScript, protože můžete určit soubory od uživatele samostatně pro krokování chování a **zásobník volání** okna. 

Funkce pouze můj kód v jazyce C++ bude považovat za neuživatelský kód bude pouze tyto funkce:

- Pro **zásobník volání** okno: 

  - Funkce s odstraněnými příslušnými daty zdroj informací v jejich soubor symbolů.  
  - Funkce, kde soubory symbolů znamenat, že neexistuje žádný zdrojový soubor odpovídá rámce zásobníku.  
  - Funkcí zadaných v  *\*.natjmc* soubory *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* složky.  
  
- Pro krokování chování:
  
  - Funkcí zadaných v  *\*.natstepfilter* soubory *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* složky.  
  
Můžete vytvořit *.natstepfilter* a *.natjmc* soubory k přizpůsobení chování funkce pouze můj kód a **zásobník volání** okna. V tématu [C++ přizpůsobit chování](#BKMK_CPP_Customize_stepping_behavior) a [chování zásobníku volání přizpůsobení C++](#BKMK_CPP_Customize_call_stack_behavior). 

<a name="BKMK_CPP_Stepping_behavior"></a> Během ladění C++:

- **Ladění** > **Krokovat s vnořením** (nebo **F11**) v neuživatelském kódu překročí kód na další řádek kódu uživatele. 
- **Ladění** > **Krokovat s Vystoupením** (nebo **Shift**+**F11**) na jiný než uživatelský kód běží na další řádek kódu uživatele. 

Pokud není žádný další kód uživatele, ladění pokračuje, dokud ho ukončí, narazí na další zarážku nebo vyvolá chybu. 

Pokud ladicí program přeruší v neuživatelském kódu (například použít **ladění** > **příkaz Pozastavit vše** nebo pozastavit během neuživatelském kódu), krokování pokračuje v neuživatelském kódu.

Pokud ladicí program narazí na výjimku, přestane na výjimku, ať už v uživatele nebo neuživatelský kód. **Uživatelem neošetřené** možnosti **nastavení výjimek** dialogové okno se ignorují.  

###  <a name="BKMK_CPP_Customize_stepping_behavior"></a> Přizpůsobení chování jazyka C++  

 V projektech C++, můžete zadat funkce převezme seznam jako neuživatelský kód v kroku  *\*.natstepfilter* soubory.  
  
- Chcete-li zadat jiný než uživatelský kód pro všechny místní uživatele sady Visual Studio, přidejte *.natstepfilter* do souboru *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* složky.  
- Chcete-li zadat jiný než uživatelský kód pro jednotlivé uživatele, přidejte *.natstepfilter* do souboru *%USERPROFILE%\My Documents\Visual Studio 2017\Visualizers* složky.  
  
A *.natstepfilter* soubor je soubor XML s následující syntaxí:  
  
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
|`Function`|Požadováno. Určuje jednu nebo více funkcí jako funkcí nedefinovaných uživatelem.|  
|`Name`|Požadováno. ECMA 262 ve formátu regulárních výrazů zadáním názvu plná funkčnost tak, aby odpovídaly. Příklad:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> sdělí ladicímu programu, že všechny metody v `MyNS::MyClass` mají být považovány za neuživatelský kód. Shoda rozlišuje velká a malá písmena.|  
|`Module`|Volitelné. ECMA 262 ve formátu regulárních výrazů zadáním úplná cesta k modulu, který obsahuje funkci. Shoda nerozlišuje malá a velká písmena.|  
|`Action`|Požadováno. Jedna z těchto hodnot malá a velká písmena:<br /><br /> `NoStepInto`  -sdělí ladicímu programu, aby přešel přes funkci.<br /> `StepInto`  -dává pokyn ladicímu programu vstup do funkce přepsání jiného `NoStepInto` pro odpovídající funkce.|  
  
###  <a name="BKMK_CPP_Customize_call_stack_behavior"></a> Přizpůsobení chování zásobníku volání jazyka C++  

Pro projekty C++, můžete zadat moduly, zdrojové soubory a funkce **zásobník volání** okno považuje za neuživatelský kód tak, že zadáte v  *\*.natjmc* soubory.  
  
-   Chcete-li zadat jiný než uživatelský kód pro všechny uživatele počítače Visual Studio, přidejte *.natjmc* do souboru *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* složky.  
-   Chcete-li zadat jiný než uživatelský kód pro jednotlivé uživatele, přidejte *.natjmc* do souboru *%USERPROFILE%\My Documents\Visual Studio 2017\Visualizers* složky.  

A *.natjmc* soubor je soubor XML s následující syntaxí:  
  
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
|`Name`|Požadováno. Úplná cesta modulu nebo modulech. Můžete použít zástupné znaky Windows `?` (žádný nebo jeden znak) a `*` (nula nebo více znaků). Například<br /><br /> `<Module Name="?:\3rdParty\UtilLibs\*" />`<br /><br /> sdělí ladicímu programu, aby považoval všechny moduly v *\3rdParty\UtilLibs* v jakékoli jednotce jako externí kód.|  
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

<a name="BKMK_JS_User_and_non_user_code"></a> Funkce pouze můj kód jazyka JavaScript – ovládací prvky krokování a volání Zobrazit zásobník zařazením do testovacích kód v jednom z těchto klasifikací:  

|||  
|-|-|  
|**MyCode**|Uživatelský kód, který vlastníte a řídíte vy.|  
|**LibraryCode**|Neuživatelský kód z knihovny, které používáte, pravidelně a vaše aplikace závisí na fungovat správně (třeba WinJS nebo knihovny jQuery).|  
|**UnrelatedCode**|Neuživatelský kód v aplikaci, kterou nevlastníte a vaše aplikace nemusí spoléhat na správné fungování. Například advertising SDK, která zobrazuje služby Active Directory může být UnrelatedCode. V projektech UPW se veškerý kód, který je načten do vaší aplikace z HTTPS URI nebo HTTP také považuje za UnrelatedCode.|  

Ladicí program jazyka JavaScript klasifikuje kód jako uživatel, nebo bez uživatelem v tomto pořadí:  
  
1. Výchozí klasifikace.  
   -   Skript spustit předáním řetězce hostitelské `eval` funkce je **MyCode**.  
   -   Skript spustit tím, že předáte řetězec `Function` konstruktor je **LibraryCode**.  
   -   Skript v odkaz na rozhraní, jako je například WinJS nebo sady Azure SDK, je **LibraryCode**.  
   -   Skript spustit tím, že předáte řetězec `setTimeout`, `setImmediate`, nebo `setInterval` je funkce **UnrelatedCode**.  
   
2. Klasifikace pro všechny projekty aplikace Visual Studio JavaScript v *%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json* souboru.  
   
3. Klasifikacích v *mycode.json* souboru aktuálního projektu.  
  
Každý krok klasifikace přepíše předchozí kroky. 

Jiný kód je klasifikován tak **MyCode**.  

Můžete upravit výchozí klasifikace a klasifikovat určité soubory a adresy URL jako uživatele nebo neuživatelský kód tak, že přidáte *.json* soubor s názvem *mycode.json* ke kořenové složce projektu JavaScript. Zobrazit [přizpůsobení JavaScript volbu pouze vlastní kód](#BKMK_JS_Customize_Just_My_Code). 

<a name="BKMK_JS_Stepping_behavior"></a> Během ladění jazyka JavaScript: 

- Pokud je funkce neuživatelský kód **ladění** > **Krokovat s vnořením** (nebo **F11**) se chová stejně jako **ladění**  >  **Krok přes** (nebo **F10**).  
- Pokud krok v vstoupí v platnost od uživatele (**LibraryCode** nebo **UnrelatedCode**) kódu, krokování dočasně chová jako není povolena funkce pouze můj kód. Po kroku zpět do uživatelského kódu, funkce pouze můj kód krokování je znovu zapnout.  
- Když uživatel výsledky krok kódu v byste museli opustit aktuální kontext spuštění, ladicí program se zastaví na další řádek kódu prováděnou uživatele. Například, pokud se provede zpětné volání v **LibraryCode** kód, ladicí program bude pokračovat, dokud provede další řádek kódu uživatele.
- **Krokovat s Vystoupením** (nebo **Shift**+**F11**) zastaví na další řádek kódu uživatele. 

Pokud není žádný další kód uživatele, ladění pokračuje, dokud ho ukončí, narazí na další zarážku nebo vyvolá chybu. 

Zarážky nastavené v kódu jsou vždy přístupů, ale je sestavení klasifikováno kód.  

- Pokud `debugger` – klíčové slovo probíhá **LibraryCode**, ladicí program se vždy přeruší.  
- Pokud `debugger` – klíčové slovo probíhá **UnrelatedCode**, ladicí program nelze zastavit.  
  
<a name="BKMK_JS_Exception_behavior"></a> Pokud dojde k neošetřené výjimce v **MyCode** nebo **LibraryCode** kód, ladicí program vždy přeruší.  

Pokud dojde k neošetřené výjimce v **UnrelatedCode**, a **MyCode** nebo **LibraryCode** je v zásobníku volání, přerušení ladicího programu.  
  
Pokud výjimkách first-chance jsou povolené pro výjimku, a vyvolá výjimku v **LibraryCode** nebo **UnrelatedCode**:  
  
-   Pokud je výjimka ošetřena, nedojde k narušení ladicího programu.  
-   Pokud výjimka není zpracována, ladicí program přeruší.  
  
###  <a name="BKMK_JS_Customize_Just_My_Code"></a> Přizpůsobení JavaScript pouze můj kód  

Ke kategorizaci uživatelů a neuživatelský kód pro jeden projekt jazyka JavaScript, můžete přidat *.json* soubor s názvem *mycode.json* ke kořenové složce projektu.  
  
Specifikace v tomto souboru přepsat výchozí klasifikace a *mycode.default.wwa.json* souboru. *Mycode.json* souboru není nutné vypsat všechny páry klíč-hodnota. **MyCode**, **knihovny**, a **Unrelated** hodnoty mohou být prázdné pole.  
  
*MyCode.JSON* souborů použijte následující syntaxi:  
  
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
  
 **(V angličtině), funkce tak vlastnost ScriptBlock**  
  
 **Eval**, **funkce**, a **ScriptBlock** páry klíč-hodnota určit, jak dynamicky generovaný kód je sestavení klasifikováno:  
  
|||  
|-|-|  
|**(V angličtině)**|Skript, který je proveden předáním řetězce hostitelské `eval` funkce. Ve výchozím nastavení, vyhodnocení skriptů klasifikovaný jako **MyCode**.|  
|**– funkce**|Skript, který je proveden tím, že předáte řetězec `Function` konstruktoru. Ve výchozím nastavení, funkce skriptu klasifikovaný jako **LibraryCode**.|  
|**Hodnota ScriptBlock**|Skript, který je proveden tím, že předáte řetězec `setTimeout`, `setImmediate`, nebo `setInterval` funkce. Ve výchozím nastavení, skript ScriptBlock klasifikovaný jako **UnrelatedCode**.|  
  
 Změňte hodnotu na jednu z těchto klíčových slov:  
  
-   `MyCode`  klasifikuje skriptu jako **MyCode**.  
-   `Library`  klasifikuje skriptu jako **LibraryCode**.  
-   `Unrelated`  klasifikuje skriptu jako **UnrelatedCode**.  
  
  **MyCode, knihovny a nemá vztah**  
  
 **MyCode**, **knihovny**, a **Unrelated** zadejte páry klíč-hodnota adresy URL nebo soubory, které chcete zahrnout do klasifikace:  
  
|||  
|-|-|  
|**MyCode**|Pole adresy URL nebo soubory, které jsou klasifikovány jako **MyCode**.|  
|**Knihovny**|Pole adresy URL nebo soubory, které jsou klasifikovány jako **LibraryCode**.|  
|**Nesouvisejících**|Pole adresy URL nebo soubory, které jsou klasifikovány jako **UnrelatedCode**.|  
  
 Adresa URL nebo soubor řetězec může mít jeden nebo více `*` znaků, které odpovídají nula nebo více znaků. `*` je stejný jako regulární výraz `.*`.
