---
title: Zobrazit nedávné úlohy
description: Přečtěte si, že po odeslání úloh můžete zobrazit seznam úloh, abyste viděli jejich stav, dobu trvání a další.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: d67ee5810c1776176e1370839f0f7f43b9d0c55e
ms.sourcegitcommit: 9c57730000d5ced37d3887f3928b17076f49d0f7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2020
ms.locfileid: "92099216"
---
# <a name="view-recent-job-performance-and-details"></a>Zobrazit výkon poslední úlohy a podrobnosti

Po odeslání úloh můžete zobrazit seznam úloh, abyste viděli jejich stav, dobu trvání a další.

1. V **Průzkumník serveru**rozbalte konkrétní výpočetní kontext.
2. Dvakrát klikněte na **Úlohy**.
3. Zobrazí se seznam úloh odeslaných do daného výpočetního kontextu.
4. Pokud chcete zobrazit podrobnosti, vyberte konkrétní **úlohu** v seznamu.

![Monitorování úloh](media/job-details/monitor-jobs.png)

> Historie úloh odeslaná do virtuálních počítačů se systémem Linux je uložena na virtuálním počítači v adresáři adresáře/TMP. Proto se při každém restartování historie úlohy vymaže. Pokud chcete mít trvalý záznam o historii úloh, nakonfigurujte prosím svůj virtuální počítač jako výpočetní kontext ve službě Azure Machine Learning a pak odešlete úlohu do Azure Machine Learning (jako výpočetní kontext vyberte virtuální počítač).
