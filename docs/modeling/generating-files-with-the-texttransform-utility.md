---
title: Generování souborů pomocí nástroje TextTransform
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 554ed126aa46b15148b902b901d8e9b664e3cdbd
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062293"
---
# <a name="generate-files-with-the-texttransform-utility"></a>Generování souborů pomocí nástroje TextTransform

TextTransform.exe je nástroj příkazového řádku, který vám pomůže transformace textové šablony. Při volání TextTransform.exe zadáte jako argument název soubor textové šablony. TextTransform.exe zavolá stroj pro transformaci textu a zpracuje textové šablony. TextTransform.exe je obvykle volána pomocí skriptů. Není však obvykle vyžaduje, protože provedením transformace textu ve Visual Studiu nebo v procesu sestavení.

> [!NOTE]
> Pokud chcete provést transformaci textu jako součást procesu sestavení, zvažte použití nástroje MSBuild úlohy transformace textu. Další informace najdete v tématu [generování kódu v procesu sestavení](../modeling/code-generation-in-a-build-process.md). Na počítači, na kterém je nainstalovaná sada Visual Studio můžete taky psát aplikace nebo rozšíření sady Visual Studio, který může transformace textových šablon. Další informace najdete v tématu [zpracování textových šablon pomocí vlastního hostitele](../modeling/processing-text-templates-by-using-a-custom-host.md).

 TextTransform.exe se nachází v následujícím adresáři:

 **\Program Files (x86)\Microsoft Visual Studio\2017\Professional\Common7\IDE**

pro edice Professional nebo

 **\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE**

 pro Enterprise edition.

V předchozích verzích sady Visual Studio se soubor nachází v následujícím umístění:

**\Program Files (x86)\Common Files\Microsoft Shared\TextTemplating\{version}**

Pokud {version} závisí na nainstalované předchozí verze.

## <a name="syntax"></a>Syntaxe

```
TextTransform [<options>] <templateName>
```

### <a name="parameters"></a>Parametry

|**Argument**|**Popis**|
|-|-|
|`templateName`|Určuje název souboru šablony, který chcete transformovat.|

|**Možnost**|**Popis**|
|-|-|
|**-out** \<název souboru >|Soubor, ke kterému je zapsán výstup transformace.|
|**-r** \<sestavení >|Používá se pro kompilaci a spuštění textové šablony sestavení.|
|**-u** \<oboru názvů >|Obor názvů, který se používá pro kompilaci šablony.|
|**-I** \<includedirectory >|Adresář, který obsahuje textové šablony, který je součástí zadané textové šablony.|
|**-P** \<referencepath >|Adresář pro vyhledávání sestavení zadaných v rámci textové šablony nebo pro použití **- r** možnost.<br /><br /> Například pokud chcete zahrnout sestavení pro rozhraní API sady Visual Studio, použijte<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-dp** \<processorName >!\< Název třídy >! \<assemblyName&#124;codeBase >|Název, úplný název typu a sestavení, který slouží ke zpracování vlastních direktiv v textové šabloně procesoru direktiv.|
|**-a** [processorName]! [directiveName]! \<parameterName >! \<parameterValue >|Zadejte hodnotu parametru pro procesor direktiv. Pokud zadáte pouze název parametru a hodnota, bude parametr k dispozici všechny procesory direktiv. Pokud chcete zadat procesor direktiv, parametr je k dispozici pouze do určeným procesorem. Pokud zadáte název direktivy, parametr je k dispozici pouze v případě, že zadané – direktiva se zpracovává.<br /><br /> Chcete-li přístup hodnoty parametrů z procesoru direktiv nebo textové šablony, použijte [ITextTemplatingEngineHost.ResolveParameterValue](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\)). V textové šabloně, patří `hostspecific` v direktivě šablony a vyvolat zprávu na `this.Host`. Příklad:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> Zadávejte vždy "!" označí, i v případě, že vynecháte volitelné procesoru a názvů direktiv. Příklad:<br /><br /> `-a !!param!value`|
|**-h**|Poskytuje nápovědu.|

## <a name="related-topics"></a>Související témata

|Úloha|Téma|
|-|-|
|Generování souborů v řešení sady Visual Studio.|[Vytvoření kódu v době návrhu pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Procesory direktiv pro transformaci zdrojích dat zápisu.|[Přizpůsobení transformace textu T4](../modeling/customizing-t4-text-transformation.md)|
|Zápis hostitele šablonování textu, který umožňuje vyvolat textových šablon z vaší aplikace.|[Zpracování textových šablon pomocí vlastního hostitele](../modeling/processing-text-templates-by-using-a-custom-host.md)|
