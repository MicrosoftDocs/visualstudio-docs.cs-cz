---
title: 'Cílová předchozí verze rozhraní .NET Framework pro F #'
description: Další informace o cílení starší verze rozhraní .NET Framework při použití F# v sadě Visual Studio.
ms.date: 07/11/2018
ms.topic: troubleshooting
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
monikerRange: vs-2017
ms.openlocfilehash: 4b5cf62dadc38802e477c7588416b4003304e852
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75584579"
---
# <a name="target-older-versions-of-net-f"></a>Cílení na starší verze rozhraní .NET (F#)

Následující chyba se může zobrazit, pokud se pokusíte cílit na rozhraní .NET Framework 2.0, 3.0 nebo 3.5 v projektu F# při instalaci sady Visual Studio v systému Windows 8.1:

**Tento projekt vyžaduje za běhu 2.0 F#, ale tento runtime není nainstalován.**

Je známo, že k této chybě dochází za následující kombinace podmínek:

- Visual Studio jste nainstalovali ve Windows 8.1.

- Před instalací sady Visual Studio jste nepovolili rozhraní .NET Framework 3.5.

- Projekt cílí na rozhraní .NET Framework 2.0, 3.0 nebo 3.5.

Při instalaci sady Visual Studio zjistí nainstalované verze rozhraní .NET Framework. Visual Studio nainstaluje za běhu F# 2.0 pouze v případě, že je nainstalována a povolena rozhraní .NET Framework 3.5.

## <a name="resolve-the-error"></a>Vyřešit chybu

Chcete-li tuto chybu vyřešit, můžete buď:

- Zacilte na novější verzi rozhraní .NET Framework.

- Povolte rozhraní .NET Framework 3.5 ve Windows 8.1 a nainstalujte zaběhu F# 2.0 opravou instalace sady Visual Studio. Kroky k tomu postupujte.

### <a name="to-enable-the-net-framework-35-on-windows-81"></a>Povolení rozhraní .NET Framework 3.5 ve Windows 8.1

1. Na **úvodní** obrazovce zadejte **Příkaz Ovládací panely**.

   Při psaní se pod nadpisem **Aplikace** zobrazí ikona **Ovládací panely.**

2. Zvolte ikonu **Ovládací panely,** zvolte ikonu **Programy** a pak zvolte odkaz **Zapnout nebo vypnout funkce systému Windows.**

3. Ujistěte se, že je zaškrtnuté políčko **.NET Framework 3.5 (včetně .NET 2.0 a 3.0)** a pak zvolte tlačítko **OK.** Není nutné zaškrtnout políčka pro všechny podřízené uzly pro volitelné součásti rozhraní .NET Framework.

   Rozhraní .NET Framework 3.5 je povoleno, pokud již nebylo.

### <a name="to-install-the-f-20-runtime"></a>Instalace za běhu F# 2.0

Postupujte [podle pokynů k opravě sady Visual Studio](../install/repair-visual-studio.md).

## <a name="see-also"></a>Viz také

- [Příručka F# (rozhraní.NET Framework)](/dotnet/fsharp/)
- [F# v sadě Visual Studio](fsharp-visual-studio.md)
