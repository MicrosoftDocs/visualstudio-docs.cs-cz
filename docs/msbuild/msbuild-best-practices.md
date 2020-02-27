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
ms.openlocfilehash: d3605109519dccaafa1367464bd8c2385df5e93e
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633418"
---
# <a name="msbuild-best-practices"></a>Osvědčené postupy nástroje MSBuild

Pro psaní skriptů MSBuild doporučujeme následující osvědčené postupy:

- Výchozí hodnoty vlastností jsou nejlépe zpracovávány pomocí atributu `Condition` a nikoli deklarováním vlastnosti, jejíž výchozí hodnota může být přepsána v příkazovém řádku. Například použijte

```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```

- Vyhněte se zástupným znakům při výběru položek. Místo toho zadejte soubory explicitně. To usnadňuje sledování chyb, které mohou nastat při přidávání nebo odstraňování souborů.

## <a name="see-also"></a>Viz také

- [Pokročilé koncepty](../msbuild/msbuild-advanced-concepts.md)
