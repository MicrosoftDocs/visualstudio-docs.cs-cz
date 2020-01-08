---
title: T4 CleanUpBehavior – direktiva
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa5883cd8a1e30e007db41d5aa73f882e1d7edd2
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591876"
---
# <a name="t4-cleanupbehavior-directive"></a>T4 CleanUpBehavior – direktiva

Pro odstranění domény appDomain po zpracování textové šablony vložte následující řádek:

```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

Textové šablony jsou zpracovávány v doméně appDomain, která je oddělena od hostitelského procesu. Ve většině případů se po zpracování jedné textové šablony použije doména appdomain znovu ke zpracování další šablony. Pokud ale zadáte CleanupBehavior, doména appDomain se odstraní a další šablona se zpracuje pomocí nové domény appDomain.

Sice se zpomalí zpracování textu, ale může to být užitečné, protože tím zajistíte likvidaci prostředků.

Tato direktiva funguje pouze u hostitele sady Visual Studio.
