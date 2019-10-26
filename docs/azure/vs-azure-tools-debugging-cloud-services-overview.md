---
title: Možnosti ladění Azure Cloud Services | Microsoft Docs
description: Ladění Azure Cloud Services
author: mikejo5000
manager: jillfra
ms.assetid: 80755da7-8350-4f5c-97ce-2962beabb36d
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 03/18/2017
ms.author: mikejo
ms.technology: vs-ide-debug
ms.openlocfilehash: 94e7d48c767ef9705c20b049b57f459290679217
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911850"
---
# <a name="learn-the-various-ways-to-debug-an-azure-cloud-service"></a>Různé způsoby ladění cloudové služby Azure
Tento článek obsahuje odkazy na různé způsoby ladění cloudové služby Azure.

## <a name="debugging-an-azure-cloud-service-in-visual-studio"></a>Ladění cloudové služby Azure v aplikaci Visual Studio
Můžete ušetřit čas a peníze pomocí emulátoru služby COMPUTE Azure pro ladění cloudové služby na místním počítači. Laděním služby v místním prostředí před tím, než je nasadíte, můžete zvýšit spolehlivost a výkon bez placení za výpočetní čas. K nějakým chybám ale může dojít jenom při spuštění cloudové služby v Azure. Chyby, ke kterým dochází jenom v případě, že spustíte cloudovou službu v Azure, můžete ladit povolením vzdáleného ladění při publikování služby a následným připojením ladicího programu k instanci role. Další informace najdete v tématu [ladění cloudové služby na místním počítači](vs-azure-tools-debug-cloud-services-virtual-machines.md#debug-your-cloud-service-on-your-local-computer).

## <a name="using-intellitrace"></a>Používání IntelliTrace
Pokud používáte Visual Studio Enterprise k psaní rolí cílených .NET Framework 4,5, můžete povolit IntelliTrace v době, kdy nasazujete cloudovou službu Azure ze sady Visual Studio. IntelliTrace poskytuje protokol, který můžete použít se sadou Visual Studio k ladění aplikace, jako kdyby byla spuštěná v Azure. Další informace najdete v tématu [Ladění publikované cloudové služby pomocí IntelliTrace a sady Visual Studio](vs-azure-tools-intellitrace-debug-published-cloud-services.md).

## <a name="remote-debugging"></a>Vzdálené ladění
V době, kdy nasazujete cloudovou službu ze sady Visual Studio, můžete povolit vzdálené ladění v cloudových službách. Pokud se rozhodnete povolit vzdálené ladění pro nasazení, služby vzdálené ladění se nainstalují na virtuální počítače, které spouštějí jednotlivé instance role. Tyto služby – například `msvsmon.exe` – nemají vliv na výkon nebo způsobují vyšší náklady. Další informace najdete v tématu [ladění cloudové služby v Azure](vs-azure-tools-debug-cloud-services-virtual-machines.md#debug-a-cloud-service-in-azure).

## <a name="next-steps"></a>Další kroky
- [Ladění cloudové služby nebo virtuálního počítače Azure v aplikaci Visual Studio](./vs-azure-tools-debug-cloud-services-virtual-machines.md) – Přečtěte si podrobnosti o tom, jak ladit Azure Cloud Services.
