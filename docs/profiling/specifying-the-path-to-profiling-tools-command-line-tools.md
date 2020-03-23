---
title: Určení nástrojů příkazového řádku Cesty k nástrojům profilování | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75406305"
---
# <a name="specify-the-path-to-profiling-tools-command-line-tools"></a>Určení cesty k nástrojům příkazového řádku nástrojů profilování

Cesta nástrojů [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] příkazového řádku Nástroje profilování není přidána do proměnné prostředí PATH. V 32bitových počítačích jsou nástroje v jednom adresáři. V 64bitových počítačích jsou k dispozici 32bitové a 64bitové verze nástrojů pro profilování.

## <a name="32-bit-computers"></a>32bitové počítače

Pro nativní kód jsou v *souboru VSPerf.dll*. Soubor záhlaví *VSPerf.h*a knihovna importu *VSPerf.lib*jsou umístěny v adresáři *Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK.*

 Pro spravovaný kód jsou rozhraní API profileru v *souboru Microsoft.VisualStudio.Profiler.dll*. Tato dll byla nalezena v adresáři *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools.*

## <a name="64-bit-computers"></a>64bitové počítače

V 64bitových počítačích zadejte cestu podle cílové platformy profilované aplikace.

- Pro 32bitové aplikace je výchozím adresářem nástrojů profileru:

     (nativní) *Microsoft Visual Studio\2017\Týmové nástroje\Nástroje výkonu\PerfSDK*
     
     (spravováno) *Aplikace Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools*

- Pro 64bitové aplikace je výchozím adresářem nástrojů profileru:

     (nativní) *Aplikace Microsoft Visual Studio\2017\Týmové nástroje\Nástroje pro výkon\x64\PerfSDK*

     (spravováno) *Aplikace Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools\x64*
