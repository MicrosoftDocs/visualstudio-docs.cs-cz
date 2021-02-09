---
title: Metadata známé položky nástroje MSBuild | Microsoft Docs
description: Přečtěte si o metadatech MSBuild přiřazených ke každé položce při vytváření a některých volitelných metadatech MSBuild, která můžete definovat pro řízení chování sestavení.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d9ca2249e6119e27574791a2cbd9e8b09a9bde63
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878179"
---
# <a name="msbuild-well-known-item-metadata"></a>Metadata známé položky nástroje MSBuild

Metadata položky jsou hodnoty připojené k položkám. Některé jsou přiřazeny nástrojem MSBuild pro položky při vytváření položek, ale můžete také definovat libovolná metadata, která potřebujete. Některé uživatelsky definované hodnoty metadat mají význam pro MSBuild, konkrétní úkoly nebo sady SDK, jako je například sada .NET SDK.

První tabulka v tomto článku popisuje metadata přiřazená každé položce při jejich vytvoření. Následující tabulka obsahuje některá volitelná metadata, která mají význam pro MSBuild, který můžete definovat pro řízení chování sestavení. V každém příkladu byla následující deklarace položky použita k zahrnutí souboru *C:\MyProject\Source\Program.cs* do projektu.

```xml
<ItemGroup>
    <MyItem Include="Source\Program.cs" />
</ItemGroup>
```

|Metadata položky|Description|
|-------------------|-----------------|
|% (FullPath)|Obsahuje úplnou cestu položky. Příklad:<br /><br /> *C:\MyProject\Source\Program.cs*|
|%(RootDir)|Obsahuje kořenový adresář položky. Příklad:<br /><br /> *R\\*|
|% (Název souboru)|Obsahuje název souboru položky bez přípony. Příklad:<br /><br /> *Program*|
|% (Rozšíření)|Obsahuje příponu názvu souboru položky. Příklad:<br /><br /> *. cs*|
|%(RelativeDir)|Obsahuje cestu zadanou v `Include` atributu, až po konečné zpětné lomítko ( \\ ). Příklad:<br /><br /> *Zdroj\\*<br /><br /> Pokud `Include` je atributem úplná cesta, `%(RelativeDir)` začíná kořenovým adresářem `%(RootDir)` .  Příklad: <br /><br /> *C:\MyProject\Source\\*|
|% (Adresář)|Obsahuje adresář položky bez kořenového adresáře. Příklad:<br /><br /> *MyProject \\ zdroj\\*|
|%(RecursiveDir)|Pokud `Include` atribut obsahuje zástupný znak \* \* , tato metadata určují část cesty, která nahrazuje zástupný znak. Další informace o zástupných znacích najdete v tématu [Postupy: výběr souborů pro sestavení](../msbuild/how-to-select-the-files-to-build.md).<br /><br /> Pokud složka *C:\MySolution\MyProject\Source \\* obsahuje soubor *program.cs* a soubor projektu obsahuje tuto položku:<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> hodnota by pak byla `%(MyItem.RecursiveDir)` *\\ MySolution\MyProject\Source*.|
|% (Identita)|Položka zadaná v `Include` atributu Příklad:<br /><br /> *Source\Program.cs*|
|%(ModifiedTime)|Obsahuje časové razítko od poslední změny položky. Příklad:<br /><br /> `2004-07-01 00:21:31.5073316`|
|%(CreatedTime)|Obsahuje časové razítko od okamžiku, kdy byla položka vytvořena. Příklad:<br /><br /> `2004-06-25 09:26:45.8237425`|
|%(AccessedTime)|Obsahuje časové razítko od posledního otevření položky.<br /><br /> `2004-08-14 16:52:36.3168743`|

## <a name="see-also"></a>Viz také

- [Společná metadata položky MSBuild](common-msbuild-item-metadata.md)
- [Položky](../msbuild/msbuild-items.md)
- [Dávkování](../msbuild/msbuild-batching.md)
- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
