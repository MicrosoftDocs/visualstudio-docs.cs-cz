---
title: Přístup k modelům z textových šablon | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, accessing models
ms.assetid: cf65395a-0ca3-4826-89c7-b1869562685c
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: f311018197040c0c908964a49f63ab130121c8c2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919855"
---
# <a name="accessing-models-from-text-templates"></a>Přístup k modelům z textových šablon
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí textových šablon, můžete vytvořit sestavy soubory, soubory se zdrojovým kódem a jiné textové soubory, které jsou založeny na modely jazyka specifického pro doménu. Základní informace o textových šablonách naleznete v tématu [generování kódu a textové šablony T4](../modeling/code-generation-and-t4-text-templates.md). Textové šablony budou fungovat v experimentálním režimu při ladění vašeho DSL a budou fungovat i v počítači, na které jste nasadili DSL.  
  
> [!NOTE]
>  Když vytvoříte řešení DSL, ukázka textové šablony  **\*.tt** soubory jsou vygenerovány v ladění projektu. Při změně názvu doménové třídy tyto šablony už nebude fungovat. Nicméně, zahrnují základní direktivy, které potřebujete a uvádějte příklady, které můžete aktualizovat tak, aby odpovídaly vašeho DSL.  
  
 Pro přístup k modelu z textové šablony:  
  
- Nastavte vlastnost Zdědit – direktiva šablony do <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation>. To poskytuje přístup k Store.  
  
- Zadejte procesory direktiv pro DSL, který chcete získat přístup. Tento kód načte sestavení vašeho DSL tak, že můžete použít své doménové třídy, vlastnosti a vztahy v kódu textové šablony. Také načte soubor modelu, který zadáte.  
  
  A `.tt` souboru podobně jako v následujícím příkladu se vytvoří v ladění projektu při vytváření nového [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] řešení ze šablony minimální jazykový DSL.  
  
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
  
 Všimněte si, že o této šabloně následující body:  
  
-   Šablonu můžete použít doménové třídy, vlastnosti a vztahy, které jste definovali v definici DSL.  
  
-   Se šablona načte, který zadáte v souboru modelu `requires` vlastnost.  
  
-   Vlastnost v `this` obsahuje kořenový element. Odtud můžete kód přejít na další prvky modelu. Název vlastnosti je obvykle stejný jako kořenový doménová třída tohoto kódu DSL. V tomto příkladu je `this.ExampleModel`.  
  
-   I když je jazyk, ve kterém jsou zapsány fragmenty kódu jazyka C#, můžete vygenerovat text jakéhokoli druhu. Můžete také napsat kód [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] tak, že přidáte vlastnost `language="VB"` k `template` směrnice.  
  
-   Chcete-li ladit šablonu, přidejte `debug="true"` k `template` směrnice. Šablonu se otevře v jiné instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Pokud dojde k výjimce. Pokud chcete do ladicího programu v konkrétním bodě v kódu, vložte – příkaz `System.Diagnostics.Debugger.Break();`  
  
     Další informace najdete v tématu [ladění textové šablony T4](../modeling/debugging-a-t4-text-template.md).  
  
## <a name="about-the-dsl-directive-processor"></a>Informace o procesoru direktiv DSL  
 Šablonu můžete použít doménové třídy definované v definici DSL. To je způsobené směrnice, které obvykle se zobrazí dříve v šabloně. V předchozím příkladu je následující.  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>  
```  
  
 Název směrnice ( `MyLanguage`, v tomto příkladu) je odvozen z názvu tohoto kódu DSL. Vyvolá *procesor direktiv* , který je generován jako součást tohoto kódu DSL. Můžete najít jeho zdrojový kód v **Dsl\GeneratedCode\DirectiveProcessor.cs**.  
  
 Procesor direktiv DSL provádí dvě hlavní úlohy:  
  
-   Vloží efektivně direktivy sestavení a importovat do šablony, která odkazuje na vaše DSL. To vám umožní používat doménové třídy v kódu šablony.  
  
-   Načte soubor, který zadáte `requires` parametr a nastaví vlastnost `this` , který odkazuje na kořenový element načíst model.  
  
## <a name="validating-the-model-before-running-the-template"></a>Ověření modelu před spuštěním šablony  
 Může způsobit modelu na ověření. před provedením šablony.  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>  
  
```  
  
 Všimněte si, že:  
  
1. `filename` a `validation` parametry jsou odděleny ";" a musí být žádné jiné oddělovače nebo mezery.  
  
2. Seznam kategorií ověřování určuje, jaké metody ověřování se spustí. Více kategorií by měla být oddělena pomocí "&#124;" a musí být žádné jiné oddělovače nebo mezery.  
  
   Pokud je nalezena chyba, se ohlásí v okně chyby a výsledek soubor obsahovat chybovou zprávu.  
  
##  <a name="Multiple"></a> Přístup k více modelů z textové šablony  
  
> [!NOTE]
>  Tato metoda umožňuje číst několik modelů v stejnou šablonu, ale nepodporuje odkazy ModelBus. Modely, které jsou vzájemně propojena ModelBus odkazy najdete v tématu [pomocí Visual Studio ModelBus v textové šabloně](../modeling/using-visual-studio-modelbus-in-a-text-template.md).  
  
 Pokud chcete pro přístup k více než jeden model ze stejné textové šablony, je nutné volat procesoru vygenerovaných direktiv vždy jednou pro každý model. Musíte zadat název souboru každý model v `requires` parametru. Je nutné zadat názvy, které chcete použít pro třídu kořenové domény v `provides` parametru. Je nutné zadat jiné hodnoty `provides` parametrů každé volání rozhraní direktiv. Předpokládejme například, že máte tři soubory modelu s názvem Library.xyz, School.xyz a Work.xyz. Pro přístup k nim ze stejné textové šablony, musí zapsat tři direktiv volání, které se podobají následující dotazy.  
  
```  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>  
```  
  
> [!NOTE]
>  Tento příklad kódu je pro jazyk, který je založen na šabloně minimální jazykový řešení.  
  
 Pro přístup k modelů do textové šablony, teď můžete psát kód podobný kód v následujícím příkladu.  
  
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
 Pokud chcete určit za běhu, které modely načtení, můžete načíst soubor modelu dynamicky ve svém kódu programu, namísto použití direktivy specifické pro DSL.  
  
 Jedna z funkcí směrnice specifické pro DSL je však pro import oboru názvů DSL tak, aby kód šablony mohl používat doménové třídy definované v tomto DSL. Vzhledem k tomu, že nepoužíváte direktivu, je nutné přidat  **\<sestavení >** a  **\<import >** direktivy pro všechny modely, které může načíst. Je to snadné, pokud jsou všechny výskyty stejného DSL různých modelů, které může načíst.  
  
 Načíst soubor, největší efektivity dosáhnete metodou je používání [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ModelBus. V rámci typického scénáře použije textová šablona direktivu specifické pro DSL načíst první model obvyklým způsobem. Tento model by obsahoval odkazy ModelBus k jinému modelu. ModelBus můžete použít k otevření odkazovaným modelem a přístup ke konkrétní elementu. Další informace najdete v tématu [pomocí Visual Studio ModelBus v textové šabloně](../modeling/using-visual-studio-modelbus-in-a-text-template.md).  
  
 V rámci méně obvyklé scénáře, můžete chtít otevřít soubor modelu, pro který máte jenom název souboru, a která nemusí být v aktuálním [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu. V takovém případě můžete otevřít soubor pomocí techniky popsané v [postupy: otevření modelu ze souboru v kódu programu](../modeling/how-to-open-a-model-from-file-in-program-code.md).  
  
## <a name="generating-multiple-files-from-a-template"></a>Generování více souborů ze šablony  
 Pokud chcete vygenerovat několik souborů – například ke generování samostatného souboru pro každý prvek v modelu, existuje několik možných přístupů. Ve výchozím nastavení je vytvořen pouze jeden soubor z každého souboru šablony.  
  
### <a name="splitting-a-long-file"></a>Rozdělení souboru dlouhý  
 V této metodě použijte šablonu pro generování jednoho souboru, oddělené oddělovačem. Soubor se poté rozděleny do částí. Existují dvě šablony, z nich se má generovat jeden soubor a druhým k ho rozdělte.  
  
 **LoopTemplate.t4** generuje dlouhé jeden soubor. Všimněte si, že jeho přípona byla ".t4", protože nemají být zpracovány přímo po kliknutí na **Transformovat všechny šablony**. Tato šablona má parametr, který určuje oddělovač řetězec, který odděluje segmenty:  
  
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
  
 `LoopSplitter.tt` Vyvolá `LoopTemplate.t4`a pak rozdělí výsledný soubor do jeho segmentů. Všimněte si, že tato šablona nemusí být šablonu modelování protože nenačítá modelu.  
  
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



