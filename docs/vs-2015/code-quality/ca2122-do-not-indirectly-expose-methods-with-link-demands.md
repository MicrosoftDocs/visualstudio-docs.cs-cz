---
title: 'CA2122: nezveřejňujte nepřímo metody s požadavky propojení | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2122
- DoNotIndirectlyExposeMethodsWithLinkDemands
helpviewer_keywords:
- DoNotIndirectlyExposeMethodsWithLinkDemands
- CA2122
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 099e5f3f9a09eef57ce1b888601f61e85ceb97c5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72643407"
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122: Nezveřejňujte nepřímo metody s požadavky propojení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|
|CheckId|CA2122|
|Kategorie|Microsoft.Security|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>příčina
 Veřejný nebo chráněný člen má odkaz na [požadavky](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) a je volán členem, který neprovádí žádné kontroly zabezpečení.

## <a name="rule-description"></a>Popis pravidla
 Požadavek propojení kontroluje pouze oprávnění bezprostředního volajícího. Pokud členský `X` neprovede žádné požadavky na zabezpečení svých volajících a volá kód chráněný požadavkem propojení, volající bez nezbytných oprávnění může použít `X` pro přístup k chráněnému členu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Přidejte data zabezpečení [a modelování](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) nebo přidejte požadavek na člena, aby již neposkytoval nezabezpečený přístup k členovi, který je chráněn požadavkem propojení.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Chcete-li bezpečně potlačit upozornění z tohoto pravidla, je nutné zajistit, aby váš kód neudělil volajícím přístup k operacím nebo prostředkům, které lze použít destruktivním způsobem.

## <a name="example"></a>Příklad
 Následující příklady znázorňují knihovnu, která porušuje pravidlo, a aplikaci, která demonstruje slabé stránky knihovny. Ukázková knihovna poskytuje dvě metody, které dohromady narušují pravidlo. Metoda `EnvironmentSetting` je zabezpečená požadavkem propojení pro neomezený přístup k proměnným prostředí. Metoda `DomainInformation` neprovede žádné požadavky na zabezpečení svých volajících před voláním `EnvironmentSetting`.

 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.UnsecuredDoNotCall/cs/FxCop.Security.UnsecuredDoNotCall.cs#1)]

## <a name="example"></a>Příklad
 Následující aplikace volá nezabezpečeného člena knihovny.

 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestUnsecuredDoNot1/cs/FxCop.Security.TestUnsecuredDoNot1.cs#1)]

 Tento příklad vytvoří následující výstup.

 **Hodnota z nezabezpečeného člena: seattle.corp.contoso.com**
## <a name="see-also"></a>Viz také
 [Pokyny pro zabezpečené kódování](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) – [odkaz požadavky](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [na data a modelování](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
