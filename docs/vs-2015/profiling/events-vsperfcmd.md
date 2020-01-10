---
title: Události (VSPerfCmd) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0d24fc7a01a8eebe356f37704c1a821332f5dca1
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850767"
---
# <a name="events-vsperfcmd"></a>Události (VSPerfCmd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Možnost **události** VSPerfCmd. exe řídí protokolování trasování událostí pro Windows (ETW). Data ETW se ukládají do souboru. ETL, který je oddělený od datového souboru profileru. Data je možné zobrazit v sestavě pomocí příkazu [VSPerfReport](../profiling/vsperfreport.md) /Summary: ETW.  
  
 Možnost **události** může být volána kdykoli před voláním příkazu VSPerfCmd **shutdown** pro zastavení profilování.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]  
```  
  
#### <a name="parameters"></a>Parametry  
 **Zapnuto**&#124;  
 Spustí nebo zastaví shromažďování dat událostí.  
  
 `Guid`  
 Identifikátor GUID ovládacího prvku poskytovatele  
  
 `ProviderName`  
 Název zprostředkovatele registrovaného pomocí rozhraní WMI (Windows Management Instrumentation) (WMI).  
  
 `Flags`  
 "0x"-předem opravené hexadecimální hodnoty, které jsou definovány poskytovatelem událostí.  
  
 `Level`  
 Určuje množství shromažďovaných dat. `Level` definuje poskytovatel události.  
  
 Možnost **události** rozumí následujícím klíčovým slovům jádra jako názvům zprostředkovatelů:  
  
 **Přihlášení**  
 Zpracování událostí  
  
 **vlákno**  
 Události vlákna  
  
 **Obrázek**  
 Události načítání a uvolňování obrázku  
  
 **Disk**  
 Události v/v disku  
  
 **Soubor**  
 Vstupně výstupní události souboru  
  
 **Hardfault**  
 Závažné chyby stránky  
  
 **Pagefault**  
 Měkké chyby stránky  
  
 **Sítě**  
 Události sítě  
  
 **Rejstříku**  
 Události přístupu k registru  
  
 Počítejte s tím, že zprostředkovatele jádra lze povolit pouze. Nedá se zakázat, ani změnit jejich příznaky, dokud se monitorování neukončí.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Pokud jsou povoleny události modulu CLR ETW, jsou v sestavě zobrazení trasování také shromažďována další spouštěcí data. Pokud chcete vyloučit události spuštění v sestavě, použijte následující příkaz:  
  
```  
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5  
```  
  
> [!IMPORTANT]
> Pokud nechcete události po spuštění vyloučit, protože tyto události nejsou uvedené v souboru formát MOF (Managed Object Format) (MOF), zobrazí se v sestavě jako identifikátory GUID. Další informace naleznete na této stránce na webu společnosti Microsoft: [vzorový soubor formát MOF (Managed Object Format) (MOF)](https://msdn.microsoft.com/library/default.aspx).  
  
## <a name="see-also"></a>Viz také  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilace samostatných aplikací](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilování webových aplikací ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilace služeb](../profiling/command-line-profiling-of-services.md)
