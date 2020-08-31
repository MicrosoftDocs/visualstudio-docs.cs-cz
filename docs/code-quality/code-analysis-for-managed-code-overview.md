---
title: Analýza kódu pro spravovaný kód
ms.date: 08/27/2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d13a8afdfcbeb6ae9f91e39779af8b82b2461000
ms.sourcegitcommit: 016bcdc7cd3e3619457beb321800e98544efb6c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2020
ms.locfileid: "89091395"
---
# <a name="overview-of-code-analysis-for-net-in-visual-studio"></a>Přehled analýzy kódu pro .NET v aplikaci Visual Studio

Visual Studio může analyzovat kód spravovaného kódu dvěma způsoby: pomocí [starší verze analýzy](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), označované také jako FxCop statická analýza spravovaných sestavení a s pokročilejšími [analyzátory kódu založeného na .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md). Analyzátory kódu založené na .NET Compiler Platform, které analyzují kód živě při psaní, nahradí starší analýzu statického kódu FxCop, která analyzuje jenom zkompilovaný kód.
