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
ms.openlocfilehash: 42bb554f8e57c036d41a89fdc2657a25ecc74e20
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540280"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: Označte vstupní body modelu Windows Forms pomocí STAThread
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|Kategorie|Microsoft. Usage|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>Příčina
 Sestavení odkazuje na <xref:System.Windows.Forms> obor názvů a jeho vstupní bod není označen <xref:System.STAThreadAttribute?displayProperty=fullName> atributem.

## <a name="rule-description"></a>Popis pravidla
 <xref:System.STAThreadAttribute> označuje, že model vláken modelu COM pro aplikaci je jedním vláknem typu apartment. Tento atribut musí být přítomen u vstupního bodu jakékoliv aplikace, která používá model Windows Forms. Pokud je vynechán, nemusí součásti systému Windows pracovat správně. Pokud atribut přítomen není, aplikace použije model Apartment s více vlákny, který není podporován pro model Windows Forms.

> [!NOTE]
> [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projekty, které používají rozhraní Application Framework, nemusí označovat metodu **Main** pomocí STAThread. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]Kompilátor to provede automaticky.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, přidejte <xref:System.STAThreadAttribute> atribut do vstupního bodu. Pokud <xref:System.MTAThreadAttribute?displayProperty=fullName> je přítomen atribut, odeberte jej.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění z tohoto pravidla, pokud vyvíjíte pro prostředí .NET Compact Framework, pro které <xref:System.STAThreadAttribute> je atribut zbytečný a není podporovaný.

## <a name="example"></a>Příklad
 Následující příklady ukazují správné využití <xref:System.STAThreadAttribute> .

 [!code-csharp[FxCop.Usage.StaThread#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/cs/FxCop.Usage.StaThread.cs#1)]
 [!code-vb[FxCop.Usage.StaThread#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/vb/FxCop.Usage.StaThread.vb#1)]
