---
title: Generování kódu a textové šablony T4 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
ms.assetid: 74a0a748-5b11-4999-8bea-49572967827d
caps.latest.revision: 84
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1f34422dfd47efdce9bf837f923da0e139a13398
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667924"
---
# <a name="code-generation-and-t4-text-templates"></a>Vytvoření kódu a textové šablony T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V systému [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] je *Textová šablona T4* kombinací textových bloků a řídicí logiky, která může vygenerovat textový soubor. Logika ovládacího prvku je zapsána jako fragmenty kódu programu v systému [!INCLUDE[csprcs](../includes/csprcs-md.md)] nebo [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] . V systému Visual Studio 2015 Update 2 a novějších můžete použít funkce C# verze 6,0 v direktivách šablon T4. Vygenerovaný soubor může být text libovolného typu, jako je například webová stránka nebo soubor prostředků nebo zdrojový kód programu v libovolném jazyce.

 Existují dva druhy textových šablon T4:

 V aplikaci jsou spouštěny textové **šablony T4** (předzpracované šablony), aby se vytvořily textové řetězce, obvykle jako součást výstupu.
Můžete například vytvořit šablonu pro definování stránky HTML:

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

 Vaše aplikace může běžet na počítači, který není [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nainstalovaný.

 Chcete-li vytvořit šablonu run-time, přidejte do projektu soubor **předzpracované textové šablony** . Alternativně můžete přidat textový soubor a nastavit jeho vlastnost **vlastní nástroj** na **TextTemplatingFilePreprocessor**.

 Další informace najdete v tématu [generování textu v době běhu s textovými šablonami T4](../modeling/run-time-text-generation-with-t4-text-templates.md). Další informace o syntaxi šablon najdete v tématu [zápis textové šablony T4](../modeling/writing-a-t4-text-template.md).

 **Textové šablony T4 v době návrhu** jsou spouštěny v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a definují část zdrojového kódu a další prostředky aplikace.
Obvykle byste použili několik šablon, které čtou data v jednom vstupním souboru nebo databázi, a vygenerujete některé z vašich `.cs` , `.vb` nebo jiných zdrojových souborů. Každá šablona generuje jeden soubor. Jsou spouštěny v rámci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nebo [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .

 Vstupní data by například mohla být soubor XML s konfiguračními daty. Při každém úpravách souboru XML během vývoje by textové šablony znovu vygenerovaly část kódu aplikace. Jedna ze šablon by mohla vypadat podobně jako v následujícím příkladu:

```
<#@ output extension=".txt" #>
<#@ assembly name="System.Xml" #>
<#
 System.Xml.XmlDocument configurationData = ...; // Read a data file here.
#>
namespace Fabrikam.<#= configurationData.SelectSingleNode("jobName").Value #>
{
  ... // More code here.
}

```

 V závislosti na hodnotách v souboru XML, vygenerovaný `.cs` soubor by vypadal takto:

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

## <a name="in-this-section"></a>V tomto oddílu
 [Generování textu v běhu s textovými šablonami T4](../modeling/run-time-text-generation-with-t4-text-templates.md) V jakékoli aplikaci, která generuje textové soubory, jsou předkompilované šablony textu snadno a spolehlivější způsob definování textu. Tuto metodu však nelze použít pro textové šablony, které se mění v době běhu.

 [Vytváření kódu v době návrhu pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md) Generování kódu a dalších prostředků z modelu umožňuje aktualizovat aplikaci aktualizací modelu.

 [Generování kódu v procesu sestavení](../modeling/code-generation-in-a-build-process.md) Pokud jste nainstalovali [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sadu vizualizací a modelování SDK, můžete zajistit, že vygenerovaný software zůstane v aktuálním stavu se změnami v modelu.

 [Zápis textové šablony T4](../modeling/writing-a-t4-text-template.md) Syntaxe souboru textové šablony

 [Návod: generování kódu pomocí textových šablon](../modeling/walkthrough-generating-code-by-using-text-templates.md) Ukázka jednoho způsobu použití generování kódu.

 [Ladění textové šablony T4](../modeling/debugging-a-t4-text-template.md) Jak ladit textové šablony a některé běžné chyby textových šablon.

 [Generování souborů pomocí nástroje TextTransform](../modeling/generating-files-with-the-texttransform-utility.md) Nástroj příkazového řádku, který lze použít ke spuštění transformací šablon textu.

 [Přizpůsobení transformace textu T4](../modeling/customizing-t4-text-transformation.md) Jak psát procesory direktiv a vlastní hostitele šablonování pro vlastní zdroje dat.

## <a name="see-also"></a>Viz také
 [Generování souborů z modelu UML](../modeling/generate-files-from-a-uml-model.md) [generování kódu z jazyka specifického pro doménu](../modeling/generating-code-from-a-domain-specific-language.md)
