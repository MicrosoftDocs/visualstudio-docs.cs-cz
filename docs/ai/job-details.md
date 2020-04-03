---
title: Zobrazit poslední úlohy
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 55865e4907175664e8a8bfb8a813ff8d02c85b69
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638435"
---
# <a name="view-recent-job-performance-and-details"></a>Zobrazit nedávný výkon úlohy a podrobnosti

Po odeslání úloh můžete zobrazit seznam úloh a zobrazit jejich stav, dobu trvání a další.

1. V **Průzkumníkovi serveru**rozbalte konkrétní kontext výpočetních prostředků.
2. Dvakrát klikněte na **Úlohy**.
3. Zobrazí se seznam úloh odeslaných do tohoto výpočetního kontextu.
4. Vyberte konkrétní **úlohu** v seznamu, chcete-li zobrazit podrobnosti.

![monitorovat úlohy](media/job-details/monitor-jobs.png)

> Historie úloh odeslaná do virtuálních počítačů S IP se ukládá na virtuálním počítači v adresáři /tmp. Proto vždy, když je restartován historie úloh je vymazána. Pro trvalý záznam historie úloh nakonfigurujte virtuální počítač jako výpočetní kontext v Azure Machine learninga a pak odešlete úlohu do Azure Machine Learning (výběr virtuálního počítače jako výpočetního kontextu).
