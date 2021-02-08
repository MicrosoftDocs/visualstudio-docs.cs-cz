---
title: Místní výuka modelu tensorflow
description: Spuštění modelu tensorflow místně v nástrojích AI pro Visual Studio
keywords: AI, Visual Studio, tensorflow, místní
author: jillre
ms.author: jillfra
manager: jmartens
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: quickstart
ms.devlang: python
ms.workload:
- multiple
ms.openlocfilehash: 0ceb21701958630c8b783d5b6850c5e0a0ab229a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841377"
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

   ![Otevřený projekt](media/tensorflow-local/open-project.png)

   ![Otevřít řešení](media/tensorflow-local/open-solution.png)

- V **Průzkumník řešení** Najděte projekt mnist ručně zapsaných, klikněte pravým tlačítkem a vyberte **nastavit jako spouštěný projekt**.

- Klikněte na tlačítko **Start**.

- Výstup je vytištěn v konzole nástroje.

   ![Ukázkový výstup z konzoly](media/tensorflow-local/console-output.png)

> [!div class="nextstepaction"]
> [Trénování modelu platformy TensorFlow v cloudu](tensorflow-vm.md)
