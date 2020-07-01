---
title: 'CA2006: použijte SafeHandle pro zapouzdření nativních prostředků | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2006
- UseSafeHandleToEncapsulateNativeResources
helpviewer_keywords:
- UseSafeHandleToEncapsulateNativeResources
- CA2006
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fdf3ff02c86a878e9c955d2b3b92879870700efa
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85521144"
---
# <a name="ca2006-use-safehandle-to-encapsulate-native-resources"></a>CA2006: Použijte SafeHandle k zapouzdření nativních prostředků
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|UseSafeHandleToEncapsulateNativeResources|
|CheckId|CA2006|
|Kategorie|Microsoft.Reliability|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Spravovaný kód používá <xref:System.IntPtr> pro přístup k nativním prostředkům.

## <a name="rule-description"></a>Popis pravidla
 Použití `IntPtr` ve spravovaném kódu může poukazovat na potenciální problém zabezpečení a spolehlivosti. `IntPtr`Aby bylo možné zjistit, zda <xref:System.Runtime.InteropServices.SafeHandle> je na svém místě vyžadováno použití nebo podobná technologie, je nutné zkontrolovat všechna použití. K problémům dojde, pokud `IntPtr` představuje určitý nativní prostředek, jako je například paměť, popisovač souboru nebo soket, který je spravovaným kódem považován za vlastní. Pokud spravovaný kód vlastní prostředek, musí také uvolnit nativní prostředky, které jsou k němu přidruženy, protože v důsledku selhání by to způsobilo únik prostředků.

 V takových scénářích budou k dispozici také problémy se zabezpečením a spolehlivostí, pokud je povolen přístup s více vlákny `IntPtr` a způsob uvolnění prostředku, který je reprezentován systémem `IntPtr` . Tyto problémy zahrnují recyklaci `IntPtr` hodnoty pro vydanou verzi prostředků, zatímco současné využití prostředku se provádí v jiném vlákně. To může způsobit časování časování, ve kterém jedno vlákno může číst nebo zapisovat data přidružená k chybnému prostředku. Například pokud váš typ uchovává popisovač operačního systému jako `IntPtr` a umožňuje uživatelům volat jak **Zavřít** , tak i jinou metodu, která tento popisovač používá současně a bez určitého druhu synchronizace, váš kód má potíže s recyklací popisovače.

 Tento problém recyklace obslužné rutiny může způsobit poškození dat a často ohrožení zabezpečení. `SafeHandle`a jeho třída na stejné úrovni <xref:System.Runtime.InteropServices.CriticalHandle> poskytuje mechanismus pro zapouzdření nativního popisovače do prostředku tak, aby se takové problémy s vlákny mohly vyhnout. Kromě toho můžete použít `SafeHandle` a jeho třídu stejné úrovně `CriticalHandle` pro jiné problémy s vlákny, například k pečlivému řízení životnosti spravovaných objektů, které obsahují kopii nativního popisovače přes volání do nativních metod. V této situaci můžete často odebrat volání do `GC.KeepAlive` . Režijní náklady na výkon Thay vám vznikne při používání `SafeHandle` a na menším stupni, `CriticalHandle` může se často snížit prostřednictvím pečlivého návrhu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Převeďte `IntPtr` použití na `SafeHandle` pro bezpečnou správu přístupu k nativním prostředkům. Příklady najdete v <xref:System.Runtime.InteropServices.SafeHandle> referenčním tématu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Toto upozornění byste neměli potlačit.

## <a name="see-also"></a>Viz také
 <xref:System.IDisposable>
