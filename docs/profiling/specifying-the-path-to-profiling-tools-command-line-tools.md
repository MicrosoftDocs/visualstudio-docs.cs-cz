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
ms.openlocfilehash: 087407f511c038a369694beca8a9fe4ecc2ff7b7
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74771570"
---
# <a name="specify-the-path-to-profiling-tools-command-line-tools"></a>Zadejte cestu k nástrojům příkazového řádku nástrojů pro profilaci

Do proměnné prostředí PATH se nepřidala cesta k nástrojům příkazového řádku [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci. Na 32 počítačů se nástroje nacházejí v jednom adresáři. K dispozici jsou 32 a 64 bitové verze nástrojů pro profilaci v počítačích s 64.

## <a name="32-bit-computers"></a>32 – bitové počítače

::: moniker range="vs-2017"
 V případě nativního kódu jsou rozhraní API profileru sady Visual Studio v *knihovně VSPerf. dll*. Hlavičkový soubor, *VSPerf. h*a knihovna importů *VSPerf. lib*, jsou umístěny v adresáři *Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK* .
::: moniker-end

 Pro spravovaný kód jsou rozhraní API profileru v *knihovně Microsoft. VisualStudio. Profiler. dll*. Tato knihovna DLL se nachází v adresáři *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools* .

## <a name="64-bit-computers"></a>64 – bitové počítače

Na 64 počítačů zadejte cestu podle cílové platformy profilované aplikace.

::: moniker range="vs-2017"
- Pro 32 aplikací je výchozím adresářem nástrojů profileru:

     nativní *Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK* (Managed) *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools*

- Pro 64 aplikací je výchozím adresářem nástrojů profileru:

     nativní *Microsoft Visual Studio\2017\Team Tools\Performance Tools\x64\PerfSDK* (Managed) *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools\x64*
::: moniker-end
