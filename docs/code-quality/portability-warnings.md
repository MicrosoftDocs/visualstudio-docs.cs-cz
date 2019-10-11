---
title: Upozornění přenositelnosti
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.PortabilityRules
helpviewer_keywords:
- portability warnings
- managed code analysis warnings, portability warnings
- warnings, portability
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 072858a9faafe312fd7c8314e7f25cf581c40844
ms.sourcegitcommit: e95dd8cedcd180e0bce6a75c86cf861757918290
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2019
ms.locfileid: "72163075"
---
# <a name="portability-warnings"></a>Upozornění přenositelnosti
Upozornění na přenositelnost podporují přenositelnost napříč různými operačními systémy.

## <a name="in-this-section"></a>V tomto oddílu

|Pravidlo|Popis|
|----------|-----------------|
|[CA1900: Pole hodnot typu by měla být Portable @ no__t-0|Toto pravidlo kontroluje, zda struktury, které jsou deklarovány pomocí explicitního atributu layout, budou správně zarovnány v případě, že jsou zařazeny do nespravovaného kódu v 64 operačních systémech.|
|[CA1901: Deklarace P/Invoke by měly být přenosné @ no__t-0|Toto pravidlo vyhodnocuje velikost každého parametru a návratovou hodnotu volání nespravovaného kódu a ověřuje, zda je jejich velikost správná, pokud je zařazena do nespravovaného kódu na 32 a 64 bitových operačních systémů.|
|[CA1903: Použít pouze rozhraní API z cílového rozhraní .NET no__t-0|Člen nebo typ používá člen nebo typ, který byl uveden v aktualizaci Service Pack, která nebyla zahrnuta stejně jako cílové rozhraní projektu.|
