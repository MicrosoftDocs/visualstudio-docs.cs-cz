---
title: 'CA2139: transparentní metody nemůžou používat atribut HandleProcessCorruptingExceptions | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2139
ms.assetid: 45a0328a-add7-40f9-8934-dff59beb02b3
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 233e4366befd2a5a0d5690b14198ac13e2fcc957
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546481"
---
# <a name="ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute"></a>CA2139: Transparentní metody nemusí používat atribut HandleProcessCorruptingExceptions
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|TransparentMethodsMustNotHandleProcessCorruptingExceptions|
|CheckId|CA2139|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Transparentní metoda je označena <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> atributem.

## <a name="rule-description"></a>Popis pravidla
 Toto pravidlo aktivuje jakoukoliv metodu, která je transparentní a pokusí se zpracovat výjimku, která je poškozená, pomocí <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> atributu. Výjimka poškození procesu je klasifikace výjimek verze 4,0, jako je například výjimka třídy CLR <xref:System.AccessViolationException> . Atribut HandleProcessCorruptedStateExceptionsAttribute lze použít pouze metodami kritickými pro bezpečnost a bude ignorován, je-li použit u transparentních metod. Aby bylo možné zpracovat výjimky poškozené procesem, tato metoda musí být kritická nebo zabezpečená zabezpečení.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, odeberte <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> atribut nebo označte metodu <xref:System.Security.SecurityCriticalAttribute> <xref:System.Security.SecuritySafeCriticalAttribute> atributem nebo.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 V tomto příkladu je průhledná metoda označena <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> atributem a selže pravidlo. Metoda by měla být také označena <xref:System.Security.SecurityCriticalAttribute> <xref:System.Security.SecuritySafeCriticalAttribute> atributem nebo.

 [!code-csharp[FxCop.Security.CA2139#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2139/cs/ca2139.cs#1)]
