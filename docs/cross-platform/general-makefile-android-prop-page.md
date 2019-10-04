---
title: Obecné vlastnosti projektu (soubor C++ pravidel pro Android) | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: f76d717c-56ed-4373-8cf9-9bd1a053a4cd
author: corob-msft
ms.author: corob
manager: jillfra
f1_keywords:
- VC.Project.VCConfiguration.OutputDirectory
- VC.Project.VCConfiguration.IntermediateDirectory
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCConfiguration.ConfigurationType
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: b7fa1b91951e7a3fb145cc26275016037d1b5f2b
ms.sourcegitcommit: 6ae0a289f1654dec63b412bfa22035511a2ef5ad
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2019
ms.locfileid: "71950582"
---
# <a name="general-project-properties-android-c-makefile"></a>Obecné vlastnosti projektu (soubor C++ pravidel pro Android)

Vlastnost | Popis | Vlastnit
--- | ---| ---
Výstupní adresář | Určuje relativní cestu k adresáři výstupního souboru. může obsahovat proměnné prostředí.
Zprostředkující adresář | Určuje relativní cestu k adresáři zprostředkujícího souboru. může obsahovat proměnné prostředí.
Soubor protokolu sestavení | Určuje soubor protokolu sestavení, do kterého se má zapisovat, pokud je povolené protokolování sestavení.
Typ konfigurace | Určuje typ výstupu, který tato konfigurace generuje. | **Dynamická knihovna (. so)** – dynamická knihovna ( *. so*)<br>**Statická knihovna (. a)** – statická knihovna ( *. a*)<br>**Nástroj** – nástroj<br>**Makefile** -makefile<br>
