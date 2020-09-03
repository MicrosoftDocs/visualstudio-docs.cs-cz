---
title: 'CA1051: Nedeklarujte viditelná pole instance | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
helpviewer_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 076ce3858774d44e2d6c4c25205ced74b7a41bf0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539760"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051: Nedeklarujte viditelná pole instance
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|CheckId|CA1051|
|Kategorie|Microsoft. Design|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Externě viditelný typ má externě viditelné pole instance.

## <a name="rule-description"></a>Popis pravidla
 Hlavní použití pole by mělo být jako podrobnost implementace. Pole by měla být `private` nebo `internal` a měla by být vystavena pomocí vlastností. Přístup k vlastnosti je snadno přístupný, protože je přístup k poli a kód v přístupových objektech vlastnosti se může změnit, protože funkce typu se rozšiřují bez úvodních změn. Vlastnosti, které vracejí jenom hodnotu privátního nebo interního pole, jsou optimalizované tak, aby se prováděly v hodnotě s přístupem k poli. k používání externě viditelných polí nad vlastnostmi je přidruženo velmi malý nárůst výkonu.

 Externě viditelné `public` jsou `protected` úrovně dostupnosti, a `protected internal` ( `Public` , a `Protected` `Protected Friend` v Visual Basic).

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, vytvořte pole `private` nebo `internal` ho zpřístupněte pomocí externě viditelné vlastnosti.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo. Externě viditelná pole neposkytují žádné výhody, které nejsou k dispozici pro vlastnosti. Veřejné pole navíc nelze chránit pomocí [požadavků propojení](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d). Viz [CA2112: zabezpečené typy by neměly vystavovat pole](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ ( `BadPublicInstanceFields` ), který porušuje toto pravidlo. `GoodPublicInstanceFields` zobrazuje opravený kód.

 [!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TypesPublicInstanceFields/cs/FxCop.Design.TypesPublicInstanceFields.cs#1)]

## <a name="related-rules"></a>Související pravidla
 [CA2112: Zabezpečené typy by neměly vystavovat pole](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>Viz také
 [Požadavky na odkaz](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)
