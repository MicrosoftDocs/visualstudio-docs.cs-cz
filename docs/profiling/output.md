---
title: Výstup | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ab01f67d44e8c6e0cc13eaf9b0046695a0132e65
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778502"
---
# <a name="output"></a>Výstup
Volba **Výstup** určuje název datového souboru profilování pro relaci výkonu. **Výstup** musí být použit s možností **Start.**

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName [Options]
```

#### <a name="parameters"></a>Parametry
 `FileName`Název datového souboru. Jsou přijímány úplné a částečné cesty. Pokud cesta není zadána, soubor je vytvořen v aktuálním adresáři.

## <a name="required-options"></a>Požadované možnosti
 Možnost **Výstup** musí být použita s možností **Start.**

 **Start:** `Method` Určuje název výstupního souboru.

## <a name="example"></a>Příklad
 V následujícím příkladu je datový soubor profilování vytvořen v aktuálním adresáři.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
```

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET webových aplikací](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilové služby](../profiling/command-line-profiling-of-services.md)
