---
title: MSBuild Známá metadata zboží | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633093"
---
# <a name="msbuild-well-known-item-metadata"></a>MSBuild dobře známá metadata položky

Následující tabulka popisuje metadata přiřazená každé položce při vytvoření. V každém příkladu byla do projektu zahrnuta následující deklarace položky pro zahrnutí souboru *C:\MyProject\Source\Program.cs.*

```xml
<ItemGroup>
    <MyItem Include="Source\Program.cs" />
</ItemGroup>
```

|Metadata položky|Popis|
|-------------------|-----------------|
|%(Úplná cesta)|Obsahuje úplnou cestu položky. Například:<br /><br /> *C:\MyProject\Source\Program.cs*|
|%(RootDir)|Obsahuje kořenový adresář položky. Například:<br /><br /> *C:\\*|
|%(Název souboru)|Obsahuje název souboru položky bez přípony. Například:<br /><br /> *Program*|
|%(Rozšíření)|Obsahuje příponu názvu souboru položky. Například:<br /><br /> *.cs*|
|%(RelativeDir)|Obsahuje cestu zadanou `Include` v atributu až do\\konečného zpětného lomítka ( ). Například:<br /><br /> *Zdroj\\*<br /><br /> Pokud `Include` je atribut úplnou `%(RelativeDir)` cestou, začíná `%(RootDir)`kořenovým adresářem .  Například: <br /><br /> *C:\MyProject\Zdroj\\*|
|%(Adresář)|Obsahuje adresář položky bez kořenového adresáře. Například:<br /><br /> *Zdroj\\myproject\\*|
|%(Rekurzivní dir)|Pokud `Include` atribut obsahuje zástupný znak \* \*, tato metadata určuje část cesty, která nahradí zástupný znak. Další informace o zástupných zástupcích naleznete v [tématu Postup: Vyberte soubory, které chcete vytvořit](../msbuild/how-to-select-the-files-to-build.md).<br /><br /> Pokud složka *C:\MySolution\MyProject\Source\\ * obsahuje soubor *Program.cs*a pokud soubor projektu obsahuje tuto položku:<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> pak hodnota `%(MyItem.RecursiveDir)` by *mysolution\MyProject\Source\\*.|
|%(Identita)|Položka zadaná `Include` v atributu. Například:<br /><br /> *Zdroj\Program.cs*|
|%(Upravený čas)|Obsahuje časové razítko z posledního okamžiku, kdy byla položka změněna. Například:<br /><br /> `2004-07-01 00:21:31.5073316`|
|%(CreatedTime)|Obsahuje časové razítko od okamžiku, kdy byla položka vytvořena. Například:<br /><br /> `2004-06-25 09:26:45.8237425`|
|%(AccessedTime)|Obsahuje časové razítko z posledního přístupu k položce.<br /><br /> `2004-08-14 16:52:36.3168743`|

## <a name="see-also"></a>Viz také

- [Items](../msbuild/msbuild-items.md)
- [Dávkování](../msbuild/msbuild-batching.md)
- [Odkaz na sestavení msbuild](../msbuild/msbuild-reference.md)
