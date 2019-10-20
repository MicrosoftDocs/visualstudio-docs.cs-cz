---
title: Generování souborů pomocí nástroje TextTransform
ms.date: 07/26/2019
ms.topic: conceptual
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f1a12da7c7cae7e862d670b3f62fb801920f34e1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666731"
---
# <a name="generate-files-with-the-texttransform-utility"></a>Generování souborů pomocí nástroje TextTransform

TextTransform. exe je nástroj příkazového řádku, který můžete použít k transformaci textové šablony. Při volání TextTransform. exe zadáte název souboru textové šablony jako argument. TextTransform. exe volá modul pro transformaci textu a zpracovává textovou šablonu. TextTransform. exe se obvykle volá ze skriptů. Obvykle není to nutné, protože je možné provést transformaci textu buď v aplikaci Visual Studio, nebo v procesu sestavení.

> [!NOTE]
> Chcete-li provést transformaci textu jako součást procesu sestavení, zvažte použití úlohy transformace textu v MSBuild. Další informace naleznete v tématu [generování kódu v procesu sestavení](../modeling/code-generation-in-a-build-process.md). V počítači, na kterém je nainstalována aplikace Visual Studio, můžete také napsat rozšíření aplikace nebo sady Visual Studio, které umožňuje transformovat textové šablony. Další informace najdete v tématu [zpracování textových šablon pomocí vlastního hostitele](../modeling/processing-text-templates-by-using-a-custom-host.md).

TextTransform. exe je umístěn v následujícím adresáři:

::: moniker range=">=vs-2019"

**\Program Files (x86) \Microsoft Visual Studio\2019\Professional\Common7\IDE**

pro Professional Edition nebo

**\Program Files (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE**

pro Enterprise Edition.

::: moniker-end

::: moniker range="vs-2017"

**\Program Files (x86) \Microsoft Visual Studio\2017\Professional\Common7\IDE**

pro Professional Edition nebo

**\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE**

pro Enterprise Edition.

V předchozích verzích sady Visual Studio se soubor nachází v následujícím umístění:

**\Program Files (x86) \Common Files\Microsoft Shared\TextTemplating \{version}**

kde {Version} závisí na tom, která předchozí verze je nainstalovaná.

::: moniker-end

## <a name="syntax"></a>Syntaxe

```
TextTransform [<options>] <templateName>
```

### <a name="parameters"></a>Parametry

|**Argument**|**Popis**|
|-|-|
|`templateName`|Určuje název souboru šablony, který chcete transformovat.|

|**Nastavení**|**Popis**|
|-|-|
|**-out** \<filename >|Soubor, na který je napsán výstup transformace.|
|**-r** \<assembly >|Sestavení používané pro kompilaci a spouštění textové šablony.|
|**-u** \<namespace >|Obor názvů, který se používá k kompilování šablony.|
|**-I** \<includedirectory >|Adresář, který obsahuje textové šablony obsažené v zadané textové šabloně.|
|**-P** \<referencepath >|Adresář, ve kterém se mají vyhledat sestavení zadaná v textové šabloně, nebo pro použití možnosti **-r** .<br /><br /> Pokud například chcete zahrnout sestavení používaná pro rozhraní API sady Visual Studio, použijte<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-dp** \<processorName >! \<className >! \<assemblyName&#124;základ kódu >|Název, úplný název typu a sestavení procesoru direktiv, který lze použít ke zpracování vlastních direktiv v rámci textové šablony.|
|**-a** [Processor]! [směrnice]! \<parameterName >! \<parameterValue >|Zadejte hodnotu parametru pro procesor direktiv. Pokud zadáte pouze název parametru a hodnotu, parametr bude k dispozici pro všechny procesory direktiv. Pokud zadáte procesor direktiv, parametr je k dispozici pouze pro zadaný procesor. Pokud zadáte název direktivy, je parametr dostupný pouze při zpracování zadané direktivy.<br /><br /> Chcete-li získat přístup k hodnotám parametrů z procesoru direktiv nebo textové šablony, použijte [ITextTemplatingEngineHost. neimplementuje atribut ResolveParameterValue](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\)). V textové šabloně zahrňte `hostspecific` v direktivě Template a vyvolejte zprávu `this.Host`. Příklad:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> Vždy zadejte značky '! ', a to i v případě, že vynecháte volitelné názvy procesorů a direktiv. Příklad:<br /><br /> `-a !!param!value`|
|**-h**|Poskytuje podporu.|

## <a name="related-topics"></a>Související témata

|Úloha|Téma|
|-|-|
|Generování souborů v řešení sady Visual Studio.|[Vytvoření kódu v době návrhu pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Zapište procesory direktiv pro transformaci vašich vlastních zdrojů dat.|[Přizpůsobení transformace textu T4](../modeling/customizing-t4-text-transformation.md)|
|Napište šablonováního hostitele s textem, který umožňuje vyvolání textových šablon z vaší vlastní aplikace.|[Zpracování textových šablon pomocí vlastního hostitele](../modeling/processing-text-templates-by-using-a-custom-host.md)|
