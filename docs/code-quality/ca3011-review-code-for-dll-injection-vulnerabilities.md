---
title: 'CA3011: Zkontrolujte ohrožení zabezpečení injektáží knihovny DLL v kódu'
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
ms.openlocfilehash: a459be8c8ab028581c850f5b5770a95cb70e3510
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237194"
---
# <a name="ca3011-review-code-for-dll-injection-vulnerabilities"></a>CA3011: Zkontrolujte ohrožení zabezpečení injektáží knihovny DLL v kódu

|||
|-|-|
|TypeName|ReviewCodeForDllInjectionVulnerabilities|
|CheckId|CA3011|
|Kategorie|Microsoft.Security|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Potenciálně nedůvěryhodný vstup požadavku HTTP dosáhne metody, která načte sestavení.

## <a name="rule-description"></a>Popis pravidla

Při práci s nedůvěryhodným vstupem nezapomeňte načíst nedůvěryhodný kód. Pokud vaše webová aplikace načte nedůvěryhodný kód, útočník může být schopen vložit do procesu škodlivé knihovny DLL a spustit škodlivý kód.

Toto pravidlo se pokouší najít vstup z požadavku HTTP, který dosáhne metody, která načte sestavení.

> [!NOTE]
> Toto pravidlo nemůže sledovat data napříč sestaveními. Například pokud jedno sestavení přečte vstup požadavku HTTP a pak ho předá do jiného sestavení, které načte sestavení, toto pravidlo nevytvoří upozornění.

> [!NOTE]
> Existuje konfigurovatelné omezení, jak hluboko bude toto pravidlo analyzovat tok dat napříč voláními metod. Postup konfigurace limitu v souboru EditorConfig naleznete v tématu [Configuration Analyzer](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) .

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Neprovádějte načítání nedůvěryhodných knihoven DLL ze vstupu uživatele.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Potlačit upozornění z tohoto pravidla

## <a name="pseudo-code-examples"></a>Příklady kódu pseudo

### <a name="violation"></a>Selhání

```csharp
using System;
using System.Reflection;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        byte[] rawAssembly = Convert.FromBase64String(input);
        Assembly.Load(rawAssembly);
    }
}
```

```vb
Imports System
Imports System.Reflection

Public Partial Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Request.Form("in")
        Dim rawAssembly As Byte() = Convert.FromBase64String(input)
        Assembly.Load(rawAssembly)
    End Sub
End Class
```
