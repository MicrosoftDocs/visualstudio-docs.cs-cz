---
title: Generování souborů pomocí nástroje TextTransform | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
ms.assetid: 06a48235-fe02-403e-a1cf-2ae70b4db62f
caps.latest.revision: 43
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 18776795fdf693c855edd3f629d674089daaaebd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666099"
---
# <a name="generating-files-with-the-texttransform-utility"></a>Generování souborů pomocí nástroje TextTransform
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

TextTransform. exe je nástroj příkazového řádku, který můžete použít k transformaci textové šablony. Při volání TextTransform. exe zadáte název souboru textové šablony jako argument. TextTransform. exe volá modul pro transformaci textu a zpracovává textovou šablonu. TextTransform. exe se obvykle volá ze skriptů. Obvykle není to nutné, protože je možné provést transformaci textu buď v aplikaci Visual Studio, nebo v procesu sestavení.

> [!NOTE]
> Chcete-li provést transformaci textu jako součást procesu sestavení, zvažte použití úlohy transformace textu v MSBuild. Další informace naleznete v tématu [generování kódu v procesu sestavení](../modeling/code-generation-in-a-build-process.md). V počítači, na kterém je nainstalován [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], můžete také napsat rozšíření aplikace nebo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], které může transformovat textové šablony. Další informace najdete v tématu [zpracování textových šablon pomocí vlastního hostitele](../modeling/processing-text-templates-by-using-a-custom-host.md).

 TextTransform. exe je umístěn v následujícím adresáři:

 **\Program Files\Common Files\Microsoft Shared\TextTemplating\11.0**

## <a name="syntax"></a>Syntaxe

```
TextTransform [<options>] <templateName>
```

#### <a name="parameters"></a>Parametry

|**Argument**|**Popis**|
|------------------|---------------------|
|`templateName`|Určuje název souboru šablony, který chcete transformovat.|

|**Nastavení**|**Popis**|
|----------------|---------------------|
|**-out** \<filename >|Soubor, na který je napsán výstup transformace.|
|**-r** \<assembly >|Sestavení používané pro kompilaci a spouštění textové šablony.|
|**-u** \<namespace >|Obor názvů, který se používá k kompilování šablony.|
|**-I** \<includedirectory >|Adresář, který obsahuje textové šablony obsažené v zadané textové šabloně.|
|**-P** \<referencepath >|Adresář, ve kterém se mají vyhledat sestavení zadaná v textové šabloně, nebo pro použití možnosti **-r** .<br /><br /> Pokud například chcete zahrnout sestavení používaná pro rozhraní API sady Visual Studio, použijte<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-dp** \<processorName >! \<className >! \<assemblyName&#124;základ kódu >|Název, úplný název typu a sestavení procesoru direktiv, který lze použít ke zpracování vlastních direktiv v rámci textové šablony.|
|**-a** [Processor]! [směrnice]! \<parameterName >! \<parameterValue >|Zadejte hodnotu parametru pro procesor direktiv. Pokud zadáte pouze název parametru a hodnotu, parametr bude k dispozici pro všechny procesory direktiv. Pokud zadáte procesor direktiv, parametr je k dispozici pouze pro zadaný procesor. Pokud zadáte název direktivy, je parametr dostupný pouze při zpracování zadané direktivy.<br /><br />  V textové šabloně zahrňte `hostspecific` v direktivě Template a vyvolejte zprávu `this.Host`. Příklad:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> Vždy zadejte značky '! ', a to i v případě, že vynecháte volitelné názvy procesorů a direktiv. Příklad:<br /><br /> `-a !!param!value`|
|**-h**|Poskytuje podporu.|

## <a name="related-topics"></a>Související témata

|Úloha|Téma|
|----------|-----------|
|Generování souborů v řešení systému [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[Vytvoření kódu v době návrhu pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Zapište procesory direktiv pro transformaci vašich vlastních zdrojů dat.|[Přizpůsobení transformace textu T4](../modeling/customizing-t4-text-transformation.md)|
|Napište šablonováního hostitele s textem, který umožňuje vyvolání textových šablon z vaší vlastní aplikace.|[Zpracování textových šablon pomocí vlastního hostitele](../modeling/processing-text-templates-by-using-a-custom-host.md)|
