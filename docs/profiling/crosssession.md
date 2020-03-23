---
title: CrossSession | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 06de982643a08e1af88073dde0fb0a9abc029900
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779451"
---
# <a name="crosssession"></a>CrossSession
*Možnost VSPerfCmd.exe* **CrossSession** umožňuje profiler shromažďovat data z libovolné relace konzoly. Možnost **Křížová relace** musí být použita s možností **Start.**

 Místo **crosssession**můžete použít zkratku **CS** .

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Start:Method /CrossSession [Options]
```

#### <a name="parameters"></a>Parametry
 Žádný

## <a name="valid-options"></a>Platné možnosti
 Chcete-li povolit profilování v jiné relaci, musí být možnost **CrossSession** zadána pomocí možnosti **Start.** **CrossSession** musí být také zadán v jakékoli následné **VSPerfCmd připojit** a **odpojit** příkazy.

 **Start:** `Method` Možnost **Start** inicializuje profiler na zadanou metodu profilování.

 **Připojit:** _PID_[**,**_PID_] Zahájí profilování zadaných procesů.

 **Odpojení**[**:**_PID_[,_PID_]] Zastaví profilování zadaných procesů.

## <a name="example"></a>Příklad
 V tomto příkladu se možnost **CrossSession** používá k připojení k aplikaci, která byla spuštěna v jiné relaci konzoly.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession
VSPerfCmd.exe /Attach:12345 /CS
```

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET webových aplikací](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilové služby](../profiling/command-line-profiling-of-services.md)
