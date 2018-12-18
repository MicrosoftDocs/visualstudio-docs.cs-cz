---
title: Obecné vlastnosti projektů (Android C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 65f4868b-b864-4989-a275-1e51869ef599
author: corob
ms.author: mblome
manager: douge
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
ms.openlocfilehash: b72cbb0d2660507a0578781c79a7cbdf60be7d8b
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/25/2018
ms.locfileid: "39252235"
---
# <a name="general-project-properties-android-c"></a>Obecné vlastnosti projektů (Android C++)

Vlastnost | Popis | Možnosti
--- | ---| ---
Výstupní adresář | Určuje relativní cestu k adresáři výstupního souboru; může obsahovat proměnné prostředí.
Zprostředkující adresář | Určuje relativní cestu k adresáři přechodového souboru; může obsahovat proměnné prostředí.
Cílový název | Určuje název souboru, který bude tento projekt generovat.
Cílová přípona | Určuje rozšíření souboru, který bude tento projekt generovat. (Příklad: *.exe* nebo *.dll*)
Přípony odstraňované při čištění | Středníkem oddělená specifikace zástupných znaků určujících, které soubory v přechodovém adresáři odstranit při čištění nebo opětovném sestavení.
Soubor protokolu sestavení | Určuje soubor protokolu sestavení pro zápis při protokolování sestavení je povolená.
Sada nástrojů platformy | Určuje, nástrojů pro sestavení aktuální konfigurace. Pokud není využito set, výchozí sady nástrojů
Typ konfigurace | Určuje typ výstupu generovaného touto konfigurací. | **Dynamická knihovna (.so)** – dynamická knihovna (*.so*)<br>**Statická knihovna (.a)** – statická knihovna (*.a*)<br>**Nástroj** – nástroj<br>**Soubor pravidel** -souboru pravidel<br>
Cílová úroveň rozhraní API | Android NDK rozhraní API: úroveň kterou míří tato konfigurace.
Použití STL | Určuje, která standardní knihovna C++ použít pro tuto konfiguraci. | **Minimální knihovny prostředí runtime jazyka C++ (systém)**<br>**Statická knihovna runtime jazyka C++ (gabi ++ _static)**<br>**Sdílená knihovna runtime jazyka C++ (gabi ++ _shared)**<br>**Sdílená knihovna běhového prostředí stlport (stlport_static)**<br>**Sdílená knihovna běhového prostředí (stlport stlport_shared)**<br>**Statická knihovna GNU STL (gnustl_static)**<br>**Sdílená knihovna GNU STL (gnustl_shared)**<br>**Knihovna LLVM libc ++ statické (c ++ _static)**<br>**Knihovna LLVM libc ++ sdílené (c ++ _shared)**<br>
Režim thumb | Generovat kód, který spouští pro mikroarchitekturu thumb. To platí jenom pro architekturu arm. | **Miniatury**<br>**Arm**<br>**Zakázané**<br>
