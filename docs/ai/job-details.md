---
title: Zobrazit nedávné úlohy
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 79b396946666077dcdedb3ee2a5ab891c2bb4fb8
ms.sourcegitcommit: 57bc1c3887838d707c13feff72a677b3bad3be4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72777398"
---
# <a name="view-recent-job-performance-and-details"></a>Zobrazit výkon poslední úlohy a podrobnosti

Po odeslání úloh můžete zobrazit seznam úloh, abyste viděli jejich stav, dobu trvání a další.

1. V **Průzkumník serveru**rozbalte konkrétní výpočetní kontext.
2. Dvakrát klikněte na **úlohy**.
3. Zobrazí se seznam úloh odeslaných do daného výpočetního kontextu.
4. Pokud chcete zobrazit podrobnosti, vyberte konkrétní **úlohu** v seznamu.

![Monitorování úloh](media/job-details/monitor-jobs.png)

> Historie úloh odeslaná do virtuálních počítačů se systémem Linux je uložena na virtuálním počítači v adresáři adresáře/TMP. Proto se při každém restartování historie úlohy vymaže. Pokud chcete mít trvalý záznam o historii úloh, nakonfigurujte prosím svůj virtuální počítač jako výpočetní kontext ve službě Azure Machine Learning a pak odešlete úlohu do Azure Machine Learning (jako výpočetní kontext vyberte virtuální počítač).
