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
ms.openlocfilehash: d375b64bbc877cb377157f13b3e4cfa7c7cf1592
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547872"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504: Zkontrolujte zavádějící názvy polí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|Kategorie|Microsoft. udržovatelnost|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Název pole instance začíná na "s_" nebo název `static` `Shared` pole (v [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) začíná řetězcem "m_".

## <a name="rule-description"></a>Popis pravidla
 Názvy polí, které začínají řetězcem "s_", jsou přidruženy ke statickým datům mnoha uživateli. Podobně jsou názvy polí, které začínají řetězcem "m_", přidruženy k datům instance (člen). Pro snazší údržbu kódu by názvy měly dodržovat obecně používané konvence.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, přejmenujte pole pomocí příslušné předpony. Případně můžete nastavit, aby se v poli souhlasila s aktuální příponou přidáním nebo odebráním `static` modifikátoru.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.
