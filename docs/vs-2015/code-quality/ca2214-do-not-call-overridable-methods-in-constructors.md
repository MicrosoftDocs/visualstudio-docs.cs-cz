---
title: 'CA2214: Nevolejte přepisovatelné metody v konstruktorech | Dokumentace Microsoftu'
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
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b43400dbd516328e133ed6e103d4a4f2a7ccf8a3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49921467"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: Nevolejte přepisovatelné metody v konstruktorech
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|Kategorie|Microsoft.Usage|
|Narušující změna|Pevné|

## <a name="cause"></a>příčina
 Konstruktor nezapečetěný typ volání virtuální metody definované ve své třídě.

## <a name="rule-description"></a>Popis pravidla
 Při volání virtuální metody, skutečný typ, který se spustí metodu není vybraná až do spuštění. Pokud konstruktor volání virtuální metody, je možné, že se neprovedlo konstruktoru pro instanci, která vyvolá metodu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, nevolejte virtuální metody tohoto typu z konstruktorů tohoto typu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo. Chcete-li odstranit volání virtuální metody by se měla změnit konstruktoru.

## <a name="example"></a>Příklad
 Následující příklad ukazuje účinek porušení tohoto pravidla. Testovací aplikace vytvoří instanci `DerivedType`, což způsobí, že její základní třídě (`BadlyConstructedType`) konstruktor ke spuštění. `BadlyConstructedType`pro konstruktor nesprávně volání virtuální metody `DoSomething`. Jak ukazuje výstup, `DerivedType.DoSomething()` spustí a nebude tak před `DerivedType`v konstruktoru.

 [!code-csharp[FxCop.Usage.CtorVirtual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/cs/FxCop.Usage.CtorVirtual.cs#1)]
 [!code-vb[FxCop.Usage.CtorVirtual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/vb/FxCop.Usage.CtorVirtual.vb#1)]

 Tento příklad vytvoří následující výstup.

 **Volání konstruktoru base. ** 
 **Odvozené DoSomething nazývá - inicializovat? Ne**
**volání odvozené ctor.**



