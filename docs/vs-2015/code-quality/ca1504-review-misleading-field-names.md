---
title: 'CA1504: Kontrola zavádějících názvů polí | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c3f1cca5dd33047a4d19c78013dd535e0e9dd6f2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607749"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504: Zkontrolujte zavádějící názvy polí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|Kategorie|Microsoft. udržovatelnost|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina
 Název pole instance začíná řetězcem "s_" nebo názvem `static` (`Shared` v [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]), začíná na "m_".

## <a name="rule-description"></a>Popis pravidla
 Názvy polí, které začínají řetězcem "s_", jsou přidruženy ke statickým datům mnoha uživateli. Podobně názvy polí, které začínají řetězcem "m_", jsou přidruženy k datům instance (člen). Pro snazší údržbu kódu by názvy měly dodržovat obecně používané konvence.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, přejmenujte pole pomocí příslušné předpony. Případně můžete nastavit, aby se v poli souhlasila s aktuální příponou přidáním nebo odebráním modifikátoru `static`.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.
