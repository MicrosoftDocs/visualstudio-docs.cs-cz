---
title: Analýza kódu pro spravovaný kód
ms.date: 06/12/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e6515c0df7a9c3389e754d5238788d716be49e2e
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88800083"
---
# <a name="overview-of-code-analysis-for-managed-code-in-visual-studio"></a>Přehled analýzy kódu pro spravovaný kód v aplikaci Visual Studio

Visual Studio může provádět analýzu kódu spravovaného kódu dvěma způsoby:
- Se [staršími verzemi analýzy](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), označované také jako FxCop static Analysis pro spravovaná sestavení.
- S pokročilejšími [analyzátory kódu založenými na .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md). Analyzátory kódu založené na .NET Compiler Platform, které analyzují kód živě při psaní, nahradí starší analýzu statického kódu FxCop, která analyzuje jenom zkompilovaný kód.