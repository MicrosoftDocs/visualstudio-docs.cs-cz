---
title: Jen můj kód | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: efcabf9c7dc201f95515cd24bf3a14727f7149fe
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302495"
---
# <a name="just-my-code"></a>Pouze můj kód
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vývojáři, kteří používají jazyky rozhraní .NET Framework, jsou obeznámeni s funkcí ladicího programu Just My Code, která vede přes systémová, frameworková a další volání mimo uživatele a sbalí tato volání v oknech zásobníku volání. Just My Code byl rozšířen na jazyky Jazyka C++ a JavaScript. Toto téma popisuje specifika použití pouze můj kód v rozhraní .NET Framework, nativní mj.  
  
## <a name="enable-or-disable-just-my-code"></a><a name="BKMK_Enable_or_disable_Just_My_Code"></a>Povolení nebo zakázání pouze můj kód  
 Chcete-li povolit nebo zakázat možnost Pouze můj kód, zvolte **možnosti a nastavení** v nabídce **Ladění.** V uzlu **Ladění** / **obecného** zvolte nebo **zrušte zaškrtnutí políčka Povolit pouze můj kód**.  
  
 ![V dialogovém okně Možnosti povolit pouze můj kód](../debugger/media/dbg-justmycode-options.png "DBG_JustMyCode_Options")  
  
> [!NOTE]
> Nastavení **Povolit pouze můj kód** je globální nastavení, které se použije pro všechny projekty sady Visual Studio ve všech jazycích.  
  
### <a name="override-call-stack-filtering"></a><a name="BKMK_Override_call_stack_filtering"></a>Přepsat filtrování zásobníku volání  
 V zobrazenízásobníku volání, jako je například zásobník volání a úkoly okna, jen můj `[External Code]`kód sbalí non-uživatelský kód do anotovaného rámce s popiskem . Chcete-li zobrazit sbalené snímky, zvolte **Zobrazit externí kód** v kontextové nabídce zobrazení zásobníku volání.  
  
> [!NOTE]
> Nastavení **Zobrazit externí kód** je uloženo do profileru aktuálního uživatele. Platí se pro všechny projekty ve všech jazycích, které jsou otevřeny uživatelem.  
  
## <a name="net-framework-just-my-code"></a><a name="BKMK__NET_Framework_Just_My_Code"></a>Rozhraní .NET Framework pouze můj kód  
  
### <a name="user-and-non-user-code"></a><a name="BKMK_NET_User_and_non_user_code"></a>Uživatelský a neuživatelský kód  
 Chcete-li odlišit uživatelský kód od kódu uživatele, pouze můj kód se dívá na soubory symbol (.pdb) a optimalizace programů. Ladicí program považuje kód za kód bez uživatele, pokud je binární soubor optimalizován nebo pokud není k dispozici soubor PDB.  
  
 Tři atributy také ovlivňují to, co ladicí program považuje za můj kód:  
  
- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute>informuje ladicí program, že kód, na který je použit, není Můj kód.  
  
- <xref:System.Diagnostics.DebuggerHiddenAttribute>skryje kód z ladicího programu, i když je vypnutý pouze můj kód.  
  
- <xref:System.Diagnostics.DebuggerStepThroughAttribute>říká ladicí program krokovat kód, který je použit, spíše než krok do kódu.  
  
  Všechny ostatní kód y jsou považovány za uživatelský kód.  
  
### <a name="stepping-behavior"></a><a name="BKMK_NET_Stepping_behavior"></a>Krokování chování  
 Když **krok do** (klávesová zkratka: F11) non-uživatelský kód, ladicí program kroky přes kód na další příkaz uživatele. Když **vystoupíte** (Klávesnice: Shift + F11), ladicí program se spustí na další řádek uživatelského kódu. Pokud není zjištěn žádný uživatelský kód, bude provádění pokračovat, dokud se aplikace neukončí, dojde k přístupu k zarážky nebo k výjimce.  
  
### <a name="breakpoint-behavior"></a><a name="BKMK_NET_Breakpoint_behavior"></a>Chování zarážky  
 Pokud je povolena možnost Jen můj kód, můžete zvolit **Možnost Přerušit vše** (Klávesnice: Ctrl + Alt + Break) a zastavit provádění v umístění, kde není žádný uživatelský kód k zobrazení. V takovém případě se zobrazí okno Bez zdroje. Pokud pak zvolíte příkaz Krok, ladicí program vás přenese na další řádek uživatelského kódu.  
  
### <a name="exception-behavior"></a><a name="BKMK_NET_Exception_behavior"></a>Chování výjimky  
 Pokud dojde k neošetřené výjimce v kódu uživatele, ladicí program se rozdělí na řádku v uživatelském kódu, kde byla výjimka generována.  
  
 Pokud jsou pro výjimku povoleny výjimky první šance, řádek uživatelského kódu je zvýrazněn zeleně. V zásobníku volání se zobrazí snímek s anotovaným označením **[Externí kód]**.  
  
## <a name="c-just-my-code"></a><a name="BKMK_C___Just_My_Code"></a>C++ jen můj kód  
  
### <a name="user-and-non-user-code"></a><a name="BKMK_CPP_User_and_non_user_code"></a>Uživatelský a neuživatelský kód  
 C++ Jen můj kód se liší od rozhraní .NET Framework a JavaScript just my code, protože chování krokování je nezávislé na chování zásobníku volání.  
  
 **Zásobníky volání**  
  
 Ve výchozím nastavení ladicí program považuje tyto funkce za neuživatelský kód v oknech zásobníku volání:  
  
- Funkce s odstraněnými zdrojovými informacemi v souboru symbolů.  
  
- Funkce, kde soubory symbolů označují, že neexistuje žádný zdrojový soubor odpovídající rámečku zásobníku.  
  
- Funkce zadané `*.natjmc` v `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` souborech ve složce.  
  
  **Krokování**  
  
  Ve výchozím nastavení jsou `*.natstepfilter` pouze `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` funkce určené v souborech ve složce považovány za kód uživatele.  
  
  Můžete vytvořit vlastní `.natstepfilter` `.natjmc` a přizpůsobit krokování a volání `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers`zásobníku okna chování v .  
  
### <a name="stepping-behavior"></a><a name="BKMK_CPP_Stepping_behavior"></a>Krokování chování  
 Když **krok do** (klávesová zkratka: F11) non-uživatelský kód z uživatelského kódu, ladicí program kroky přes kód na další řádek uživatelského kódu. Když **vystoupíte** (Klávesnice: Shift + F11), ladicí program se spustí na další řádek uživatelského kódu. Pokud není zjištěn žádný uživatelský kód, bude provádění pokračovat, dokud se aplikace neukončí, dojde k přístupu k zarážky nebo k výjimce.  
  
 Pokud ladicí program rozdělí v kódu uživatele (například pokud break All příkaz zastaví v kódu bez uživatele), krokování pokračuje v kódu uživatele.  
  
### <a name="exception-behavior"></a><a name="BKMK_CPP_Exception_behavior"></a>Chování výjimky  
 Když ladicí program narazí na výjimku, zastaví se na výjimku bez ohledu na to, zda je v uživatelském kódu nebo mimo uživatelský kód. Volby **neošetřené uživatelem** v dialogovém okně **Výjimky** jsou ignorovány.  
  
### <a name="customize-stepping-behavior"></a><a name="BKMK_CPP_Customize_stepping_behavior"></a>Přizpůsobení chování krokování  
 Můžete určit funkce, které chcete krokovat, a `*.natstepfilter` to tak, že je v souborech uvedete jako neuživatelský kód.  
  
- Chcete-li zadat neuživatelský kód pro všechny uživatele počítače sady Visual Studio, `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` přidejte do složky soubor Natstepfilter.  
  
- Chcete-li zadat neuživatelský kód pro jednotlivého uživatele, přidejte `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` do složky soubor Natstepfilter.  
  
  Soubory .natstepfilter jsou soubory XML s touto syntaxí:  
  
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
|`Name`|Povinná hodnota. Regulární výraz ECMA-262, který určuje úplný název funkce, který se má shodovat. Například:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> informuje ladicí program, `MyNS::MyClass` že všechny metody v programu mají být považovány za neuživatelský kód. Shoda rozlišuje malá a velká písmena.|  
|`Module`|Nepovinný parametr. Regulární výraz ECMA-262, který určuje úplnou cestu k modulu obsahujícímu funkci. Shoda nerozlišuje malá a velká písmena.|  
|`Action`|Povinná hodnota. Jedna z těchto hodnot rozlišujících malá a velká písmena:<br /><br /> -   `NoStepInto`– informuje ladicí program, aby překročil odpovídající funkci.<br />-   `StepInto`– říká ladicí program krok do odpovídající funkce, `NoStepInto` přepsání jakékoli jiné pro odpovídající funkce.|  
  
### <a name="customize-call-stack-behavior"></a><a name="BKMK_CPP_Customize_call_stack_behavior"></a>Přizpůsobení chování zásobníku volání  
 Můžete zadat moduly, zdrojové soubory a funkce, které chcete považovat za neuživatelský kód v balíčcích volání zadáním v `*.natjmc` souborech.  
  
- Chcete-li zadat neuživatelský kód pro všechny uživatele počítače sady Visual Studio, přidejte do `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` složky soubor NATJMC.  
  
- Chcete-li zadat neuživatelský kód pro jednotlivého uživatele, přidejte do `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` složky soubor NATJMC.  
  
  .natjmc soubory jsou xml soubory s touto syntaxí:  
  
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
  
 **Atributy prvku modulu**  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Name`|Povinná hodnota. Úplná cesta modulu nebo modulů. Můžete použít zástupné znaky `?` systému Windows (nula nebo jeden znak) a `*` (nula nebo více znaků). Například:<br /><br /> `<Module Name=”?:\3rdParty\UtilLibs\*” />`<br /><br /> informuje ladicí program, aby `\3rdParty\UtilLibs` všechny moduly na libovolné jednotce považoval za externí kód.|  
|`Company`|Nepovinný parametr. Název společnosti, která publikuje modul vložený do spustitelného souboru. Tento atribut můžete použít k rozdvojení modulů.|  
  
 **Atributy elementu souboru**  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Name`|Povinná hodnota. Úplná cesta ke zdrojovému souboru nebo souborům, které mají být považovány za externí kód. Můžete použít zástupné znaky `?` `*` systému Windows a při zadávání cesty.|  
  
 **Atributy funkčního prvku**  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Name`|Povinná hodnota. Plně kvalifikovaný název funkce považovat za externí kód.|  
|`Module`|Nepovinný parametr. Název nebo úplná cesta k modulu, který obsahuje funkci. Tento atribut můžete použít k rozdvojení funkcí se stejným názvem.|  
|`ExceptionImplementation`|Pokud je `true`nastavena na , zásobník volání zobrazí funkci, která vyvolala výjimku, nikoli tuto funkci.|  
  
## <a name="javascript-just-my-code"></a><a name="BKMK_JavaScript_Just_My_Code"></a>JavaScript jen můj kód  
  
### <a name="user-and-non-user-code"></a><a name="BKMK_JS_User_and_non_user_code"></a>Uživatelský a neuživatelský kód  
 **Klasifikace kódu**  
  
 JavaScript Just My Code řídí zobrazení krokového a volání pomocí kategorizace kódu v jedné z těchto klasifikací:  
  
|||  
|-|-|  
|**MyCode**|Uživatelský kód, který vlastníte a ovládáte.|  
|**Kód knihovny**|Neuživatelský kód z knihoven, které používáte pravidelně a vaše aplikace závisí na funkci správně (například WinJS nebo jQuery).|  
|**Nesouvisejícíkód**|Neuživatelský kód, který by mohl být spuštěn ve vaší aplikaci, ale nevlastníte a vaše aplikace na něj přímo nespoléhá, že bude fungovat správně (například reklamní sada SDK, která zobrazuje reklamy). V projektech Windows Store se za nesouvisející kód považuje také jakýkoli kód načtený do vaší aplikace z identifikátoru URI HTTP nebo HTTPS.|  
  
 Ladicí program JavaScript automaticky klasifikuje tyto typy kódu:  
  
- Skript, který je spuštěn předáním řetězce `eval` do funkce poskytované hostitelem, je klasifikován jako **MyCode**.  
  
- Skript, který je spuštěn předáním `Function` řetězce konstruktoru, je klasifikován jako **LibraryCode**.  
  
- Skript, který je obsažen v odkazu na rozhraní, jako je například WinJS nebo Sada Azure SDK, je klasifikován jako **LibraryCode**.  
  
- Skript, který je spuštěn předáním `setTimeout` `setImmediate`řetězce `setInterval` do funkce , nebo je klasifikován jako **UnrelatedCode**.  
  
- Určuje `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` jiný uživatelský a neuživatelský kód pro všechny projekty JavaScript u sady Visual Studio.  
  
  Můžete upravit výchozí klasifikace a klasifikovat konkrétní soubory a adresy URL `mycode.json` přidáním souboru JSON s názvem do kořenové složky projektu.  
  
  Všechny ostatní kódy jsou klasifikovány jako **MyCode**.  
  
### <a name="stepping-behavior"></a><a name="BKMK_JS_Stepping_behavior"></a>Krokování chování  
  
- Pokud funkce není kód uživatele **(MyCode),** **Krok do** (Klávesová zkratka: F11) se chová jako **Krok přes** (Klávesnice: F10).  
  
- Pokud krok začíná v kódu bez uživatele (**LibraryCode** nebo **UnrelatedCode**), pak krokování dočasně chová, jako by nebyl povolen pouze můj kód. Jakmile krok zpět na uživatelský kód, Jen můj kód krokování je znovu povolena.  
  
- Pokud krok v uživatelském kódu má za následek opuštění aktuální ho dispozičního kontextu (například provedení kroku na posledním řádku obslužné rutiny události), ladicí program se zastaví na dalším řádku uživatelského kódu. Například pokud zpětné volání provede v **kódu LibraryCode** ladicí program pokračuje, dokud se spustí další řádek uživatelského kódu.  
  
- **Krok ven** (Klávesnice: Shift + F11) se zastaví na dalším řádku uživatelského kódu. Pokud není zjištěn žádný uživatelský kód, bude provádění pokračovat, dokud se aplikace neukončí, dojde k přístupu k zarážky nebo k výjimce.  
  
### <a name="breakpoint-behavior"></a><a name="BKMK_JS_Breakpoint_behavior"></a>Chování zarážky  
  
- Zarážky, které byly nastaveny v libovolném kódu, budou vždy přístupů bez ohledu na klasifikaci tohoto kódu  
  
- Pokud `debugger` je klíčové slovo zjištěno v:  
  
  - **Kód LibraryCode,** ladicí program se vždy přeruší.  

  - **NesouvisejícíKód,** ladicí program se nezastaví.  
  
### <a name="exception-behavior"></a><a name="BKMK_JS_Exception_behavior"></a>Chování výjimky  
 Pokud dojde k neošetřené výjimce v:  
  
- **MyCode** nebo **LibraryCode** kód, ladicí program vždy přestávky.  
  
- **UnrelatedCode** kód a **MyCode** nebo **LibraryCode** kód je v zásobníku volání, ladicí program přestávky.  
  
  Pokud jsou povoleny výjimky první šance pro výjimku v dialogovém okně Výjimky a výjimka je vyvolána v **kódu LibraryCode** nebo **UnrelatedCode:**  
  
- Pokud je výjimka zpracována, ladicí program se nepřeruší.  
  
- Pokud výjimka není zpracována, ladicí program se rozdělí.  
  
### <a name="customize-just-my-code"></a><a name="BKMK_JS_Customize_Just_My_Code"></a>Přizpůsobit pouze můj kód  
 Chcete-li kategorizovat uživatelský a neuživatelský kód pro jeden projekt sady `mycode.json` Visual Studio, přidejte soubor JSON pojmenovaný do kořenové složky projektu.  
  
 Klasifikace jsou prováděny v tomto pořadí:  
  
1. Výchozí klasifikace  
  
2. Klasifikace v `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` souboru  
  
3. Klasifikace v `mycode. json` souboru aktuálního projektu.  
  
   Každý krok klasifikace přepíše předchozí kroky. Soubor JSON nemusí vypsat všechny dvojice hodnot klíčů a hodnoty **MyCode**, **Libraries**a **Unrelated** mohou být prázdná pole.  
  
   Soubory Můj kód json používají tuto syntaxi:  
  
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
  
 **Eval, funkce a ScriptBlock**  
  
 Dvojice hodnot klíče **Eval**, **Function**a **ScriptBlock** určují, jak je dynamicky generovaný kód klasifikován.  
  
|||  
|-|-|  
|**Eval**|Skript, který je spuštěn předáním řetězce do `eval` funkce poskytované hostitelem. Ve výchozím nastavení je skript Eval klasifikován jako **MyCode**.|  
|**Funkce**|Skript, který je spuštěn předáním `Function` řetězce konstruktoru. Ve výchozím nastavení je skript function klasifikován jako **LibraryCode**.|  
|**Blok skriptu**|Skript, který je spuštěn předáním `setTimeout` `setImmediate`řetězce `setInterval` do funkce , nebo. Ve výchozím nastavení je skript ScriptBlock klasifikován jako **UnrelatedCode**.|  
  
 Hodnotu můžete změnit na jedno z těchto klíčových slov:  
  
- `MyCode`klasifikuje skript jako **MyCode**.  
  
- `Library`klasifikuje skript jako **LibraryCode**.  
  
- `Unrelated`klasifikuje skript jako **UnrelatedCode**.  
  
  **MyCode, knihovny a nesouvisející**  
  
  Dvojice hodnot **mycode**, **knihovny**a **nesouvisející** klíče určují adresy URL nebo soubory, které chcete zahrnout do klasifikace:  
  
|||  
|-|-|  
|**MyCode**|Pole adres URL nebo souborů, které jsou klasifikovány jako **MyCode**.|  
|**Knihovny**|Pole adres URL nebo souborů, které jsou klasifikovány jako **LibraryCode**.|  
|**Nesouvisející**|Pole adres URL nebo souborů, které jsou klasifikovány jako **UnrelatedCode**.|  
  
 Řetězec url nebo souboru může `*` obsahovat jeden nebo více znaků, které odpovídají nule nebo více znakům. `*`je ekvivalentem regulárního výrazu `.*`.
