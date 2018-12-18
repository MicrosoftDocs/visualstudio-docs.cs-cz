---
title: 'CA2114: Zabezpečení metody by mělo být nadmnožinou typu | Dokumentace Microsoftu'
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
- MethodSecurityShouldBeASupersetOfType
- CA2114
helpviewer_keywords:
- CA2114
- MethodSecurityShouldBeASupersetOfType
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5bdb7d5eb43958a892320fad244625f09fcd7592
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49878281"
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114: Zabezpečení metody by mělo být nadmnožinou typu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MethodSecurityShouldBeASupersetOfType|
|CheckId|CA2114|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Typ má deklarativní zabezpečení a jeden z jeho metod má deklarativní zabezpečení pro stejnou akci zabezpečení a akce zabezpečení není [požadavky propojení](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) nebo [požadavky na dědičnost](http://msdn.microsoft.com/en-us/28b9adbb-8f08-4f10-b856-dbf59eb932d9)a oprávnění vráceno uživatelem typu nejsou podmnožinu oprávnění ověří pomocí metody.

## <a name="rule-description"></a>Popis pravidla
 Metoda by neměla mít v obou úrovni metody nebo typ deklarativní zabezpečení pro stejnou akci. Dva kontroly nejsou sloučeny; je použita pouze vyžádání úrovni metod. Například, pokud typ požaduje oprávnění `X`, a jeden z jeho metod požaduje oprávnění `Y`, kód nemá oprávnění k `X` spustí metodu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Zrevidujete váš kód, abyste měli jistotu, že obě akce se vyžadují. Pokud obě akce, ujistěte se, že úroveň metody akce obsahuje zabezpečení na úrovni typu. Například, pokud váš typ požaduje oprávnění `X`, a její metoda musí také vyžadují oprávnění `Y`, metoda by měla explicitně vyžadují `X` a `Y`.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění tohoto pravidla, pokud metoda nevyžaduje zabezpečení podle typu. To však není běžné scénáře a může znamenat potřebu přezkoumání Pečlivý návrh.

## <a name="example"></a>Příklad
 Následující příklad používá oprávnění prostředí k předvedení nebezpečí porušení tohoto pravidla. V tomto příkladu kódu aplikace vytvoří instanci typu zabezpečené před odepřením oprávnění vyžadovaný typem. Ve scénáři hrozbami reálného světa bude aplikace vyžadovat, aby jiný způsob, jak získat instanci objektu.

 V následujícím příkladu knihovna požadavků pro typ oprávnění k zápisu a oprávnění ke čtení pro metodu.

 [!code-csharp[FxCop.Security.MethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MethodLevelSecurity/cs/FxCop.Security.MethodLevelSecurity.cs#1)]

## <a name="example"></a>Příklad
 Následující kód aplikace ukazuje ohrožení zabezpečení knihovny voláním metody i v případě, že nesplňuje požadavek na zabezpečení na úrovni typu.

 [!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestMethodLevelSecurity/cs/FxCop.Security.TestMethodLevelSecurity.cs#1)]

 Tento příklad vytvoří následující výstup.

 **[Všechna oprávnění] Osobní údaje: 6/16/1964 12:00:00 AM**
 **[žádné oprávnění k zápisu (požadováno podle typu)] osobní údaje: 6/16/1964 12:00:00 AM**
 **[žádné čtení oprávnění () vyžadována metoda)] nelze přístup k osobním informacím: požadavek se nezdařil.**
## <a name="see-also"></a>Viz také
 [Pokyny pro zabezpečené kódování](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [požadavky na dědičnost](http://msdn.microsoft.com/en-us/28b9adbb-8f08-4f10-b856-dbf59eb932d9) [požadavky na propojení](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [Data a modelování](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)



