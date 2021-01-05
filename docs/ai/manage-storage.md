---
title: Procházení úložiště pro nahrávání dat
description: Přečtěte si, jak můžete procházet veškeré úložiště ve vzdáleném počítači nebo sdílené složce Azure a povolit nahrávání dat nebo stahování modelů a protokolů.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: b145c4acf4047356b8996d09d746679900314f1b
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2020
ms.locfileid: "97726563"
---
# <a name="browse-storage-to-upload-data-or-download-models-and-logs"></a>Procházení úložiště pro nahrávání dat nebo stahování modelů a protokolů

Můžete procházet veškeré úložiště ve vzdáleném počítači nebo sdílené složce Azure a povolit nahrávání dat nebo stahování modelů a protokolů. Nebo pokud chcete získat přístup k protokolům a výstupům úloh pro konkrétní úlohu, můžete to udělat i v prohlížeči úloh.

## <a name="to-access-all-data-on-the-remote-machine-or-file-share"></a>Přístup ke všem datům ve vzdáleném počítači nebo sdílené složce

1. Otevřete **Průzkumník serveru**.
2. Rozbalte vzdálený počítač nebo Batch AI výpočetního kontextu.
3. Klikněte pravým tlačítkem na **úložiště**; pak klikněte na tlačítko **Procházet**.

    ![Snímek obrazovky Průzkumník serveru se rozšířenou složkou vzdálené počítače Ve stromové struktuře složek je zvýrazněné úložiště a v místní nabídce se vybere možnost Procházet.](media/manage-storage/browse-storage.png)

## <a name="to-access-job-specific-data-on-the-remote-machine-or-file-share"></a>Přístup k datům specifickým pro úlohu ve vzdáleném počítači nebo sdílené složce

1. Otevřete [historii úlohy](job-details.md) .
2. Vyberte úlohu.
3. Klikněte na **pracovní složka** nebo pro rychlý přístup k těmto důležitým souborům protokolu klikněte na **stdout/stderr** .

    ![Snímek obrazovky okna prohlížeče úloh v Průzkumník serveru. Je vybraná úloha train_mnist a v části Podrobnosti o úloze se vybere odkaz pracovní složka.](media/manage-storage/job-workingfolder.png)
