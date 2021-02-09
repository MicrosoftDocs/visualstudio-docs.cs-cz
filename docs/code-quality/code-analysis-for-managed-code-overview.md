---
title: Analýza kódu pro spravovaný kód
ms.date: 08/27/2020
description: Přečtěte si informace o analyzátorech kódu založených na .NET Compiler Platform v aplikaci Visual Studio. Zjistěte, proč tyto analyzátory nahrazují FxCop statickou analýzu spravovaných sestavení.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 542747f650888b384a9f9c4910b0d9caea93e948
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860565"
---
# <a name="overview-of-code-analysis-for-net-in-visual-studio"></a>Přehled analýzy kódu pro .NET v aplikaci Visual Studio

Visual Studio může analyzovat kód spravovaného kódu dvěma způsoby: pomocí [starší verze analýzy](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), označované také jako FxCop statická analýza spravovaných sestavení a s pokročilejšími [analyzátory kódu založeného na .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md). Analyzátory kódu založené na .NET Compiler Platform, které analyzují kód živě při psaní, nahradí starší analýzu statického kódu FxCop, která analyzuje jenom zkompilovaný kód.
