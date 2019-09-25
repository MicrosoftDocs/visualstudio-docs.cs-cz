---
title: 'CA2232: Označte vstupní body modelu Windows Forms pomocí STAThread'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MarkWindowsFormsEntryPointsWithStaThread
- CA2232
helpviewer_keywords:
- CA2232
- MarkWindowsFormsEntryPointsWithStaThread
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 06772f8dd91c27834b329293d06cfbc2a7dcfcef
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71230760"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: Označte vstupní body modelu Windows Forms pomocí STAThread

|||
|-|-|
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|Kategorie|Microsoft.Usage|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina
Sestavení odkazuje na <xref:System.Windows.Forms> obor názvů a jeho vstupní bod není označen <xref:System.STAThreadAttribute?displayProperty=fullName> atributem.

## <a name="rule-description"></a>Popis pravidla
 <xref:System.STAThreadAttribute>označuje, že model vláken modelu COM pro aplikaci je jedním vláknem typu apartment. Tento atribut musí být přítomen u vstupního bodu jakékoliv aplikace, která používá model Windows Forms. Pokud je vynechán, nemusí součásti systému Windows pracovat správně. Pokud atribut přítomen není, aplikace použije model Apartment s více vlákny, který není podporován pro model Windows Forms.

> [!NOTE]
> [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]projekty, které používají rozhraní Application Framework, nemusí označovat metodu **Main** pomocí STAThread. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Kompilátor to provede automaticky.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, přidejte <xref:System.STAThreadAttribute> atribut do vstupního bodu. Pokud je přítomen atribut, odeberte jej. <xref:System.MTAThreadAttribute?displayProperty=fullName>

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Je bezpečné potlačit upozornění z tohoto pravidla, pokud vyvíjíte pro prostředí .NET Compact Framework, pro které <xref:System.STAThreadAttribute> je atribut zbytečný a není podporovaný.

## <a name="example"></a>Příklad
Následující příklady ukazují správné použití <xref:System.STAThreadAttribute>:

[!code-csharp[FxCop.Usage.StaThread#1](../code-quality/codesnippet/CSharp/ca2232-mark-windows-forms-entry-points-with-stathread_1.cs)]
[!code-vb[FxCop.Usage.StaThread#1](../code-quality/codesnippet/VisualBasic/ca2232-mark-windows-forms-entry-points-with-stathread_1.vb)]