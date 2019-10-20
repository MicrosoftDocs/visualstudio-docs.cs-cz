---
title: 'CA2207: inicializovat typ hodnoty – vložená statická pole | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InitializeValueTypeStaticFieldsInline
- CA2207
helpviewer_keywords:
- CA2207
- InitializeValueTypeStaticFieldsInline
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a2b3c1faf4ecf3ecf79a3c78d0ded106b88345ee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72609368"
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207: Inicializujte vloženou hodnotu statických polí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InitializeValueTypeStaticFieldsInline|
|CheckId|CA2207|
|Kategorie|Microsoft. Usage|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>příčina
 Typ hodnoty deklaruje explicitní statický konstruktor.

## <a name="rule-description"></a>Popis pravidla
 Je-li deklarován typ hodnoty, je napřed výchozí inicializací, kde všechna pole typu hodnoty jsou nastavena na hodnotu nula a všechna pole typu odkazu jsou nastavena na hodnotu `null` (`Nothing` v Visual Basic). Explicitní statický konstruktor je zaručen pouze před tím, než je volán konstruktor instance nebo statický člen typu. Proto pokud je typ vytvořen bez volání konstruktoru instance, není zaručeno spuštění statického konstruktoru.

 Pokud jsou všechna statická data inicializována vložená a není deklarován žádný explicitní statický konstruktor C# , kompilátory a Visual Basic přidá příznak `beforefieldinit` do definice třídy jazyka MSIL. Kompilátory také přidávají privátní statický konstruktor, který obsahuje kód statické inicializace. Pro tento soukromý statický konstruktor je zaručeno, že bude spuštěn před tím, než budou k dispozici jakákoliv statická pole typu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, proveďte inicializaci všech statických dat, je-li deklarována a odeberte statický konstruktor.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="related-rules"></a>Související pravidla
 [CA1810: Inicializujte odkazový typ statického pole vloženě](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)
