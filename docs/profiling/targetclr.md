---
title: TargetCLR | Microsoft Docs
description: Přečtěte si, jak možnost TargetCLR určuje verzi modulu CLR (Common Language Runtime), která se má profilovat, pokud je v aplikaci načtena více než jedna verze modulu CLR.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 76454a77a895a44d4c6871ad5061ee4b6079e604
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868177"
---
# <a name="targetclr"></a>TargetCLR
Možnost **TargetCLR** určuje verzi modulu CLR (Common Language Runtime), která má být profilovaná v případě, že je do aplikace načtena více než jedna verze modulu CLR.

 Ve výchozím nastavení [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci cílem první verze modulu CLR, který je načten aplikací.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]
```

#### <a name="parameters"></a>Parametry
 `ClrVersion` Číslo verze modulu CLR. Použijte formát verze **vn. N. NNNNN**.

## <a name="required-options"></a>Požadované možnosti
 Možnost **TargetCLR** lze použít pouze s možnostmi **Spustit** nebo **připojit** .

 **Spustit:** `AppName` Spustí zadanou aplikaci a začne profilovat.

 **Připojit:** `PID` Spustí profilování zadaného procesu.

## <a name="example"></a>Příklad
 V tomto příkladu se používá možnost TargetCLR k ujištění, že soubor CLR verze 4.0.11003 je profilování.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003
```
