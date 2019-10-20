---
title: 'CA2232: označte model Windows Forms vstupními body STAThread | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkWindowsFormsEntryPointsWithStaThread
- CA2232
helpviewer_keywords:
- CA2232
- MarkWindowsFormsEntryPointsWithStaThread
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 084e7a093f92aa8eda9d9edc11865ac319adfad0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662795"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: Označte vstupní bod modelu Windows Forms pomocí STAThread
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|Kategorie|Microsoft. Usage|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>příčina
 Sestavení odkazuje na obor názvů <xref:System.Windows.Forms> a jeho vstupní bod není označen atributem <xref:System.STAThreadAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Popis pravidla
 <xref:System.STAThreadAttribute> znamená, že model vláken modelu COM pro aplikaci je jedním vláknem typu apartment. Tento atribut musí být přítomen u vstupního bodu jakékoliv aplikace, která používá model Windows Forms. Pokud je vynechán, nemusí součásti systému Windows pracovat správně. Pokud atribut přítomen není, aplikace použije model Apartment s více vlákny, který není podporován pro model Windows Forms.

> [!NOTE]
> [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projekty, které používají rozhraní Application Framework, nemusí označovat metodu **Main** pomocí STAThread. Kompilátor [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] provádí automaticky.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, přidejte do vstupního bodu atribut <xref:System.STAThreadAttribute>. Pokud je přítomen atribut <xref:System.MTAThreadAttribute?displayProperty=fullName>, odeberte jej.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Pokud vyvíjíte pro prostředí .NET Compact Framework, pro který je atribut <xref:System.STAThreadAttribute> zbytečný a není podporovaný, je bezpečné potlačit upozornění od tohoto pravidla.

## <a name="example"></a>Příklad
 Následující příklady ukazují správné použití <xref:System.STAThreadAttribute>.

 [!code-csharp[FxCop.Usage.StaThread#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/cs/FxCop.Usage.StaThread.cs#1)]
 [!code-vb[FxCop.Usage.StaThread#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/vb/FxCop.Usage.StaThread.vb#1)]
