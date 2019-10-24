---
title: Místní výuka modelu tensorflow
description: Spuštění modelu tensorflow místně v nástrojích AI pro Visual Studio
keywords: AI, Visual Studio, tensorflow, místní
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: quickstart
ms.devlang: python
ms.workload:
- multiple
ms.openlocfilehash: 43ce126baeb96efcaab3c40bac912274ee1cd8c7
ms.sourcegitcommit: 57bc1c3887838d707c13feff72a677b3bad3be4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72777434"
---
# <a name="train-a-tensorflow-model-locally"></a>Místní výuka modelu TensorFlow

V tomto rychlém startu vytvoříme TensorFlow model s datovou sadou [mnist ručně zapsaných](http://yann.lecun.com/exdb/mnist/) lokálně v Visual Studio Tools for AI.

Databáze MNIST ručně zapsaných má školicí sadu 60 000 příkladů a sadu testů 10 000 příkladů rukou psaných číslic.

## <a name="prerequisites"></a>Požadavky

Než začnete, ujistěte se, že máte nainstalované následující:

### <a name="google-tensorflow"></a>Google TensorFlow

V terminálu spusťte následující příkaz:

```cmd
C:\>pip.exe install tensorflow
```

### <a name="numpy-and-scipy"></a>NumPy a SciPy
Nainstalujte [numpy](https://www.lfd.uci.edu/~gohlke/pythonlibs/#numpy) a [SciPy](https://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy).

### <a name="download-sample-code"></a>Stáhnout vzorový kód
Stáhněte si toto [úložiště GitHub](https://github.com/Microsoft/samples-for-ai) obsahující ukázky pro Začínáme s hloubkovým učením napříč TENSORFLOW, CNTK, Theano a dalšími.

## <a name="open-solution-and-train-model"></a>Otevřít řešení a model výuky

- Spusťte Visual Studio a vyberte **soubor > otevřít > projekt/řešení**.

- Vyberte složku **Příklady Tensorflow** z staženého úložiště ukázek a otevřete soubor **TensorflowExamples. sln** .

   ![Otevřít projekt](media/tensorflow-local/open-project.png)

   ![Otevřít řešení](media/tensorflow-local/open-solution.png)

- V **Průzkumník řešení**Najděte projekt mnist ručně zapsaných, klikněte pravým tlačítkem a vyberte **nastavit jako spouštěný projekt**.

- Klikněte na tlačítko **Start**.

- Výstup je vytištěn v konzole nástroje.

   ![Ukázkový výstup z konzoly](media/tensorflow-local/console-output.png)

> [!div class="nextstepaction"]
> [Výuka modelu TensorFlow v cloudu](tensorflow-vm.md)
