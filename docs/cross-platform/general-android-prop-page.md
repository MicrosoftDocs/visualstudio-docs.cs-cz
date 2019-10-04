---
title: Obecné vlastnosti projektu (Android C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 65f4868b-b864-4989-a275-1e51869ef599
author: corob-msft
ms.author: corob
manager: jillfra
f1_keywords:
- VC.Project.VCConfiguration.OutputDirectory
- VC.Project.VCConfiguration.IntermediateDirectory
- VC.Project.VCConfiguration.TargetName
- VC.Project.VCConfiguration.TargetExt
- VC.Project.VCConfiguration.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCConfiguration.PlatformToolset
- VC.Project.VCConfiguration.ConfigurationType
- VC.Project.VCConfiguration.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.UseOfSTL
- VC.Project.VCConfiguration.ThumbMode
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 4526a329b4e047a449995b7b5ef66362aff1cc8f
ms.sourcegitcommit: 6ae0a289f1654dec63b412bfa22035511a2ef5ad
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2019
ms.locfileid: "71950589"
---
# <a name="general-project-properties-android-c"></a>Obecné vlastnosti projektů (Android C++)

Vlastnost | Popis | Vlastnit
--- | ---| ---
Výstupní adresář | Určuje relativní cestu k adresáři výstupního souboru. může obsahovat proměnné prostředí.
Zprostředkující adresář | Určuje relativní cestu k adresáři zprostředkujícího souboru. může obsahovat proměnné prostředí.
Cílový název | Určuje název souboru, který bude tento projekt generovat.
Cílová Přípona | Určuje příponu souboru, kterou bude tento projekt generovat. (Příklad: *. exe* nebo *. dll*)
Přípony k odstranění při čištění | Středníky oddělená specifikace zástupných znaků, pro které se soubory v zprostředkujícím adresáři odstraňují při čištění nebo opětovném sestavení.
Soubor protokolu sestavení | Určuje soubor protokolu sestavení, do kterého se má zapisovat, pokud je povolené protokolování sestavení.
Sada nástrojů platformy | Určuje sadu nástrojů použitou pro sestavení aktuální konfigurace. Pokud není nastavená, použije se výchozí sada nástrojů.
Typ konfigurace | Určuje typ výstupu, který tato konfigurace generuje. | **Dynamická knihovna (. so)** – dynamická knihovna ( *. so*)<br>**Statická knihovna (. a)** – statická knihovna ( *. a*)<br>**Nástroj** – nástroj<br>**Makefile** -makefile<br>
Cílová úroveň rozhraní API | Úroveň rozhraní API pro Android NDK, na kterou cílí Tato konfigurace.
Použití STL | Určuje, C++ která standardní knihovna se má použít pro tuto konfiguraci. | **Minimální C++ běhová knihovna (systém)**<br>**C++Statická knihovna modulu runtime (Gabi + + _static)**<br>**C++Běhová knihovna Shared (Gabi + + _shared)**<br>**Statická knihovna sdílená knihovna běhového runtime (stlport_static)**<br>**Sdílená knihovna sdílená knihovna běhového runtime (stlport_shared)**<br>**Statická knihovna GNU STL (gnustl_static)**<br>**Sdílená knihovna GNU STL (gnustl_shared)**<br>**Statická knihovna LLVM libc + + (c++ _static)**<br>**Sdílená knihovna LLVM libc + + (c++ _shared)**<br>
Režim miniatur | Vygeneruje kód, který se spustí pro mikroarchitekturu pro palec. To platí jenom pro architekturu ARM. | **Táhl**<br>**ARM**<br>**Disabled** (Zakázáno)<br>
