---
title: Metadata známé položky nástroje MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, item metadata
- MSBuild, well-known item metadata
ms.assetid: b5e791b5-c68f-4978-ad8a-9247d03bb6c0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6e9320525d770344f131d9e3f04b357de43b5e73
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633093"
---
# <a name="msbuild-well-known-item-metadata"></a>Metadata dobře známé položky nástroje MSBuild

Následující tabulka popisuje metadata přiřazená každé položce při vytvoření. V každém příkladu byla následující deklarace položky použita k zahrnutí souboru *C:\MyProject\Source\Program.cs* do projektu.

```xml
<ItemGroup>
    <MyItem Include="Source\Program.cs" />
</ItemGroup>
```

|Metadata položky|Popis|
|-------------------|-----------------|
|% (FullPath)|Obsahuje úplnou cestu položky. Příklad:<br /><br /> *C:\MyProject\Source\Program.cs*|
|%(RootDir)|Obsahuje kořenový adresář položky. Příklad:<br /><br /> *C:\\*|
|% (Název souboru)|Obsahuje název souboru položky bez přípony. Příklad:<br /><br /> *Editoru*|
|% (Rozšíření)|Obsahuje příponu názvu souboru položky. Příklad:<br /><br /> *. cs*|
|%(RelativeDir)|Obsahuje cestu zadanou v atributu `Include` až po konečné zpětné lomítko (\\). Příklad:<br /><br /> *\\ zdroje*<br /><br /> Pokud je atribut `Include` úplnou cestou, `%(RelativeDir)` začíná kořenovým adresářovým `%(RootDir)`.  Příklad: <br /><br /> *C:\MyProject\Source\\*|
|% (Adresář)|Obsahuje adresář položky bez kořenového adresáře. Příklad:<br /><br /> *Zdrojový\\ MyProject\\*|
|%(RecursiveDir)|Pokud atribut `Include` obsahuje zástupný znak \*\*, tato metadata určují část cesty, která nahrazuje zástupný znak. Další informace o zástupných znacích najdete v tématu [Postupy: výběr souborů pro sestavení](../msbuild/how-to-select-the-files-to-build.md).<br /><br /> Pokud složka *C:\MySolution\MyProject\Source\\* obsahuje soubor *program.cs*, a pokud soubor projektu obsahuje tuto položku:<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> pak bude hodnota `%(MyItem.RecursiveDir)` *MySolution\MyProject\Source\\* .|
|% (Identita)|Položka zadaná v atributu `Include`. Příklad:<br /><br /> *Source\Program.cs*|
|%(ModifiedTime)|Obsahuje časové razítko od poslední změny položky. Příklad:<br /><br /> `2004-07-01 00:21:31.5073316`|
|%(CreatedTime)|Obsahuje časové razítko od okamžiku, kdy byla položka vytvořena. Příklad:<br /><br /> `2004-06-25 09:26:45.8237425`|
|%(AccessedTime)|Obsahuje časové razítko od posledního otevření položky.<br /><br /> `2004-08-14 16:52:36.3168743`|

## <a name="see-also"></a>Viz také

- [Položky](../msbuild/msbuild-items.md)
- [Dávkování](../msbuild/msbuild-batching.md)
- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
