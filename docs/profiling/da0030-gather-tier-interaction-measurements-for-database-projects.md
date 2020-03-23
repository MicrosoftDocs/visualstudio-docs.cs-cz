---
title: 'DA0030: Shromážděte měření interakce vrstev pro databázové projekty | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0030
- vs.performance.rules.DA0030
- vs.performance.30
ms.assetid: 42b2f69d-0cfa-4854-82c4-589c3d8b4557
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 26b0905882ef8ec2e3fcddc4cf699ecae7dbe7a4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777473"
---
# <a name="da0030-gather-tier-interaction-measurements-for-database-projects"></a>DA0030: Shromážděte měření interakce vrstev pro databázové projekty

|||
|-|-|
|Id pravidla|DA0030|
|Kategorie|Využití nástrojů profilování|
|Metoda profilování|Vzorkování|
|Zpráva|Shromažďování měření interakcí pro vícevrstvé aplikace vám pomůže pochopit vzorce využití databáze a zpoždění přístupu ke klíčovým datům. Zkuste aplikaci profilovat znovu s povolenou možností profilování interakce vrstvy.|
|Typ pravidla|Informace|

## <a name="cause"></a>Příčina
 Volání <xref:System.Data> metod jsou významnou částí dat profilování a v průběhu profilování jste neshromáždili data interakce vrstvy. Zvažte profilování znovu a přidání dat interakce vrstvy.

## <a name="rule-description"></a>Popis pravidla
 Toto pravidlo je aktivována vždy, když je významná aktivita <xref:System.Data.Linq> <xref:System.Data.Linq>ve funkcích, které jsou umístěny v System.Data obory názvů, včetně .

 Vícevrstvé aplikace používají vrstvené služby pro své prezentační a datové vrstvy. Často je datová vrstva samostatný proces se systémem pro správu databáze, jako je microsoft SQL Server. Datová vrstva může být dokonce spuštěna na samostatném počítači od zbytku aplikace. Vzorkovací profily poskytují malý přehled o funkcích a službách, které jsou mimo proces nebo vzdáleně.

 Nástroje profilování mohou shromažďovat informace o časování pro vícevrstvé aplikace, které interagují s datovou vrstvou serveru Microsoft SQL Server pomocí asynchronních volání ADO.NET služeb. Je nutné explicitně povolit profilování interakce vrstvy. Ve výchozím nastavení není zapnuta.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
 Toto pravidlo je pouze pro informaci a nemusí vyžadovat nápravná opatření.

 Informace o tom, jak přidat data interakce vrstvy do profilování dat z ide Sady Visual Studio, naleznete v [tématu Shromažďování dat interakce vrstvy](../profiling/collecting-tier-interaction-data.md). Informace o tom, jak přidat data interakce vrstvy z příkazového řádku, naleznete v [tématu Shromažďování dat interakce vrstvy](../profiling/adding-tier-interaction-data-from-the-command-line.md).
