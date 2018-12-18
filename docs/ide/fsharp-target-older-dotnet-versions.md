---
title: 'Cílí na předchozí verze rozhraní .NET Framework pro F #.'
description: 'Přečtěte si o cílení na starší verzi rozhraní .NET Framework při používání jazyka F # v sadě Visual Studio.'
ms.date: 07/11/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: troubleshooting
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 2cb32f37bde0a55da081105cbee52a8744db2b88
ms.sourcegitcommit: e5a382de633156b85b292f35e3d740f817715d47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/12/2018
ms.locfileid: "38978503"
---
# <a name="target-older-versions-of-net-f"></a>Starší verze cílového rozhraní .NET (F #)

Může objevit následující chyba, pokud se pokusíte cílit na rozhraní .NET Framework 2.0, 3.0 nebo 3.5 v jazyka F # projektu při instalaci sady Visual Studio na Windows 8.1:

**Tento projekt vyžaduje 2.0 runtime F #, ale tento modul runtime není nainstalována.**

Tato chyba se ví, že dojde k pod následující kombinace podmínek:

- Instalaci sady Visual Studio na Windows 8.1.

- Před instalací sady Visual Studio jste nepovolili rozhraní .NET Framework 3.5.

- Váš projekt cílí na .NET Framework 2.0, 3.0 nebo 3.5.

Při instalaci sady Visual Studio zjistí nainstalovaných verzí rozhraní .NET Framework. Visual Studio nainstaluje modul runtime F # 2.0 pouze v případě, že je nainstalované a povolené rozhraní .NET Framework 3.5.

## <a name="resolve-the-error"></a>Pokud chcete chybu vyřešit

Chcete-li vyřešit tuto chybu, můžete buď:

- Cílení na novější verzi rozhraní .NET Framework.

- Povolení rozhraní .NET Framework 3.5 ve Windows 8.1 a pak nainstalujte modul runtime F # 2.0 tak, že opravíte instalaci sady Visual Studio. Postupujte podle kroků provedete to tak.

### <a name="to-enable-the-net-framework-35-on-windows-81"></a>Chcete-li povolit rozhraní .NET Framework 3.5 ve Windows 8.1

1. Na **Start** zadejte **ovládací panely**.

   Při psaní **ovládací panely** ikona se zobrazuje v části **aplikace** záhlaví.

2. Zvolte **ovládací panely** ikonu, zvolte **programy** ikony a klikněte na tlačítko **Windows zapnout nebo vypnout funkce** odkaz.

3. Ujistěte se, že **rozhraní .NET Framework 3.5 (zahrnuje .NET 2.0 a 3.0)** zaškrtávací políčko zaškrtnuto a klikněte na tlačítko **OK** tlačítko. Není nutné zaškrtněte políčka pro všechny podřízené uzly pro volitelné součásti rozhraní .NET Framework.

   Rozhraní .NET Framework 3.5 je povolená, pokud ho ještě nebyl.

### <a name="to-install-the-f-20-runtime"></a>Chcete-li nainstalovat modul runtime F # 2.0

Postupujte podle [kroky pro opravu sady Visual Studio 2017](../install/repair-visual-studio.md).

## <a name="see-also"></a>Viz také:

- [Průvodce jazykem F # (.NET Framework)](/dotnet/fsharp/)
- [F # v sadě Visual Studio](fsharp-visual-studio.md)