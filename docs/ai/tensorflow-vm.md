---
title: Spuštění modelu TensorFlow v cloudu
description: spuštění modelu tensorflow ve virtuálním počítači Azure s hloubkovým učením
keywords: AI, Visual Studio, virtuální počítač s hloubkovým učením
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: tutorial
ms.devlang: python
ms.workload:
- multiple
ms.openlocfilehash: 9cb06220c99abb86c24808f6831cf98280133f2e
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2020
ms.locfileid: "75915830"
---
# <a name="train-a-tensorflow-model-in-the-cloud"></a>Výuka modelu TensorFlow v cloudu

V tomto kurzu provedeme model TensorFlow s využitím [datové sady mnist ručně zapsaných](http://yann.lecun.com/exdb/mnist/) na virtuálním počítači Azure s [hloubkovým učením](/azure/machine-learning/data-science-virtual-machine/deep-learning-dsvm-overview) .

Databáze MNIST ručně zapsaných má školicí sadu 60 000 příkladů a sadu testů 10 000 příkladů rukou psaných číslic.

## <a name="prerequisites"></a>Požadavky
Než začnete, ujistěte se, že máte nainstalované a nakonfigurované následující:

### <a name="setup-azure-deep-learning-virtual-machine"></a>Nastavit virtuální počítač Azure s hloubkovým učením

> [!NOTE]
> Nastavte **typ operačního systému** na Linux.

Pokyny k nastavení virtuálního počítače pro hloubkové učení najdete [tady](/azure/machine-learning/data-science-virtual-machine/provision-deep-learning-dsvm).

### <a name="remove-comment-in-parens"></a>Odebrat komentář v Parens

```bash
echo -e ". /etc/profile\n$(cat ~/.bashrc)" > ~/.bashrc
```

### <a name="download-sample-code"></a>Stáhnout vzorový kód

Stáhněte si toto [úložiště GitHub](https://github.com/Microsoft/samples-for-ai) obsahující ukázky pro Začínáme s obsáhlým učením na TENSORFLOW, CNTK, Theano a dalších.

## <a name="open-project"></a>Otevřený projekt

- Spusťte Visual Studio a vyberte **soubor > otevřít > projekt/řešení**.

- Vyberte složku **Příklady Tensorflow** z staženého úložiště ukázek a otevřete soubor **TensorflowExamples. sln** .

   ![Otevřený projekt](media/tensorflow-local/open-project.png)

   ![Otevřít řešení](media/tensorflow-local/open-solution.png)

## <a name="add-azure-remote-vm"></a>Přidat vzdálený virtuální počítač Azure

V Průzkumník serveru klikněte pravým tlačítkem myši na uzel **vzdálených počítačů** pod uzlem nástroje AI a vyberte Přidat.... Zadejte zobrazovaný název vzdáleného počítače, hostitel IP, port SSH, uživatelské jméno a soubor hesla nebo klíče.

![Přidat nový vzdálený počítač](media/tensorflow-vm/add-remote-vm.png)

## <a name="submit-job-to-azure-vm"></a>Odeslat úlohu do virtuálního počítače Azure
V **Průzkumník řešení** klikněte pravým tlačítkem na projekt mnist ručně zapsaných a vyberte **Odeslat úlohu**.

![Odeslání úlohy do vzdáleného počítače](media/tensorflow-vm/job-submission.png)

V okně pro odeslání:

- V seznamu clusteru, **který se má použít**, vyberte vzdálený počítač (s předponou "RM:"), do kterého se má úloha odeslat.

- Zadejte **název úlohy**.

- Klikněte na **Submit** (Odeslat).

## <a name="check-status-of-job"></a>Stav kontroly úlohy
Zobrazení stavu a podrobností úloh: rozbalte virtuální počítač, na který jste úlohu odeslali, do **Průzkumník serveru**. Dvakrát klikněte na **úlohy**.

![Prohlížeč úloh](media/tensorflow-vm/job-browser.png)

## <a name="clean-up-resources"></a>Vyčištění prostředků

Pokud se chystáte tento virtuální počítač používat v blízké budoucnosti, zastavte ho. Pokud jste s tímto kurzem hotovi, spusťte následující příkaz pro vyčištění prostředků:

```azurecli-interactive
az group delete --name myResourceGroup
```
