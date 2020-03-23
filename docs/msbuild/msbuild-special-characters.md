---
title: Zvláštní znaky MSBuild | Dokumenty společnosti Microsoft
ms.date: 06/12/2019
ms.topic: conceptual
helpviewer_keywords:
- escape characters
- escape
- MSBuild Escape Characters
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fdc9024db06fe27fab5dfdf9589300a6eb671368
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633210"
---
# <a name="msbuild-special-characters"></a>MSBuild speciální znaky

MSBuild rezervuje některé znaky pro zvláštní použití v konkrétních kontextech. Tyto znaky musíte uniknout pouze v případě, že je chcete použít doslova v kontextu, ve kterém jsou vyhrazeny. Například hvězdička má zvláštní význam pouze `Include` `Exclude` v atributy a definice položky `CreateItem`a volání . Pokud chcete, aby se hvězdička v jednom z těchto kontextů zobrazovala jako hvězdička, musíte ji uniknout. V každém jiném kontextu stačí zadat hvězdičku tam, kde se má zobrazit.

 Chcete-li uniknout speciální znak,\<použijte syntaxe % xx>, kde \<xx> představuje hexadecimální hodnotu ASCII znaku. Další informace naleznete [v tématu How to: Escape special characters in MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).

## <a name="special-characters"></a>Speciální znaky

 V následující tabulce jsou uvedeny speciální znaky MSBuild:

|**Znak**|**Ascii**|**Rezervované použití**|
|-------------------|---------------|------------------------|
|%|%25|Odkazování na metadata|
|$|%24|Odkazování na vlastnosti|
|@|%40|Odkazování na seznamy položek|
|'|%27|Podmínky a jiné výrazy|
|;|%3B|Oddělovač seznamu|
|?|%3F|Zástupný znak pro `Include` názvy souborů a `Exclude` atributy|
|*|%2A|Zástupný znak pro použití `Include` v `Exclude` názvech souborů a atributech|

## <a name="see-also"></a>Viz také

- [Pokročilé koncepty](../msbuild/msbuild-advanced-concepts.md)
- [Items](../msbuild/msbuild-items.md)
