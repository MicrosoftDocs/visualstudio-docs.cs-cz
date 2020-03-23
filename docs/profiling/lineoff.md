---
title: Lineoff | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ac671c3b0ba40c462403b2afa850c3936156d6d2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74774123"
---
# <a name="lineoff"></a>LineOff
Ve výchozím nastavení profiler shromažďuje data posunu čísla řádku zdrojového kódu a čísla řádku, když používáte metodu profilování vzorkování. VSPerfCmd **LineOff** možnost zakáže shromažďování dat číslo řádku při VSPerfCmd se používá ke spuštění aplikace. Profilování dat jsou shromažďovány na úrovni funkce při **LineOff** je zadán.

 **LineOff** můžete použít pouze s možností **Spustit** a pouze v případě, že profiler byl inicializován na vzorkování pomocí **možnosti Start**:**Ukázka.**

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Launch:AppName /LineOff [Options]
```

#### <a name="parameters"></a>Parametry
 Žádný

## <a name="required-options"></a>Požadované možnosti
 Možnost **LineOff** lze použít pouze na příkazovém řádku, který obsahuje možnost **Spustit.**

 **Spuštění:** `AppName` Spustí zadanou aplikaci a začne profilování metodou vzorkování.

## <a name="example"></a>Příklad
 Tento příklad spustí aplikaci a profiler a zakáže vzorkování na úrovni řádku.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /LineOff
```

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET webových aplikací](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilové služby](../profiling/command-line-profiling-of-services.md)
