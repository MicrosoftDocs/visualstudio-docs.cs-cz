---
title: 'CA1025: Nahraďte opakované argumenty polem parametrů | Dokumentace Microsoftu'
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
- CA1025
- ReplaceRepetitiveArgumentsWithParamsArray
helpviewer_keywords:
- ReplaceRepetitiveArgumentsWithParamsArray
- CA1025
ms.assetid: f009b340-dea3-4459-8fe1-2143aa8b5d0b
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b649a5eaa26365fcf7b620ae10db037269716b08
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49912809"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025: Nahraďte opakované argumenty polem parametrů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|
|CheckId|CA1025|
|Kategorie|Microsoft.Design|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina
 Veřejná nebo chráněná metoda veřejného typu má více než tři parametry a její poslední tři parametry jsou stejného typu.

## <a name="rule-description"></a>Popis pravidla
 Pole parametrů. použijte namísto opakovaných argumentů, pokud není znám přesný počet argumentů a proměnné argumenty jsou stejného typu, nebo mohou být předány jako stejného typu. Například <xref:System.Console.WriteLine%2A> metoda poskytuje pro obecné účely přetížení, která používá pole parametrů tak, aby přijímal libovolný počet <xref:System.Object> argumenty.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, nahraďte opakované argumenty polem parametrů.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je vždy bezpečné potlačit upozornění tohoto pravidla; Tento návrh však může způsobit problémy použitelnost.

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ, který porušuje tato pravidla.

 [!code-csharp[FxCop.Design.RepeatArgs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RepeatArgs/cs/FxCop.Design.RepeatArgs.cs#1)]



