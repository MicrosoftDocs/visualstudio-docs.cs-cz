---
title: Import – Element (MSBuild) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7dd5b0aa6f0ed56aaa3315c03aeef6ed1b77ad62
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49839606"
---
# <a name="import-element-msbuild"></a>Import – element (MSBuild)
Importuje obsah jednoho souboru projektu do jiného souboru projektu.  

 \<Project>  
 \<Import >  

## <a name="syntax"></a>Syntaxe  

```xml  
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

### <a name="child-elements"></a>Podřízené prvky  
 Žádné  

### <a name="parent-elements"></a>Nadřazené prvky  

| Prvek | Popis |
| - | - |
| [Projekt](../msbuild/project-element-msbuild.md) | Požadovaný kořenový element [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] souboru projektu. |
| [Importgroup –](../msbuild/importgroup-element.md) | Obsahuje kolekci `Import` prvky seskupené pod nadpisem nepovinnou podmínku. |

## <a name="remarks"></a>Poznámky  
 S použitím `Import` element, můžete znovu použít kód, který je společná pro mnoho souborů projektu. Díky tomu je snazší údržbu kódu, protože všechny aktualizace, které provedete sdílený kód získat rozšíří do všech projektů, které naimportujete.  

 Podle konvence jsou uloženy soubory sdílený projekt importovaný jako *.targets* soubory, ale jsou standardní [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] soubory projektu. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] není by vám bránily importu projektu, který má příponu názvu souboru jiné, ale doporučujeme použít *.targets* rozšíření pro zajištění konzistence.  

 Relativní cesty importovaných projekty jsou interpretovány relativní k adresáři importu projektu. Proto pokud soubor projektu je importovat do několika souborů projektu v různých umístěních, relativní cesty v importovaném projektu souboru budou interpretovány odlišně pro každý importovaný projekt.  

 Všechny [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] rezervované vlastnosti, které se vztahují k souboru projektu, například `MSBuildProjectDirectory` a `MSBuildProjectFile`, který je odkazováno v importovaném projektu jsou přiřazeny hodnoty na základě importu souboru projektu.  

 Pokud importovaném projektu nemá `DefaultTargets` atribut importovat projekty jsou kontrolovány v pořadí, ve kterém se importují, a hodnotu prvního zjištění `DefaultTargets` atribut se používá. Například, pokud ProjectA importuje ProjectB a ProjectC (v uvedeném pořadí) a ProjectB importuje ProjectD [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] nejprve hledá `DefaultTargets` zadat pro výzkum, pak ProjectB, pak ProjectD a nakonec ProjectC.  

 Schéma importovaném projektu je stejný jako u standardní projekt. I když [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] může být možné sestavit importovaném projektu, nepravděpodobné, protože importovaném projektu obvykle neobsahuje informace o vlastnosti, které k sadě nebo pořadí, ve kterém se spustí cíle. Importovaném projektu závisí na projektu, do kterého je importován předejte tyto informace.  

> [!NOTE]
>  Do příkazového řádku MSBuilds práci import podmíněné příkazy, nefungují, pomocí nástroje MSBuild v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrované vývojové prostředí (IDE). Podmíněné importy vyhodnocují se pomocí hodnoty konfigurace a platformy, které jsou nastaveny při načtení projektu. Pokud následně změn, které vyžadují přehodnocení podmíněné příkazy v souboru projektu, například změna platformu, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] přehodnotí podmínky vlastností a položek, ale ne importy. Protože podmíněné import již není znovu, import se přeskočí.  
> 
>  Chcete-li tento problém obejít, umístěte podmíněné importy *.targets* soubory nebo vložení kód s podmínkou blokovat, jako [zvolit – element (MSBuild)](../msbuild/choose-element-msbuild.md) bloku.  

## <a name="wildcards"></a>Zástupné znaky  
 V rozhraní .NET Framework 4 nástroj MSBuild umožňuje zástupné znaky v atributu projektu. Po zástupné znaky se nalezeny všechny shody jsou seřazené (pro reprodukovatelnost) a potom jejich importování v tomto pořadí jakoby pořadí měli explicitně nastavit.  

 To je užitečné, pokud chcete nabízet bod rozšiřitelnosti, aby někdo mohl importovat soubor bez nutnosti explicitně přidat název souboru do souboru importu. Pro tento účel *cílů Microsoft.Common.Targets* obsahuje následující řádek na začátek souboru.  

```xml  
<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore\*" Condition="'$(ImportByWildcardBeforeMicrosoftCommonTargets)' == 'true' and exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore')"/>  
```  

## <a name="example"></a>Příklad  
 Následující příklad ukazuje projekt, který má několik položek a vlastností a importuje soubor obecné projektu.  

```xml  
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

## <a name="see-also"></a>Viz také:  
 [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)   
 [Postupy: použití stejného cíle ve více souborech projektu](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)
