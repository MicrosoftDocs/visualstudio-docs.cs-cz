---
title: Určení cesty pro Nástroje pro profilaci nástrojů příkazového řádku | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f66ed17aec8c6e5303ea61741021dd25032fcb37
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75406305"
---
# <a name="specify-the-path-to-profiling-tools-command-line-tools"></a>Zadejte cestu k nástrojům příkazového řádku nástrojů pro profilaci

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Do proměnné prostředí PATH se nepřidala cesta k nástrojům příkazového řádku nástroje pro profilaci. Na 32 počítačů se nástroje nacházejí v jednom adresáři. K dispozici jsou 32 a 64 bitové verze nástrojů pro profilaci v počítačích s 64.

## <a name="32-bit-computers"></a>32 – bitové počítače

V případě nativního kódu jsou rozhraní API profileru sady Visual Studio v *VSPerf.dll*. Hlavičkový soubor, *VSPerf. h*a knihovna importů *VSPerf. lib*, jsou umístěny v adresáři *Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK* .

 Pro spravovaný kód jsou rozhraní API profileru v *Microsoft.VisualStudio.Profiler.dll*. Tato knihovna DLL se nachází v adresáři *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools* .

## <a name="64-bit-computers"></a>64bitové počítače

Na 64 počítačů zadejte cestu podle cílové platformy profilované aplikace.

- Pro 32 aplikací je výchozím adresářem nástrojů profileru:

     nativní *Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK*
     
     starosti *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools*

- Pro 64 aplikací je výchozím adresářem nástrojů profileru:

     nativní *Microsoft Visual Studio\2017\Team Tools\Performance Tools\x64\PerfSDK*

     starosti *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools\x64*
