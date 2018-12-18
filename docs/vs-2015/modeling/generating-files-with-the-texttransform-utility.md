---
title: Generování souborů pomocí nástroje TextTransform | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
ms.assetid: 06a48235-fe02-403e-a1cf-2ae70b4db62f
caps.latest.revision: 43
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: e7dbe189c9b46c10dc7bac5da4b87457d7c6ecbf
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49227445"
---
# <a name="generating-files-with-the-texttransform-utility"></a>Generování souborů pomocí nástroje TextTransform
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

TextTransform.exe je nástroj příkazového řádku, který vám pomůže transformace textové šablony. Při volání TextTransform.exe zadáte jako argument název soubor textové šablony. TextTransform.exe zavolá stroj pro transformaci textu a zpracuje textové šablony. TextTransform.exe je obvykle volána pomocí skriptů. Není však obvykle vyžaduje, protože provedením transformace textu ve Visual Studiu nebo v procesu sestavení.  
  
> [!NOTE]
>  Pokud chcete provést transformaci textu jako součást procesu sestavení, zvažte použití nástroje MSBuild úlohy transformace textu. Další informace najdete v tématu [generování kódu v procesu sestavení](../modeling/code-generation-in-a-build-process.md). V počítači, ve kterém [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] je nainstalovaný, můžete je zapsat také aplikace nebo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozšíření, které můžete transformace textových šablon. Další informace najdete v tématu [zpracování textových šablon pomocí vlastního hostitele](../modeling/processing-text-templates-by-using-a-custom-host.md).  
  
 TextTransform.exe se nachází v následujícím adresáři:  
  
 **\Program Files\Microsoft Shared\TextTemplating\11.0**  
  
## <a name="syntax"></a>Syntaxe  
  
```  
TextTransform [<options>] <templateName>  
```  
  
#### <a name="parameters"></a>Parametry  
  
|**Argument**|**Popis**|  
|------------------|---------------------|  
|`templateName`|Určuje název souboru šablony, který chcete transformovat.|  
  
|**Možnost**|**Popis**|  
|----------------|---------------------|  
|**-out** \<název souboru >|Soubor, ke kterému je zapsán výstup transformace.|  
|**-r** \<sestavení >|Používá se pro kompilaci a spuštění textové šablony sestavení.|  
|**-u** \<oboru názvů >|Obor názvů, který se používá pro kompilaci šablony.|  
|**-I** \<includedirectory >|Adresář, který obsahuje textové šablony, který je součástí zadané textové šablony.|  
|**-P** \<referencepath >|Adresář pro vyhledávání sestavení zadaných v rámci textové šablony nebo pro použití **- r** možnost.<br /><br /> Například pokud chcete zahrnout sestavení pro rozhraní API sady Visual Studio, použijte<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|  
|**-dp** \<processorName >!\< Název třídy >! \<assemblyName&#124;codeBase >|Název, úplný název typu a sestavení, který slouží ke zpracování vlastních direktiv v textové šabloně procesoru direktiv.|  
|**-a** [processorName]! [directiveName]! \<parameterName >! \<parameterValue >|Zadejte hodnotu parametru pro procesor direktiv. Pokud zadáte pouze název parametru a hodnota, bude parametr k dispozici všechny procesory direktiv. Pokud chcete zadat procesor direktiv, parametr je k dispozici pouze do určeným procesorem. Pokud zadáte název direktivy, parametr je k dispozici pouze v případě, že zadané – direktiva se zpracovává.<br /><br />  V textové šabloně, patří `hostspecific` v direktivě šablony a vyvolat zprávu na `this.Host`. Příklad:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> Zadávejte vždy "!" označí, i v případě, že vynecháte volitelné procesoru a názvů direktiv. Příklad:<br /><br /> `-a !!param!value`|  
|**-h**|Poskytuje nápovědu.|  
  
## <a name="related-topics"></a>Související témata  
  
|Úloha|Téma|  
|----------|-----------|  
|Generování souborů v řešení systému [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[Vytvoření kódu v době návrhu pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|  
|Procesory direktiv pro transformaci zdrojích dat zápisu.|[Přizpůsobení transformace textu T4](../modeling/customizing-t4-text-transformation.md)|  
|Zápis hostitele šablonování textu, který umožňuje vyvolat textových šablon z vaší aplikace.|[Zpracování textových šablon pomocí vlastního hostitele](../modeling/processing-text-templates-by-using-a-custom-host.md)|



