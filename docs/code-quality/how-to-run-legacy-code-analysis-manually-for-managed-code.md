---
title: Ruční spuštění analýzy starších kódů pro spravovaný kód
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- code analysis, running
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 38c3de83dc0df39314ad236f647c69bbe614b75d
ms.sourcegitcommit: 48e93538f1e352fc1f972b642bb5fcce2f6834a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2020
ms.locfileid: "85371817"
---
# <a name="how-to-run-legacy-code-analysis-manually-for-managed-code"></a>Postupy: ruční spuštění analýzy starších kódů pro spravovaný kód
Nástroj Analýza kódu poskytuje informace o možných vadch ve vašem zdrojovém kódu. Můžete spustit analýzu kódu automaticky s každým sestavením kódu projektu a také můžete spustit analýzu kódu ručně. Pravidla, která jsou kontrolována při spuštění analýzy kódu, jsou uvedena na stránce vlastností projektu na stránce Analýza kódu. Další informace naleznete v tématu [Postupy: konfigurace analýzy kódu pro projekt spravovaného kódu](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).

## <a name="to-run-code-analysis-manually"></a>Ruční spuštění analýzy kódu

1. Pokud jste v aplikaci Visual Studio 2019 verze 16,5 nebo novější, spusťte před spuštěním sady Visual Studio na příkazovém řádku následující příkaz:

```
set EnableLegacyCodeAnalysis = true
```

2. V **Průzkumník řešení**klikněte na projekt.

3. V nabídce **analyzovat** klikněte na možnost **Spustit analýzu kódu na** *název projektu*.

