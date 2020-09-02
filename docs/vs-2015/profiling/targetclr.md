---
title: TargetCLR | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1e4ca52f631b3e2de9c01daab7e6268c42f20268
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145612"
---
# <a name="targetclr"></a>TargetCLR
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Možnost **TargetCLR** určuje verzi modulu CLR (Common Language Runtime), která má být profilovaná v případě, že je do aplikace načtena více než jedna verze modulu CLR.  
  
 Ve výchozím nastavení [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Nástroje pro profilaci cílem první verze modulu CLR, který je načten aplikací.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]   
```  
  
#### <a name="parameters"></a>Parametry  
 `ClrVersion`  
 Číslo verze modulu CLR. Použijte formát verze **vn. N. NNNNN**.  
  
## <a name="required-options"></a>Požadované možnosti  
 Možnost **TargetCLR** lze použít pouze s možnostmi **Spustit** nebo **připojit** .  
  
 **Spustit:**`AppName`  
 Spustí zadanou aplikaci a začne profilovat.  
  
 **Připojit:**`PID`  
 Spustí profilování zadaného procesu.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se používá možnost TargetCLR k ujištění, že soubor CLR verze 4.0.11003 je profilování.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003  
```
