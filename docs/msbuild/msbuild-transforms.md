---
title: Transformace nástroje MSBuild | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bcfc3c-14fa-455e-805c-63ccffa4a3bf
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b1a3ff7cbd2025a909ab0c5fb044bb61b24388ff
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151197"
---
# <a name="msbuild-transforms"></a>Transformace nástroje MSBuild
Transformace je 1: 1 převod jednu položku seznamu do jiného. Kromě povolení projekt převést seznamy položek, umožňuje transformace cíl k identifikaci přímé mapování mezi její vstupy a výstupy. Toto téma vysvětluje, transformace a jak [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] používá k sestavení projektů efektivněji.  
  
## <a name="transform-modifiers"></a>Transformace modifikátory  
Transformace nejsou libovolného, ale se uplatňuje limit vycházející speciální syntaxe, ve kterém všechny transformace modifikátory musí být ve formátu %(\<ItemMetaDataName >). Veškerá metadata položky můžete použít jako modifikátor transformace. To zahrnuje známá metadata položky, která je přiřazená každé položce při jeho vytvoření. Seznam známá metadata položky, naleznete v tématu [známá metadata položky](../msbuild/msbuild-well-known-item-metadata.md).  
  
V následujícím příkladu, seznam *RESX* soubory se transformuje na seznam *.resources* soubory. Určuje modifikátor %(filename) transformace každý *.resources* soubor má stejný název jako odpovídající *RESX* souboru.  
  
```xml  
@(RESXFile->'%(filename).resources')  
```

Například, pokud jsou položky v seznamu položek @(RESXFile) *Form1.resx*, *Form2.resx*, a *Form3.resx*, budou výstupy v seznamu transformovaný  *Form1.Resources*, *Form2.resources*, a *Form3.resources*.  

> [!NOTE]
>  Vlastní oddělovač pro transformovaná položky seznamu můžete zadat stejným způsobem zadejte oddělovač pro standardní položky seznamu. Například samostatné transformovaný položky seznamu oddělte čárkou (,) namísto výchozí středníkem (;), použijte následující kód XML:  
> `@(RESXFile->'Toolset\%(filename)%(extension)', ',')`
  
## <a name="use-multiple-modifiers"></a>Použití více modifikátory  
 Transformace výraz může obsahovat více modifikátory, ve kterých je možné kombinovat v libovolném pořadí a lze je opakovat. V následujícím příkladu se změní název adresáře, který obsahuje soubory, ale soubory zachovat původní přípona názvu název a soubor.  
  
```xml  
@(RESXFile->'Toolset\%(filename)%(extension)')  
```  
  
 Například, pokud položek, které jsou součástí `RESXFile` položky seznamu jsou *Project1\Form1.resx*, *Project1\Form2.resx*, a *Project1\Form3.text*, výstupy v seznamu transformovaný bude *Toolset\Form1.resx*, *Toolset\Form2.resx*, a *Toolset\Form3.text*.  
  
## <a name="dependency-analysis"></a>Analýza závislosti  
 Transformace zaručit mapování 1: 1 mezi transformovaný položky seznamu a původní seznam položek. Proto, pokud cíl vytvoří výstupy, které jsou transformací vstupních hodnot, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] můžete analyzovat časová razítka vstupy a výstupy a rozhodnout, jestli se má přeskočit, sestavení nebo částečně znovu sestavit cíl.  
  
 V [úlohu kopírování](../msbuild/copy-task.md) v následujícím příkladu každý soubor v `BuiltAssemblies` seznamu položek se mapuje na soubor v cílové složce úkolů, zadat pomocí transformace `Outputs` atribut. Pokud soubor v `BuiltAssemblies` položky seznamu změny `Copy` úloha je spuštěna pouze změněný soubor a všechny ostatní soubory se přeskočí. Další informace o analýzu závislostí a jak pomocí transformace, najdete v části [postupy: přírůstkové sestavování](../msbuild/how-to-build-incrementally.md).  
  
```xml  
<Target Name="CopyOutputs"  
    Inputs="@(BuiltAssemblies)"  
    Outputs="@(BuiltAssemblies -> '$(OutputPath)%(Filename)%(Extension)')">  
  
    <Copy  
        SourceFiles="@(BuiltAssemblies)"  
        DestinationFolder="$(OutputPath)"/>  
  
</Target>  
```  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] soubor projektu, který používá transformací. Tento příklad předpokládá, že existuje pouze jedna *XSD* soubor *c:\sub0\sub1\sub2\sub3* adresáře a že je v pracovním adresáři *c:\sub0*.  
  
### <a name="code"></a>Kód  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Schema Include="sub1\**\*.xsd"/>  
    </ItemGroup>  
  
    <Target Name="Messages">  
        <Message Text="rootdir: @(Schema->'%(rootdir)')"/>  
        <Message Text="fullpath: @(Schema->'%(fullpath)')"/>  
        <Message Text="rootdir + directory + filename + extension: @(Schema->'%(rootdir)%(directory)%(filename)%(extension)')"/>  
        <Message Text="identity: @(Schema->'%(identity)')"/>  
        <Message Text="filename: @(Schema->'%(filename)')"/>  
        <Message Text="directory: @(Schema->'%(directory)')"/>  
        <Message Text="relativedir: @(Schema->'%(relativedir)')"/>  
        <Message Text="extension: @(Schema->'%(extension)')"/>  
    </Target>  
</Project>  
```  
  
### <a name="comments"></a>Komentáře  
 Tento příklad vytvoří následující výstup:  
  
```  
rootdir: C:\  
fullpath: C:\xmake\sub1\sub2\sub3\myfile.xsd  
rootdir + directory + filename + extension: C:\xmake\sub1\sub2\sub3\myfile.xsd  
identity: sub1\sub2\sub3\myfile.xsd  
filename: myfile  
directory: xmake\sub1\sub2\sub3\  
relativedir: sub1\sub2\sub3\  
extension: .xsd  
```  
  
## <a name="see-also"></a>Viz také:  
 [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)   
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)   
 [Postupy: přírůstkové sestavování](../msbuild/how-to-build-incrementally.md)