---
title: Příprava na ladění služeb systému Windows | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], Windows services
- Windows Service applications, debugging
ms.assetid: ac0a99f7-ec3d-4a20-b17f-698a817fdcc2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3161f6d2c328e8e33dd82ed206aa8aa20e654cc9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738078"
---
# <a name="debugging-preparation-windows-services"></a>Příprava ladění: služby systému Windows
Služba systému Windows je program, který běží na pozadí v systému Microsoft Windows. Mezi příklady patří služba Telnet a služba Systémový čas, která aktualizuje zobrazené hodiny vašeho počítače. Služba systému Windows nemůže být spuštěna v rámci [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]; musí běžet v kontextu správce řízení služeb. Další informace naleznete v tématu [vytváření služeb systému Windows](/dotnet/framework/windows-services/how-to-create-windows-services), [ladění aplikací služby systému Windows](/dotnet/framework/windows-services/how-to-debug-windows-service-applications)a [aplikací služby systému Windows](/dotnet/framework/windows-services/index).

## <a name="see-also"></a>Viz také:
- [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)
- [Typy projektů jazyka C#, F# a Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Nastavení projektu pro konfiguraci ladění jazyka C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Nastavení projektu pro konfiguraci ladění jazyka Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Postupy: Ladění metody OnStart](../debugger/how-to-debug-the-onstart-method.md)