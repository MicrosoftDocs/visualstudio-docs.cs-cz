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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "72777411"
---
# <a name="browse-storage-to-upload-data-or-download-models-and-logs"></a>Procházení úložiště pro nahrávání dat nebo stahování modelů a protokolů

Můžete procházet všechna úložiště na vzdáleném počítači nebo sdílené složce Azure a povolit nahrávání dat nebo stahování modelů a protokolů. Nebo pokud chcete získat přístup k protokolům a výstupům úloh pro konkrétní úlohu, můžete to udělat také v prohlížeči úloh.

## <a name="to-access-all-data-on-the-remote-machine-or-file-share"></a>Přístup ke všem datům ve vzdáleném počítači nebo sdílené složce

1. Otevřete **Průzkumníka serveru**.
2. Rozbalte kontext výpočetního výkonu vzdáleného počítače nebo batch AI.
3. Klikněte pravým tlačítkem na **Úložiště**; potom klepněte na **tlačítko Procházet**.

    ![úložiště](media/manage-storage/browse-storage.png)

## <a name="to-access-job-specific-data-on-the-remote-machine-or-file-share"></a>Přístup k datům specifickým pro danou úlohu ve vzdáleném počítači nebo sdílené složce

1. Otevření [historie úloh](job-details.md)
2. Vyberte úlohu.
3. Klepněte na **položku Pracovní složka** nebo klepněte na položku **StdOut / Stderr,** abyste měli rychlý přístup k těmto důležitým souborům protokolu.

    ![úložiště](media/manage-storage/job-workingfolder.png)
