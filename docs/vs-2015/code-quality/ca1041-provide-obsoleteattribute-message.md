---
title: 'CA1041: zadejte zprávu ObsoleteAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d738cf15ebe734cb74e553f38f6eb26af17e8cfd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542308"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041: Poskytněte zprávu ObsoleteAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|ProvideObsoleteAttributeMessage|
|CheckId|CA1041|
|Kategorie|Microsoft. Design|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Typ nebo člen je označen pomocí <xref:System.ObsoleteAttribute?displayProperty=fullName> atributu, který nemá <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> zadanou vlastnost.

## <a name="rule-description"></a>Popis pravidla
 <xref:System.ObsoleteAttribute> slouží k označení zastaralých typů a členů knihovny. Příjemci knihovny by se měli vyhnout použití libovolného typu nebo člena, který je označený jako zastaralý. Důvodem je to, že nemusí být podporován a nakonec bude odebrán z novějších verzí knihovny. Je-li typ nebo člen označený pomocí <xref:System.ObsoleteAttribute> je zkompilován, je <xref:System.ObsoleteAttribute.Message%2A> zobrazena vlastnost atributu. To uživateli poskytuje informace o zastaralém typu nebo členu. Tyto informace obecně zahrnují, jak dlouho bude zastaralý typ nebo člen podporovaný Návrháři knihovny a upřednostňovanou náhradou, která se má použít.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, přidejte `message` parametr do <xref:System.ObsoleteAttribute> konstruktoru.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačí upozornění z tohoto pravidla, protože <xref:System.ObsoleteAttribute.Message%2A> vlastnost poskytuje kritické informace o zastaralém typu nebo členu.

## <a name="example"></a>Příklad
 Následující příklad ukazuje zastaralý člen, který má správně deklarovaný <xref:System.ObsoleteAttribute> .

 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cpp/FxCop.Design.ObsoleteAttributeOnMember.cpp#1)]
 [!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cs/FxCop.Design.ObsoleteAttributeOnMember.cs#1)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/vb/FxCop.Design.ObsoleteAttributeOnMember.vb#1)]

## <a name="see-also"></a>Viz také
 <xref:System.ObsoleteAttribute?displayProperty=fullName>
