---
title: 'Postup: Určení běhu rozhraní .NET Framework | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, .NET Framework versions
- .NET Framework versions,profililng
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 4ab53a6cf265b36ee423a2df176014187860f635
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778671"
---
# <a name="how-to-specify-the-net-framework-runtime"></a>Postupy: Určení modulu runtime .NET Framework

S vydáním rozhraní .NET Framework 4 mohou být aplikace složeny z modulů, které byly vytvořeny pomocí různých verzí modulu run-time rozhraní .NET Framework. Ve výchozím nastavení nástroje profilování sady Visual Studio profilují první runtime načtený aplikací. Můžete určit run-time do profilu při spuštění aplikace s profiler a při připojení profiler k již spuštěné aplikace.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>Určení běhu rozhraní .NET Framework do profilu při spuštění aplikace pomocí profileru

1. V **Průzkumníku výkonu**klepněte pravým tlačítkem myši na relaci výkonu, klepněte na příkaz **Vlastnosti**a potom klepněte na příkaz **Upřesnit**.

     V seznamu **Cílová verze CLR** se zobrazují **automatické** a verze runtime rozhraní .NET Framework, které jsou nainstalovány v počítači.

2. Proveďte jeden z následujících kroků:

    - Klikněte na verzi clr, kterou chcete profilovat.

    - Chcete-li profilovat první verzi načtenou aplikací, klepněte na **tlačítko Automaticky.**

## <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>Určení běhu rozhraní .NET Framework k profilu při připojování profileru k aplikaci

1. V nabídce **Analyzovat** přejděte na **položku Profiler**a klepněte na tlačítko **Připojit nebo odpojit**.

2. V dialogovém okně **Připojit profiler ke zpracování** klikněte na proces, který chcete profilovat.

     **Seznam Cílové verze CLR** s **Automatické** a verze runtime rozhraní .NET Framework, které jsou nainstalovány v počítači.

3. Proveďte jeden z následujících kroků:

    - Klikněte na verzi clr, kterou chcete profilovat.

    - Chcete-li profilovat verzi načtenou při připojení profileru k aplikaci, klepněte na **tlačítko Automaticky.**
