---
title: Začátek | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b85d0fe9-f67a-4b7c-8d48-7eecf3f2dfe9
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: df3ccda9730be02bafb7f7d069a26193a4528d1e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778268"
---
# <a name="start"></a>Start
Možnost **Start** je možnost *VSPerfCmd.exe,* která inicializuje profiler na zadanou metodu profilování.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName [Options]
```

#### <a name="parameters"></a>Parametry
 `Method`Musí se jednat o jedno z následujících klíčových slov:

- **TRASA** - Určuje metodu instrumentace.

- **SAMPLE** - Určuje metodu vzorkování.

- **POKRYTÍ** - Určuje pokrytí kódu.

- **CONCURRENCY** - Určuje metodu konfliktu prostředků.

## <a name="required-options"></a>Požadované možnosti
 **Možnost Výstup** musí být zadána, pokud je na příkazovém řádku zadána možnost **Start.**

 **Výstup:** `filename` Určuje název výstupního souboru.

## <a name="exclusive-options"></a>Exkluzivní možnosti
 Následující možnosti lze použít pouze s možností **Start** na příkazovém řádku.

 **CrossSession**&#124;**CS** Umožňuje profilování mezi procesy. Podporovány jsou názvy možností **CrossSession** a **CS.**

 **Uživatel:**`domain\`[`username` ] Umožňuje klientovi přístup k monitoru ze zadaného účtu.

 **WinCounter:** `Path` [**Automark**:`n`] **WinCounter** určuje čítač výkonu systému Windows, který má být zahrnut jako značka do datového souboru profilování. **AutoMark** určuje interval v milisekundách mezi kolekcemi datového souboru.

## <a name="invalid-options"></a>Neplatné možnosti
 Následující možnosti nelze použít s možností **Start** na příkazovém řádku.

 **Stav** **stav** se vztahuje na ty procesy, které jsou profilovány. Obsahuje seznam procesů a vláken a jejich aktuální stav profilu (Zapnuto/Vypnuto). Pokud je například proces zastaven, **stav** to v sestavě neoznačí. **Stav** se zobrazí, že proces je profilován nebo ne.

 **Vypnutí**[**:**`Timeout`] Vypne profiler.

## <a name="example"></a>Příklad
 Následující příklad ukazuje, jak použít Možnost **Start** *VSPerfCmd.exe* k inicializaci profileru.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
```

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET webových aplikací](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilové služby](../profiling/command-line-profiling-of-services.md)
