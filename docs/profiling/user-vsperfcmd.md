---
title: Uživatel (VSPerfCmd) | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779958"
---
# <a name="user-vsperfcmd"></a>Uživatel (VSPerfCmd)
Možnost **uživatel** určuje doménu a uživatelské jméno účtu, který vlastní profilace procesu. Tato možnost je vyžadována, pouze pokud je proces spuštěn jako jiný uživatel než přihlášený uživatel. Vlastník procesu je uveden ve sloupci uživatelské jméno na kartě **procesy** ve Správci úloh systému Windows.

 Možnost **uživatel** lze zadat pouze v příkazovém řádku, který obsahuje také možnost **Start** .

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]
```

#### <a name="parameters"></a>Parametry
 `Domain` název domény uživatele.

 `UserName` jméno uživatele.

## <a name="required-options"></a>Požadované možnosti
 Možnost **uživatele** lze použít pouze s možností **Start** .

 **Start:** `Method` inicializuje Profiler na určenou metodu profilace.

## <a name="example"></a>Příklad
 Následující příklad ukazuje použití možnosti **uživatele** .

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM
```

## <a name="see-also"></a>Viz také:
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET webové aplikace Profile](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilovací služby](../profiling/command-line-profiling-of-services.md)
