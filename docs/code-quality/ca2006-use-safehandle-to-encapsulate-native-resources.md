---
title: 'CA2006: Použijte SafeHandle k zapouzdření nativních prostředků'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2006
- UseSafeHandleToEncapsulateNativeResources
helpviewer_keywords:
- UseSafeHandleToEncapsulateNativeResources
- CA2006
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 0e671deab060346bb998932495e5590f19945eaa
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233106"
---
# <a name="ca2006-use-safehandle-to-encapsulate-native-resources"></a>CA2006: Použijte SafeHandle k zapouzdření nativních prostředků

|||
|-|-|
|TypeName|UseSafeHandleToEncapsulateNativeResources|
|CheckId|CA2006|
|Kategorie|Microsoft.Reliability|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Spravovaný kód používá <xref:System.IntPtr> pro přístup k nativním prostředkům.

## <a name="rule-description"></a>Popis pravidla

`IntPtr` Použití ve spravovaném kódu může poukazovat na potenciální problém zabezpečení a spolehlivosti. Aby bylo možné `IntPtr` zjistit, zda je na svém místě vyžadováno použití <xref:System.Runtime.InteropServices.SafeHandle> nebo podobná technologie, je nutné zkontrolovat všechna použití. K problémům dojde, pokud `IntPtr` představuje určitý nativní prostředek, jako je například paměť, popisovač souboru nebo soket, který je spravovaným kódem považován za vlastní. Pokud spravovaný kód vlastní prostředek, musí také uvolnit nativní prostředky, které jsou k němu přidruženy, protože v důsledku selhání by to způsobilo únik prostředků.

V takových scénářích budou k dispozici také problémy se zabezpečením a spolehlivostí, pokud je povolen `IntPtr` přístup s více vlákny a způsob uvolnění prostředku, který je `IntPtr` reprezentován systémem. Tyto problémy zahrnují recyklaci `IntPtr` hodnoty pro vydanou verzi prostředků, zatímco současné využití prostředku se provádí v jiném vlákně. To může způsobit časování časování, ve kterém jedno vlákno může číst nebo zapisovat data přidružená k chybnému prostředku. Například pokud váš typ uchovává popisovač operačního systému jako `IntPtr` a umožňuje uživatelům volat jak **Zavřít** , tak i jinou metodu, která tento popisovač používá současně a bez určitého druhu synchronizace, váš kód má potíže s recyklací popisovače.

Tento problém recyklace obslužné rutiny může způsobit poškození dat a často ohrožení zabezpečení. `SafeHandle`a jeho třída <xref:System.Runtime.InteropServices.CriticalHandle> na stejné úrovni poskytuje mechanismus pro zapouzdření nativního popisovače do prostředku tak, aby se takové problémy s vlákny mohly vyhnout. Kromě toho můžete použít `SafeHandle` a jeho třídu `CriticalHandle` stejné úrovně pro jiné problémy s vlákny, například k pečlivému řízení životnosti spravovaných objektů, které obsahují kopii nativního popisovače přes volání do nativních metod. V této situaci můžete často odebrat volání do `GC.KeepAlive`. Režie na výkon, kterou jste se zaznamenali při používání `SafeHandle` a, na menší `CriticalHandle`stupeň, se může často snížit prostřednictvím pečlivého návrhu.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Převeďte `IntPtr` použití `SafeHandle` na pro bezpečnou správu přístupu k nativním prostředkům. Příklady najdete <xref:System.Runtime.InteropServices.SafeHandle> v referenčním článku.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Toto upozornění potlačit.

## <a name="see-also"></a>Viz také:

- <xref:System.IDisposable>