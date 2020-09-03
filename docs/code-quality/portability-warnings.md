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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f48cef7ffaf08fc26566fdd04bee15a3e3e1b85f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "78167570"
---
# <a name="portability-warnings"></a>Upozornění přenositelnosti
Upozornění na přenositelnost podporují přenositelnost napříč různými operačními systémy.

## <a name="in-this-section"></a>V tomto oddílu

|Pravidlo|Popis|
|----------|-----------------|
|[CA1900: Pole typů hodnot by měla být přenosná](../code-quality/ca1900.md)|Toto pravidlo kontroluje, zda struktury, které jsou deklarovány pomocí explicitního atributu layout, budou správně zarovnány v případě, že jsou zařazeny do nespravovaného kódu v 64 operačních systémech.|
|[CA1901: deklarace P/Invoke by měly být přenosné](../code-quality/ca1901.md)|Toto pravidlo vyhodnocuje velikost každého parametru a návratovou hodnotu volání nespravovaného kódu a ověřuje, zda je jejich velikost správná, pokud je zařazena do nespravovaného kódu na 32 a 64 bitových operačních systémů.|
|[CA1903: Používejte jen rozhraní API z cílové architektury](../code-quality/ca1903.md)|Člen nebo typ používá člen nebo typ, který byl uveden v aktualizaci Service Pack, která nebyla zahrnuta stejně jako cílové rozhraní projektu.|
