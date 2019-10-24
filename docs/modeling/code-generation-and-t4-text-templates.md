---
title: Vytvoření kódu a textové šablony T4
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.TextTemplating.TextTemplating
helpviewer_keywords:
- generating text
- .tt files
- code generation
- text templates
- generating code
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8d3684ac79ce0dde8641e11a455238d927f2adb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748510"
---
# <a name="code-generation-and-t4-text-templates"></a>Vytvoření kódu a textové šablony T4

V aplikaci Visual Studio je *Textová šablona T4* kombinací textových bloků a řídicí logiky, která může vygenerovat textový soubor. Logika ovládacího prvku je zapsána jako fragmenty kódu programu v [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] nebo [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. V systému Visual Studio 2015 Update 2 a novějších můžete použít C# funkce verze 6,0 v direktivách šablon T4. Vygenerovaný soubor může být text libovolného typu, jako je například webová stránka nebo soubor prostředků nebo zdrojový kód programu v libovolném jazyce.

Existují dva druhy textových šablon T4: doba běhu a doba návrhu.

## <a name="run-time-t4-text-templates"></a>Šablony textu T4 v době běhu

Známé také jako šablony předzpracovaného běhu jsou spouštěny ve vaší aplikaci, aby vytvořily textové řetězce, obvykle jako součást výstupu. Můžete například vytvořit šablonu pro definování stránky HTML:

```
<html><body>
 The date and time now is: <#= DateTime.Now #>
</body></html>
```

Všimněte si, že šablona se podobá vygenerovanému výstupu. Podobnost šablony s výsledným výstupem vám pomůže vyhnout se chybám, když je chcete změnit.

Kromě toho šablona obsahuje fragmenty kódu programu. Tyto fragmenty můžete použít k opakování oddílů textu, k vytvoření podmíněných oddílů a k zobrazení dat z aplikace.

Chcete-li vygenerovat výstup, vaše aplikace volá funkci, která je vygenerována šablonou. Příklad:

```csharp
string webResponseText = new MyTemplate().TransformText();
```

Vaše aplikace může běžet na počítači, na kterém není nainstalovaná aplikace Visual Studio.

Chcete-li vytvořit šablonu run-time, přidejte do projektu soubor **předzpracované textové šablony** . Alternativně můžete přidat textový soubor a nastavit jeho vlastnost **vlastní nástroj** na **TextTemplatingFilePreprocessor**.

Další informace najdete v tématu [generování textu v době běhu s textovými šablonami T4](../modeling/run-time-text-generation-with-t4-text-templates.md). Další informace o syntaxi šablon najdete v tématu [zápis textové šablony T4](../modeling/writing-a-t4-text-template.md).

## <a name="design-time-t4-text-templates"></a>Šablony textu T4 v době návrhu

Šablony návrhu definují část zdrojového kódu a dalších prostředků vaší aplikace. Obvykle používáte několik šablon, které čtou data v jednom vstupním souboru nebo databázi, a vygenerujete některé z vašich souborů *. cs*, *. vb*nebo jiných zdrojových souborů. Každá šablona generuje jeden soubor. Jsou spouštěny v sadě Visual Studio nebo MSBuild.

Vstupní data by například mohla být soubor XML s konfiguračními daty. Kdykoli upravíte soubor XML během vývoje, textové šablony znovu vygenerují část kódu aplikace. Jedna ze šablon by mohla vypadat podobně jako v následujícím příkladu:

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

V závislosti na hodnotách v souboru XML by generovaný soubor *. cs* vypadal takto:

```
namespace Fabrikam.FirstJob
{
  ... // More code here.
}
```

Jako další příklad může být vstup diagram pracovního postupu v obchodní aktivitě. Když uživatelé změní svůj obchodní pracovní postup nebo když začnete pracovat s novými uživateli, kteří mají jiný pracovní postup, můžete kód snadno vygenerovat tak, aby odpovídal novému modelu.

Šablony návrhu umožňují rychlejší a spolehlivější změnu konfigurace v případě změny požadavků. Obvykle je vstup definovaný v souladu s obchodními požadavky, jako v příkladu pracovního postupu. Díky tomu je snazší diskutovat o změnách s vašimi uživateli. Šablony návrhu jsou proto užitečným nástrojem v procesu agilního vývoje.

Chcete-li vytvořit šablonu pro dobu návrhu, přidejte do projektu soubor **textové šablony** . Alternativně můžete přidat textový soubor a nastavit jeho vlastnost **vlastní nástroj** na **hodnotu TextTemplatingFileGenerator**.

Další informace najdete v tématu [generování kódu v době návrhu pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md). Další informace o syntaxi šablon najdete v tématu [zápis textové šablony T4](../modeling/writing-a-t4-text-template.md).

> [!NOTE]
> Termínový *model* se někdy používá k popisu dat přečtených jednou nebo více šablonami. Model může být v libovolném formátu v jakémkoli typu souboru nebo databáze. Nemusí se jednat o model UML ani model jazyka specifického pro doménu. Model označuje pouze to, že data lze definovat v rámci obchodních konceptů místo toho, aby se nemusela podobat kódu.

Funkce transformace textové šablony má název *T4*.

## <a name="see-also"></a>Viz také:

- [Vytváření kódu z jazyka specifického pro doménu](../modeling/generating-code-from-a-domain-specific-language.md)
