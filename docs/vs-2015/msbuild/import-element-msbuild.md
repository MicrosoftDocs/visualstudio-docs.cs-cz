---
title: Import – element (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 9f8edefc8e097f7ada67041b807231f594774548
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64833522"
---
# <a name="import-element-msbuild"></a>Import – element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Importuje obsah jednoho souboru projektu do jiného souboru projektu.  
  
 \<Project>  
 \<Import>  
  
## <a name="syntax"></a>Syntax  
  
```  
<Import Project="ProjectPath"  
    Condition="'String A'=='String B'" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Project`|Požadovaný atribut.<br /><br /> Cesta k souboru projektu, který se má importovat Cesta může obsahovat zástupné znaky. Vyhovující soubory jsou importovány v seřazeném pořadí. Pomocí této funkce můžete přidat kód do projektu pouhým přidáním souboru kódu do adresáře.|  
|`Condition`|Nepovinný atribut.<br /><br /> Podmínka, která má být vyhodnocena. Další informace najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[Projekt](../msbuild/project-element-msbuild.md)|Požadovaný kořenový prvek [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] souboru projektu.|  
|[ImportGroup –](../msbuild/importgroup-element.md)|Obsahuje kolekci `Import` prvků seskupených pod volitelnou podmínkou.|  
  
## <a name="remarks"></a>Poznámky  
 Pomocí `Import` elementu lze znovu použít kód, který je společný pro mnoho souborů projektu. To usnadňuje udržování kódu, protože jakékoli aktualizace, které provedete v rámci sdíleného kódu, se rozšíří do všech projektů, které ho importují.  
  
 Podle konvence jsou sdílené importované soubory projektu uloženy jako soubory. targets, ale jedná se o standardní [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] soubory projektu. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] nebrání v importu projektu, který má jinou příponu názvu souboru, doporučujeme ale použít rozšíření. targets pro zajištění konzistence.  
  
 Relativní cesty v importovaných projektech jsou interpretovány relativně k adresáři importovaného projektu. Proto pokud je soubor projektu importován do několika souborů projektu v různých umístěních, relativní cesty v importovaném souboru projektu budou interpretovány jinak pro každý importovaný projekt.  
  
 Všechny [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] vyhrazené vlastnosti, které se vztahují k souboru projektu, například `MSBuildProjectDirectory` a `MSBuildProjectFile` , které jsou odkazovány v importovaném projektu, jsou přiřazeny hodnoty na základě importu souboru projektu.  
  
 Pokud importovaný projekt nemá `DefaultTargets` atribut, importované projekty jsou zkontrolovány v pořadí, v jakém jsou importovány, a je použita hodnota prvního zjištěného `DefaultTargets` atributu. Například pokud Projecta importuje ProjectB a ProjectC (v tomto pořadí) a importy ProjectBd, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] nejdříve se vyhledá `DefaultTargets` v Projecta, pak na ProjectB, pak na projekt a nakonec ProjectC.  
  
 Schéma importovaného projektu je stejné jako standardní projekt. I když [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] může být možné sestavit importovaný projekt, není pravděpodobné, protože importovaný projekt obvykle neobsahuje informace o tom, které vlastnosti se mají nastavit nebo pořadí, ve kterém se mají spustit cíle. Importovaný projekt závisí na projektu, do kterého je importován, aby poskytoval tyto informace.  
  
> [!NOTE]
> I když podmíněné příkazy import fungují v nástrojích příkazového řádku MSBuild, nefungují s nástrojem MSBuild v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrovaném vývojovém prostředí (IDE). Podmíněné importy jsou vyhodnocovány pomocí hodnot konfigurace a platformy, které jsou nastaveny při načtení projektu. Pokud jsou následně provedeny změny, které vyžadují nové vyhodnocení podmínk v souboru projektu, například změna platformy, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] přehodnotí podmínky pro vlastnosti a položky, ale ne pro import. Vzhledem k tomu, že není znovu vyhodnocený podmíněný import, import se přeskočí.  
>   
> Chcete-li se tomuto problému vyhnout, vložte podmíněné importy do souborů. Targets nebo vložte kód do podmíněného bloku, jako je například " [Choose element (MSBuild)](../msbuild/choose-element-msbuild.md) Block.  
  
## <a name="wildcards"></a>Zástupné znaky  
 V .NET Framework 4 umožňuje MSBuild v atributu projektu zástupné znaky. Pokud existují zástupné znaky, všechny nalezené shody jsou seřazené (za účelem reprodukovatelnosti) a poté jsou importovány v tomto pořadí, jako kdyby byla objednávka explicitně nastavena.  
  
 To je užitečné, pokud chcete nabízet bod rozšiřitelnosti, aby mohl někdo jiný importovat soubor bez nutnosti explicitně přidat název souboru do importovaného souboru. Pro tento účel obsahuje Microsoft. Common. targets v horní části souboru následující řádek.  
  
```  
<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore\*" Condition="'$(ImportByWildcardBeforeMicrosoftCommonTargets)' == 'true' and exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore')"/>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje projekt, který obsahuje několik položek a vlastností a importuje obecný soubor projektu.  
  
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
