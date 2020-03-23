---
title: Události (VSPerfCmd) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 46b47f9b615c824d25e931cd3d05f5d2a04257ba
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777318"
---
# <a name="events-vsperfcmd"></a>Události (VSPerfCmd)
Možnost *Události VSPerfCmd.exe* **Events** řídí protokolování trasování událostí pro systém Windows (ETW). Data ETW jsou uložena do souboru .etl, který je oddělený od datového souboru profileru. Data lze zobrazit v sestavě pomocí příkazu [VSPerfReport](../profiling/vsperfreport.md) /summary:etw.

 **Možnost Události** lze volat kdykoli před Příkaz **vypnutí** VSPerfCmd je volána k zastavení profilování.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]
```

#### <a name="parameters"></a>Parametry
 **V**&#124;**Vypnuto** Spustí nebo zastaví shromažďování dat událostí.

 `Guid`Identifikátor GUID ovládacího prvku zprostředkovatele.

 `ProviderName`Název zprostředkovatele, který je registrován pomocí služby WMI (WMI).

 `Flags`Hodnota hexadecimálních příznaků s předponou 0x, která je definována zprostředkovatelem události.

 `Level`Určuje množství shromážděných dat. `Level`je definována poskytovatelem události.

 Možnost **Události** rozumí následujícím klíčovým slovům jádra jako názvům zprostředkovatelů:

 **Proces** Zpracovat události

 **Vlákno** Události podprocesu

 **Obrázek** Události načtení a uvolnění bitové kopie

 **Disk** Události vstupně-no disku

 **Soubor** Události vstupně-no souborů

 **Tvrdá chyba** Chyby pevné stránky

 **Pagefault** Chyby měkké stránky

 **Síť** Síťové události

 **Registr** Události přístupu k registru

 Všimněte si, že zprostředkovatele jádra lze povolit pouze. Nelze jej zakázat ani upravit jeho příznaky, dokud se monitor nevypne.

## <a name="remarks"></a>Poznámky

> [!NOTE]
> Pokud jsou povoleny události CLR ETW, další spouštěcí data jsou také shromažďovány v sestavě zobrazení trasování. Chcete-li vyloučit události spuštění z zobrazování v sestavě, použijte následující příkaz:

```cmd
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5
```

> [!IMPORTANT]
> Pokud nevylučujete události při spuštění, pak protože tyto události nejsou uvedeny v souboru Formát spravovaného objektu (MOF), zobrazí se v sestavě jako identifikátory GUID. Další informace naleznete na této stránce na webu společnosti Microsoft: [Ukázkový formát spravovaného objektu (MOF).](https://msdn.microsoft.com/library/default.aspx)

## <a name="see-also"></a>Viz také
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilovat samostatné aplikace](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET webových aplikací](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilové služby](../profiling/command-line-profiling-of-services.md)
