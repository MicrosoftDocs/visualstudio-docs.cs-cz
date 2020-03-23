---
title: Trénování modelu tendence místně
description: Místní spuštění modelu tenzorového toku v nástrojích AI pro Visual Studio
keywords: ai, vizuální studio, tensorflow, místní
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: quickstart
ms.devlang: python
ms.workload:
- multiple
ms.openlocfilehash: 43ce126baeb96efcaab3c40bac912274ee1cd8c7
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "72777434"
---
# <a name="train-a-tensorflow-model-locally"></a>Trénování modelu TensorFlow místně

V tomto rychlém startu budeme trénovat model TensorFlow s datovou sadou [MNIST](http://yann.lecun.com/exdb/mnist/) místně v nástroji Visual Studio pro AI.

Databáze MNIST má sadu školení 60 000 příkladů a testovací sadu 10 000 příkladů ručně psaných číslic.

## <a name="prerequisites"></a>Požadavky

Než začnete, ujistěte se, že máte nainstalovány následující:

### <a name="google-tensorflow"></a>Google TensorFlow

V terminálu spusťte následující příkaz:

```cmd
C:\>pip.exe install tensorflow
```

### <a name="numpy-and-scipy"></a>NumPy a SciPy
Nainstalujte [NumPy](https://www.lfd.uci.edu/~gohlke/pythonlibs/#numpy) a [SciPy](https://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy).

### <a name="download-sample-code"></a>Stáhnout ukázkový kód
Stáhněte si toto úložiště GitHub obsahující [ukázky,](https://github.com/Microsoft/samples-for-ai) kde můžete začít s hlubokým učením napříč TensorFlow, CNTK, Theano a dalšími.

## <a name="open-solution-and-train-model"></a>Otevřené řešení a model vlaku

- Spusťte Visual Studio a vyberte **Soubor > Otevřít > Project/Solution**.

- Vyberte složku **Příklady tentensorflow** z úložiště ukázek stažených a otevřete soubor **TensorflowExamples.sln.**

   ![Otevřený projekt](media/tensorflow-local/open-project.png)

   ![Otevřené řešení](media/tensorflow-local/open-solution.png)

- Najděte projekt MNIST v **Průzkumníku řešení**, klepněte pravým tlačítkem myši a vyberte **nastavit jako počáteční projekt**.

- Klepněte na tlačítko **Start**.

- Výstup je vytištěn v konzole.

   ![Ukázkový výstup z konzoly](media/tensorflow-local/console-output.png)

> [!div class="nextstepaction"]
> [Trénování modelu TensorFlow v cloudu](tensorflow-vm.md)
