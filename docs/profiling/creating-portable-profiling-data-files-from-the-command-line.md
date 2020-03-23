---
title: Vytváření přenosných datových souborů profilování z příkazového řádku | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 8caa1a4976da39b155edde36d538ca193bd1addd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779490"
---
# <a name="create-portable-profiling-data-files-from-the-command-line"></a>Vytvoření přenosných datových souborů profilování z příkazového řádku
Chcete-li usnadnit sdílení dat profilování, můžete použít nástroj příkazového řádku [VSPerfReport](../profiling/vsperfreport.md) k vložení symbolů pro profilování spustit do . *vsp.*

 Můžete také vytvořit předem analyzovaná data profilování (.* vsps*) soubor, který je menší a je rychlejší načíst v ide.

> [!NOTE]
> Ujistěte se, že symbol (.* pdb*) soubory jsou k dispozici **VSPerfReport**. Další informace naleznete v [tématu Postup: Určení umístění souborů symbolů z příkazového řádku](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).
>
> Informace o cestě k **vsestavě**naleznete [v tématu Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).
>
> Profilování dat v . *vsps* soubor nelze filtrovat.

### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>Chcete-li vložit symboly pro profilování spustit do profilování data (.* vsp*) soubor

- V okně příkazového řádku zadejte následující příkaz:

   \<Cesta><strong>VSPerfReport \< </strong>VSP> **/PackSymbols**

   Ve výchozím nastavení. *vsps* soubor je pojmenován se základním názvem . *vsp.* Alternativní název můžete zadat pomocí možnosti **Výstup.**

### <a name="to-create-a-summary-profiling-data-file"></a>Vytvoření souboru dat souhrnného profilování

- V okně příkazového řádku zadejte následující příkaz:

   \<Cesta><strong>VSPerfReport \< </strong>Soubor vSP> **/SummaryFile** [**/Output:**\<Název souboru>]

   Ve výchozím nastavení. *vsps* soubor je pojmenován se základním názvem . *vsp.* Alternativní název můžete zadat pomocí možnosti **Výstup.**
