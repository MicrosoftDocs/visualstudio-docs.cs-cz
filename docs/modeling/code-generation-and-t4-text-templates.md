---
title: Vytvoření kódu a textové šablony T4
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.TextTemplating.TextTemplating
helpviewer_keywords:
- generating text
- .tt files
- code generation
- text templates
- generating code
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a273e6a82bbf99d1a3d57f3759504fedaa5532e6
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2018
ms.locfileid: "39176278"
---
# <a name="code-generation-and-t4-text-templates"></a>Vytvoření kódu a textové šablony T4

V sadě Visual Studio *textové šablony T4* je kombinací textové bloky a logiky ovládacího prvku, který může vytvořit textový soubor. Ovládací prvek logiky je zapsán jako fragmenty kódu programu v [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] nebo [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. V aplikaci Visual Studio 2015 Update 2 nebo novější můžete použít funkce verze 6.0 C# ve směrnicích šablony T4. Vygenerovaný soubor může být text jakéhokoli druhu, například webovou stránku nebo soubor prostředků nebo zdrojový kód aplikace v jakémkoli jazyce.

Existují dva typy textových šablon T4: spuštění a čas návrhu.

## <a name="run-time-t4-text-templates"></a>Spuštění textové šablony T4

Označované také jako "předzpracovaná" šablony, spusťte čas šablony jsou spouštěny ve vaší aplikaci k vytvoření textových řetězců, obvykle jako část jeho výstup. Můžete například vytvořit šablonu, která definují stránku HTML:

```
<html><body>
 The date and time now is: <#= DateTime.Now #>
</body></html>
```

Všimněte si, že šablona vypadá podobně jako generovaný výstup. Podobnost na základě šablony, která má výsledný výstup umožňuje vyhnout se chyby, pokud chcete změnit.

Kromě toho šablona obsahuje fragmenty kódu programu. Tyto fragmenty slouží k opakování úseků textu, aby Podmíněné sekce a zobrazit data z vaší aplikace.

Vaše aplikace generovat výstup, volání funkce, která je generována pomocí šablony. Příklad:

```csharp
string webResponseText = new MyTemplate().TransformText();
```

Vaše aplikace mohla spustit na počítači, který nemá nainstalovanou sadu Visual Studio.

Chcete-li vytvořit šablonu za běhu, přidejte **Předzpracovaný textové šablony** soubor do projektu. Alternativně můžete přidat soubor s prostým textem a nastavte jeho **Custom Tool** vlastnost **TextTemplatingFilePreprocessor**.

Další informace najdete v tématu [generování textu za běhu pomocí textových šablon T4](../modeling/run-time-text-generation-with-t4-text-templates.md). Další informace o syntaxi šablony najdete v tématu [vytvoření textové šablony T4](../modeling/writing-a-t4-text-template.md).

## <a name="design-time-t4-text-templates"></a>Návrh textové šablony T4

Šablony doby návrhu definovat část zdrojového kódu a další prostředky vaší aplikace. Obvykle pomocí několik šablon, které načítají data v jeden vstupní soubor nebo databáze a generovat některé z vašich *.cs*, *.vb*, nebo jiných zdrojových souborech. Každá šablona generuje jeden soubor. Jsou prováděna v rámci sady Visual Studio nebo nástroje MSBuild.

Vstupní data může být například soubor XML konfigurační data. Pokaždé, když upravíte soubor XML během vývoje, znovu textových šablon část kódu aplikace. Některé ze šablon mohou vypadat podobně jako v následujícím příkladu:

```
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml" #>
<#
 System.Xml.XmlDocument configurationData = ...; // Read a data file here.
#>
namespace Fabrikam.<#= configurationData.SelectSingleNode("jobName").Value #>
{
  ... // More code here.
}
```

V závislosti na hodnoty v souboru XML generované *.cs* soubor bude vypadat takto:

```
namespace Fabrikam.FirstJob
{
  ... // More code here.
}
```

Další příklad může být vstup diagram pracovního postupu v obchodních aktivit. Když uživatelé změní jejich obchodních pracovních postupů, nebo při zahájení práce s novým uživatelům, kteří mají jiný pracovní postup, je snadné se znova vygenerovat kód podle nového modelu.

Návrhových šablonách usnadňují rychlejší a spolehlivější a změňte konfiguraci při změně požadavků. Vstup je obvykle definován z hlediska obchodní požadavky, jako v příkladu pracovního postupu. To usnadňuje můžete projednávat změny s uživateli. Návrhových šablonách proto jsou užitečným nástrojem v procesu agilního vývoje.

Chcete-li vytvořit šablonu návrhu, přidejte **textové šablony** soubor do projektu. Alternativně můžete přidat soubor s prostým textem a nastavte jeho **Custom Tool** vlastnost **TextTemplatingFileGenerator**.

Další informace najdete v tématu [vytvoření kódu v době návrhu pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md). Další informace o syntaxi šablony najdete v tématu [vytvoření textové šablony T4](../modeling/writing-a-t4-text-template.md).

> [!NOTE]
> Termín *modelu* někdy se používá k popisu dat čtených jednu nebo více šablon. Model může být v libovolném formátu v libovolný typ souborů nebo databáze. Nemusí být modelu UML nebo model jazyka specifického pro doménu. "Vzor" právě označuje, že data lze definovat v podmínkách obchodních konceptů, spíše než podobné kód.

Název funkce transformace textu šablony *T4*.

## <a name="see-also"></a>Viz také

- [Vytváření kódu z jazyka specifického pro doménu](../modeling/generating-code-from-a-domain-specific-language.md)
