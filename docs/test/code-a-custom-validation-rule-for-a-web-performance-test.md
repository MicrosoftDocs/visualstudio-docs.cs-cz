---
title: Vytvoření vlastního ověřovacího pravidla pro test výkonnosti webu
description: Naučte se vytvářet vlastní pravidla ověřování odvozená od třídy ověřovacího pravidla a ověřovacího pravidla.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- custom validation rules
- validation rules, creating
- web performance tests, creating custom validation rules
- rules, validation
- validation rules
ms.assetid: 989124bc-1a86-41f7-b37d-8f9e54dd4f0b
dev_langs:
- CSharp
- VB
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 627122368c90163cf9aef4c8035bfbb67c4a0dba
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2020
ms.locfileid: "95441817"
---
# <a name="code-a-custom-validation-rule-for-a-web-performance-test"></a>Kódování vlastního ověřovacího pravidla pro test výkonnosti webu

Můžete vytvořit vlastní ověřovací pravidla. Za tímto účelem odvozujete vlastní třídu pravidla od třídy pravidla ověřování. Pravidla ověření jsou odvozena ze <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule> základní třídy.

> [!NOTE]
> Můžete také vytvořit vlastní pravidla pro extrakci. Další informace naleznete v tématu [Vytvoření vlastního kódu a modulů plug-in pro zátěžové testy](../test/create-custom-code-and-plug-ins-for-load-tests.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-create-custom-validation-rules"></a>Vytvoření vlastních ověřovacích pravidel

1. Otevřete projekt testů, který obsahuje test výkonnosti webu.

2. Volitelné Vytvořte samostatný projekt knihovny tříd, do kterého chcete uložit ověřovací pravidlo.

    > [!IMPORTANT]
    > Třídu lze vytvořit ve stejném projektu, ve kterém jsou testy. Nicméně pokud chcete pravidlo znovu použít, je vhodnější vytvořit samostatný projekt knihovny tříd, do které pravidlo uložíte. Pokud vytvoříte samostatný projekt, je nutné provést volitelné kroky v tomto postupu.

3. Volitelné V projektu knihovny tříd přidejte odkaz na knihovnu DLL Microsoft. VisualStudio. QualityTools. WebTestFramework.

4. Vytvořte třídu, která je odvozena od třídy <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule>. Implementujte členy <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule.Validate*> a <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule.RuleName*>.

5. (Volitelné) Vytvořte nový projekt knihovny tříd.

6. Volitelné V testovacím projektu přidejte odkaz na projekt knihovny tříd, který obsahuje vlastní ověřovací pravidlo.

7. V projektu testu otevřete test výkonnosti webu v **Editor testu výkonnosti webu**.

8. Chcete-li přidat vlastní ověřovací pravidlo do žádosti o test výkonnosti webu, klikněte pravým tlačítkem myši na požadavek a vyberte možnost **přidat ověřovací pravidlo**.

     Zobrazí se dialogové okno **přidat ověřovací pravidlo** . V seznamu **vybrat pravidlo** se zobrazí vaše vlastní ověřovací pravidlo spolu s předdefinovanými ověřovacími pravidly. Vyberte vlastní ověřovací pravidlo a pak zvolte **OK**.

9. Spusťte test výkonnosti webu.

## <a name="example"></a>Příklad

Následující kód ukazuje implementaci vlastního ověřovacího pravidla. Toto pravidlo ověřování napodobuje chování předdefinovaného ověřovacího pravidla značky. Tento příklad slouží jako výchozí bod pro vlastní ověřovací pravidla.

> [!WARNING]
> Veřejné vlastnosti v kódu pro vlastní validátor nemohou mít hodnoty null.

```csharp
using System;
using System.Diagnostics;
using System.Globalization;
using Microsoft.VisualStudio.TestTools.WebTesting;

namespace SampleWebTestRules
{
    //-------------------------------------------------------------------------
    // This class creates a custom validation rule named "Custom Validate Tag"
    // The custom validation rule is used to check that an HTML tag with a
    // particular name is found one or more times in the HTML response.
    // The user of the rule can specify the HTML tag to look for, and the
    // number of times that it must appear in the response.
    //-------------------------------------------------------------------------
    public class CustomValidateTag : ValidationRule
    {
        /// Specify a name for use in the user interface.
        /// The user sees this name in the Add Validation dialog box.
        //---------------------------------------------------------------------
        public override string RuleName
        {
            get { return "Custom Validate Tag"; }
        }

        /// Specify a description for use in the user interface.
        /// The user sees this description in the Add Validation dialog box.
        //---------------------------------------------------------------------
        public override string RuleDescription
        {
            get { return "Validates that the specified tag exists on the page."; }
        }

        // The name of the required tag
        private string RequiredTagNameValue;
        public string RequiredTagName
        {
            get { return RequiredTagNameValue; }
            set { RequiredTagNameValue = value; }
        }

        // The minimum number of times the tag must appear in the response
        private int MinOccurrencesValue;
        public int MinOccurrences
        {
            get { return MinOccurrencesValue; }
            set { MinOccurrencesValue = value; }
        }

        // Validate is called with the test case Context and the request context.
        // These allow the rule to examine both the request and the response.
        //---------------------------------------------------------------------
        public override void Validate(object sender, ValidationEventArgs e)
        {
            bool validated = false;
            int numTagsFound = 0;

            foreach (HtmlTag tag in e.Response.HtmlDocument.GetFilteredHtmlTags(RequiredTagName))
            {
                Debug.Assert(string.Equals(tag.Name, RequiredTagName, StringComparison.InvariantCultureIgnoreCase));

                if (++numTagsFound >= MinOccurrences)
                {
                    validated = true;
                    break;
                }
            }

            e.IsValid = validated;

            // If the validation fails, set the error text that the user sees
            if (!validated)
            {
                if (numTagsFound > 0)
                {
                    e.Message = String.Format("Only found {0} occurrences of the tag", numTagsFound);
                }
                else
                {
                    e.Message = String.Format("Did not find any occurrences of tag '{0}'", RequiredTagName);
                }
            }
        }
    }
}
```

```vb
Imports System
Imports System.Diagnostics
Imports System.Globalization
Imports Microsoft.VisualStudio.TestTools.WebTesting

Namespace SampleWebTestRules

    '-------------------------------------------------------------------------
    ' This class creates a custom validation rule named "Custom Validate Tag"
    ' The custom validation rule is used to check that an HTML tag with a
    ' particular name is found one or more times in the HTML response.
    ' The user of the rule can specify the HTML tag to look for, and the
    ' number of times that it must appear in the response.
    '-------------------------------------------------------------------------
    Public Class CustomValidateTag
        Inherits Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule

        ' Specify a name for use in the user interface.
        ' The user sees this name in the Add Validation dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleName() As String
            Get
                Return "Custom Validate Tag"
            End Get
        End Property

        ' Specify a description for use in the user interface.
        ' The user sees this description in the Add Validation dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleDescription() As String
            Get
                Return "Validates that the specified tag exists on the page."
            End Get
        End Property

        ' The name of the required tag
        Private RequiredTagNameValue As String
        Public Property RequiredTagName() As String
            Get
                Return RequiredTagNameValue
            End Get
            Set(ByVal value As String)
                RequiredTagNameValue = value
            End Set
        End Property

        ' The minimum number of times the tag must appear in the response
        Private MinOccurrencesValue As Integer
        Public Property MinOccurrences() As Integer
            Get
                Return MinOccurrencesValue
            End Get
            Set(ByVal value As Integer)
                MinOccurrencesValue = value
            End Set
        End Property

        ' Validate is called with the test case Context and the request context.
        ' These allow the rule to examine both the request and the response.
        '---------------------------------------------------------------------
        Public Overrides Sub Validate(ByVal sender As Object, ByVal e As ValidationEventArgs)

            Dim validated As Boolean = False
            Dim numTagsFound As Integer = 0

            For Each tag As HtmlTag In e.Response.HtmlDocument.GetFilteredHtmlTags(RequiredTagName)

                Debug.Assert(String.Equals(tag.Name, RequiredTagName, StringComparison.InvariantCultureIgnoreCase))

                numTagsFound += 1
                If numTagsFound >= MinOccurrences Then

                    validated = True
                    Exit For
                End If
            Next

            e.IsValid = validated

            ' If the validation fails, set the error text that the user sees
            If Not (validated) Then
                If numTagsFound > 0 Then
                    e.Message = String.Format("Only found {0} occurrences of the tag", numTagsFound)
                Else
                    e.Message = String.Format("Did not find any occurrences of tag '{0}'", RequiredTagName)
                End If
            End If
        End Sub
    End Class
End Namespace
```

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidateFormField>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleFindText>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleRequestTime>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleRequiredAttributeValue>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleRequiredTag>
- [Vytvoření vlastního pravidla extrakce pro test výkonnosti webu](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
