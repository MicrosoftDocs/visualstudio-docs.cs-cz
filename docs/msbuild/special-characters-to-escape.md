---
title: Speciální znaky pro Escape | Microsoft Docs
description: Přečtěte si o speciálních znacích, které musí být uvozeny pouze v případě, že mají zvláštní význam v kontextu, ve kterém jsou používány.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 433e762bf68b6a3956616e0ccccc229bca8f86b9
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048272"
---
# <a name="special-characters-to-escape"></a>Speciální řídicí znaky

Speciální znaky musí být uvozeny pouze v případě, že mají zvláštní význam v kontextu, ve kterém jsou používány. Například hvězdička (*) je speciální znak pouze v atributech include a Exclude definice položky nebo v volání <xref:Microsoft.Build.Tasks.CreateItem> . Ve všech ostatních případech je hvězdička považována za literální hvězdičku. Nemusíte-li v souborech projektu zacházet hvězdičkami, není to nijak poškozeno.

 Použijte notaci% \<xx> místo speciálního znaku, kde \<xx> představuje hexadecimální hodnotu znaku ASCII. Chcete-li například použít hvězdičku (*) jako literální znak, použijte hodnotu `%2A` .

 Úplný seznam speciálních znaků, které mají být uvozeny následujícím způsobem:

|Znak|Kódování ASCII|Description|
|---------|----------|-----------|
|%|%25|Symbol procenta, který se používá k odkazování na metadata|
|$|%24|Znak dolaru, který se používá k odkazování na vlastnosti.|
|@|%40|Na znaménko, používá se pro odkazování na seznamy položek.|
|(|%28|Levou závorku, která se používá v seznamech|
|)|%29|V seznamech se použijí uzavírací závorky.|
|;|% 3B|Středník, oddělovač seznamu.|
|?|% 3F|Otazník, zástupný znak při popisu specifikace souboru v sekci include/Exclude položky|
|* |%2A|Hvězdička (zástupný znak) při popisu specifikace souboru v oddílu include/Exclude položky položky.|

> [!NOTE]
> V některých scénářích může být nutné řídicí znaky dvojité uvozovky ("), například při použití v rámci `Exec` úkolu.

## <a name="see-also"></a>Viz také

- [Postupy: sekvence speciálních znaků v nástroji MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md)
- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
