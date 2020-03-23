---
title: Transformace msbuild | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 34394ba35a349a1564f6c3fdd43052be3e1fdf03
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633106"
---
# <a name="msbuild-transforms"></a>Transformace MSBuild

Transformace je převod 1:1 jednoho seznamu položek do druhého. Kromě povolení projektu převést seznamy položek, transformace umožňuje cíl identifikovat přímé mapování mezi jeho vstupy a výstupy. Toto téma vysvětluje transformace a jak je MSBuild používá k efektivnějšímu vytváření projektů.

## <a name="transform-modifiers"></a>Modifikátory transformace

Transformace nejsou libovolné, ale jsou omezeny speciální syntaxí, ve které musí být\<všechny modifikátory transformace ve formátu %( ItemMetaDataName>). Jako modifikátor transformace lze použít libovolná metadata položky. To zahrnuje dobře známé položky metadata, která je přiřazena ke každé položce při jeho vytvoření. Seznam známých metadat položek naleznete v [tématu Známá metadata položek](../msbuild/msbuild-well-known-item-metadata.md).

V následujícím příkladu je seznam souborů *RESX* transformován do seznamu souborů *.resources.* Modifikátor transformace %(název souboru) určuje, že každý soubor *.resources* má stejný název souboru jako odpovídající soubor *RESX.*

```xml
@(RESXFile->'%(filename).resources')
```

Pokud jsou například položky v seznamu položek @(RESXFile) *form1.resx*, *Form2.resx*a *Form3.resx*, budou výstupy v transformovaném seznamu *Form1.resources*, *Form2.resources*a *Form3.resources*.

> [!NOTE]
> Vlastní oddělovač pro seznam transformovaných položek můžete určit stejným způsobem, jakým určíte oddělovač pro standardní seznam položek. Chcete-li například oddělit seznam transformovaných položek pomocí čárky (,) namísto výchozího středníku (;), použijte následující kód XML:`@(RESXFile->'Toolset\%(filename)%(extension)', ',')`

## <a name="use-multiple-modifiers"></a>Použití více modifikátorů

 Transformační výraz může obsahovat více modifikátorů, které lze kombinovat v libovolném pořadí a lze je opakovat. V následujícím příkladu se změní název adresáře, který obsahuje soubory, ale soubory si zachovají původní název a příponu názvu souboru.

```xml
@(RESXFile->'Toolset\%(filename)%(extension)')
```

 Pokud jsou například položky obsažené `RESXFile` v seznamu položek *Projekt1\Form1.resx*, *Project1\Form2.resx*a *Project1\Form3.text*, budou výstupy v transformovaném seznamu *sady nástrojů\Form1.resx*, *Toolset\Form2.resx*a *Toolset\Form3.text*.

## <a name="dependency-analysis"></a>Analýza závislostí

 Transformace zaručují mapování 1:1 mezi seznamem transformovaných položek a původním seznamem položek. Proto pokud cíl vytvoří výstupy, které jsou transformace vstupů, MSBuild můžete analyzovat časová razítka vstupů a výstupů a rozhodnout, zda přeskočit, sestavení nebo částečně znovu sestavit cíl.

 V [úkolu Kopírovat](../msbuild/copy-task.md) v následujícím příkladu `BuiltAssemblies` se každý soubor v seznamu položek mapuje na soubor v `Outputs` cílové složce úkolu určený pomocí transformace v atributu. Pokud se soubor `BuiltAssemblies` v seznamu `Copy` položek změní, úloha se spustí pouze pro změněný soubor a všechny ostatní soubory budou přeskočeny. Další informace o analýze závislostí a použití transformací naleznete v [tématu How to: Build incrementally](../msbuild/how-to-build-incrementally.md).

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

 Následující příklad ukazuje soubor projektu MSBuild, který používá transformace. Tento příklad předpokládá, že v adresáři *c:\sub0\sub1\sub3* je pouze jeden soubor *XSD* a že pracovní adresář je *c:\sub0*.

### <a name="code"></a>kód

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

 Tento příklad vytváří následující výstup:

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

## <a name="see-also"></a>Viz také

- [Koncepty MSBuild](../msbuild/msbuild-concepts.md)
- [Odkaz na sestavení msbuild](../msbuild/msbuild-reference.md)
- [Postup: Sestavení postupně](../msbuild/how-to-build-incrementally.md)
