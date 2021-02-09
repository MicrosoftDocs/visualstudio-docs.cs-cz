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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 83527ac4b7d16d2cb06c797924c18f2567f12350
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919186"
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
