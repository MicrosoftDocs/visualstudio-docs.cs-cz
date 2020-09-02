---
title: Vytváření přenosných datových souborů profilace z příkazového řádku | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5d343392c9e554c5e51325964949cd3ea13237b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64791224"
---
# <a name="creating-portable-profiling-data-files-from-the-command-line"></a>Vytváření přenosných datových souborů profilování z příkazového řádku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby bylo snazší sdílet data profilování, můžete použít nástroj příkazového řádku [VSPerfReport](../profiling/vsperfreport.md) k vložení symbolů pro spuštění profilování do souboru. vsp.  
  
 Můžete také vytvořit předem analyzovaný soubor dat profilování (. vsps), který je menší a rychlejší ho načíst v integrovaném vývojovém prostředí (IDE).  
  
> [!NOTE]
> Ujistěte se, že jsou soubory symbolů (PDB) k dispozici pro **VSPerfReport**. Další informace naleznete v tématu [How to: určení umístění souborů symbolů z příkazového řádku](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).  
>   
> Informace o cestě k **VSReport**naleznete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
> Data profilování v souboru. vsps nelze filtrovat.  
  
### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>Vložení symbolů pro spuštění profilování do souboru dat profilování (. vsp)  
  
- V okně příkazového řádku zadejte následující příkaz:  
  
   \<Path><strong>\<</strong>Soubor VSPerfReport VSP> **/PackSymbols**  
  
   Ve výchozím nastavení má soubor. vsps název se základním názvem souboru. vsp. Alternativní název můžete zadat pomocí možnosti **výstup** .  
  
### <a name="to-create-a-summary-profiling-data-file"></a>Vytvoření souhrnného datového souboru profilace  
  
- V okně příkazového řádku zadejte následující příkaz:  
  
   \<Path><strong>\<</strong>Soubor VSPerfReport VSP> **/SummaryFile** [**/output:** \<File Name> ]  
  
   Ve výchozím nastavení má soubor. vsps název se základním názvem souboru. vsp. Alternativní název můžete zadat pomocí možnosti **výstup** .
