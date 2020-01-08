---
title: Speciální znaky pro Escape | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- special characters to escape
- msbuild, special characters to escape
ms.assetid: 5b5172c3-41e4-4f38-a16f-2aeac831a5fc
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 686640cbe3c93cbe3d938cd3025a77129c829bd7
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595108"
---
# <a name="special-characters-to-escape"></a>Speciální znaky k úniku
Speciální znaky musí být uvozeny pouze v případě, že mají zvláštní význam v kontextu, ve kterém jsou používány. Například hvězdička (*) je speciální znak pouze v atributech include a Exclude definice položky nebo v volání <xref:Microsoft.Build.Tasks.CreateItem>. Ve všech ostatních případech je hvězdička považována za literální hvězdičku. Nemusíte-li v souborech projektu zacházet hvězdičkami, není to nijak poškozeno.

 Místo speciálního znaku použijte notaci%\<xx >, kde \<xx > představuje hexadecimální hodnotu znaku ASCII. Chcete-li například použít hvězdičku (*) jako literální znak, použijte hodnotu `%2A`.

 Úplný seznam speciálních znaků, které mají být uvozeny následujícím způsobem:

|Znak|Popis|
|---------------|-----------------|
|%|Symbol procenta, který se používá k odkazování na metadata|
|$|Znak dolaru, který se používá k odkazování na vlastnosti.|
|@|Na znaménko, používá se pro odkazování na seznamy položek.|
|(|Levou závorku, která se používá v seznamech|
|)|V seznamech se použijí uzavírací závorky.|
|;|Středník, oddělovač seznamu.|
|?|Otazník, zástupný znak při popisu specifikace souboru v sekci include/Exclude položky|
|*|Hvězdička (zástupný znak) při popisu specifikace souboru v oddílu include/Exclude položky položky.|

> [!NOTE]
> V některých scénářích může být nutné řídicí znaky dvojité uvozovky ("), například při použití v rámci úlohy `Exec`.

## <a name="see-also"></a>Viz také:
- [Postupy: sekvence speciálních znaků v nástroji MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md)
- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
