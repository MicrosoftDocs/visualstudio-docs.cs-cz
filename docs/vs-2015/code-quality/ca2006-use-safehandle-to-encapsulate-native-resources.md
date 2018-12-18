---
title: 'CA2006: Použijte SafeHandle pro zapouzdření nativních prostředků | Dokumentace Microsoftu'
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
- CA2006
- UseSafeHandleToEncapsulateNativeResources
helpviewer_keywords:
- UseSafeHandleToEncapsulateNativeResources
- CA2006
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 88d53d90d00f58706e366b54dfa78b59e499bc24
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49935377"
---
# <a name="ca2006-use-safehandle-to-encapsulate-native-resources"></a>CA2006: Použijte SafeHandle pro zapouzdření nativních prostředků
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseSafeHandleToEncapsulateNativeResources|
|CheckId|CA2006|
|Kategorie|Microsoft.Reliability|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina
 Spravovat kód používá <xref:System.IntPtr> pro přístup k nativní prostředky.

## <a name="rule-description"></a>Popis pravidla
 Použití `IntPtr` ve spravovaném kódu může znamenat potenciální problém zabezpečení a spolehlivost. Všechny výskyty `IntPtr` musí být přezkoumána k určení, zda použití <xref:System.Runtime.InteropServices.SafeHandle> , nebo podobné technologie, je nutné na příslušné místo. Pokud dojde k problémům `IntPtr` představuje některé nativní prostředky, jako je například paměť, popisovače souboru nebo soketu, že spravovaný kód se považuje za vlastní. Pokud spravovaný kód vlastní prostředek, se musí také uvolnit nativní prostředky spojené s ním, protože selhání k tomu by způsobilo úniku prostředků.

 V takových scénářích, problémy zabezpečení a spolehlivosti bude také existovat, pokud je povolen přístup s více vlákny na `IntPtr` a způsob, jak uvolnění prostředků, která je reprezentována `IntPtr` je k dispozici. Tyto potíže týkají recyklaci `IntPtr` hodnotu na uvolnění prostředků během souběžné používání prostředku v jiném vlákně. To může způsobit konflikty časování kde jedno vlákno může číst nebo zapisovat data, která souvisí s nesprávnou prostředků. Například, pokud váš typ uloží popisovač operačního systému jako `IntPtr` a umožňuje uživatelům pro volání obou **Zavřít** a jiným způsobem, který používá tento popisovač současně a využijte bez nějaký druh synchronizace, váš kód obsahuje popisovač recyklace došlo k potížím.

 Tento popisovač recyklace problém může způsobit poškození dat a často, ohrožení zabezpečení. `SafeHandle` a své třídy na stejné úrovni <xref:System.Runtime.InteropServices.CriticalHandle> poskytují mechanismus pro zapouzdření nativní popisovač pro prostředek tak, aby tyto problémy dělení na vlákna se můžete vyhnout. Kromě toho můžete použít `SafeHandle` a jeho třída na stejné úrovni `CriticalHandle` pro ostatní problémy s tvorbou vláken, například pečlivě řídit dobu života spravovaných objektů, které obsahují kopii nativní popisovač prostřednictvím volání do nativní metody. V takovém případě můžete často eliminovat, volání `GC.KeepAlive`. Režie získána výkon při použití se vám účtovat `SafeHandle` a menší míře `CriticalHandle`, často bylo možné zmenšit prostřednictvím pečlivého návrhu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Převést `IntPtr` informací o využití a `SafeHandle` pro bezpečnou správu přístupu pro nativní prostředky. Zobrazit <xref:System.Runtime.InteropServices.SafeHandle> referenční téma pro příklady.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Neměli potlačení tohoto upozornění.

## <a name="see-also"></a>Viz také
 <xref:System.IDisposable>



