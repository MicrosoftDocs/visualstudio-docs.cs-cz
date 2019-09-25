---
title: 'CA3010: Zkontrolujte ohrožení zabezpečení injektáží XAML v kódu'
ms.date: 04/03/2019
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: efd30a783f534d76f7f7f3fa18fd181dbe7e98a1
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237236"
---
# <a name="ca3010-review-code-for-xaml-injection-vulnerabilities"></a>CA3010: Zkontrolujte ohrožení zabezpečení injektáží XAML v kódu

|||
|-|-|
|TypeName|ReviewCodeForXamlInjectionVulnerabilities|
|CheckId|CA3010|
|Kategorie|Microsoft.Security|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Potenciálně nedůvěryhodný vstup požadavku HTTP dosáhne <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> metody Load.

## <a name="rule-description"></a>Popis pravidla

Při práci s nedůvěryhodným vstupem si vědomete útoků prostřednictvím injektáže XAML. XAML je jazyk značek, který přímo představuje instanci objektu a provádění. To znamená, že prvky vytvořené v jazyce XAML mohou pracovat se systémovými prostředky (například síťový přístup a vstupně-výstupní operace systému souborů). Pokud by útočník mohl řídit vstup pro <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> volání metody Load, může útočník spustit kód.

Toto pravidlo se pokouší najít vstup z požadavků HTTP, které dosáhnou <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> metody Load.

> [!NOTE]
> Toto pravidlo nemůže sledovat data napříč sestaveními. Například pokud jedno sestavení přečte vstup požadavku HTTP a pak ho předává do jiného sestavení, které načte kód XAML, toto pravidlo nevytvoří upozornění.

> [!NOTE]
> Existuje konfigurovatelné omezení, jak hluboko bude toto pravidlo analyzovat tok dat napříč voláními metod. Postup konfigurace limitu v souboru EditorConfig naleznete v tématu [Configuration Analyzer](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) .

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Nenačte nedůvěryhodný kód XAML.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Potlačit upozornění z tohoto pravidla

## <a name="pseudo-code-examples"></a>Příklady kódu pseudo

### <a name="violation"></a>Selhání

```csharp
using System;
using System.IO;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        byte[] bytes = Convert.FromBase64String(input);
        MemoryStream ms = new MemoryStream(bytes);
        System.Windows.Markup.XamlReader.Load(ms);
    }
}
```

```vb
Imports System
Imports System.IO

Public Partial Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Request.Form("in")
        Dim bytes As Byte() = Convert.FromBase64String(input)
        Dim ms As MemoryStream = New MemoryStream(bytes)
        System.Windows.Markup.XamlReader.Load(ms)
    End Sub
End Class
```
