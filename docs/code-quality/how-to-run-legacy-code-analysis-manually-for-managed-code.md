---
title: 'Postup: Ruční spuštění analýzy staršíverze kódu pro spravovaný kód'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code analysis, running
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 9d2693bcff8e83839b4171bae60b138c967f10e5
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79432229"
---
# <a name="how-to-run-legacy-code-analysis-manually-for-managed-code"></a>Postup: Ruční spuštění analýzy staršíverze kódu pro spravovaný kód
Nástroj pro analýzu kódu poskytuje informace o možných vadách ve zdrojovém kódu. Analýzu kódu můžete spustit automaticky s každým sestavením projektu kódu a analýzu kódu můžete spustit také ručně. Pravidla, která jsou kontrolována při spuštění analýzy kódu jsou určeny na stránce Analýza kódu stránek vlastností projektu. Další informace naleznete v [tématu How to: Configure Code Analysis for a Managed Code Project](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).

## <a name="to-run-code-analysis-manually"></a>Ruční spuštění analýzy kódu

1. Pokud jste na Visual Studio 2019 verze 16.5 nebo novější, spusťte následující příkaz na příkazovém řádku před spuštěním sady Visual Studio:

```
set EnableLegacyCodeAnalysis = true
```

2. V **Průzkumníku řešení**klikněte na projekt.

3. V nabídce **Analyzovat** klepněte na **položku Spustit analýzu kódu v nabídce** *Název projektu*.

