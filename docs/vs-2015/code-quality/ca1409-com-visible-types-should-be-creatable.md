---
title: 'CA1409: viditelné typy modelu COM by měly být vytvořitelné | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 180a8d6bbc7f035fa0ae2eeafaa4e2c884cddc8d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547326"
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409: Viditelné typy modelu COM by měly být vytvořitelné
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|ComVisibleTypesShouldBeCreatable|
|CheckId|CA1409|
|Kategorie|Microsoft. interoperabilita|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Odkazový typ, který je konkrétně označený jako viditelný pro model COM (Component Object Model) obsahuje veřejný parametrizovaný konstruktor, ale neobsahuje veřejný výchozí konstruktor (bez parametrů).

## <a name="rule-description"></a>Popis pravidla
 Typ bez veřejného výchozího konstruktoru nelze vytvořit pomocí klientů modelu COM. Nicméně k tomuto typu může mít přístup klienti modelu COM, pokud je k dispozici jiný způsob, jak vytvořit typ a předat ho klientovi (například prostřednictvím návratové hodnoty volání metody).

 Pravidlo ignoruje typy, které jsou odvozeny z <xref:System.Delegate?displayProperty=fullName> .

 Ve výchozím nastavení jsou následující prvky viditelné v modelu COM: sestavení, veřejné typy, členy veřejné instance ve veřejných typech a všechny členy typů veřejné hodnoty.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, přidejte veřejný výchozí konstruktor nebo odeberte z tohoto <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> typu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění z tohoto pravidla, pokud jsou k dispozici jiné způsoby vytváření a předávání objektu klientovi modelu COM.

## <a name="related-rules"></a>Související pravidla
 [CA1017: Označte sestavení pomocí ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Viz také
 [Kvalifikace typů .NET pro](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) spolupráci [s nespravovaným kódem](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
