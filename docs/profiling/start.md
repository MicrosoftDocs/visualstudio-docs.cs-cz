---
title: Spustit | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74778268"
---
# <a name="start"></a>Spustit
Možnost **Start** je *VSPerfCmd.exe* možnost, která inicializuje Profiler na určenou metodu profilace.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName [Options]
```

#### <a name="parameters"></a>Parametry
 `Method` Musí být jedno z následujících klíčových slov:

- **Trace** – určuje metodu instrumentace.

- **Sample** – určuje metodu vzorkování.

- **Pokrytí** – určuje pokrytí kódu.

- **Concurrency** – určuje metodu kolizí prostředků.

## <a name="required-options"></a>Požadované možnosti
 Možnost **Output** musí být zadána, je-li na příkazovém řádku zadán **Start** .

 **Výstup:** `filename` Určuje název výstupního souboru.

## <a name="exclusive-options"></a>Exkluzivní možnosti
 Následující možnosti lze použít pouze s možností **Start** na příkazovém řádku.

 **CrossSession**&#124;**cs** umožňuje profilování mezi procesy. Podporují se i názvy možností **CrossSession** a **cs** .

 **Uživatel:**[ `domain\` ] `username` povolí klientský přístup k monitorování ze zadaného účtu.

 **WinCounter:** `Path` [**AutoMark**: `n` ] **WinCounter** určuje čítač výkonu systému Windows, který má být zahrnut jako značka v souboru dat profilování. **AutoMark** určuje interval v milisekundách mezi kolekcemi datového souboru.

## <a name="invalid-options"></a>Neplatné možnosti
 Následující možnosti nelze použít s možností **Start** na příkazovém řádku.

 **Stav stavu** **se týká těchto** procesů, které jsou profilované. Uvádí procesy a vlákna a jejich aktuální stav profilu (zapnuto/vypnuto). Například pokud je proces zastavený, **stav** se v sestavě neuvádí. **Stav** zobrazí, že proces je profilování nebo nikoli.

 **Vypnutí**[**:** `Timeout` ] vypne Profiler.

## <a name="example"></a>Příklad
 Následující příklad ukazuje, jak použít možnost *VSPerfCmd.exe* **Start** pro inicializaci profileru.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
```

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET webové aplikace Profile](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilovací služby](../profiling/command-line-profiling-of-services.md)
