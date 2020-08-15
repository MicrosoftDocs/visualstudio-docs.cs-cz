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
ms.openlocfilehash: 901c66a97a763345ee32b1a1540a7998934d0ff3
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2020
ms.locfileid: "88248981"
---
# <a name="overview-of-code-analysis-for-managed-code-in-visual-studio"></a>Přehled analýzy kódu pro spravovaný kód v aplikaci Visual Studio

Visual Studio může analyzovat kód spravovaného kódu dvěma způsoby: pomocí [starší verze analýzy](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), označované také jako FxCop statická analýza spravovaných sestavení a s pokročilejšími [analyzátory kódu založeného na .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md). Analyzátory kódu založené na .NET Compiler Platform, které analyzují kód živě při psaní, nahradí starší analýzu statického kódu FxCop, která analyzuje jenom zkompilovaný kód.
