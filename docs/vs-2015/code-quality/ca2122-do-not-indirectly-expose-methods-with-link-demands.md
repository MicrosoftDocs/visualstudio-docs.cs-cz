---
title: 'CA2122: Nezveřejňujte nepřímo metody s požadavky propojení | Dokumentace Microsoftu'
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
- CA2122
- DoNotIndirectlyExposeMethodsWithLinkDemands
helpviewer_keywords:
- DoNotIndirectlyExposeMethodsWithLinkDemands
- CA2122
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 563805fdd8ba8c30e9fb241cc24136ad0c9e9e06
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49912835"
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122: Nezveřejňujte nepřímo metody s požadavky propojení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|
|CheckId|CA2122|
|Kategorie|Microsoft.Security|
|Narušující změna|Pevné|

## <a name="cause"></a>příčina
 Veřejný nebo chráněný člen má [požadavky propojení](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) a je volán členem, který neprovádí žádné bezpečnostní kontroly.

## <a name="rule-description"></a>Popis pravidla
 Požadavek propojení kontroluje pouze oprávnění bezprostředního volajícího. Pokud člen `X` provádí žádné požadavky na zabezpečení svých volající a kód chráněn pomocí požadavku propojení, volající bez nezbytná oprávnění můžete použít volání `X` přístup chráněný člen.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Přidat bezpečnostní [Data a modelování](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) nebo vyžádání propojit člen tak, aby už neposkytuje nezabezpečený přístup na vyžádání chráněné člena odkazu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Můžete bezpečně potlačit upozornění tohoto pravidla, ujistěte se, že váš kód bez možnosti udělovat volajících přístup pro operace nebo prostředky použité destruktivním způsobem.

## <a name="example"></a>Příklad
 Následující příklady ukazují knihovnu, která porušuje pravidlo a aplikace, která ukazuje slabé stránky knihovny. Ukázky knihovny poskytuje dvě metody, které společně pravidlo porušují. `EnvironmentSetting` Metoda je zabezpečena pomocí požadavku propojení pro neomezený přístup k proměnným prostředí. `DomainInformation` Metoda provádí žádné požadavky na zabezpečení volajících před voláním `EnvironmentSetting`.

 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.UnsecuredDoNotCall/cs/FxCop.Security.UnsecuredDoNotCall.cs#1)]

## <a name="example"></a>Příklad
 Následující aplikace volá člen nezabezpečené knihovny.

 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestUnsecuredDoNot1/cs/FxCop.Security.TestUnsecuredDoNot1.cs#1)]

 Tento příklad vytvoří následující výstup.

 **Hodnota od nezabezpečené člena: seattle.corp.contoso.com**
## <a name="see-also"></a>Viz také
 [Pokyny pro zabezpečené kódování](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [požadavky na propojení](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [Data a modelování](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)



