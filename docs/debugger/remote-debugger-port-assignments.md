---
title: Přiřazení portů vzdáleného ladicího programu | Microsoft Docs
description: Pochopte přiřazování portů programu Visual Studio Remote Debugger na 32 operačních systémech, 64 operačních systémů a Azure. Přečtěte si o portu zjišťování.
ms.custom: SEO-VS-2020
ms.date: 05/18/2018
ms.topic: reference
ms.assetid: 238bb4ec-bb00-4c2b-986e-18ac278f3959
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 40081f276dc9649cf448bf00e80d11fc80f58f47
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2021
ms.locfileid: "98204823"
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

Jinými slovy, číslo portu přiřazené vzdálenému ladicímu programu se zvýší o 2 pro každou verzi. Pokud chcete, můžete nastavit jiné číslo portu. Vyvysvětlíme, jak se v pozdější části nastavují čísla portů.

## <a name="the-remote-debugger-port-on-32-bit-operating-systems"></a>Port vzdáleného ladicího programu v 32 operačních systémech

::: moniker range=">=vs-2019"
 TCP 4024 (v aplikaci Visual Studio 2019) je hlavní port a je vyžadován pro všechny scénáře. Můžete ji nakonfigurovat buď z příkazového řádku, nebo z okna vzdáleného ladicího programu.
::: moniker-end
::: moniker range="vs-2017"
 TCP 4022 (v aplikaci Visual Studio 2017) je hlavní port a je vyžadován pro všechny scénáře. Můžete ji nakonfigurovat buď z příkazového řádku, nebo z okna vzdáleného ladicího programu.
::: moniker-end

 V okně vzdáleného ladicího programu klikněte na **nástroje > možnosti** a nastavte číslo portu TCP/IP.

 Na příkazovém řádku spusťte vzdálený ladicí program s přepínačem **/port** : **msvsmon/port \<port number>**.

 Všechny přepínače příkazového řádku vzdáleného ladícího programu najdete v nápovědě pro vzdálené ladění (stisknutím klávesy **F1** nebo kliknutím na **Nápověda > použití** v okně vzdáleného ladicího programu).

## <a name="the-remote-debugger-port-on-64-bit-operating-systems"></a>Port vzdáleného ladicího programu v 64 operačních systémech
::: moniker range=">=vs-2019"
 64 po spuštění 32bitové verze vzdáleného ladicího programu se ve výchozím nastavení používá hlavní port (4024).  Pokud provedete ladění 32ho procesu, verze 64 vzdáleného ladicího programu 32 spustí na portu 4025 verzi vzdáleného ladicího programu, která je na portu (číslo hlavního portu se zvyšuje o 1). Pokud spustíte 32 vzdálený ladicí program, použije 4024 a 4025 se nepoužije.
::: moniker-end
::: moniker range="vs-2017"
 64 po spuštění 32bitové verze vzdáleného ladicího programu se ve výchozím nastavení používá hlavní port (4022).  Pokud provedete ladění 32ho procesu, verze 64 vzdáleného ladicího programu 32 spustí na portu 4023 verzi vzdáleného ladicího programu, která je na portu (číslo hlavního portu se zvyšuje o 1). Pokud spustíte 32 vzdálený ladicí program, použije 4022 a 4023 se nepoužije.
:::moniker-end

 Tento port lze konfigurovat z příkazového řádku: **msvsmon/wow64port \<port number>**.

## <a name="the-discovery-port"></a>Port zjišťování
 UDP 3702 se používá k nalezení spuštěných instancí vzdáleného ladicího programu v síti (například dialogového okna **Najít** v dialogovém okně **připojit k procesu** ). Používá se jenom pro zjišťování počítače, na kterém běží vzdálený ladicí program, takže je volitelný, pokud máte nějaký jiný způsob, jak znát název počítače nebo IP adresu cílového počítače. Toto je standardní port pro zjišťování, takže číslo portu nelze nakonfigurovat.

 Pokud nechcete povolit zjišťování, můžete spustit msvsmon z příkazového řádku se zakázaným zjišťováním:  **msvsmon/nodiscovery**.

## <a name="remote-debugger-ports-on-azure"></a>Porty vzdáleného ladicího programu v Azure
 Následující porty používá vzdálený ladicí program v Azure. Porty v cloudové službě jsou namapované na porty na jednotlivém virtuálním počítači. Všechny porty jsou TCP.

|Připojení|Port v cloudové službě|Port na virtuálním počítači|
|-|-|-|
|Microsoft. WindowsAzure. plugins. Remotedebuggeru. Connector|30400|30398|
|Microsoft. WindowsAzure. plugins. Remotedebuggeru. resílaer|31400|31398|
|Microsoft. WindowsAzure. plugins. Remotedebuggeru. Forwarderx86|31401|31399|
|Nahrání Microsoft. WindowsAzure. plugins. Remotedebuggeru.|32400|32398|

## <a name="see-also"></a>Viz také
- [Vzdálené ladění](../debugger/remote-debugging.md)
