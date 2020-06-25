---
title: Procházení úložiště pro nahrávání dat
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 188ebee353261ba49f6677a0f96db68b7e8d46d9
ms.sourcegitcommit: 48e93538f1e352fc1f972b642bb5fcce2f6834a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2020
ms.locfileid: "85371609"
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
