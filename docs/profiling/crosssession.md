---
title: CrossSession | Microsoft Docs
description: Naučte se používat možnost VSPerfCmd.exe CrossSession, pokud chcete, aby Profiler mohl shromažďovat data z jakékoli relace konzoly. Je nutné zadat také možnost Start.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a52acb80bac511706086c56074eb5bfe450b7674
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955902"
---
# <a name="crosssession"></a>CrossSession
Možnost *VSPerfCmd.exe* **CrossSession** umožňuje profileru shromažďovat data z jakékoli relace konzoly. Možnost **CrossSession** je nutné použít s možností **Start** .

 Místo **CrossSession** můžete použít zkratku **cs** .

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Start:Method /CrossSession [Options]
```

#### <a name="parameters"></a>Parametry
 Žádné

## <a name="valid-options"></a>Platné možnosti
 Chcete-li povolit profilaci v jiné relaci, možnost **CrossSession** musí být zadána s možností **Start** . **CrossSession** se musí zadat taky v dalších příkazech připojení a **odpojení** **VSPerfCmd** .

 **Začátek:** `Method` Možnost **Spustit** inicializuje Profiler na určenou metodu profilace.

 **Připojit:** _PID_[**,**_PID_] začne profilovat zadané procesy.

 **Odpojení**[**:**_PID_[,_PID_]] zastaví profilaci zadaných procesů.

## <a name="example"></a>Příklad
 V tomto příkladu se používá možnost **CrossSession** pro připojení k aplikaci, která byla spuštěna v jiné relaci konzoly.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession
VSPerfCmd.exe /Attach:12345 /CS
```

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET webové aplikace Profile](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilovací služby](../profiling/command-line-profiling-of-services.md)
