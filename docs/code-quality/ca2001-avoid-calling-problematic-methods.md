---
title: 'CA2001: Vyhněte se volání problematických metod'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2001
- AvoidCallingProblematicMethods
helpviewer_keywords:
- CA2001
- AvoidCallingProblematicMethods
ms.assetid: 19db8edb-31ce-441c-b0de-a0f2746155b7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 95209067f3821b6446b64dc7990e189720d20cea
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233196"
---
# <a name="ca2001-avoid-calling-problematic-methods"></a>CA2001: Vyhněte se volání problematických metod

|||
|-|-|
|TypeName|AvoidCallingProblematicMethods|
|CheckId|CA2001|
|Kategorie|Microsoft.Reliability|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Člen volá potencionálně nebezpečnou nebo problematickou metodu.

## <a name="rule-description"></a>Popis pravidla

Vyhněte se zbytečným a potenciálně nebezpečným voláním metody. Porušení tohoto pravidla nastane, když člen volá jednu z následujících metod:

|Metoda|Popis|
|------------|-----------------|
|<xref:System.GC.Collect%2A?displayProperty=fullName>|Volání GC. Shromažďování může významně ovlivnit výkon aplikace a je zřídka nezbytné. Další informace najdete v tématu o záznamu [Mariani Performance pikantní pro výkon](http://go.microsoft.com/fwlink/?LinkId=169256) na webu MSDN.|
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|Vlákno. Suspend a Thread. Resume bylo Zastaralé z důvodu jejich nepředvídatelného chování.  <xref:System.Threading> Použijte jiné třídy v oboru názvů, <xref:System.Threading.Monitor>například, <xref:System.Threading.Mutex>a <xref:System.Threading.Semaphore>, k synchronizaci vláken nebo ochraně prostředků.|
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|Metoda DangerousGetHandle představuje bezpečnostní riziko, protože může vrátit neplatný popisovač. Další informace o tom <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> , jak bezpečně používat metodu DangerousGetHandle, naleznete v tématu ametody.<xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A>|
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|Tyto metody mohou načítat sestavení z neočekávaných umístění. Podívejte se například na blogové příspěvky [v Suzanne Cookovy pro .NET LoadFile vs. LoadFrom](http://go.microsoft.com/fwlink/?LinkId=164450) a [Výběr kontextu vazby](http://go.microsoft.com/fwlink/?LinkId=164451) pro informace o metodách, které načítají sestavení.|
|[CoSetProxyBlanket](http://go.microsoft.com/fwlink/?LinkID=169250) (Ole32)<br /><br /> [CoInitializeSecurity](http://go.microsoft.com/fwlink/?LinkId=169255) (Ole32)|V době, kdy se uživatelský kód začne spouštět ve spravovaném procesu, je příliš pozdě spolehlivě volat CoSetProxyBlanket. Modul CLR (Common Language Runtime) provede inicializační akce, které mohou zabránit úspěšnému volání uživatelů.<br /><br /> Pokud je třeba volat CoSetProxyBlanket pro spravovanou aplikaci, doporučujeme spustit proces pomocí spustitelného souboru nativního kódu (C++), zavolat CoSetProxyBlanket v nativním kódu a pak spustit aplikaci spravovaného kódu v procesu. (Nezapomeňte zadat číslo verze modulu runtime.)|

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, odeberte nebo nahraďte volání nebezpečné nebo problematické metody.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Zprávy z tohoto pravidla byste měli potlačit pouze v případě, že nejsou k dispozici žádné alternativy problematické metody.

## <a name="see-also"></a>Viz také:

- [Upozornění spolehlivosti](../code-quality/reliability-warnings.md)