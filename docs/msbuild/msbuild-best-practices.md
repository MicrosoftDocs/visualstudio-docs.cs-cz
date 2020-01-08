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
ms.openlocfilehash: b1aee1a6ae3abc06846523df9470ad75d316a50b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592084"
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

## <a name="see-also"></a>Viz také:
- [Pokročilé koncepty](../msbuild/msbuild-advanced-concepts.md)
