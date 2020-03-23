---
title: Args | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3b6d01a95b7e0872d6bb36c6d9f3917bc6a05b3b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779815"
---
# <a name="args"></a>Args
VSPerfCmd.exe **Args** možnost určuje seznam argumentů, které jsou předány do cílové aplikace dílčího příkazu **Spuštění.**

 **Args** lze použít pouze v **případě, že** je na příkazovém řádku zadáno také spuštění. **Args** je volitelný, když je **zadáno spuštění.**

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Launch:AppName /Args:Arguments [Options]
```

#### <a name="parameters"></a>Parametry
 `Arguments`Seznam argumentů pro cílovou aplikaci příkazu **Spustit.**

## <a name="required-options"></a>Požadované možnosti
 **Spuštění:** `AppName` Spustí zadanou aplikaci a začne profilování metodou vzorkování.

## <a name="example"></a>Příklad
 Následující příklad používá **Args** možnost předat argumenty TestApp.exe.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"
```

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilování samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilování ASP.NET webových aplikací](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilování služeb](../profiling/command-line-profiling-of-services.md)
