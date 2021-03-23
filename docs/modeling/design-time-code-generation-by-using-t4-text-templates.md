---
title: Vytvoření kódu v době návrhu pomocí textových šablon T4
description: Přečtěte si, jak textové šablony T4 v době návrhu umožňují generovat kód programu a další soubory v projektu sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- text templates, guidelines for code generation
- text templates, data source model
- TextTemplatingFileGenerator custom tool
- Transform All Templates
- text templates, getting started
- Text Template project item
- text templates, generating code for your application
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ec309be7fbeb81951af73517412f36f7b28bc82f
ms.sourcegitcommit: 20f546a0b13b56e7b0da21abab291d42a5ba5928
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/23/2021
ms.locfileid: "104884145"
---
# <a name="design-time-code-generation-by-using-t4-text-templates"></a>Vytvoření kódu v době návrhu pomocí textových šablon T4

Textové šablony T4 v době návrhu umožňují generovat kód programu a další soubory v projektu aplikace Visual Studio. Obvykle píšete šablony tak, aby lišily kód, který generují podle dat z *modelu*. Model je soubor nebo databáze obsahující klíčové informace o požadavcích vaší aplikace.

Můžete mít například model definující pracovní postup, a to buď jako tabulku, nebo jako diagram. Z modelu můžete vygenerovat software, který spouští pracovní postup. Když se změní požadavky vašich uživatelů, je snadné diskutovat o novém pracovním postupu s uživateli. Opětovné generování kódu z pracovního postupu je spolehlivější než ruční aktualizace kódu.

> [!NOTE]
> *Model* je zdroj dat, který popisuje konkrétní aspekt aplikace. Může to být libovolný formulář v jakémkoli typu souboru nebo databáze. Nemusí být v žádném konkrétním formuláři, jako je model UML nebo model Domain-Specificho jazyka. Typické modely jsou ve formě tabulek nebo souborů XML.

Již jste obeznámeni s generováním kódu. Při definování prostředků v souboru **. resx** v řešení aplikace Visual Studio se automaticky generuje sada tříd a metod. Soubor prostředků je mnohem jednodušší a spolehlivější pro úpravu prostředků, než by bylo nutné v případě, že jste museli upravovat třídy a metody. Pomocí textových šablon můžete kód vytvořit stejným způsobem ze zdroje vlastního návrhu.

Textová šablona obsahuje kombinaci textu, který chcete vygenerovat, a kód programu, který generuje proměnné části textu. Programový kód umožňuje opakovat nebo podmíněně vynechat části vygenerovaného textu. Generovaný text může být samotný programový kód, který bude tvořit součást vaší aplikace.

## <a name="create-a-design-time-t4-text-template"></a>Vytvoření textové šablony Design-Time T4

1. Vytvořte nový projekt sady Visual Studio nebo otevřete existující projekt.

2. Přidejte textový soubor šablony do projektu a pojmenujte ho s příponou **. TT**.

    Chcete-li to provést, v **Průzkumník řešení** v místní nabídce projektu vyberte možnost **Přidat**  >  **novou položku**. V dialogovém okně **Přidat novou položku** vyberte v prostředním podokně **textovou šablonu** .

    Všimněte si, že vlastnost **vlastního nástroje** souboru je **hodnotu TextTemplatingFileGenerator**.

3. Otevřete tento soubor. Již bude obsahovat následující direktivy:

   ```
   <#@ template hostspecific="false" language="C#" #>
   <#@ output extension=".txt" #>
   ```

    Pokud jste přidali šablonu do [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projektu, atribut Language bude " `VB` ".

4. Na konec souboru přidejte nějaký text. Například:

   ```
   Hello, world!
   ```

5. Soubor uložte.

    Může se zobrazit okno s **upozorněním zabezpečení** , které vás vyzve k potvrzení, že chcete šablonu spustit. Klikněte na **OK**.

6. V **Průzkumník řešení** rozbalte uzel soubor šablony a vyhledejte soubor s příponou **. txt**. Soubor obsahuje text vygenerovaný ze šablony.

   > [!NOTE]
   > Pokud je projekt Visual Basic projektu, musíte kliknout na **Zobrazit všechny soubory** , aby se zobrazil výstupní soubor.

### <a name="regenerate-the-code"></a>Znovu vygenerovat kód

Spustí se šablona, která generuje soubor dceřiné společnosti v některém z následujících případů:

- Upravte šablonu a pak změňte fokus na jiné okno sady Visual Studio.

- Uložte šablonu.

- V nabídce **sestavení** klikněte na **transformovat všechny šablony** . Tím dojde k transformaci všech šablon v řešení sady Visual Studio.

- V **Průzkumník řešení** v místní nabídce libovolného souboru vyberte možnost **Spustit vlastní nástroj**. Tuto metodu použijte, chcete-li transformovat vybranou podmnožinu šablon.

Můžete také nastavit projekt sady Visual Studio tak, aby byly šablony spouštěny při změně datových souborů, které čtou. Další informace naleznete v tématu [Automatické generování kódu](#Regenerating).

## <a name="generate-variable-text"></a>Generovat text proměnné

Textové šablony umožňují použít kód programu k odlišení obsahu generovaného souboru.

1. Změnit obsah `.tt` souboru:

   ```csharp
   <#@ template hostspecific="false" language="C#" #>
   <#@ output extension=".txt" #>
   <#int top = 10;

   for (int i = 0; i<=top; i++)
   { #>
      The square of <#= i #> is <#= i*i #>
   <# } #>
   ```

   ```vb
   <#@ template hostspecific="false" language="VB" #>
   <#@ output extension=".txt" #>
   <#Dim top As Integer = 10

   For i As Integer = 0 To top
   #>
       The square of <#= i #> is <#= i*i #>
   <#
   Next
   #>
   ```

2. Uložte soubor. TT a znovu zkontrolujte vygenerovaný soubor. txt. Zobrazuje čtverce čísel od 0 do 10.

   Všimněte si, že příkazy jsou uzavřeny v rámci `<#...#>` a jednotlivé výrazy v rámci `<#=...#>` . Další informace najdete v tématu [zápis textové šablony T4](../modeling/writing-a-t4-text-template.md).

   Pokud píšete kód generování v nástroji [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] , `template` direktiva by měla obsahovat `language="VB"` . `"C#"` je výchozí možnost.

## <a name="debugging-a-design-time-t4-text-template"></a>Ladění textové šablony Design-Time T4

Ladění textové šablony:

- Vložte `debug="true"` do `template` direktivy. Například:

   `<#@ template debug="true" hostspecific="false" language="C#" #>`

- Nastavte zarážky v šabloně stejným způsobem jako běžný kód.

- V místní nabídce souboru textové šablony v Průzkumník řešení vyberte **ladit šablonu T4** .

   Šablona se spustí a zastaví na zarážekch. Můžete kontrolovat proměnné a krokovat kód obvyklým způsobem.

> [!TIP]
> `debug="true"` Vytvoří mapu generovaného kódu přesněji pro textovou šablonu vložením dalších direktiv pro číslování řádků do generovaného kódu. Pokud je necháte, zarážky mohou zastavit běh v nesprávném stavu.
>
> Ale můžete ponechat klauzuli v direktivě šablony i v případě, že neladíte. To způsobuje pouze velmi malý pokles výkonu.

## <a name="generating-code-or-resources-for-your-solution"></a>Generování kódu nebo prostředků pro vaše řešení

V závislosti na modelu můžete vygenerovat soubory programu, které se liší. Model je vstupní, například databáze, konfigurační soubor, model UML, model DSL nebo jiný zdroj. Obvykle vygenerujete několik programových souborů ze stejného modelu. Toho dosáhnete tak, že vytvoříte soubor šablony pro každý vygenerovaný programový soubor a všechny šablony budou číst stejný model.

### <a name="to-generate-program-code-or-resources"></a>Generování kódu programu nebo prostředků

1. Změňte direktivu Output tak, aby vygenerovala soubor příslušného typu, jako je například cs,. vb,. resx nebo. XML.

2. Vložte kód, který vygeneruje kód řešení, který budete potřebovat. Například pokud chcete generovat tři deklarace polí typu Integer ve třídě:

    ```csharp

    <#@ template debug="false" hostspecific="false" language="C#" #>
    <#@ output extension=".cs" #>
    <# var properties = new string [] {"P1", "P2", "P3"}; #>
    // This is generated code:
    class MyGeneratedClass {
    <# // This code runs in the text template:
      foreach (string propertyName in properties)  { #>
      // Generated code:
      private int <#= propertyName #> = 0;
    <# } #>
    }
    ```

    ```vb
    <#@ template debug="false" hostspecific="false" language="VB" #>
    <#@ output extension=".cs" #>
    <# Dim properties = {"P1", "P2", "P3"} #>
    class MyGeneratedClass {
    <#
       For Each propertyName As String In properties
    #>
      private int <#= propertyName #> = 0;
    <#
       Next
    #>
    }

    ```

3. Uložte soubor a zkontrolujte vygenerovaný soubor, který teď obsahuje následující kód:

    ```csharp
    class MyGeneratedClass {
      private int P1 = 0;
      private int P2 = 0;
      private int P3 = 0;
    }
    ```

### <a name="generating-code-and-generated-text"></a>Generování kódu a vygenerovaný text

Při generování kódu programu je nejdůležitější se vyhnout vygenerování kódu, který se spouští ve vaší šabloně, a výslednému generovanému kódu, který se stal součástí vašeho řešení. Tyto dva jazyky nemusí být stejné.

Předchozí příklad obsahuje dvě verze. V jedné verzi je generování kódu v jazyce C#. V druhé verzi je generovaný kód Visual Basic. Ale text generovaný oběma z nich je stejný a jedná se o třídu jazyka C#.

Stejným způsobem můžete použít [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] šablonu k vygenerování kódu v libovolném jazyce. Vygenerovaný text nemusí být v žádném konkrétním jazyce a nemusí se jednat o programový kód.

### <a name="structuring-text-templates"></a>Strukturování textových šablon

V důsledku dobrého postupu můžeme kód šablony rozdělit do dvou částí:

- Část konfigurace nebo shromažďování dat, která nastavuje hodnoty v proměnných, ale neobsahuje textové bloky. V předchozím příkladu je tato část inicializací `properties` .

   To se někdy označuje jako oddíl "model", protože vytváří model in-Store a obvykle čte soubor modelu.

- Část pro generování textu ( `foreach(...){...}` v příkladu), která používá hodnoty proměnných.

   Toto není nezbytné oddělení, ale jedná se o styl, který usnadňuje čtení šablony snížením složitosti součásti, která obsahuje text.

## <a name="reading-files-or-other-sources"></a>Čtení souborů nebo jiných zdrojů

Pro přístup k souboru modelu nebo databázi může váš kód šablony použít sestavení jako System.XML. Chcete-li získat přístup k těmto sestavením, je nutné vložit direktivy, jako například:

```
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>
<#@ import namespace="System.IO" #>
```

`assembly`Direktiva zpřístupní zadané sestavení kódu šablony stejným způsobem jako oddíl odkazy projektu sady Visual Studio. Nemusíte zahrnovat odkaz na System.dll, na který se odkazuje automaticky. `import`Direktiva umožňuje používat typy bez použití jejich plně kvalifikovaných názvů stejným způsobem jako `using` direktiva v běžném programovém souboru.

Například po importu **System.IO** můžete napsat:

```csharp

<# var properties = File.ReadLines("C:\\propertyList.txt");#>
...
<# foreach (string propertyName in properties) { #>
...
```

```vb
<# For Each propertyName As String In
             File.ReadLines("C:\\propertyList.txt")
#>
```

### <a name="opening-a-file-with-a-relative-pathname"></a>Otevření souboru s relativní cestou

Chcete-li načíst soubor z umístění relativního k textové šabloně, můžete použít `this.Host.ResolvePath()` . Pro použití. Hostitel, musíte nastavit `hostspecific="true"` v `template` :

```
<#@ template debug="false" hostspecific="true" language="C#" #>
```

Pak můžete napsat například:

```csharp
<# string filename = this.Host.ResolvePath("filename.txt");
  string [] properties = File.ReadLines(filename);
#>
...
<#  foreach (string propertyName in properties { #>
...
```

```vb
<# Dim filename = Me.Host.ResolvePath("propertyList.txt")
   Dim properties = File.ReadLines(filename)
#>
...
<#   For Each propertyName As String In properties
...
#>
```

Můžete také použít `this.Host.TemplateFile` , který určuje název aktuálního souboru šablony.

Typ `this.Host` (v jazyce VB, `Me.Host` ) je `Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost` .

### <a name="getting-data-from-visual-studio"></a>Získávání dat ze sady Visual Studio

Chcete-li použít služby poskytované v aplikaci Visual Studio, nastavte `hostSpecific` atribut a načtěte `EnvDTE` sestavení. Importujte `Microsoft.VisualStudio.TextTemplating` , který obsahuje `GetCOMService()` metodu rozšíření.  Pro přístup k DTE a dalším službám pak můžete použít IServiceProvider. GetCOMService (). Například:

```src
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="Microsoft.VisualStudio.TextTemplating" #>
<#
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetCOMService(typeof(EnvDTE.DTE));
#>

Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>
```

> [!TIP]
> Textová šablona se spouští ve své vlastní doméně aplikace a služby jsou k dispozici v zařazování. V této situaci je GetCOMService () spolehlivější než GetService ().

## <a name="regenerating-the-code-automatically"></a><a name="Regenerating"></a> Opětovné generování kódu automaticky

Obvykle se několik souborů v řešení sady Visual Studio generuje s jedním vstupním modelem. Každý soubor je vygenerován z vlastní šablony, ale šablony všechny odkazují na stejný model.

Pokud se zdrojový model změní, měli byste znovu spustit všechny šablony v řešení. Chcete-li to provést ručně, vyberte možnost **transformovat všechny šablony** v nabídce **sestavení** .

Pokud jste nainstalovali sadu Visual Studio Modeling SDK, můžete mít všechny šablony transformované automaticky pokaždé, když provedete sestavení. Chcete-li to provést, upravte soubor projektu (. csproj nebo. vbproj) v textovém editoru a přidejte následující řádky poblíž konce souboru za všechny ostatní `<import>` příkazy:

> [!NOTE]
> Sada text Template Transform SDK a sada Visual Studio Modeling SDK jsou nainstalovány automaticky při instalaci specifických funkcí sady Visual Studio. Další podrobnosti najdete v [tomto blogovém příspěvku](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/).

::: moniker range="vs-2017"

```xml
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v15.0\TextTemplating\Microsoft.TextTemplating.targets" />
<PropertyGroup>
   <TransformOnBuild>true</TransformOnBuild>
   <!-- Other properties can be inserted here -->
</PropertyGroup>
```

::: moniker-end

::: moniker range=">=vs-2019"

```xml
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v16.0\TextTemplating\Microsoft.TextTemplating.targets" />
<PropertyGroup>
   <TransformOnBuild>true</TransformOnBuild>
   <!-- Other properties can be inserted here -->
</PropertyGroup>
```

::: moniker-end

Další informace naleznete v tématu [generování kódu v procesu sestavení](../modeling/code-generation-in-a-build-process.md).

## <a name="error-reporting"></a>Hlášení chyb

Chcete-li umístit chybové zprávy a upozornění v okně chyby sady Visual Studio, můžete použít tyto metody:

```
Error("An error message");
Warning("A warning message");
```

## <a name="converting-an-existing-file-to-a-template"></a><a name="Converting"></a> Převod existujícího souboru na šablonu

Užitečnou funkcí šablon je, že vypadají velmi podobně jako soubory, které generují, spolu s některým vloženého programového kódu. To navrhuje užitečnou metodu tvorby šablony. Nejprve vytvořte běžný soubor jako prototyp, jako je například [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] soubor, a pak postupně zaveďte kód generování, který se liší od výsledného souboru.

### <a name="to-convert-an-existing-file-to-a-design-time-template"></a>Převod existujícího souboru na šablonu pro dobu návrhu

1. Do projektu aplikace Visual Studio přidejte soubor typu, který chcete vygenerovat, jako je například `.cs` , `.vb` nebo `.resx` soubor.

2. Otestujte nový soubor, abyste se ujistili, že funguje.

3. V Průzkumník řešení změňte příponu názvu souboru na **. TT**.

4. Ověřte následující vlastnosti souboru **. TT** :

   |Vlastnost |Nastavení |
   |-|-|
   | **Vlastní nástroj =** | **Hodnotu TextTemplatingFileGenerator** |
   | **Akce sestavení =** | **Žádný** |

5. Na začátek souboru vložte následující řádky:

   ```
   <#@ template debug="false" hostspecific="false" language="C#" #>
   <#@ output extension=".cs" #>
   ```

    Chcete-li zapsat kód generování šablony v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] , nastavte `language` atribut na `"VB"` místo `"C#"` .

    Nastavte `extension` atribut na příponu názvu souboru pro typ souboru, který chcete vygenerovat, například `.cs` `.resx` nebo `.xml` .

6. Soubor uložte.

    Vytvoří se soubor pobočky se zadaným rozšířením. Jeho vlastnosti jsou správné pro typ souboru. Například vlastnost **Akce sestavení** souboru. cs by byla **zkompilována**.

    Ověřte, že vygenerovaný soubor obsahuje stejný obsah jako původní soubor.

7. Identifikujte část souboru, kterou chcete změnit. Například část, která se zobrazí pouze za určitých podmínek, nebo jako část, která se opakuje, nebo kde se konkrétní hodnoty liší. Vložte kód pro generování kódu. Uložte soubor a ověřte, zda je soubor dceřiné společnosti správně vygenerován. Opakujte tento krok.

## <a name="guidelines-for-code-generation"></a>Pokyny pro generování kódu

Přečtěte si [pokyny pro psaní textových šablon T4](../modeling/guidelines-for-writing-t4-text-templates.md).

## <a name="next-steps"></a>Další kroky

|Další krok|Téma|
|-|-|
|Napsat a ladit pokročilejší textovou šablonu s kódem, který používá pomocné funkce, zahrnuté soubory a externí data.|[Tvorba textové šablony T4](../modeling/writing-a-t4-text-template.md)|
|Vygeneruje v době běhu dokumenty ze šablon.|[Generování textu za běhu pomocí textových šablon T4](../modeling/run-time-text-generation-with-t4-text-templates.md)|
|Spuštění generování textu mimo Visual Studio.|[Generování souborů pomocí nástroje TextTransform](../modeling/generating-files-with-the-texttransform-utility.md)|
|Transformujte data ve formě jazyka specifického pro doménu.|[Vytváření kódu z jazyka specifického pro doménu](../modeling/generating-code-from-a-domain-specific-language.md)|
|Zapište procesory direktiv pro transformaci vašich vlastních zdrojů dat.|[Přizpůsobení transformace textu T4](../modeling/customizing-t4-text-transformation.md)|

## <a name="see-also"></a>Viz také

- [Pokyny pro zápis textových šablon T4](../modeling/guidelines-for-writing-t4-text-templates.md)
