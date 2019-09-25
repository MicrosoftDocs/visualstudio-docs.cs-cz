---
title: 'CA3004: Zkontrolujte ohrožení zabezpečení zpřístupněním informací v kódu'
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
ms.openlocfilehash: 4965c9df3c2256511b8e44de8d388a9155d0d8f9
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237381"
---
# <a name="ca3004-review-code-for-information-disclosure-vulnerabilities"></a>CA3004: Zkontrolujte ohrožení zabezpečení zpřístupněním informací v kódu

|||
|-|-|
|TypeName|ReviewCodeForInformationDisclosureVulnerabilities|
|CheckId|CA3004|
|Kategorie|Microsoft.Security|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Webový výstup představuje zprávu o výjimce, trasování zásobníku nebo řetězcové vyjádření.

## <a name="rule-description"></a>Popis pravidla

Vydávání informací o výjimce poskytne útočníkům přehled o vnitřních verzích vaší aplikace, které můžou útočníkům pomoci najít další ohrožení zabezpečení pro zneužití.

Toto pravidlo se pokouší najít zprávu o výjimce, trasování zásobníku nebo řetězcové vyjádření, které jsou odesílány do odpovědi HTTP.

> [!NOTE]
> Toto pravidlo nemůže sledovat data napříč sestaveními. Například pokud jedno sestavení zachytí výjimku a poté předá do jiného sestavení, které vrací výjimku, toto pravidlo nevydá upozornění.

> [!NOTE]
> Existuje konfigurovatelné omezení, jak hluboko bude toto pravidlo analyzovat tok dat napříč voláními metod. Postup konfigurace limitu v souboru EditorConfig naleznete v tématu [Configuration Analyzer](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) .

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Nevytvářejte výstup informací o výjimkách odpovědí HTTP. Místo toho zadejte obecnou chybovou zprávu. Další pokyny najdete na [stránce o zpracování chyb v OWASP](https://www.owasp.org/index.php/Error_Handling) .

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Pokud víte, že váš webový výstup spadá do hranice vztahu důvěryhodnosti vaší aplikace a nikdy se nezveřejňuje mimo, je možné toto upozornění potlačit. To je zřídka. Vezměte v úvahu, že hranice vztahu důvěryhodnosti vaší aplikace a toky dat se můžou v průběhu času měnit.

## <a name="pseudo-code-examples"></a>Příklady kódu pseudo

### <a name="violation"></a>Selhání

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs eventArgs)
    {
        try
        {
            object o = null;
            o.ToString();
        }
        catch (Exception e)
        {
            this.Response.Write(e.ToString());
        }
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs As EventArgs)
        Try
            Dim o As Object = Nothing
            o.ToString()
        Catch e As Exception
            Me.Response.Write(e.ToString())
        End Try
    End Sub
End Class
```

### <a name="solution"></a>Řešení

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs eventArgs)
    {
        try
        {
            object o = null;
            o.ToString();
        }
        catch (Exception e)
        {
            this.Response.Write("An error occurred. Please try again later.");
        }
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs As EventArgs)
        Try
            Dim o As Object = Nothing
            o.ToString()
        Catch e As Exception
            Me.Response.Write("An error occurred. Please try again later.")
        End Try
    End Sub
End Class
```