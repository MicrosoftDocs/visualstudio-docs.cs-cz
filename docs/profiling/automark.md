---
title: AutoMark | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c4de965e-0364-4f78-9936-1f509e85df74
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: aaa1e7f39a9dcaedec51eb6a40ed3a2d06bcfb0e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85330612"
---
# <a name="automark"></a>AutoMark
Možnost **AutoMark** určuje počet milisekund mezi kolekcí událostí čítače výkonu softwaru systému Windows. Čítače výkonu systému Windows jsou zadány v možnosti **WinCounter** .

 V příkazovém řádku lze zadat pouze jednu možnost automatického **označení** . Všimněte si, že interval vzorkování **WinCounter** určený parametrem **AutoMark** je nezávislý na hlavním intervalu vzorkování.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Start:Method /WinCounter:Path /AutoMark:Milliseconds
```

#### <a name="parameters"></a>Parametry
 `Milliseconds` Určuje počet milisekund mezi kolekcemi událostí čítače výkonu systému Windows.

## <a name="required-options"></a>Požadované možnosti
 **WinCounter:** `Path` Určuje čítač výkonu systému Windows, který má být shromážděn. Pokud používáte metodu instrumentace, je možné zadat více čítačů systému Windows. Při použití metody vzorkování lze zadat pouze jeden čítač softwaru. Možnost **WinCounter** je nutné zadat na příkazovém řádku, který obsahuje možnost **Start** .

## <a name="example"></a>Příklad
 V tomto příkladu je pro dva čítače výkonu systému Windows nastaven interval vzorkování 1000 milisekund.

```cmd
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /WinCounter:"\Process(*)\% Processor Time" /WinCounter:"\ASP.NET\Pages/sec" /AutoMark:1000
VSPerfCmd.exe /Launch:TestApp.exe
```

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET webové aplikace Profile](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilovací služby](../profiling/command-line-profiling-of-services.md)
