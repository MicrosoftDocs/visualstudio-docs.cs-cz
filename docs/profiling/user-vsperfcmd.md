---
title: Uživatel (VSPerfCmd) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ee1a478e-374d-4f30-ae28-d260b9d4723a
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7dbb1a155e8e0ffd2690b5850299b8075a63ea3d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779958"
---
# <a name="user-vsperfcmd"></a>Uživatel (VSPerfCmd)
Možnost **Uživatel** určuje doménu a uživatelské jméno účtu, který vlastní profilovaný proces. Tato možnost je vyžadována pouze v případě, že proces je spuštěn jako uživatel než přihlášený uživatel. Vlastník procesu je uveden ve sloupci Uživatelské jméno na kartě **Procesy** ve Správci úloh systému Windows.

 Možnost **Uživatel** lze zadat pouze na příkazovém řádku, který obsahuje také možnost **Start.**

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]
```

#### <a name="parameters"></a>Parametry
 `Domain`Název domény uživatele.

 `UserName`Jméno uživatele.

## <a name="required-options"></a>Požadované možnosti
 Možnost **Uživatel** lze použít pouze s možností **Start.**

 **Start:** `Method` Inicializuje profiler na zadanou metodu profilování.

## <a name="example"></a>Příklad
 Následující příklad ukazuje použití možnosti **Uživatel.**

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM
```

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET webových aplikací](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilové služby](../profiling/command-line-profiling-of-services.md)
