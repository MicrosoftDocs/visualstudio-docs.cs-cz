---
title: Uživatel (VSPerfCmd) | Microsoft Docs
description: Zjistěte, jak možnost uživatel Určuje doménu a uživatelské jméno účtu, který vlastní profilace procesu.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ee1a478e-374d-4f30-ae28-d260b9d4723a
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b0240a4dcf0830dca6667bcbd055d677ef7bc204
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885999"
---
# <a name="user-vsperfcmd"></a>Uživatel (VSPerfCmd)
Možnost **uživatel** určuje doménu a uživatelské jméno účtu, který vlastní profilace procesu. Tato možnost je vyžadována, pouze pokud je proces spuštěn jako jiný uživatel než přihlášený uživatel. Vlastník procesu je uveden ve sloupci uživatelské jméno na kartě **procesy** ve Správci úloh systému Windows.

 Možnost **uživatel** lze zadat pouze v příkazovém řádku, který obsahuje také možnost **Start** .

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]
```

#### <a name="parameters"></a>Parametry
 `Domain` Název domény uživatele.

 `UserName` Jméno uživatele.

## <a name="required-options"></a>Požadované možnosti
 Možnost **uživatele** lze použít pouze s možností **Start** .

 **Začátek:** `Method` Inicializuje Profiler na určenou metodu profilace.

## <a name="example"></a>Příklad
 Následující příklad ukazuje použití možnosti **uživatele** .

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM
```

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET webové aplikace Profile](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilovací služby](../profiling/command-line-profiling-of-services.md)
