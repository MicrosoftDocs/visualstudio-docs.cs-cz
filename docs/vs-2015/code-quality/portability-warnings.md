---
title: Upozornění přenositelnosti | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codeanalysis.PortabilityRules
helpviewer_keywords:
- portability warnings
- managed code analysis warnings, portability warnings
- warnings, portability
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3b7c38f8380fc8e52707b9c4817880b1ce86b4b9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49173074"
---
# <a name="portability-warnings"></a>Upozornění přenositelnosti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Upozornění přenositelnosti podporují přenositelnost napříč různými operačními systémy.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
|Pravidlo|Popis|  
|----------|-----------------|  
|[CA1900: Pole hodnot by měla být přenosná](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Toto pravidlo zkontroluje, že budou při zařazení na nespravovaný kód v 64bitových operačních systémech správně zarovnány struktury, které jsou deklarovány pomocí explicitního rozložení atribut.|  
|[CA1901: Deklarace volání nespravovaného kódu by měly být přenosné](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Toto pravidlo vyhodnotí velikost každého parametru a vrácené hodnoty deklarace P/Invoke a ověří, jestli je správná při zařazení na nespravovaný kód v 32bitové a 64bitové operační systémy jejich velikost.|  
|[CA1903: Použijte pouze API z cílového rozhraní .NET Framework](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Člen nebo typ používá člen nebo typ, který byl uveden v aktualizaci Service Pack, která nebyla zahrnuta stejně jako cílové rozhraní projektu.|



