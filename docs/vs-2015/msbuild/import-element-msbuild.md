---
title: Import – Element (MSBuild) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Import
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Import element [MSBuild]
- <Import> element [MSBuild]
ms.assetid: 3bfecaf1-69fd-4008-b651-c9dafd4389d9
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 575fd2e83abd309b67e6e1684fd38b8d5c9953ac
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49248466"
---
# <a name="import-element-msbuild"></a>Import – element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Importuje obsah jednoho souboru projektu do jiného souboru projektu.  
  
 \<Project>  
 \<Import >  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<Import Project="ProjectPath"  
    Condition="'String A'=='String B'" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Project`|Požadovaný atribut.<br /><br /> Cesta souboru projektu k importu. Cesta může obsahovat zástupné znaky. Odpovídající soubory importují v seřazeném pořadí. Pomocí této funkce můžete přidat kód do projektu pouze přidáním kódu souboru do adresáře.|  
|`Condition`|Nepovinný atribut.<br /><br /> Stav, který se má vyhodnotit. Další informace najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[Projekt](../msbuild/project-element-msbuild.md)|Požadovaný kořenový element [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] souboru projektu.|  
|[Importgroup –](../msbuild/importgroup-element.md)|Obsahuje kolekci `Import` prvky seskupené pod nadpisem nepovinnou podmínku.|  
  
## <a name="remarks"></a>Poznámky  
 S použitím `Import` element, můžete znovu použít kód, který je společná pro mnoho souborů projektu. Díky tomu je snazší údržbu kódu, protože všechny aktualizace, které provedete sdílený kód získat rozšíří do všech projektů, které naimportujete.  
  
 Podle konvence jsou uloženy soubory sdílený projekt importovaný jako – soubory .targets, ale jsou standardní [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] soubory projektu. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] není by vám bránily importu projektu, který má příponu názvu souboru jiné, ale doporučujeme použít rozšíření .targets pro zajištění konzistence.  
  
 Relativní cesty importovaných projekty jsou interpretovány relativní k adresáři importu projektu. Proto pokud soubor projektu je importovat do několika souborů projektu v různých umístěních, relativní cesty v importovaném projektu souboru budou interpretovány odlišně pro každý importovaný projekt.  
  
 Všechny [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] rezervované vlastnosti, které se vztahují k souboru projektu, například `MSBuildProjectDirectory` a `MSBuildProjectFile`, který je odkazováno v importovaném projektu jsou přiřazeny hodnoty na základě importu souboru projektu.  
  
 Pokud importovaném projektu nemá `DefaultTargets` atribut importovat projekty jsou kontrolovány v pořadí, ve kterém se importují, a hodnotu prvního zjištění `DefaultTargets` atribut se používá. Například, pokud ProjectA importuje ProjectB a ProjectC (v uvedeném pořadí) a ProjectB importuje ProjectD [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] nejprve hledá `DefaultTargets` zadat pro výzkum, pak ProjectB, pak ProjectD a nakonec ProjectC.  
  
 Schéma importovaném projektu je stejný jako u standardní projekt. I když [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] může být možné sestavit importovaném projektu, nepravděpodobné, protože importovaném projektu obvykle neobsahuje informace o vlastnosti, které k sadě nebo pořadí, ve kterém se spustí cíle. Importovaném projektu závisí na projektu, do kterého je importován předejte tyto informace.  
  
> [!NOTE]
>  Do příkazového řádku MSBuilds práci import podmíněné příkazy, nefungují, pomocí nástroje MSBuild v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrované vývojové prostředí (IDE). Podmíněné importy vyhodnocují se pomocí hodnoty konfigurace a platformy, které jsou nastaveny při načtení projektu. Pokud následně změn, které vyžadují přehodnocení podmíněné příkazy v souboru projektu, například změna platformu, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] přehodnotí podmínky vlastností a položek, ale ne importy. Protože podmíněné import již není znovu, import se přeskočí.  
>   
>  Chcete-li tento problém obejít, umístěte podmíněné importy v souborech .targets nebo ukládejte kód podmíněný blok, jako [zvolte – Element (MSBuild)](../msbuild/choose-element-msbuild.md) bloku.  
  
## <a name="wildcards"></a>Zástupné znaky  
 V rozhraní .NET Framework 4 nástroj MSBuild umožňuje zástupné znaky v atributu projektu. Po zástupné znaky se nalezeny všechny shody jsou seřazené (pro reprodukovatelnost) a potom jejich importování v tomto pořadí jakoby pořadí měli explicitně nastavit.  
  
 To je užitečné, pokud chcete nabízet bod rozšiřitelnosti, aby někdo mohl importovat soubor bez nutnosti explicitně přidat název souboru do souboru importu. Pro tento účel Microsoft.Common.Targets obsahuje následující řádek na začátek souboru.  
  
```  
<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore\*" Condition="'$(ImportByWildcardBeforeMicrosoftCommonTargets)' == 'true' and exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore')"/>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje projekt, který má několik položek a vlastností a importuje soubor obecné projektu.  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <resourcefile>Strings.resx</resourcefile>  
  
        <compiledresources>  
            $(O)\$(MSBuildProjectName).Strings.resources  
        </compiledresources>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <CSFile Include="*.cs" />  
  
        <Reference Include="System" />  
        <Reference Include="System.Data" />  
    </ItemGroup>  
  
    <Import Project="$(CommonLocation)\General.targets" />  
</Project>  
```  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)   
 [Postupy: Použití stejného cíle ve více souborech projektu](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)



