---
title: Sledování souborů | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77634198"
---
# <a name="file-tracking"></a>Sledování souborů

Protokol sledování souborů volá do systému souborů systému Windows pro proces a jeho podřízené procesy. Voláním níže uvedených funkcí programy řídí, kdy zapnout a vypnout protokolování a zadat soubor protokolu, který se má použít.

- [EndTrackingContext](../msbuild/endtrackingcontext.md) Zastavit sledování aktuálního kontextu.

- [ResumeTracking](../msbuild/resumetracking.md) Obnoví sledování po volání [SuspendTracking](../msbuild/suspendtracking.md).

- [SetThreadCount](../msbuild/setthreadcount.md) Nastavte počet vláken, která se mají použít pro sledování.

- [StartTrackingContext](../msbuild/starttrackingcontext.md) Zahajte nový kontext sledování.

- [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md) Zahajte nový kontext sledování se zadaným kořenem.

- [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md) Ukončit sledování a uvolnit použité prostředky.

- [SuspendTracking](../msbuild/suspendtracking.md) Dočasné pozastavení sledování.

- [WriteAllTLogs](../msbuild/writealltlogs.md) Zapište protokoly sledování pro všechny kontexty.

- [WriteContextTLogs](../msbuild/writecontexttlogs.md) Vypište protokol sledování pro aktuální kontext.
