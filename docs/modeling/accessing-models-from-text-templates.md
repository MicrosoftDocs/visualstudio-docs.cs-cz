---
title: Přístup k modelům z textových šablon
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, accessing models
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9ac9fb023797db98f3b83aa4da7b92e71f0e71e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590615"
---
# <a name="access-models-from-text-templates"></a>Přístup k modelům z textových šablon

Pomocí textových šablon můžete vytvářet soubory sestav, soubory zdrojového kódu a další textové soubory založené na modelech jazyka specifického pro doménu. Základní informace o textových šablonách naleznete v tématu [generování kódu a textové šablony T4](../modeling/code-generation-and-t4-text-templates.md). Textové šablony budou fungovat v experimentálním režimu při ladění DSL a budou fungovat i na počítači, na kterém jste nasadili DSL.

> [!NOTE]
> Když vytvoříte řešení DSL, ukázková textová šablona **\*soubory. TT** jsou generovány v ladění projektu. Když změníte názvy doménových tříd, tyto šablony již nebudou fungovat. Nicméně obsahují základní direktivy, které potřebujete, a poskytněte příklady, které můžete aktualizovat tak, aby odpovídaly vaší DSL.

 Přístup k modelu z textové šablony:

- Nastavte vlastnost zdědit direktivy Template na [Microsoft. VisualStudio. TextTemplating. VSHost. ModelingTextTransformation](/previous-versions/bb893209(v=vs.140)). To poskytuje přístup ke Storu.

- Zadejte procesory direktiv pro DSL, ke kterým chcete získat přístup. Tím se načte sestavení pro vaši DSL, abyste mohli používat své doménové třídy, vlastnosti a vztahy v kódu textové šablony. Načte také soubor modelu, který zadáte.

  `.tt` soubor podobný následujícímu příkladu je vytvořen v projektu ladění při vytváření nového řešení sady Visual Studio ze šablony minimálního jazyka DSL.

```
<#@ template inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>
<#@ output extension=".txt" #>
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>

This text will be output directly.

This is the name of the model: <#= this.ModelRoot.Name #>

Here is a list of elements in the model:
<#
  // When you change the DSL Definition, some of the code below may not work.
  foreach (ExampleElement element in this.ExampleModel.Elements)
  {#>
<#= element.Name #>
<#
  }
#>
```

 Všimněte si následujících bodů této šablony:

- Šablona může používat doménové třídy, vlastnosti a vztahy, které jste definovali v definici DSL.

- Šablona načte soubor modelu, který zadáte ve vlastnosti `requires`.

- Vlastnost v `this` obsahuje kořenový element. Odtud může váš kód přejít na jiné prvky modelu. Název vlastnosti je obvykle stejný jako třída kořenové domény vaší DSL. V tomto příkladu je to `this.ExampleModel`.

- I když jazyk, ve kterém jsou fragmenty kódu napsané, je C#, můžete vygenerovat text libovolného typu. Můžete také napsat kód v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] přidáním vlastnosti `language="VB"` do direktivy `template`.

- Chcete-li ladit šablonu, přidejte `debug="true"` do direktivy `template`. Šablona se otevře v jiné instanci sady Visual Studio, pokud dojde k výjimce. Pokud chcete přerušit ladicí program v určitém místě v kódu, vložte příkaz `System.Diagnostics.Debugger.Break();`

   Další informace najdete v tématu [ladění textové šablony T4](../modeling/debugging-a-t4-text-template.md).

## <a name="about-the-dsl-directive-processor"></a>O procesoru direktiv DSL
 Šablona může používat doménové třídy, které jste definovali v definici DSL. To se týká direktivy, která se obvykle zobrazuje v blízkosti začátku šablony. V předchozím příkladu je to následující.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>
```

 Název direktivy (`MyLanguage`v tomto příkladu) je odvozený od názvu vaší DSL. Vyvolá *procesor direktiv* , který se generuje jako součást vaší DSL. Svůj zdrojový kód můžete najít v **Dsl\GeneratedCode\DirectiveProcessor.cs**.

 Procesor direktiv DSL provádí dvě hlavní úlohy:

- Do šablony, která odkazuje na DSL, to efektivně vloží direktivy Assembly a import. To vám umožňuje používat vaše doménové třídy v kódu šablony.

- Načte soubor, který zadáte v parametru `requires` a nastaví vlastnost v `this`, která odkazuje na kořenový prvek načteného modelu.

## <a name="validating-the-model-before-running-the-template"></a>Ověřování modelu před spuštěním šablony
 Můžete způsobit, že se model ověří před provedením šablony.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>
```

 Všimněte si, že:

1. Parametry `filename` a `validation` jsou odděleny znakem ";" a nesmí existovat žádné jiné oddělovače nebo mezery.

2. Seznam kategorií ověřování určuje, které metody ověřování budou provedeny. Více kategorií by mělo být odděleno&#124;znakem "" a nesmí existovat žádné jiné oddělovače nebo mezery.

   Pokud je nalezena chyba, bude uvedena v okně chyby a výsledný soubor bude obsahovat chybovou zprávu.

## <a name="Multiple"></a>Přístup k více modelům z textové šablony

> [!NOTE]
> Tato metoda umožňuje číst více modelů ve stejné šabloně, ale nepodporuje ModelBus odkazy. Chcete-li číst modely propojené odkazy ModelBus, přečtěte si téma [použití Visual Studio Modelbus v textové šabloně](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

 Pokud chcete získat přístup k více než jednomu modelu ze stejné textové šablony, je nutné zavolat procesor vygenerovaný direktivou jednou pro každý model. V parametru `requires` musíte zadat název souboru každého modelu. Je nutné zadat názvy, které chcete použít pro kořenovou třídu domény v parametru `provides`. V každém volání direktivy musíte zadat jiné hodnoty parametrů `provides`. Předpokládejme například, že máte tři soubory modelu s názvem Library. xyz, School. xyz a Work. xyz. Chcete-li získat přístup ze stejné textové šablony, je nutné zapsat tři volání direktiv, která připomínají následující.

```
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>
```

> [!NOTE]
> Tento ukázkový kód je určen pro jazyk, který je založen na šabloně minimálního jazyka řešení.

 Chcete-li získat přístup k modelům v textové šabloně, můžete nyní napsat kód podobný kódu v následujícím příkladu.

```csharp
<#
foreach (ExampleElement element in this.LibraryModel.Elements)
...
foreach (ExampleElement element in this.SchoolModel.Elements)
...
foreach (ExampleElement element in this.WorkModel.Elements)
...
#>
```

```vb
<#
For Each element As ExampleElement In Me.LibraryModel.Elements
...
For Each element As ExampleElement In Me.SchoolModel.Elements
...
For Each element As ExampleElement In Me.WorkModel.Elements
...
#>
```

## <a name="loading-models-dynamically"></a>Dynamické načítání modelů
 Pokud chcete určit za běhu, které modely se mají načíst, můžete dynamicky načíst soubor modelu do kódu programu namísto použití direktivy specifické pro DSL.

 Jedna z funkcí direktivy specifické pro DSL je však importovat obor názvů DSL, aby kód šablony mohl používat doménové třídy definované v této DSL. Vzhledem k tomu, že nepoužíváte direktivu, je nutné přidat **\<> sestavení** a **\<importovat** direktivy > pro všechny modely, které lze načíst. To je jednoduché, pokud jsou různé modely, které můžete načíst, všechny instance stejné DSL.

 Pro načtení souboru je nejúčinnější metodou použití Visual Studio ModelBus. V typickém scénáři vaše textová šablona použije direktivu specifickou pro načtení prvního modelu obvyklým způsobem. Tento model by obsahoval odkazy ModelBus na jiný model. Můžete použít ModelBus k otevření odkazovaného modelu a přístup k určitému prvku. Další informace najdete v tématu [pomocí Visual Studio ModelBus v textové šabloně](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

 V méně obvyklém scénáři můžete chtít otevřít soubor modelu, pro který máte pouze název souboru a který nemusí být v aktuálním projektu sady Visual Studio. V tomto případě můžete soubor otevřít pomocí techniky popsané v tématu [Postupy: otevření modelu ze souboru v kódu programu](../modeling/how-to-open-a-model-from-file-in-program-code.md).

## <a name="generating-multiple-files-from-a-template"></a>Generování více souborů ze šablony
 Pokud chcete vygenerovat několik souborů – například pro vygenerování samostatného souboru pro každý prvek v modelu, existuje několik možných přístupů. Ve výchozím nastavení je z každého souboru šablony vytvořen pouze jeden soubor.

### <a name="splitting-a-long-file"></a>Rozdělení dlouhého souboru
 V této metodě použijete šablonu k vygenerování jednoho souboru odděleného oddělovačem. Pak soubor rozdělíte na jeho části. Existují dvě šablony, jeden pro vygenerování jednoho souboru a druhý pro rozdělení.

 **LoopTemplate. T4** generuje dlouhý jeden soubor. Všimněte si, že jeho Přípona souboru je ". T4", protože by neměla být zpracována přímo po kliknutí na možnost **transformovat všechny šablony**. Tato šablona přebírá parametr, který určuje řetězec oddělovače, který odděluje segmenty:

```
<#@ template ninherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>
<#@ parameter name="delimiter" type="System.String" #>
<#@ output extension=".txt" #>
<#@ MyDSL processor="MyDSLDirectiveProcessor" requires="fileName='SampleModel.mydsl1';validation='open|load|save|menu'" #>
<#
  // Create a file segment for each element:
  foreach (ExampleElement element in this.ExampleModel.Elements)
  {
    // First item is the delimiter:
#>
<#= string.Format(delimiter, element.Id) #>

   Element: <#= element.Name #>
<#
   // Here you generate more content derived from the element.
  }
#>
```

 `LoopSplitter.tt` vyvolá `LoopTemplate.t4`a pak rozdělí výsledný soubor na jeho segmenty. Všimněte si, že tato šablona nemusí mít šablonu modelování, protože nečte model.

```
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="Microsoft.VisualStudio.TextTemplating" #>
<#@ import namespace="System.Runtime.Remoting.Messaging" #>
<#@ import namespace="System.IO" #>

<#
  // Get the local path:
  string itemTemplatePath = this.Host.ResolvePath("LoopTemplate.t4");
  string dir = Path.GetDirectoryName(itemTemplatePath);

  // Get the template for generating each file:
  string loopTemplate = File.ReadAllText(itemTemplatePath);

  Engine engine = new Engine();

  // Pass parameter to new template:
  string delimiterGuid = Guid.NewGuid().ToString();
  string delimiter = "::::" + delimiterGuid + ":::";
  CallContext.LogicalSetData("delimiter", delimiter + "{0}:::");
  string joinedFiles = engine.ProcessTemplate(loopTemplate, this.Host);

  string [] separateFiles = joinedFiles.Split(new string [] {delimiter}, StringSplitOptions.None);

  foreach (string nameAndFile in separateFiles)
  {
     if (string.IsNullOrWhiteSpace(nameAndFile)) continue;
     string[] parts = nameAndFile.Split(new string[]{":::"}, 2, StringSplitOptions.None);
     if (parts.Length < 2) continue;
#>
 Generate: [<#= dir #>] [<#= parts[0] #>]
<#
     // Generate a file from this item:
     File.WriteAllText(Path.Combine(dir, parts[0] + ".txt"), parts[1]);
  }
#>
```
