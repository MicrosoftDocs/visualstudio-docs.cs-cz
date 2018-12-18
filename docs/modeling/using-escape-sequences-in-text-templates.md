---
title: Použití řídicích sekvencí v textových šablonách
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: b8e92a4bbd149d96b6db710daf32dc72024d57da
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31950384"
---
# <a name="using-escape-sequences-in-text-templates"></a>Použití řídicích sekvencí v textových šablonách
Můžete použít řídicích sekvencí v textových šablonách mají vygenerovat značky text šablony a (v C# pouze kód) řídicí řídicí znaky a znaky uvozovek.

 Pokud chcete vytisknout otevření a zavření značky pro blok kódu standardního výstupního souboru, vyhnuli značek následujícím způsobem:

```
\<# ... \#>
```

 Můžete provést stejný s jiné text šablony směrnice a kód bloku značky.

 Obsahuje-li bloku řetězce používá k uvození textové šablony značky, pak můžete použít následující řídicí sekvence:

-   Pokud je před značku text šablony sudý počet řídicí (\\) znaků šablony analyzátor bude zahrnovat polovinu řídicí znaky a obsahovat pořadí jako značku text šablony. Například, pokud existují čtyři řídicí znaky v textové šablony, budou existovat dvě "\\" znaků v generovaném souboru.

-   Pokud text šablony značky předchází lichý počet řídicí (\\) znaky, šablony analyzátor bude obsahovat polovinu "\\" znaků plus samotné značky (\<# nebo #>). Značky se nepovažuje za značku text šablony.

-   Pokud řídicí (\\) znak zobrazí kdekoliv jinde v libovolném pořadí, než kde je řídicí sekvence řídicí znak nebo uvozovky (v jazyku C# pouze), znak, který bude výstup přímo.

## <a name="see-also"></a>Viz také

- [Postupy: Generování šablon ze šablon pomocí řídicích sekvencí](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)