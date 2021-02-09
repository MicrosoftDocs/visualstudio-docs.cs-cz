---
title: Sledování souborů | Microsoft Docs
description: Funkce sledování souborů nástroje MSBuild slouží k protokolování volání do systému souborů systému Windows pro proces a jeho podřízené procesy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d61c3478515f2c8fa867666e6ff4ff72a0d4e65b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877119"
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
