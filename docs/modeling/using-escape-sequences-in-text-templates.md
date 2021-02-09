---
title: Použití řídicích sekvencí v textových šablonách
description: Zjistěte, jak lze pomocí řídicích sekvencí v textových šablonách vygenerovat značky textových šablon a řídicí znaky a uvozovky pouze v kódu jazyka C#.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 126fe3f4e42c9c6cf0b75bf740e1e7e2c4b269ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924334"
---
# <a name="use-escape-sequences-in-text-templates"></a>Použití řídicích sekvencí v textových šablonách

Pomocí řídicích sekvencí v textových šablonách můžete vygenerovat značky textových šablon a (pouze v kódu jazyka C#) pro řídicí znaky a uvozovky.

Chcete-li vytisknout značky Open a Close pro standardní blok kódu do výstupního souboru, zařídí značky následujícím způsobem:

```
\<# ... \#>
```

Můžete to samé provést s jinou direktivou textové šablony a Tagy bloku kódu.

Pokud textový blok obsahuje řetězce, které slouží k řídicím značkám textové šablony, můžete použít následující sekvence Escape:

- Je-li před značkou textové šablony uveden sudý počet znaků escape ( \\ ), analyzátor šablony bude obsahovat polovinu řídicích znaků a zahrnout sekvenci jako značku textové šablony. Například pokud jsou v textové šabloně čtyři řídicí znaky, \\ ve vygenerovaném souboru budou dva znaky "".

- Pokud je před značkou textové šablony uveden lichý počet znaků escape ( \\ ), analyzátor šablony bude obsahovat polovinu " \\ " znaků a samotné značky ( \<# or #> ). Značka není považována za značku textové šablony.

- Pokud \\ se znak escape () nachází kdekoli jinde v jiné sekvenci, než kde řídí řídicí znak nebo uvozovky (pouze v jazyce C#), bude znak přímo výstup.

## <a name="see-also"></a>Viz také

- [Postupy: Generování šablon ze šablon pomocí řídicích sekvencí](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)
