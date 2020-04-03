---
title: Spuštění modelu TensorFlow v cloudu
description: spuštění modelu tensorflow ve virtuálním počítači azure deep learning
keywords: ai, visual studio, virtuální stroj pro hluboké učení
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: tutorial
ms.devlang: python
ms.workload:
- multiple
ms.openlocfilehash: 6cd833a687591ba4f49e785746381f9a5d738f5e
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638757"
---
# <a name="train-a-tensorflow-model-in-the-cloud"></a>Trénování modelu TensorFlow v cloudu

V tomto kurzu budeme trénovat model TensorFlow pomocí [datové sady MNIST](http://yann.lecun.com/exdb/mnist/) na virtuálním počítači Azure [Deep Learning.](/azure/machine-learning/data-science-virtual-machine/deep-learning-dsvm-overview)

Databáze MNIST má sadu školení 60 000 příkladů a testovací sadu 10 000 příkladů ručně psaných číslic.

## <a name="prerequisites"></a>Požadavky
Než začnete, ujistěte se, že máte nainstalovány a nakonfigurovány následující:

### <a name="setup-azure-deep-learning-virtual-machine"></a>Nastavení virtuálního počítače Azure pro hloubkové učení

> [!NOTE]
> Nastavte **typ operačního systému** na Linux.

Pokyny pro nastavení Deep Learning Virtual Machine najdete [zde](/azure/machine-learning/data-science-virtual-machine/provision-deep-learning-dsvm).

### <a name="remove-comment-in-parens"></a>Odebrat komentář v parens

```bash
echo -e ". /etc/profile\n$(cat ~/.bashrc)" > ~/.bashrc
```

### <a name="download-sample-code"></a>Stáhnout ukázkový kód

Stáhněte si toto úložiště GitHub obsahující [ukázky,](https://github.com/Microsoft/samples-for-ai) kde můžete začít s hlubokým učením na TensorFlow, CNTK, Theano a dalších.

## <a name="open-project"></a>Otevřený projekt

- Spusťte Visual Studio a vyberte **Soubor > Otevřít > Project/Solution**.

- Vyberte složku **Příklady tentensorflow** z úložiště ukázek stažených a otevřete soubor **TensorflowExamples.sln.**

   ![Otevřený projekt](media/tensorflow-local/open-project.png)

   ![Otevřené řešení](media/tensorflow-local/open-solution.png)

## <a name="add-azure-remote-vm"></a>Přidání vzdáleného virtuálního počítače Azure

V Průzkumníkovi serveru klikněte pravým tlačítkem myši na uzel **Vzdálené počítače** pod uzu Nástroje AI a vyberte "Přidat...". Zadejte zobrazovaný název vzdáleného počítače, hostitele IP, port SSH, uživatelské jméno a soubor hesla/klíče.

![Přidání nového vzdáleného počítače](media/tensorflow-vm/add-remote-vm.png)

## <a name="submit-job-to-azure-vm"></a>Odeslání úlohy do virtuálního počítače Azure
Klikněte pravým tlačítkem myši na projekt MNIST v **Průzkumníku řešení** a vyberte **odeslat úlohu**.

![Odeslání úlohy do vzdáleného počítače](media/tensorflow-vm/job-submission.png)

V okně podání:

- V seznamu **clusteru, který se má použít**, vyberte vzdálený počítač (s předponou "rm:" ), do který se má úloha odeslat.

- Zadejte **název úlohy**.

- Klepněte na **tlačítko Odeslat**.

## <a name="check-status-of-job"></a>Zkontrolovat stav úlohy
Chcete-li zobrazit stav a podrobnosti o úlohách: rozbalte virtuální počítač, do který jste úlohu odeslali, v **Průzkumníku serveru**. Poklepejte na **pracovní místa**.

![Prohlížeč úloh](media/tensorflow-vm/job-browser.png)

## <a name="clean-up-resources"></a>Vyčištění prostředků

Pokud ho plánujete v blízké budoucnosti používat, zastavte virtuální počítač. Pokud jste hotovi s tímto kurzem, spusťte následující příkaz vyčistit prostředky:

```azurecli-interactive
az group delete --name myResourceGroup
```
