---
title: 'CA2114: zabezpečení metody by mělo být nadmnožinou typu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MethodSecurityShouldBeASupersetOfType
- CA2114
helpviewer_keywords:
- CA2114
- MethodSecurityShouldBeASupersetOfType
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d7879d8b2aa9eb4ece1ce07f89681b6c0b0f5f31
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534703"
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114: Zabezpečení metod by mělo být nadmnožinou typu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|MethodSecurityShouldBeASupersetOfType|
|CheckId|CA2114|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Typ má deklarativní zabezpečení a jedna z jeho metod má deklarativní zabezpečení pro stejnou akci zabezpečení a akce zabezpečení není [odkazování na požadavky](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) nebo [požadavky na dědičnost](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9)a oprávnění zkontrolovaných typem nejsou podmnožinou oprávnění zkontrolovaných metodou.

## <a name="rule-description"></a>Popis pravidla
 Metoda by neměla mít deklarativní zabezpečení na úrovni metody i typu pro stejnou akci. Tyto dvě kontroly nejsou kombinovány. použije se jenom požadavek úrovně metody. Například pokud typ vyžaduje oprávnění `X` a jedna z jeho metod požaduje oprávnění `Y` , kód nemusí mít oprávnění `X` ke spuštění metody.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Zkontrolujte kód a ujistěte se, že jsou nutné obě akce. Pokud jsou požadovány obě akce, ujistěte se, že akce na úrovni metody zahrnuje zabezpečení specifikované na úrovni typu. Například pokud váš typ požaduje oprávnění `X` a jeho metoda musí také vyžadovat oprávnění `Y` , metoda by měla explicitně vyžadovat `X` a `Y` .

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 V případě, že metoda nevyžaduje zabezpečení určené typem, je bezpečné potlačit upozornění od tohoto pravidla. Nejedná se ale o běžný scénář a může to znamenat, že je potřeba pečlivé přezkoumání návrhu.

## <a name="example"></a>Příklad
 Následující příklad používá oprávnění prostředí k demonstraci nebezpečí porušení tohoto pravidla. V tomto příkladu kód aplikace vytvoří instanci zabezpečeného typu před odepřením oprávnění vyžadovaných typem. Ve scénáři reálného ohrožení vyžaduje aplikace další způsob, jak získat instanci objektu.

 V následujícím příkladu Knihovna požaduje oprávnění k zápisu pro typ a oprávnění číst pro metodu.

 [!code-csharp[FxCop.Security.MethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MethodLevelSecurity/cs/FxCop.Security.MethodLevelSecurity.cs#1)]

## <a name="example"></a>Příklad
 Následující kód aplikace demonstruje ohrožení zabezpečení knihovny voláním metody, i když nesplňuje požadavek zabezpečení na úrovni typu.

 [!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestMethodLevelSecurity/cs/FxCop.Security.TestMethodLevelSecurity.cs#1)]

 Tento příklad vytvoří následující výstup.

 **[Všechna oprávnění] osobní informace: 6/16/1964 12:00:00 dop.** 
 **[Žádné oprávnění k zápisu (vyžádané podle typu)] osobní informace: 6/16/1964 12:00:00 dop.** 
 **[Žádné oprávnění ke čtení (vyžádané metodou)] se nepovedlo získat přístup k osobním informacím: požadavek se nezdařil.**
## <a name="see-also"></a>Viz také
 [Zásady zabezpečeného kódování](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [požadavky dědičnosti](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) požadavky [propojení vyžaduje](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [data a modelování](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) .
