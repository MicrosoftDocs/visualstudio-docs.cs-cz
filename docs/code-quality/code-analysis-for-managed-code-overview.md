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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89091395"
---
# <a name="overview-of-code-analysis-for-net-in-visual-studio"></a>Přehled analýzy kódu pro .NET v aplikaci Visual Studio

Visual Studio může analyzovat kód spravovaného kódu dvěma způsoby: pomocí [starší verze analýzy](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), označované také jako FxCop statická analýza spravovaných sestavení a s pokročilejšími [analyzátory kódu založeného na .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md). Analyzátory kódu založené na .NET Compiler Platform, které analyzují kód živě při psaní, nahradí starší analýzu statického kódu FxCop, která analyzuje jenom zkompilovaný kód.
