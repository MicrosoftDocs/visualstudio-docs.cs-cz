---
title: Procházení úložiště pro nahrávání dat
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 7d0f2522117f4c5a5b85e99e2779d10cffcb7f22
ms.sourcegitcommit: 57bc1c3887838d707c13feff72a677b3bad3be4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72777411"
---
# <a name="browse-storage-to-upload-data-or-download-models-and-logs"></a>Procházení úložiště pro nahrávání dat nebo stahování modelů a protokolů

Můžete procházet veškeré úložiště ve vzdáleném počítači nebo sdílené složce Azure a povolit nahrávání dat nebo stahování modelů a protokolů. Nebo pokud chcete získat přístup k protokolům a výstupům úloh pro konkrétní úlohu, můžete to udělat i v prohlížeči úloh.

## <a name="to-access-all-data-on-the-remote-machine-or-file-share"></a>Přístup ke všem datům ve vzdáleném počítači nebo sdílené složce

1. Otevřete **Průzkumník serveru**.
2. Rozbalte vzdálený počítač nebo Batch AI výpočetního kontextu.
3. Klikněte pravým tlačítkem na **úložiště**; pak klikněte na tlačítko **Procházet**.

    ![úložiště](media/manage-storage/browse-storage.png)

## <a name="to-access-job-specific-data-on-the-remote-machine-or-file-share"></a>Přístup k datům specifickým pro úlohu ve vzdáleném počítači nebo sdílené složce

1. Otevřete [historii úlohy](job-details.md) .
2. Vyberte úlohu.
3. Klikněte na **pracovní složka** nebo pro rychlý přístup k těmto důležitým souborům protokolu klikněte na **stdout/stderr** .

    ![úložiště](media/manage-storage/job-workingfolder.png)
