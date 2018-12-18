---
title: T4 – Direktiva Include | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c3de9f3-755a-47c5-a30a-65717dcaaac2
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: e8de721b7f26152cd4e7f5df1ee7eb4d04770511
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49835940"
---
# <a name="t4-include-directive"></a>T4 – direktiva Include
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V textové šabloně v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], můžete vložit text z jiného souboru pomocí `<#@include#>` směrnice. Můžete umístit `include` direktivy kamkoli do šablony textu před blok funkcí první třídy `<#+ ... #>`. Zahrnuté soubory mohou také obsahovat `include` direktivy a jiné direktivy. Díky tomu můžete kód šablony a často používaný text sdílet mezi šablonami.  
  
## <a name="using-include-directives"></a>Použití direktiv include  
  
```  
<#@ include file="filePath" [once="true"] #>  
```  
  
- `filePath` může být absolutní nebo relativní k aktuálnímu souboru šablony.  
  
   Kromě toho zvláštní [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozšíření můžou určit vlastní adresáře pro vyhledávání vložených souborů. Například pokud jste nainstalovali Visualization and Modeling SDK (DSL Tools), následující složka se přidá do seznamu pro zahrnutí: `Program Files\Microsoft Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\DSL SDK\DSL Designer\11.0\TextTemplates`.  
  
   Tyto další složky vkládaných souborů mohou záviset na příponě vkládaného souboru. Například nástroje DSL zahrnují složku, která je přístupná pro zahrnutí souborů, které mají příponu souboru `.tt`  
  
- `filePath` může obsahovat proměnné prostředí oddělené znakem "%". Příklad:  
  
  ```  
  <#@ include file="%HOMEPATH%\MyIncludeFile.t4" #>  
  ```  
  
- Název začleněného souboru nemusí používat rozšíření `".tt"`.  
  
   Můžete chtít použít jinou příponu, třeba `".t4"` pro vkládané soubory. Důvodem je, že pokud přidáte `.tt` soubor do projektu, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] automaticky nastaví jeho **Custom Tool** vlastnost `TextTemplatingFileGenerator`. Vkládané soubory obvykle nechcete transformovat individuálně.  
  
   Na druhé straně byste měli vědět, že v některých případech přípona souboru ovlivňuje, v jakých dalších složkách se budou hledat vkládané soubory. To může být důležité, pokud máte vkládaný soubor, který obsahuje jiné soubory.  
  
- Vložený obsah se zpracuje téměř jako kdyby byl součástí textové šablony, která ho vkládá. Však vložit soubor obsahující blok funkcí třídy `<#+...#>` i v případě, `include` – direktiva následuje běžný text a standardní řídicí bloky.  
  
- Použití `once="true"` zajistit, že šablona je zahrnuta pouze jednou, i když je volána z více než jednoho jiného vkládaného souboru.  
  
   Umožňuje tato funkce usnadňuje sestavení knihovny opakovaně použitelných fragmentů T4, kterou můžete v dojde bez obav, který některé další fragment kódu je již součástí je.  Předpokládejme například, že máte knihovnu velmi jemně odstupňovaných fragmentů kódu, které se zabývají zpracování šablon a generování jazyka C#.  Pak tyto jsou používány některé úlohy konkrétní nástroje, jako jsou generování výjimek, které pak můžete použít z libovolné šabloně více specifické pro aplikaci. Pokud si nakreslíte graf závislostí, uvidíte, že některé fragmenty kódu budou vloženy několikrát. Ale `once` parametr zakazuje následné zahrnutí.  
  
  **MyTextTemplate.tt:**  
  
```  
<#@ output extension=".txt" #>  
Output message 1 (from top template).  
<#@ include file="TextFile1.t4"#>  
Output message 5 (from top template).  
<#  
   GenerateMessage(6); // defined in TextFile1.t4  
   AnotherGenerateMessage(7); // defined in TextFile2.t4  
#>  
  
```  
  
 **TextFile1.t4:**  
  
```  
   Output Message 2 (from included file).  
<#@include file="TextFile2.t4" #>  
   Output Message 4 (from included file).  
<#+ // Start of class feature control block.  
void GenerateMessage(int n)  
{  
#>  
   Output Message <#= n #> (from GenerateMessage method).  
<#+  
}  
#>  
  
```  
  
 **TextFile2.t4:**  
  
```  
        Output Message 3 (from included file 2).  
<#+ // Start of class feature control block.  
void AnotherGenerateMessage(int n)  
{  
#>  
       Output Message <#= n #> (from AnotherGenerateMessage method).  
<#+  
}  
#>  
  
```  
  
 **Výsledný vygenerovaný soubor MyTextTemplate.txt:**  
  
```  
Output message 1 (from top template).  
   Output Message 2 (from included file).  
        Output Message 3 (from included file 2).  
  
   Output Message 4 (from included file).  
  
Output message 5 (from top template).  
   Output Message 6 (from GenerateMessage method).  
       Output Message 7 (from AnotherGenerateMessage method).  
  
```  
  
##  <a name="msbuild"></a> Používání vlastností projektu v nástroji MSBuild a sadě Visual Studio  
 Ačkoli v direktivě include lze používat makra sady Visual Studio, například $(SolutionDir), v nástroji MSBuild nefungují. Chcete-li transformovat šablony v sestavovacím počítači, je nutné místo toho použít vlastnosti projektu.  
  
 Úpravou souboru .csproj nebo .vbproj definujte vlastnost projektu. Tento příklad definuje vlastnost s názvem `myIncludeFolder`:  
  
```xml  
<!-- Define a project property, myIncludeFolder: -->  
<PropertyGroup>  
    <myIncludeFolder>$(MSBuildProjectDirectory)\..\libs</myIncludeFolder>  
</PropertyGroup>  
  
<!-- Tell the MSBuild T4 task to make the property available: -->  
<ItemGroup>  
    <T4ParameterValues Include="myIncludeFolder">  
      <Value>$(myIncludeFolder)</Value>  
    </T4ParameterValues>  
  </ItemGroup>  
  
```  
  
 Tuto vlastnost projektu nyní můžete použít v textových šablonách, které se správně transformují jak v sadě Visual Studio, tak v nástroji MSBuild:  
  
```  
<#@ include file="$(myIncludeFolder)\defs.tt" #>  
```



