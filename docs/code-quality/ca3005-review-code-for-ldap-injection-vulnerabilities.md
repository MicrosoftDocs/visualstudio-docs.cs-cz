---
title: 'CA3005: Zkontrolujte ohrožení zabezpečení injektáží protokolu LDAP v kódu'
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
ms.openlocfilehash: c0c99d5d0adb145a061693f8a83b1f674e05eed4
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237344"
---
# <a name="ca3005-review-code-for-ldap-injection-vulnerabilities"></a>CA3005: Zkontrolujte ohrožení zabezpečení injektáží protokolu LDAP v kódu

|||
|-|-|
|TypeName|ReviewCodeForLdapInjectionVulnerabilities|
|CheckId|CA3005|
|Kategorie|Microsoft.Security|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Potenciálně nedůvěryhodný vstup požadavku HTTP dosáhne příkazu LDAP.

## <a name="rule-description"></a>Popis pravidla

Při práci s nedůvěryhodným vstupem si vědomete útoků prostřednictvím injektáže protokolu LDAP (Lightweight Directory Access Protocol). Útočník může potenciálně spustit škodlivé příkazy LDAP na informačních adresářích. Aplikace, které používají vstup uživatele k vytváření dynamických příkazů LDAP pro přístup k adresářovým službám, jsou obzvláště zranitelné.

Toto pravidlo se pokouší najít vstup z požadavků HTTP, které dosáhnou příkazu LDAP.

> [!NOTE]
> Toto pravidlo nemůže sledovat data napříč sestaveními. Například pokud jedno sestavení přečte vstup požadavku HTTP a pak ho předává do jiného sestavení, které spustí příkaz LDAP, toto pravidlo nevytvoří upozornění.

> [!NOTE]
> Existuje konfigurovatelné omezení, jak hluboko bude toto pravidlo analyzovat tok dat napříč voláními metod. Postup konfigurace limitu v souboru EditorConfig naleznete v tématu [Configuration Analyzer](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) .

## <a name="how-to-fix-violations"></a>Jak opravit porušení

V případě uživatelsky řízené části příkazů protokolu LDAP zvažte jednu z těchto akcí:
- Povolí pouze bezpečný seznam znaků, které nejsou speciální.
- Zakázat speciální znak
- Speciální znaky escape.

Další pokyny najdete v [listu tahák prevence vkládání LDAP v OWASP](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/LDAP_Injection_Prevention_Cheat_Sheet.md) .

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Pokud víte, že vstup byl ověřen nebo byl jeho řídicím znakem zabezpečený, je v pořádku Toto upozornění potlačit.

## <a name="pseudo-code-examples"></a>Příklady kódu pseudo

### <a name="violation"></a>Selhání

```csharp
using System;
using System.DirectoryServices;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string userName = Request.Params["user"];
        string filter = "(uid=" + userName + ")";  // searching for the user entry

        // In this example, if we send the * character in the user parameter which will
        // result in the filter variable in the code to be initialized with (uid=*).
        // The resulting LDAP statement will make the server return any object that
        // contains a uid attribute.
        DirectorySearcher searcher = new DirectorySearcher(filter);
        SearchResultCollection results = searcher.FindAll();

        // Iterate through each SearchResult in the SearchResultCollection.
        foreach (SearchResult searchResult in results)
        {
            // ...
        }
    }
}
```

```vb
Imports System
Imports System.DirectoryServices

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(send As Object, e As EventArgs)
        Dim userName As String = Me.Request.Params(""user"")
        Dim filter As String = ""(uid="" + userName + "")""    ' searching for the user entry

        ' In this example, if we send the * character in the user parameter which will
        ' result in the filter variable in the code to be initialized with (uid=*).
        ' The resulting LDAP statement will make the server return any object that
        ' contains a uid attribute.
        Dim searcher As DirectorySearcher = new DirectorySearcher(filter)
        Dim results As SearchResultCollection = searcher.FindAll()

        ' Iterate through each SearchResult in the SearchResultCollection.
        For Each searchResult As SearchResult in results
            ' ...
        Next searchResult
    End Sub
End Class
```
