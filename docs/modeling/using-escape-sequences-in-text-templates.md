---
title: Použití řídicích sekvencí v textových šablonách
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4e03f5eafc00b8431725ed06da10371a93692fb5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662921"
---
# <a name="use-escape-sequences-in-text-templates"></a>Použití řídicích sekvencí v textových šablonách

Pomocí řídicích sekvencí v textových šablonách můžete vygenerovat značky textových šablon a C# (pouze v kódu) pro řídicí znaky a uvozovky.

Chcete-li vytisknout značky Open a Close pro standardní blok kódu do výstupního souboru, zařídí značky následujícím způsobem:

```
\<# ... \#>
```

Můžete to samé provést s jinou direktivou textové šablony a Tagy bloku kódu.

Pokud textový blok obsahuje řetězce, které slouží k řídicím značkám textové šablony, můžete použít následující sekvence Escape:

- Pokud je před značkou textové šablony uveden sudý počet znaků escape (\\), analyzátor šablony bude obsahovat polovinu řídicích znaků a zahrnout sekvenci jako značku textové šablony. Například pokud jsou v textové šabloně čtyři řídicí znaky, ve vygenerovaném souboru budou dva "\\" znaky.

- Pokud je před značkou textové šablony uveden lichý počet řídicích znaků (\\), analyzátor šablony bude obsahovat polovinu znaků "\\" a samotné značky (\< # nebo # >). Značka není považována za značku textové šablony.

- Pokud se znak escape (\\) nachází kdekoli jinde v jiné sekvenci, než kde řídí řídicí znak nebo uvozovku (pouze v C# ), bude znak přímo výstupem.

## <a name="see-also"></a>Viz také:

- [Postupy: Generování šablon ze šablon pomocí řídicích sekvencí](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)