---
title: DA0030 – shromáždění měření interakce vrstev pro databázové projekty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 47ac30d4a1df36e72b8b12fa9aefb1b36aed6204
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544596"
---
# <a name="da0030-gather-tier-interaction-measurements-for-database-projects"></a>DA0030: shromáždění měření interakce vrstev pro databázové projekty

|Položka|Hodnota|
|-|-|
|ID pravidla|DA0030|
|Kategorie|Využití Nástroje pro profilaci|
|Metoda profilace|Vzorkování|
|Zpráva|Shromažďování výsledků interakce pro vícevrstvé aplikace vám pomůže pochopit vzorce využití databáze a klíčová zpoždění přístupu k datům. Zkuste aplikaci profilovat znovu s povolenou možností Profilování interakce vrstev.|
|Typ pravidla|Informace|

## <a name="cause"></a>Příčina
 Volání <xref:System.Data> metod jsou významným podílem dat profilace a neshromáždili jste data interakce vrstev při spuštění profilace. Zvažte znovu profilaci a přidejte data interakce vrstev.

## <a name="rule-description"></a>Popis pravidla
 Toto pravidlo je vyvoláno pokaždé, když ve funkcích, které jsou umístěny v oborech názvů System. data, jsou významné aktivity, včetně <xref:System.Data.Linq> <xref:System.Data.Linq> .

 Vícevrstvé aplikace používají vrstvené služby pro svou prezentační a datovou vrstvu. Datová vrstva je často samostatný proces, který spouští systém správy databáze, například Microsoft SQL Server. Datová vrstva může dokonce běžet na samostatném počítači ze zbytku aplikace. Vzorkovací profily poskytují malý přehled o funkcích a službách, které se spouštějí mimo proces nebo vzdáleně.

 Nástroje pro profilaci můžou shromažďovat informace o časování pro vícevrstvé aplikace, které pracují s Microsoft SQL Server datovou vrstvou pomocí asynchronních volání služeb ADO.NET Services. Musíte explicitně povolit profilaci interakce vrstev. Ve výchozím nastavení není zapnutý.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
 Toto pravidlo je pouze pro informace a nemusí vyžadovat nápravné akce.

 Informace o tom, jak přidat data interakce vrstvy k profilaci dat z integrovaného vývojového prostředí (IDE) sady Visual Studio, najdete v tématu [shromáždění dat interakce vrstev](../profiling/collecting-tier-interaction-data.md). Informace o tom, jak přidat data interakce vrstev z příkazového řádku, najdete v tématu [shromáždění dat interakce vrstev](../profiling/adding-tier-interaction-data-from-the-command-line.md).
