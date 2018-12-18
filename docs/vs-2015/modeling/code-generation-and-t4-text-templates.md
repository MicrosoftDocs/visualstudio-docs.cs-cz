---
title: Generování kódu a textové šablony T4 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: d1310d08138e4df172a5dc9f390d0407a68fe769
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49229817"
---
# <a name="code-generation-and-t4-text-templates"></a>Vytvoření kódu a textové šablony T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], *textové šablony T4* je kombinací textové bloky a logiky ovládacího prvku, který může vytvořit textový soubor. Ovládací prvek logiky je zapsán jako fragmenty kódu programu v [!INCLUDE[csprcs](../includes/csprcs-md.md)] nebo [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]. V aplikaci Visual Studio 2015 Update 2 nebo novější můžete použít funkce verze 6.0 C# ve směrnicích šablony T4. Vygenerovaný soubor může být text jakéhokoli druhu, například webovou stránku nebo soubor prostředků nebo zdrojový kód aplikace v jakémkoli jazyce.  
  
 Existují dva typy textových šablon T4:  
  
 **Spuštění textové šablony T4** ("předzpracovaná' šablony) jsou provedeny v aplikaci k vytvoření textových řetězců, obvykle jako část jeho výstup.  
 Můžete například vytvořit šablonu, která definují stránku HTML:  
  
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
  
 Vaše aplikace mohla spustit na počítači, který nemá [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nainstalované.  
  
 Chcete-li vytvořit šablonu za běhu, přidejte **Předzpracovaný textové šablony** soubor do projektu. Alternativně můžete přidat soubor s prostým textem a nastavte jeho **Custom Tool** vlastnost **TextTemplatingFilePreprocessor**.  
  
 Další informace najdete v tématu [generování textu za běhu pomocí textových šablon T4](../modeling/run-time-text-generation-with-t4-text-templates.md). Další informace o syntaxi šablony najdete v tématu [vytvoření textové šablony T4](../modeling/writing-a-t4-text-template.md).  
  
 **Textové šablony T4 návrhu** jsou provedeny v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] definovat část zdrojového kódu a další prostředky vaší aplikace.  
 Obvykle použít několik šablon, které načítají data v jeden vstupní soubor nebo databáze a generovat některé z vašich `.cs`, `.vb`, nebo jiných zdrojových souborech. Každá šablona generuje jeden soubor. Jsou spouštěny v rámci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nebo [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].  
  
 Vstupní data může být například soubor XML konfigurační data. Pokaždé, když upravíte soubor XML během vývoje, textové šablony by znovu vygenerovat část kódu aplikace. Některé ze šablon mohou vypadat podobně jako v následujícím příkladu:  
  
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
  
 Závisí na hodnoty v souboru XML generované `.cs` soubor bude vypadat takto:  
  
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
>  Termín *modelu* někdy se používá k popisu dat čtených jednu nebo více šablon. Model může být v libovolném formátu v libovolný typ souborů nebo databáze. Nemusí být modelu UML nebo model jazyka specifického pro doménu. "Vzor" právě označuje, že data lze definovat v podmínkách obchodních konceptů, spíše než podobné kód.  
  
 Název funkce transformace textu šablony *T4*.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Generování textu za běhu pomocí textových šablon T4](../modeling/run-time-text-generation-with-t4-text-templates.md)  
 V jakékoli aplikaci, která generuje textové soubory předkompilované textové šablony jsou jednoduchá a spolehlivá metodu definování text. Tato metoda však nelze použít pro textové šablony, které se mění v době běhu.  
  
 [Vytvoření kódu v době návrhu pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)  
 Generování kódu a dalších prostředků z modelu vám umožní aktualizovat aplikace prostřednictvím aktualizace modelu.  
  
 [Vytvoření kódu v procesu sestavení](../modeling/code-generation-in-a-build-process.md)  
 Pokud jste nainstalovali [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Visualization and Modeling SDK, můžete zajistit generované softwaru udržuje aktuální změny v modelu.  
  
 [Zápis textové šablony T4](../modeling/writing-a-t4-text-template.md)  
 Syntaxe soubor textové šablony.  
  
 [Návod: Vytvoření kódu pomocí textových šablon](../modeling/walkthrough-generating-code-by-using-text-templates.md)  
 Ukázka jeden ze způsobů použití generování kódu.  
  
 [Ladění textové šablony T4](../modeling/debugging-a-t4-text-template.md)  
 Postup ladění textové šablony a některé běžné chyby textové šablony.  
  
 [Generování souborů pomocí nástroje TextTransform](../modeling/generating-files-with-the-texttransform-utility.md)  
 Nástroj příkazového řádku, který můžete použít ke spuštění transformace šablony textu.  
  
 [Přizpůsobení transformace textu T4](../modeling/customizing-t4-text-transformation.md)  
 Jak napsat procesorů pro direktivy a hostitelé vlastních šablon pro zdroje dat došlo k chybě.  
  
## <a name="see-also"></a>Viz také  
 [Generování souborů z modelu UML](../modeling/generate-files-from-a-uml-model.md)   
 [Vytváření kódu z jazyka specifického pro doménu](../modeling/generating-code-from-a-domain-specific-language.md)



