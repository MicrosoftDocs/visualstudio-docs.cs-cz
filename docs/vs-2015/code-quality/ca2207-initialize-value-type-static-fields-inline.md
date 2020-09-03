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
ms.openlocfilehash: 792fe18a4f472d0b8a4fd62c652f2ae34fcf6864
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546299"
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207: Inicializujte statická pole s typem hodnoty vloženě
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|InitializeValueTypeStaticFieldsInline|
|CheckId|CA2207|
|Kategorie|Microsoft. Usage|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>Příčina
 Typ hodnoty deklaruje explicitní statický konstruktor.

## <a name="rule-description"></a>Popis pravidla
 Je-li deklarován typ hodnoty, je napřed výchozí inicializací, kde jsou všechna pole typu hodnoty nastavena na hodnotu nula a všechna pole typu odkazu jsou nastavena na hodnotu `null` ( `Nothing` v Visual Basic). Explicitní statický konstruktor je zaručen pouze před tím, než je volán konstruktor instance nebo statický člen typu. Proto pokud je typ vytvořen bez volání konstruktoru instance, není zaručeno spuštění statického konstruktoru.

 Pokud jsou všechna statická data inicializována vložená a není deklarován žádný explicitní statický konstruktor, kompilátory jazyka C# a Visual Basic přidají `beforefieldinit` příznak do definice třídy jazyka MSIL. Kompilátory také přidávají privátní statický konstruktor, který obsahuje kód statické inicializace. Pro tento soukromý statický konstruktor je zaručeno, že bude spuštěn před tím, než budou k dispozici jakákoliv statická pole typu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, proveďte inicializaci všech statických dat, je-li deklarována a odeberte statický konstruktor.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="related-rules"></a>Související pravidla
 [CA1810: Inicializujte odkazový typ statického pole vloženě](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)
