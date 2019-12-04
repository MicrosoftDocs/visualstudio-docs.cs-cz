---
title: Vytváření přenosných datových souborů profilace z příkazového řádku | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779490"
---
# <a name="create-portable-profiling-data-files-from-the-command-line"></a>Vytváření přenosných datových souborů profilace z příkazového řádku
Aby bylo sdílení dat profilace snazší, můžete použít nástroj příkazového řádku [VSPerfReport](../profiling/vsperfreport.md) k vložení symbolů pro spuštění profilování do. soubor *VSP* .

 Můžete také vytvořit předem Analyzovaná data profilace (. *vsps*), který je menší a je rychlejší načíst v integrovaném vývojovém prostředí (IDE).

> [!NOTE]
> Ujistěte se, že symbol (. *soubory PDB*jsou k dispozici pro **VSPerfReport**. Další informace naleznete v tématu [How to: určení umístění souborů symbolů z příkazového řádku](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).
>
> Informace o cestě k **VSReport**naleznete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).
>
> Data profilování v. soubor *vsps* se nedá filtrovat.

### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>Chcete-li vložit symboly pro profilování, které se spustí, do dat profilace (. *VSP*) soubor

- V okně příkazového řádku zadejte následující příkaz:

   \<cesta ><strong>VSPerfReport \<</strong>souboru VSP > **/PackSymbols**

   Ve výchozím nastavení je to. soubor *vsps* má název se základním názvem. soubor *VSP* . Alternativní název můžete zadat pomocí možnosti **výstup** .

### <a name="to-create-a-summary-profiling-data-file"></a>Vytvoření souhrnného datového souboru profilace

- V okně příkazového řádku zadejte následující příkaz:

   \<cesta ><strong>VSPerfReport \<</strong>VSP soubor > **/SummaryFile** [ **/Output:** \<název souboru >]

   Ve výchozím nastavení je to. soubor *vsps* má název se základním názvem. soubor *VSP* . Alternativní název můžete zadat pomocí možnosti **výstup** .
