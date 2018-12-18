---
title: 'CA1009: Deklarujte správně obslužné rutiny událostí | Dokumentace Microsoftu'
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
- CA1009
- DeclareEventHandlersCorrectly
helpviewer_keywords:
- CA1009
- DeclareEventHandlersCorrectly
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7a405ebbf4cd11a695c6e93231d260d8ceae2483
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49918503"
---
# <a name="ca1009-declare-event-handlers-correctly"></a>CA1009: Deklarujte správně obslužné rutiny událostí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DeclareEventHandlersCorrectly|
|CheckId|CA1009|
|Kategorie|Microsoft.Design|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Delegát, který zpracovává událost veřejná nebo chráněná nemá správný podpis, návratový typ nebo názvy parametrů.

## <a name="rule-description"></a>Popis pravidla
 Metody zpracování událostí přebírají dva parametry. První je typu <xref:System.Object?displayProperty=fullName> a je pojmenován "sender". Je jím objekt, který vyvolal událost. Druhý parametr je typu <xref:System.EventArgs?displayProperty=fullName> a je pojmenován "e". Představuje data přidružená k události. Například pokud se vyvolá událost pokaždé, když je soubor otevřen, data událostí obvykle obsahuje název souboru.

 Obslužné rutiny události by neměly vracet hodnotu. V jazyce C# programovací jazyk, je toto označeno návratovým typem `void`. Obslužné rutiny události můžete vyvolat několik metod v několika objektů. Pokud metody se může vrátit hodnotu, by tomu bylo více vrácených hodnot pro každou jednotlivou událost a bude k dispozici pouze hodnotu poslední metodu, která byla vyvolána.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, opravte podpis, návratový typ nebo názvy parametrů delegáta. Podrobnosti najdete v tématu v následujícím příkladu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Následující příklad ukazuje delegáta, který je vhodný pro zpracování událostí. Metody, které mohou být vyvolány touto obslužnou rutinou události v souladu s podpisu, který je zadán v pokyny návrhu. `AlarmEventHandler` je název typu delegáta. `AlarmEventArgs` je odvozena ze základní třídy pro data události <xref:System.EventArgs>, a obsahuje budíku data události.

 [!code-cpp[FxCop.Design.EventsTwoParams#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/cpp/FxCop.Design.EventsTwoParams.cpp#1)]
 [!code-csharp[FxCop.Design.EventsTwoParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/cs/FxCop.Design.EventsTwoParams.cs#1)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/vb/FxCop.Design.EventsTwoParams.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA2109: Revize viditelných obslužných rutin událostí](../code-quality/ca2109-review-visible-event-handlers.md)

## <a name="see-also"></a>Viz také
 <xref:System.EventArgs?displayProperty=fullName><xref:System.Object?displayProperty=fullName>
 [NIB: Delegáti a události](http://msdn.microsoft.com/en-us/d98fd58b-fa4f-4598-8378-addf4355a115)



