---
title: 'CA1009: deklarujte správně obslužné rutiny událostí | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1009
- DeclareEventHandlersCorrectly
helpviewer_keywords:
- CA1009
- DeclareEventHandlersCorrectly
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6a4a4e2e6990772b50568043c4d18ff29248571d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547885"
---
# <a name="ca1009-declare-event-handlers-correctly"></a>CA1009: Deklarujte správně obslužné rutiny událostí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|DeclareEventHandlersCorrectly|
|CheckId|CA1009|
|Kategorie|Microsoft. Design|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Delegát, který zpracovává veřejnou nebo chráněnou událost, nemá správný podpis, návratový typ nebo názvy parametrů.

## <a name="rule-description"></a>Popis pravidla
 Metody zpracování událostí přebírají dva parametry. První je typu <xref:System.Object?displayProperty=fullName> a má název Sender. Je jím objekt, který vyvolal událost. Druhý parametr je typu <xref:System.EventArgs?displayProperty=fullName> a má název "e". Představuje data přidružená k události. Například pokud je událost vyvolána při každém otevření souboru, data události obvykle obsahují název souboru.

 Metody obslužné rutiny událostí by neměly vracet hodnotu. V programovacím jazyce C# je to označeno návratovým typem `void` . Obslužná rutina události může vyvolat více metod ve více objektech. Pokud metody mohly vracet hodnotu, pro každou událost by se měly vyskytovat více návratových hodnot a k dispozici je jenom hodnota posledního vyvolané metody.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, opravte podpis, návratový typ nebo názvy parametrů delegáta. Podrobnosti najdete v následujícím příkladu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Následující příklad ukazuje delegáta, který je vhodný pro zpracování událostí. Metody, které mohou být vyvolány touto obslužnou rutinou události, jsou v rozporu s signaturou, která je uvedena v pokynech pro návrh. `AlarmEventHandler`je název typu delegáta. `AlarmEventArgs`je odvozen ze základní třídy pro data události <xref:System.EventArgs> a obsahuje data události alarmu.

 [!code-cpp[FxCop.Design.EventsTwoParams#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/cpp/FxCop.Design.EventsTwoParams.cpp#1)]
 [!code-csharp[FxCop.Design.EventsTwoParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/cs/FxCop.Design.EventsTwoParams.cs#1)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/vb/FxCop.Design.EventsTwoParams.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA2109: Zkontrolujte viditelné obslužné rutiny událostí](../code-quality/ca2109-review-visible-event-handlers.md)

## <a name="see-also"></a>Viz také
 <xref:System.EventArgs?displayProperty=fullName> <xref:System.Object?displayProperty=fullName>
 [NIB: události a Delegáti](https://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115)
