---
title: Procházení úložiště pro nahrávání dat
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: ece3ffa3a273e903f403fd7df7005bfb54172f62
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638441"
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
