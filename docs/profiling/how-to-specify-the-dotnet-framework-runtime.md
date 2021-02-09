---
title: Zadat modul runtime .NET Framework | Microsoft Docs
description: Zjistěte, jak mohou být aplikace tvořeny moduly, které byly vytvořeny pomocí různých verzí .NET Framework modulu runtime.
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Profiling Tools, .NET Framework versions
- .NET Framework versions,profililng
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: da2a19b702e29589a71e84776fbff939dc468914
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918807"
---
# <a name="how-to-specify-the-net-framework-runtime"></a>Postupy: Určení modulu runtime .NET Framework

S vydáním .NET Framework 4 mohou být aplikace tvořeny moduly, které byly vytvořeny pomocí různých verzí .NET Framework modulu runtime. Ve výchozím nastavení Visual Studio Nástroje pro profilaci Profilovat první modul runtime, který je načten aplikací. Můžete určit, že při spuštění aplikace s profilerem a při připojení profileru k již spuštěné aplikaci budete profilovat.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>Určení .NET Framework při spouštění aplikace pomocí profileru profilace modulu runtime

1. V **prohlížeč výkonu** klikněte pravým tlačítkem na relaci výkonu, klikněte na **vlastnosti** a pak klikněte na **Upřesnit**.

     Seznam **cílová verze CLR** zobrazuje **automaticky** a verze .NET Framework runtime, které jsou nainstalovány v počítači.

2. Proveďte jeden z následujících kroků:

    - Klikněte na verzi modulu CLR, kterou chcete profilovat.

    - Klikněte na tlačítko **automaticky** a profilujte první verzi, která je načtena aplikací.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>Určení profilu modulu runtime .NET Framework k profilování při připojení profileru k aplikaci

1. V nabídce **analyzovat** přejděte na **Profiler** a pak klikněte na **připojit nebo odpojit**.

2. V dialogovém okně **Připojit profiler k procesu** klikněte na proces, který chcete profilovat.

     Seznam **cílových verzí modulu CLR** s **automatickým** a verze .NET Framework runtime, které jsou nainstalovány v počítači.

3. Proveďte jeden z následujících kroků:

    - Klikněte na verzi modulu CLR, kterou chcete profilovat.

    - Kliknutím na **automaticky** můžete profilovat verzi, která se načte, když se Profiler připojí k aplikaci.
