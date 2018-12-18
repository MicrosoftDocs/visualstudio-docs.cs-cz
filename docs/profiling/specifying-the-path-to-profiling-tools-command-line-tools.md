---
title: Určení cesty k profilace nástroje příkazového řádku nástroje | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1afb0b00a7e121c611dedbc235684a67cc9cec53
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2018
ms.locfileid: "34814492"
---
# <a name="specify-the-path-to-profiling-tools-command-line-tools"></a>Zadejte cestu k nástrojům příkazového řádku pro profilaci
Cesta [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nástroje příkazového řádku v nástrojích pro profilaci nebyla přidána do proměnné prostředí PATH. Na počítačích 32bitová verze nástroje jsou v jednom adresáři. Existují 32bitové a 64bitové verze nástrojů pro profilaci na 64bitových počítačích.  
  
## <a name="32-bit-computers"></a>32bitové počítače  
 Na 32bitové počítače, je výchozí adresář profileru nástroje *disk\Program 11.0\Team Files\Microsoft Visual Studio Tools nástroje*.  
  
## <a name="64-bit-computers"></a>64bitové počítače  
 Na 64bitových počítačích zadejte cestu podle cílové platformy PROFILOVANÉHO aplikace.  
  
-   Pro 32bitové aplikace je výchozí adresář profiler nástrojů:  
  
     *disk\Program soubory (x86) \Microsoft Visual Studio 11.0\Team nástrojů nástroje*  
  
-   Pro 64bitové aplikace je výchozí adresář profiler nástrojů:  
  
     *disk\Program soubory (x86) \Microsoft Visual Studio 11.0\Team Tools\x64 nástroje*