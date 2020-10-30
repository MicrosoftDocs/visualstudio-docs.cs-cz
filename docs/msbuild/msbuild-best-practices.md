---
title: Osvědčené postupy nástroje MSBuild | Microsoft Docs
description: Seznamte se s osvědčenými postupy pro psaní skriptů MSBuild, například používání atributů podmínky a používání zástupných znaků.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2742324f737a4e70221e3cbe4c78cff56fa7e7ca
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047664"
---
# <a name="msbuild-best-practices"></a>Doporučené postupy nástroje MSBuild

Pro psaní skriptů MSBuild doporučujeme následující osvědčené postupy:

- Výchozí hodnoty vlastností jsou nejlépe zpracovávány pomocí `Condition` atributu a nikoli deklarováním vlastnosti, jejíž výchozí hodnota může být přepsána v příkazovém řádku. Například použijte

```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```

- Obecně platí, že při výběru položek nepoužívejte zástupné znaky. Místo toho zadejte soubory explicitně. Důvodem je, že ve většině typů projektů MSBuild rozbalí zástupné znaky v různých časech, například při přidávání nebo odebírání položek, což může vést k neočekávanému chování. Výjimkou je v projektech ve stylu .NET Core SDK, které správně zpracovávají zástupné znaky.

## <a name="see-also"></a>Viz také

- [Pokročilé koncepty](../msbuild/msbuild-advanced-concepts.md)
