---
title: Zobrazit poslední úlohy
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 79b396946666077dcdedb3ee2a5ab891c2bb4fb8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "72777398"
---
# <a name="view-recent-job-performance-and-details"></a>Zobrazit nedávný výkon úlohy a podrobnosti

Po odeslání úloh můžete zobrazit seznam úloh a zobrazit jejich stav, dobu trvání a další.

1. V **Průzkumníkovi serveru**rozbalte konkrétní kontext výpočetních prostředků.
2. Dvakrát klikněte na **Úlohy**.
3. Zobrazí se seznam úloh odeslaných do tohoto výpočetního kontextu.
4. Vyberte konkrétní **úlohu** v seznamu, chcete-li zobrazit podrobnosti.

![monitorovat úlohy](media/job-details/monitor-jobs.png)

> Historie úloh odeslaná do virtuálních počítačů S IP se ukládá na virtuálním počítači v adresáři /tmp. Proto vždy, když je restartován historie úloh je vymazána. Pro trvalý záznam historie úloh nakonfigurujte virtuální počítač jako výpočetní kontext v Azure Machine learninga a pak odešlete úlohu do Azure Machine Learning (výběr virtuálního počítače jako výpočetního kontextu).
