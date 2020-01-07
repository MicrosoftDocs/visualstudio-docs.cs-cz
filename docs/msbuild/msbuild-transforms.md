---
title: Nástroj MSBuild transformuje | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bcfc3c-14fa-455e-805c-63ccffa4a3bf
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5c4262ed1a7b92170565f7006c9ed06ed884f928
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593769"
---
# <a name="msbuild-transforms"></a>Transformace nástroje MSBuild
Transformace je převod 1:1 na jeden seznam položek na jiný. Kromě povolení projektu pro převod seznamů položek umožňuje transformace cíli identifikovat přímé mapování mezi vstupy a výstupy. Toto téma vysvětluje transformace a způsob, jakým [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] používá k efektivnějšímu vytváření projektů.

## <a name="transform-modifiers"></a>Modifikátory transformace
Transformace nejsou žádné, ale jsou omezeny speciální syntaxí, ve které všechny modifikátory transformace musí být ve formátu%(\<ItemMetaDataName >). Jakákoli metadata položky lze použít jako modifikátor Transform. To zahrnuje dobře známá metadata položky, která jsou přiřazena ke každé položce při jejím vytvoření. Seznam známých metadat položek najdete v tématu [známá metadata položky](../msbuild/msbuild-well-known-item-metadata.md).

V následujícím příkladu se seznam souborů *. resx* transformuje na seznam souborů *. Resources* . Modifikátor transformace% (filename) určuje, že každý soubor *. Resources* má stejný název souboru jako odpovídající soubor *. resx* .

```xml
@(RESXFile->'%(filename).resources')
```

Například pokud položky v seznamu @ (RESXFile) jsou *Form1. resx*, *Form2. resx*a *Form3. resx*, budou výstupy v seznamu transformovaných položek *Form1. Resources*, *Form2. Resources*a *Form3. Resources*.

> [!NOTE]
> Můžete zadat vlastní oddělovač pro seznam transformovaných položek stejným způsobem jako oddělovač pro seznam položek Standard. Chcete-li například oddělit seznam transformovaných položek pomocí čárky (,) namísto výchozího středníku (;), použijte následující kód XML: `@(RESXFile->'Toolset\%(filename)%(extension)', ',')`

## <a name="use-multiple-modifiers"></a>Použití více modifikátorů
 Transformační výraz může obsahovat více modifikátorů, které mohou být kombinovány v libovolném pořadí a lze je opakovat. V následujícím příkladu se změní název adresáře, který obsahuje soubory, ale původní název a přípona názvu souboru zůstanou v souborech.

```xml
@(RESXFile->'Toolset\%(filename)%(extension)')
```

 Například pokud jsou položky, které jsou obsaženy v seznamu `RESXFile` položky, *Project1\Form1.resx*, *Project1\Form2.resx*a *Project1\Form3.text*, výstupy v seznamu transformovaný budou *Toolset\Form1.resx*, *Toolset\Form2.resx*a *Toolset\Form3.text*.

## <a name="dependency-analysis"></a>Analýza závislostí
 Transformace garantuje mapování 1:1 mezi seznamem transformovaných položek a původní seznam položek. Proto pokud cíl vytvoří výstupy, které jsou transformují vstupy, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] mohou analyzovat časová razítka vstupů a výstupů a rozhodnout, zda chcete přeskočit, sestavit nebo částečně znovu sestavit cíl.

 V [úloze kopírování](../msbuild/copy-task.md) v následujícím příkladu všechny soubory v seznamu `BuiltAssemblies` položky jsou mapovány na soubor v cílové složce úkolu, který je určen pomocí transformace v atributu `Outputs`. Pokud se soubor v seznamu `BuiltAssemblies` položka změní, úloha `Copy` se spustí jenom pro změněný soubor a všechny ostatní soubory se přeskočí. Další informace o analýze závislostí a o tom, jak používat transformace, naleznete v tématu [How to: Build přírůstkově](../msbuild/how-to-build-incrementally.md).

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
 Následující příklad ukazuje [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] soubor projektu, který používá transformace. V tomto příkladu se předpokládá, že v adresáři *c:\sub0\sub1\sub2\sub3* je pouze jeden soubor *. xsd* a že pracovní adresář je *c:\sub0*.

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
fullpath: C:\sub0\sub1\sub2\sub3\myfile.xsd
rootdir + directory + filename + extension: C:\sub0\sub1\sub2\sub3\myfile.xsd
identity: sub1\sub2\sub3\myfile.xsd
filename: myfile
directory: sub0\sub1\sub2\sub3\
relativedir: sub1\sub2\sub3\
extension: .xsd
```

## <a name="see-also"></a>Viz také:
- [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)
- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
- [Postupy: přírůstkové sestavení](../msbuild/how-to-build-incrementally.md)
