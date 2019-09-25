---
title: 'CA3007: Zkontrolujte ohrožení zabezpečení otevřeným přesměrováním v kódu'
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
ms.openlocfilehash: 0226c0e2e66a6543b81cd8ee674a743766b65f3e
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237275"
---
# <a name="ca3007-review-code-for-open-redirect-vulnerabilities"></a>CA3007: Zkontrolujte ohrožení zabezpečení otevřeným přesměrováním v kódu

|||
|-|-|
|TypeName|ReviewCodeForOpenRedirectVulnerabilities|
|CheckId|CA3007|
|Kategorie|Microsoft.Security|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Potenciálně nedůvěryhodný vstup požadavku HTTP dosáhne přesměrování odpovědi HTTP.

## <a name="rule-description"></a>Popis pravidla

Při práci s nedůvěryhodným vstupem nezapomeňte na otevřené chyby zabezpečení přesměrování. Útočník může zneužít otevřenou chybu zabezpečení přesměrování pro použití vašeho webu k poskytnutí vzhledu legitimní adresy URL, ale přesměruje nepodezřelého návštěvníka na podvodný nebo jinou škodlivou webovou stránku.

Toto pravidlo se pokouší najít vstup z požadavků HTTP, které dosáhly adresy URL pro přesměrování HTTP.

> [!NOTE]
> Toto pravidlo nemůže sledovat data napříč sestaveními. Například pokud jedno sestavení přečte vstup požadavku HTTP a pak ho předává do jiného sestavení, které reaguje na přesměrování HTTP, toto pravidlo nevytvoří upozornění.

> [!NOTE]
> Existuje konfigurovatelné omezení, jak hluboko bude toto pravidlo analyzovat tok dat napříč voláními metod. Postup konfigurace limitu v souboru EditorConfig naleznete v tématu [Configuration Analyzer](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) .

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Mezi přístupy k opravě slabých chyb zabezpečení při přesměrování patří:

- Nepovolujte uživatelům iniciování přesměrování.
- Nepovolujte uživatelům zadání jakékoli části adresy URL ve scénáři přesměrování.
- Omezí přesměrování na předdefinovaný seznam povolených adres URL.
- Ověřte adresy URL přesměrování.
- Pokud je to možné, zvažte použití stránky s omezením, když se uživatelé přesměrují z webu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Pokud víte, že jste ověřili, že vstup bude omezený na zamýšlené adresy URL, je dobré toto upozornění potlačit.

## <a name="pseudo-code-examples"></a>Příklady kódu pseudo

### <a name="violation"></a>Selhání

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["url"];
        this.Response.Redirect(input);
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs As EventArgs)
        Dim input As String = Me.Request.Form("url")
        Me.Response.Redirect(input)
    End Sub
End Class
```

### <a name="solution"></a>Řešení

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        if (String.IsNullOrWhiteSpace(input))
        {
            this.Response.Redirect("https://example.org/login.html");
        }
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs As EventArgs)
        Dim input As String = Me.Request.Form("in")
        If String.IsNullOrWhiteSpace(input) Then
            Me.Response.Redirect("https://example.org/login.html")
        End If
    End Sub
End Class
```
