---
title: Vytvoření kódu a textové šablony T4
description: Zjistěte, jak je textová šablona T4 kombinace textových bloků a řídicí logiky, která může generovat textový soubor.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
f1_keywords:
- VS.ToolsOptionsPages.TextTemplating.TextTemplating
helpviewer_keywords:
- generating text
- .tt files
- code generation
- text templates
- generating code
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 76714be09c38f6426626e94ee7734873c823f704
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389771"
---
# <a name="code-generation-and-t4-text-templates"></a>Vytvoření kódu a textové šablony T4

V Visual Studio *textová šablona T4* je kombinace textových bloků a řídicí logiky, která může generovat textový soubor. Řídicí logika se zapisuje jako fragmenty programového kódu v [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] nebo [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] . V Visual Studio 2015 Update 2 a novějších verzích můžete použít funkce jazyka C# verze 6.0 v direktivách šablon T4. Vygenerovaný soubor může být libovolný text, například webová stránka, soubor prostředků nebo zdrojový kód programu v libovolném jazyce.

Existují dva druhy textových šablon T4: doba běhu a doba návrhu.

## <a name="run-time-t4-text-templates"></a>Textové šablony T4 za běhu

Šablony běhu, označované také jako předzpracované šablony, se ve vaší aplikaci spouštěly, aby se vytvářely textové řetězce, obvykle jako součást jejího výstupu. Můžete například vytvořit šablonu pro definování stránky HTML:

```
<html><body>
 The date and time now is: <#= DateTime.Now #>
</body></html>
```

Všimněte si, že šablona vypadá podobně jako vygenerovaný výstup. Podobnost šablony s výsledným výstupem vám pomůže vyhnout se chybám, když ji chcete změnit.

Kromě toho šablona obsahuje fragmenty kódu programu. Pomocí těchto fragmentů můžete opakovat oddíly textu, vytvořit podmíněné oddíly a zobrazit data z vaší aplikace.

K vygenerování výstupu volá aplikace funkci, která je vygenerována šablonou. Příklad:

```csharp
string webResponseText = new MyTemplate().TransformText();
```

Vaše aplikace může běžet na počítači, který nemá nainstalované Visual Studio počítače.

Pokud chcete vytvořit šablonu za běhu, přidejte **do** projektu soubor předzpracované textové šablony. Případně můžete přidat soubor prostého textu a nastavit jeho vlastnost **Vlastní** nástroj na **TextTemplatingFilePreprocessor.**

Další informace najdete v tématu Generování textu za běhu pomocí [textových šablon T4.](../modeling/run-time-text-generation-with-t4-text-templates.md) Další informace o syntaxi šablon najdete v tématu [Zápis textové šablony T4.](../modeling/writing-a-t4-text-template.md)

## <a name="design-time-t4-text-templates"></a>Textové šablony T4 doby návrhu

Šablony času návrhu definují část zdrojového kódu a další prostředky vaší aplikace. Obvykle se používá několik šablon, které čtou data v jednom vstupním souboru nebo databázi a generují některé zdrojové soubory *.cs*, *.vb* nebo jiné. Každá šablona vygeneruje jeden soubor. Jsou spouštěny v rámci Visual Studio nebo MSBuild.

Vstupními daty může být například soubor XML konfiguračních dat. Pokaždé, když upravíte soubor XML během vývoje, textové šablony znovu vygenerují část kódu aplikace. Jedna ze šablon může vypadat podobně jako v následujícím příkladu:

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

V závislosti na hodnotách v souboru XML by vygenerovaný soubor *.cs* měl vypadat takto:

```
namespace Fabrikam.FirstJob
{
  ... // More code here.
}
```

Dalším příkladem může být diagram pracovního postupu v obchodní aktivitě. Když uživatelé změní pracovní postup nebo když začnete pracovat s novými uživateli, kteří mají jiný pracovní postup, je snadné znovu vygenerovat kód tak, aby odpovídal novému modelu.

Šablony v době návrhu urychlí a spolehlivěji změní konfiguraci při změně požadavků. Vstup je obvykle definován z hlediska obchodních požadavků, jako v příkladu pracovního postupu. To usnadňuje diskuzi o změnách s uživateli. Šablony v době návrhu jsou proto užitečným nástrojem v procesu agilní vývoje.

Pokud chcete vytvořit šablonu návrhu, přidejte **do** projektu soubor textové šablony. Případně můžete přidat soubor prostého textu a nastavit jeho vlastnost **Vlastní** nástroj na **TextTemplatingFileGenerator**.

Další informace najdete v tématu [Generování kódu při návrhu pomocí textových šablon T4.](../modeling/design-time-code-generation-by-using-t4-text-templates.md) Další informace o syntaxi šablon najdete v tématu [Zápis textové šablony T4.](../modeling/writing-a-t4-text-template.md)

> [!NOTE]
> Termín *model se* někdy používá k popisu dat přečteých jednou nebo více šablonami. Model může být v libovolném formátu v libovolném typu souboru nebo databáze. Nemusí to být model UML ani model jazyka Domain-Specific modelu. "Model" pouze indikuje, že data je možné definovat z hlediska obchodních konceptů, a nikoli zoznačovat kód.

Funkce transformace textové šablony má název *T4*.

## <a name="see-also"></a>Viz také

- [Vytváření kódu z jazyka specifického pro doménu](../modeling/generating-code-from-a-domain-specific-language.md)
