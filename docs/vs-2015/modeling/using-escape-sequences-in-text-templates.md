---
title: Použití řídicích sekvencí v textových šablonách | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
ms.assetid: 36fff542-2f42-460f-a2d5-03fc76817f3b
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8a45aa36ddce57141a7e1e851f7f0766b77015ee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659425"
---
# <a name="using-escape-sequences-in-text-templates"></a>Použití řídicích sekvencí v textových šablonách
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="see-also"></a>Viz také
 [Postupy: Generování šablon ze šablon pomocí řídicích sekvencí](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)
