---
title: Sledování souborů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9335ca6608d36edbd17e47a441e13aecaa41c890
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634198"
---
# <a name="file-tracking"></a>Sledování souborů

Protokoly sledování souborů volají do systému souborů systému Windows pro proces a jeho podřízené procesy. Voláním níže uvedených funkcí určují programy, kdy má být toto přihlašování zapínat a vypínat, a zadávat soubor protokolu, který má být používán.

- [EndTrackingContext](../msbuild/endtrackingcontext.md) Zastavit sledování aktuálního kontextu.

- [Pokračovatv sledování](../msbuild/resumetracking.md) Pokračovat sledování po volání [SuspendTracking](../msbuild/suspendtracking.md).

- [SetThreadCount](../msbuild/setthreadcount.md) Nastavte počet podprocesů, které mají být používány pro sledování.

- [StartTrackingContext](../msbuild/starttrackingcontext.md) Začněte nový kontext sledování.

- [StartTrackingContextWithroot](../msbuild/starttrackingcontextwithroot.md) Začněte nový kontext sledování se zadaným kořenem.

- [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md) Ukončite použité prostředky sledování a uvolnění.

- [Pozastavit](../msbuild/suspendtracking.md) Dočasně pozastavit sledování.

- [ZápisAllTLogs](../msbuild/writealltlogs.md) Zapište protokoly sledování pro všechny kontexty.

- [ZápisContextTLogs](../msbuild/writecontexttlogs.md) Zapište protokol sledování pro aktuální kontext.
