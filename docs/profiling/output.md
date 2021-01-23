---
title: Výstup | Microsoft Docs
description: Přečtěte si, jak možnost Output Určuje název souboru dat profilování pro relaci výkonu. Výstup musí být použit s možností Start.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6067e13e33875be778ff59739f5511c4116937ed
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722799"
---
# <a name="output"></a>Výstup
Možnost **výstup** Určuje název souboru dat profilování pro relaci výkonu. **Výstup** musí být použit s možností **Start** .

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName [Options]
```

#### <a name="parameters"></a>Parametry
 `FileName` Název datového souboru. Jsou přijímány úplné a částečné cesty. Pokud není zadaná cesta, vytvoří se soubor v aktuálním adresáři.

## <a name="required-options"></a>Požadované možnosti
 Možnost **Output** musí být použita s možností **Start** .

 **Začátek:** `Method` Určuje název výstupního souboru.

## <a name="example"></a>Příklad
 V následujícím příkladu je soubor dat profilace vytvořen v aktuálním adresáři.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
```

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET webové aplikace Profile](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilovací služby](../profiling/command-line-profiling-of-services.md)
