---
title: 'CA1504: Zkontrolujte zavádějící názvy polí'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 31c147c67854dd59f1fb7c9202f553edfb4a77a8
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234510"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504: Zkontrolujte zavádějící názvy polí

|||
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|Kategorie|Microsoft. udržovatelnost|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina
Název pole instance začíná řetězcem "s_", nebo název `static` pole (`Shared` v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) začíná řetězcem "m_".

## <a name="rule-description"></a>Popis pravidla
Názvy polí, které začínají řetězcem "s_", jsou přidruženy ke statickým datům mnoha uživateli. Podobně názvy polí, které začínají řetězcem "m_", jsou přidruženy k datům instance (člen). Pro snazší údržbu kódu by názvy měly dodržovat obecně používané konvence.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, přejmenujte pole pomocí příslušné předpony. Případně můžete nastavit, aby se v poli souhlasila s aktuální příponou přidáním `static` nebo odebráním modifikátoru.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo.