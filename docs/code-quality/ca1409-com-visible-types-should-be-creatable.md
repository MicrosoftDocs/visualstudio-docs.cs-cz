---
title: 'CA1409: Viditelné typy modelu COM by měly být vytvořitelné'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 54630b7fba69ef96a2c08486e535ae45d8e614b8
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234768"
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409: Viditelné typy modelu COM by měly být vytvořitelné

|||
|-|-|
|TypeName|ComVisibleTypesShouldBeCreatable|
|CheckId|CA1409|
|Kategorie|Microsoft. interoperabilita|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina
Odkazový typ, který je konkrétně označený jako viditelný pro model COM (Component Object Model) obsahuje veřejný parametrizovaný konstruktor, ale neobsahuje veřejný výchozí konstruktor (bez parametrů).

## <a name="rule-description"></a>Popis pravidla
Typ bez veřejného výchozího konstruktoru nelze vytvořit pomocí klientů modelu COM. Nicméně k tomuto typu může mít přístup klienti modelu COM, pokud je k dispozici jiný způsob, jak vytvořit typ a předat ho klientovi (například prostřednictvím návratové hodnoty volání metody).

Pravidlo ignoruje typy, které jsou odvozeny z <xref:System.Delegate?displayProperty=fullName>.

Ve výchozím nastavení jsou následující prvky viditelné v modelu COM: sestavení, veřejné typy, členy veřejné instance ve veřejných typech a všechny členy typů veřejné hodnoty.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, přidejte veřejný výchozí konstruktor nebo odeberte <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> z tohoto typu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Je bezpečné potlačit upozornění z tohoto pravidla, pokud jsou k dispozici jiné způsoby vytváření a předávání objektu klientovi modelu COM.

## <a name="related-rules"></a>Související pravidla
[CA1017: Označte sestavení pomocí ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Viz také:

- [Kvalifikace typů .NET pro spolupráci](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Spolupráce s nespravovaným kódem](/dotnet/framework/interop/index)