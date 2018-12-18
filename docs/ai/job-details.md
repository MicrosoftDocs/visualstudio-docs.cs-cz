---
ms.technology: vs-ai-tools
ms.openlocfilehash: ebf412dbeb4e0ecc391c52d7da5ea49d12e6231f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49930359"
---
# <a name="view-recent-job-performance-and-details"></a>Zobrazit poslední výkon úlohy a podrobnosti

Po odeslání úloh můžete zobrazit seznam úloh, které chcete zobrazit jejich stav, dobu trvání a další.

1. V **Průzkumníka serveru**, rozbalte konkrétní výpočetní kontext.
2. Dvakrát klikněte na panel **úlohy**.
3. Zobrazí se seznam odeslaných do daného kontextu výpočetních úloh.
4. Vyberte konkrétní **úlohy** v seznamu zobrazíte podrobnosti.

![Monitorování úloh](media/job-details/monitor-jobs.png)

> Historie úlohy odeslané do virtuálních počítačů s Linuxem je uložen na virtuálním počítači v adresáři TMP. Proto pokaždé, když se bude vyžadovat restartování se vymaže historii úlohy. Trvalé záznamu historie úlohy nakonfigurujte prosím váš virtuální počítač jako výpočetní kontext v Azure Machine learning, pak odeslat úlohu do Azure Machine Learning (jako výpočetní kontext výběru virtuálního počítače).