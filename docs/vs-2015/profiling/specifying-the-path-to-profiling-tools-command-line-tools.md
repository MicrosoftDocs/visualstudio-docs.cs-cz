---
title: Určení cesty pro Nástroje pro profilaci nástrojů příkazového řádku | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7fadcff84c4b927a7718d7d4ad1311918ae0f18a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199781"
---
# <a name="specifying-the-path-to-profiling-tools-command-line-tools"></a>Určení cesty k nástrojům příkazového řádku pro profilaci
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Do proměnné prostředí PATH se nepřidala cesta k nástrojům příkazového řádku nástroje pro profilaci. Na 32 počítačů se nástroje nacházejí v jednom adresáři. K dispozici jsou 32 a 64 bitové verze nástrojů pro profilaci v počítačích s 64.  
  
## <a name="32-bit-computers"></a>32 – bitové počítače  
 V 32 počítačích je výchozím adresářem nástrojů profileru *jednotka*\Program Files\Microsoft Visual Studio 11.0 \ Team Tools\Performance Tools.  
  
## <a name="64-bit-computers"></a>64bitové počítače  
 Na 64 počítačů zadejte cestu podle cílové platformy profilované aplikace.  
  
- Pro 32 aplikací je výchozím adresářem nástrojů profileru:  
  
     *Jednotka*\Program Files (x86) \Microsoft Visual Studio 11.0 \ Team Tools\Performance Tools  
  
- Pro 64 aplikací je výchozím adresářem nástrojů profileru:  
  
     *Jednotka*\Program Files (x86) \Microsoft Visual Studio 11.0 \ Team Tools\Performance Tools\x64
