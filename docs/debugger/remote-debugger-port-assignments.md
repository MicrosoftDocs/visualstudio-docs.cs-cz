---
title: Přiřazení portů vzdáleného ladicího programu | Microsoft Docs
ms.custom: ''
ms.date: 05/18/2018
ms.topic: reference
ms.assetid: 238bb4ec-bb00-4c2b-986e-18ac278f3959
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2d99a1aff2c241e81e8914a247d2f6d8981ee273
ms.sourcegitcommit: 9c7d8693108ecd2042a70c04cebe3c44af657baf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74239460"
---
# <a name="remote-debugger-port-assignments"></a>Přiřazení portů vzdáleného ladicího programu
Visual Studio Remote Debugger může běžet jako aplikace nebo jako služba na pozadí. Když je aplikace spuštěna jako aplikace, používá port, který je přiřazen ve výchozím nastavení následujícím způsobem:
::: moniker range=">=vs-2019"
- Visual Studio 2019:4024
::: moniker-end
- Visual Studio 2017:4022

- Visual Studio 2015:4020

- Visual Studio 2013:4018

- Visual Studio 2012:4016

Jinými slovy, číslo portu přiřazené vzdálenému ladicímu programu se zvýší o 2 pro každou verzi. Můžete nastavit jiné číslo portu, které chcete. Vyvysvětlíme, jak se v pozdější části nastavují čísla portů.

## <a name="the-remote-debugger-port-on-32-bit-operating-systems"></a>Port vzdáleného ladicího programu v 32 operačních systémech

::: moniker range=">=vs-2019"
 TCP 4024 (v aplikaci Visual Studio 2019) je hlavní port a je vyžadován pro všechny scénáře. Můžete ji nakonfigurovat buď z příkazového řádku, nebo z okna vzdáleného ladicího programu.
::: moniker-end
::: moniker range="vs-2017"
 TCP 4022 (v aplikaci Visual Studio 2017) je hlavní port a je vyžadován pro všechny scénáře. Můžete ji nakonfigurovat buď z příkazového řádku, nebo z okna vzdáleného ladicího programu.
::: moniker-end

 V okně vzdáleného ladicího programu klikněte na **nástroje > možnosti**a nastavte číslo portu TCP/IP.

 Na příkazovém řádku spusťte vzdálený ladicí program s přepínačem **/port** : **msvsmon/port \<číslo portu >** .

 Všechny přepínače příkazového řádku vzdáleného ladícího programu najdete v nápovědě pro vzdálené ladění (stisknutím klávesy **F1** nebo kliknutím na **Nápověda > použití** v okně vzdáleného ladicího programu).

## <a name="the-remote-debugger-port-on-64-bit-operating-systems"></a>Port vzdáleného ladicího programu v 64 operačních systémech
::: moniker range=">=vs-2019"
 64 po spuštění 32bitové verze vzdáleného ladicího programu se ve výchozím nastavení používá hlavní port (4024).  Pokud provedete ladění 32ho procesu, verze 64 vzdáleného ladicího programu 32 spustí na portu 4025 verzi vzdáleného ladicího programu, která je na portu (číslo hlavního portu se zvyšuje o 1). Pokud spustíte 32 vzdálený ladicí program, použije 4024 a 4025 se nepoužije.
::: moniker-end
::: moniker range="vs-2017"
 64 po spuštění 32bitové verze vzdáleného ladicího programu se ve výchozím nastavení používá hlavní port (4022).  Pokud provedete ladění 32ho procesu, verze 64 vzdáleného ladicího programu 32 spustí na portu 4023 verzi vzdáleného ladicího programu, která je na portu (číslo hlavního portu se zvyšuje o 1). Pokud spustíte 32 vzdálený ladicí program, použije 4022 a 4023 se nepoužije.
:::moniker-end

 Tento port lze konfigurovat z příkazového řádku: **msvsmon/wow64port \<číslo portu >** .

## <a name="the-discovery-port"></a>Port zjišťování
 UDP 3702 se používá k nalezení spuštěných instancí vzdáleného ladicího programu v síti (například dialogového okna **Najít** v dialogovém okně **připojit k procesu** ). Používá se jenom pro zjišťování počítače, na kterém běží vzdálený ladicí program, takže je volitelný, pokud máte nějaký jiný způsob, jak znát název počítače nebo IP adresu cílového počítače. Toto je standardní port pro zjišťování, takže číslo portu nelze nakonfigurovat.

 Pokud nechcete povolit zjišťování, můžete spustit msvsmon z příkazového řádku se zakázaným zjišťováním: **msvsmon/nodiscovery**.

## <a name="remote-debugger-ports-on-azure"></a>Porty vzdáleného ladicího programu v Azure
 Následující porty používá vzdálený ladicí program v Azure. Porty v cloudové službě jsou namapované na porty na jednotlivém virtuálním počítači. Všechny porty jsou TCP.

|Připojení|Port v cloudové službě|Port na virtuálním počítači|
|-|-|-|
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector|30400|30398|
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Forwarder|31400|31398|
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Forwarderx86|31401|31399|
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.FileUpload|32400|32398|

## <a name="see-also"></a>Viz také:
- [Vzdálené ladění](../debugger/remote-debugging.md)
