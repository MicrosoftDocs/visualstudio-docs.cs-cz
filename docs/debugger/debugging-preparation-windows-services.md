---
title: Příprava na ladění služeb systému Windows | Microsoft Docs
description: Příprava na ladění služeb systému Windows, což jsou programy, které jsou spuštěny na pozadí v systému Windows v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 01448fcd477f5b17b78ad2b142b965f30798746b
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387733"
---
# <a name="debugging-preparation-windows-services"></a>Příprava ladění: služby systému Windows
Služba systému Windows je program, který běží na pozadí v systému Microsoft Windows. Mezi příklady patří služba Telnet a služba Systémový čas, která aktualizuje zobrazené hodiny vašeho počítače. Službu systému Windows nelze spustit z portálu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ; musí být spuštěna v kontextu správce řízení služeb. Další informace naleznete v tématu [vytváření služeb systému Windows](/dotnet/framework/windows-services/how-to-create-windows-services), [ladění aplikací služby systému Windows](/dotnet/framework/windows-services/how-to-debug-windows-service-applications)a [aplikací služby systému Windows](/dotnet/framework/windows-services/index).

## <a name="see-also"></a>Viz také
- [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)
- [Typy projektů jazyka C#, F# a Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Nastavení projektu pro konfiguraci ladění v jazyce C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Nastavení projektu pro konfiguraci Visual Basicho ladění](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Postupy: ladění metody OnStart](../debugger/how-to-debug-the-onstart-method.md)