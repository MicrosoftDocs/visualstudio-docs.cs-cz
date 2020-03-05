---
title: Osvědčené postupy nástroje MSBuild | Microsoft Docs
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
ms.openlocfilehash: 91b2e157ee64f5e4d91bc75a5d6f8d65d4312862
ms.sourcegitcommit: 3ed59ce39692124fe61c484df4348c0b9abee9b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2020
ms.locfileid: "78263146"
---
# <a name="msbuild-best-practices"></a>Doporučené postupy nástroje MSBuild

Pro psaní skriptů MSBuild doporučujeme následující osvědčené postupy:

- Výchozí hodnoty vlastností jsou nejlépe zpracovávány pomocí atributu `Condition` a nikoli deklarováním vlastnosti, jejíž výchozí hodnota může být přepsána v příkazovém řádku. Například použijte

```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```

- Obecně platí, že při výběru položek nepoužívejte zástupné znaky. Místo toho zadejte soubory explicitně. Důvodem je, že ve většině typů projektů MSBuild rozbalí zástupné znaky v různých časech, například při přidávání nebo odebírání položek, což může vést k neočekávanému chování. Výjimkou je v projektech ve stylu .NET Core SDK, které správně zpracovávají zástupné znaky.

## <a name="see-also"></a>Viz také:

- [Pokročilé koncepty](../msbuild/msbuild-advanced-concepts.md)
