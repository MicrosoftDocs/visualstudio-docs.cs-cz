---
title: 'CA2108: Revize deklarativních zabezpečení na hodnotách | Dokumentace Microsoftu'
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
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
helpviewer_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b437fa656c2a2d0650463fd0ab78119f67099ac7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49889659"
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108: Revize deklarativních zabezpečení na hodnotách
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewDeclarativeSecurityOnValueTypes|
|CheckId|CA2108|
|Kategorie|Microsoft.Security|
|Narušující změna|Pevné|

## <a name="cause"></a>příčina
 Veřejný nebo chráněný hodnotový typ je zabezpečen pomocí [Data a modelování](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) nebo [požadavky propojení](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d).

## <a name="rule-description"></a>Popis pravidla
 Typy hodnot jsou přiděleny a inicializován pomocí jejich výchozí konstruktory před další konstruktory. Pokud hodnota typ je zabezpečen pomocí s požadavkem nebo LinkDemand a volající nemá oprávnění, které splňují kontrola zabezpečení, některý konstruktor jiné než výchozí hodnota se nezdaří a bude vyvolána výjimka zabezpečení. Typ hodnoty není uvolněný; je ponechána ve stavu, nastavte jeho výchozí konstruktor. Nepředpokládejte, že volající, který předá instance typu hodnoty má oprávnění k vytváření a přístup k instanci.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Pokud odeberete z typu kontroly zabezpečení a použití zabezpečení na úrovni metoda zkontroluje místo něj nelze opravit porušení tohoto pravidla. Všimněte si, že oprava porušení tímto způsobem nezabrání volajícím s nedostatečná oprávnění od získání instance typu hodnoty. Ujistěte se, že instance typu hodnoty ve svém výchozím stavu není zveřejnit citlivé informace a nelze použít škodlivých způsobem.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Upozornění tohoto pravidla můžete potlačit, pokud jakýkoli volající můžete získat instance typu hodnoty ve svém výchozím stavu bez představující ohrožení zabezpečení.

## <a name="example"></a>Příklad
 Následující příklad ukazuje knihovnu obsahující hodnotový typ, který porušuje tato pravidla. Všimněte si, `StructureManager` typ předpokládá, že volající, který předá instance typu hodnoty má oprávnění k vytváření a přístup k instanci.

 [!code-csharp[FxCop.Security.DemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.DemandOnValueType/cs/FxCop.Security.DemandOnValueType.cs#1)]

## <a name="example"></a>Příklad
 Následující aplikace ukazuje slabé stránky knihovny.

 [!code-csharp[FxCop.Security.TestDemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestDemandOnValueType/cs/FxCop.Security.TestDemandOnValueType.cs#1)]

 Tento příklad vytvoří následující výstup.

 **Struktura vlastního konstruktoru: požadavek se nezdařil. ** 
 **Nové hodnoty SecuredTypeStructure 100 100**
**nové hodnoty SecuredTypeStructure 200 200**
## <a name="see-also"></a>Viz také
 [Požadavky na propojení](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [Data a modelování](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)



