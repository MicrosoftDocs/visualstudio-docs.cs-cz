---
title: 'CA3002: Zkontrolujte ohrožení zabezpečení proti XSS v kódu'
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
ms.openlocfilehash: 6bcf32401abdeae499097bc5187d11154e7dfc6e
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237421"
---
# <a name="ca3002-review-code-for-xss-vulnerabilities"></a>CA3002: Zkontrolujte ohrožení zabezpečení proti XSS v kódu

|||
|-|-|
|TypeName|ReviewCodeForXssVulnerabilities|
|CheckId|CA3002|
|Kategorie|Microsoft.Security|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Potenciálně nedůvěryhodný vstup požadavku HTTP dostane nezpracovaný výstup HTML.

## <a name="rule-description"></a>Popis pravidla

Při práci s nedůvěryhodným vstupem z webových požadavků zajistěte útoky skriptování XSS (mezi weby). Útok XSS vloží nedůvěryhodný vstup do nezpracovaného výstupu HTML a umožní útočníkovi spustit škodlivé skripty nebo škodlivým způsobem upravovat obsah na webové stránce. Typickou technikou je umístit `<script>` prvky se škodlivým kódem do vstupu. Další informace najdete v tématu [OWASP skriptování xss](https://www.owasp.org/index.php/Cross-site_Scripting_(XSS)).

Toto pravidlo se pokusí najít vstup z požadavků HTTP, které dosáhnou nezpracovaného výstupu HTML.

> [!NOTE]
> Toto pravidlo nemůže sledovat data napříč sestaveními. Například pokud jedno sestavení přečte vstup požadavku HTTP a pak ho předává do jiného sestavení, které výstupuje nezpracovaných HTML, toto pravidlo nevytvoří upozornění.

> [!NOTE]
> Existuje konfigurovatelné omezení, jak hluboko bude toto pravidlo analyzovat tok dat napříč voláními metod. Postup konfigurace limitu v souboru EditorConfig naleznete v tématu [Configuration Analyzer](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) .

## <a name="how-to-fix-violations"></a>Jak opravit porušení

- Místo výstupu nezpracovaného kódu HTML použijte metodu nebo vlastnost, která nejprve zakóduje svůj vstup ve formátu HTML.
- HTML – kódování nedůvěryhodných dat před výstupem nezpracovaného HTML.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Upozornění z tohoto pravidla je bezpečné potlačit, pokud:
- Víte, že vstup je ověřený proti známé bezpečné sadě znaků, které neobsahují kód HTML.
- Víte, že data jsou ve formátu HTML kódovaná způsobem, který toto pravidlo nerozpoznalo.

> [!NOTE]
> Toto pravidlo může hlásit falešně pozitivní výsledky některých metod nebo vlastností, které jsou ve formátu HTML zakódováním jejich vstupu.

## <a name="pseudo-code-examples"></a>Příklady kódu pseudo

### <a name="violation"></a>Selhání

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        Response.Write("<HTML>" + input + "</HTML>");
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Me.Request.Form("in")
        Me.Response.Write("<HTML>" + input + "</HTML>")
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

        // Example usage of System.Web.HttpServerUtility.HtmlEncode().
        Response.Write("<HTML>" + Server.HtmlEncode(input) + "</HTML>");
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Me.Request.Form("in")

        ' Example usage of System.Web.HttpServerUtility.HtmlEncode().
        Me.Response.Write("<HTML>" + Me.Server.HtmlEncode(input) + "</HTML>")
    End Sub
End Class
```