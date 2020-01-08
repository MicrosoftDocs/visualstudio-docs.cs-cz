---
title: Cílit na předchozí verze .NET Framework proF#
description: Přečtěte si o cílení na starší verzi .NET Framework F# při použití v aplikaci Visual Studio.
ms.date: 07/11/2018
ms.topic: troubleshooting
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
monikerRange: vs-2017
ms.openlocfilehash: 4b5cf62dadc38802e477c7588416b4003304e852
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75584579"
---
# <a name="target-older-versions-of-net-f"></a>Cílové starší verze rozhraní .NET (F#)

Následující chyba se může zobrazit, pokud se pokusíte cílit na .NET Framework 2,0, 3,0 nebo 3,5 v F# projektu při instalaci sady Visual Studio v Windows 8.1:

**Tento projekt vyžaduje modul runtime F# 2,0, ale tento modul runtime není nainstalován.**

Tato chyba se objevuje při následující kombinaci podmínek:

- Nainstalovali jste aplikaci Visual Studio na Windows 8.1.

- Před instalací sady Visual Studio jste nepovolili .NET Framework 3,5.

- Projekt cílí na .NET Framework 2,0, 3,0 nebo 3,5.

Při instalaci sady Visual Studio se zjistí nainstalované verze .NET Framework. Visual Studio nainstaluje modul F# runtime 2,0 pouze v případě, že je nainstalovaná a povolená .NET Framework 3,5.

## <a name="resolve-the-error"></a>Vyřešit chybu

Chcete-li tuto chybu vyřešit, můžete:

- Zacílení na novější verzi .NET Framework.

- Povolte .NET Framework 3,5 na Windows 8.1 a pak nainstalujte modul runtime F# 2,0 pomocí opravy instalace sady Visual Studio. Postup je následující:

### <a name="to-enable-the-net-framework-35-on-windows-81"></a>Povolení .NET Framework 3,5 na Windows 8.1

1. Na **úvodní** obrazovce zadejte **Ovládací panely**.

   Při psaní se v záhlaví **aplikace** zobrazí ikona **Ovládací panely** .

2. Zvolte ikonu **Ovládací panely** , zvolte ikonu **programy** a pak zvolte odkaz **zapnout nebo vypnout funkce systému Windows** .

3. Ujistěte se, že je zaškrtnuté políčko **.NET Framework 3,5 (zahrnuje rozhraní .net 2,0 a 3,0)** , a pak klikněte na tlačítko **OK** . Pro volitelné součásti .NET Framework nemusíte zaškrtnout políčka u všech podřízených uzlů.

   .NET Framework 3,5 je povoleno, pokud ještě neexistovala.

### <a name="to-install-the-f-20-runtime"></a>Instalace modulu runtime F# 2,0

Proveďte [opravu sady Visual Studio podle pokynů](../install/repair-visual-studio.md).

## <a name="see-also"></a>Viz také:

- [F#Průvodce (.NET Framework)](/dotnet/fsharp/)
- [F#v aplikaci Visual Studio](fsharp-visual-studio.md)
