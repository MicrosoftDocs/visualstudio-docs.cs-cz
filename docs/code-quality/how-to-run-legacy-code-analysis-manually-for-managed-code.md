---
title: Ruční spuštění analýzy starších kódů (.NET)
description: Naučte se detekovat možné nedostatky ve zdrojovém kódu. Informace o tom, jak spustit starší analýzu kódu ručně ve spravovaném kódu v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- code analysis, running
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: Mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: f214ac47ad3d831432b91652c5bbe3249ce5f1c5
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223482"
---
# <a name="how-to-run-legacy-code-analysis-manually-for-managed-code"></a>Postupy: ruční spuštění analýzy starších kódů pro spravovaný kód

Nástroj Analýza kódu poskytuje informace o možných vadch ve vašem zdrojovém kódu. Můžete spustit analýzu kódu automaticky s každým sestavením kódu projektu a také můžete spustit analýzu kódu ručně. Pravidla, která jsou kontrolována při spuštění analýzy kódu, jsou uvedena na stránce vlastností projektu na stránce Analýza kódu. Další informace naleznete v tématu [Postupy: konfigurace analýzy kódu pro projekt spravovaného kódu](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).

## <a name="to-run-code-analysis-manually"></a>Ruční spuštění analýzy kódu

1. Pokud jste v aplikaci Visual Studio 2019 verze 16,5 nebo novější, spusťte před spuštěním sady Visual Studio na příkazovém řádku následující příkaz:

```
setx EnableLegacyCodeAnalysis true
```

2. V **Průzkumník řešení** klikněte na projekt.

3. V nabídce **analyzovat** klikněte na možnost **Spustit analýzu kódu na** *název projektu*.
