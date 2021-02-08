---
title: Zobrazit nedávné úlohy
description: Přečtěte si, že po odeslání úloh můžete zobrazit seznam úloh, abyste viděli jejich stav, dobu trvání a další.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jmartens
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 13d78913e0d5d708c5e75a80611ae9cc1c2f7366
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841429"
---
# <a name="view-recent-job-performance-and-details"></a>Zobrazit výkon poslední úlohy a podrobnosti

Po odeslání úloh můžete zobrazit seznam úloh, abyste viděli jejich stav, dobu trvání a další.

1. V **Průzkumník serveru** rozbalte konkrétní výpočetní kontext.
2. Dvakrát klikněte na **Úlohy**.
3. Zobrazí se seznam úloh odeslaných do daného výpočetního kontextu.
4. Pokud chcete zobrazit podrobnosti, vyberte konkrétní **úlohu** v seznamu.

![Monitorování úloh](media/job-details/monitor-jobs.png)

> Historie úloh odeslaná do virtuálních počítačů se systémem Linux je uložena na virtuálním počítači v adresáři adresáře/TMP. Proto se při každém restartování historie úlohy vymaže. Pokud chcete mít trvalý záznam o historii úloh, nakonfigurujte prosím svůj virtuální počítač jako výpočetní kontext ve službě Azure Machine Learning a pak odešlete úlohu do Azure Machine Learning (jako výpočetní kontext vyberte virtuální počítač).
