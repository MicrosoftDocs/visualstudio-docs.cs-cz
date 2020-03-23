---
title: Cílová nařízení o čl. Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: fffcab1d841840c15957e8dae0ff0f87b20de28d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74771598"
---
# <a name="targetclr"></a>TargetCLR
Možnost **TargetCLR** určuje verzi běžného jazyka run-time (CLR) pro profil při načtení více než jedné verze CLR v aplikaci.

 Ve výchozím [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nastavení profilovací nástroje cílí na první verzi CLR načtenou aplikací.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]
```

#### <a name="parameters"></a>Parametry
 `ClrVersion`Číslo verze CLR. Použijte formát verze **vN.N.NNNNN**.

## <a name="required-options"></a>Požadované možnosti
 Možnost **TargetCLR** lze použít pouze s možnostmi **Spustit** nebo **Připojit.**

 **Spuštění:** `AppName` Spustí zadanou aplikaci a spustí profil.

 **Připojit:** `PID` Spustí profil zadaný proces.

## <a name="example"></a>Příklad
 V tomto příkladu targetclr možnost se používá k ujistěte se, že CLR verze 4.0.11003 je profilován.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003
```
