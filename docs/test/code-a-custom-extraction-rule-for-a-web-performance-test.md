---
title: Vytvoření vlastního pravidla extrakce pro test výkonnosti webu
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- extraction rules
- Web performance tests, creating custom extraction rules
- extraction rules, creating custom
ms.assetid: 6bcc5712-6cc6-4f59-8933-6e8078318c45
dev_langs:
- CSharp
- VB
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9aeb80d348e31de0934d515754c59346fac3c2ea
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665263"
---
# <a name="code-a-custom-extraction-rule-for-a-web-performance-test"></a>Kód vlastní pravidlo extrakce pro test výkonnosti webu

Můžete vytvořit vlastní pravidla pro extrakci, a to odvozením vlastních pravidel od třídy pravidla pro extrakci. Pravidla pro extrakci se odvozují od základní třídy <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule>.

> [!NOTE]
> Lze také vytvořit vlastní ověřovací pravidla. Další informace naleznete v tématu [Vytvoření vlastního kódu a modulů plug-in pro zátěžové testy](../test/create-custom-code-and-plug-ins-for-load-tests.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-create-a-custom-extraction-rule"></a>Vytvoření vlastního pravidla pro extrakci

1. Otevřete projekt testů, který obsahuje test výkonnosti webu.

2. (Volitelné) Vytvořte samostatný projekt knihovny tříd, do které bude uloženo pravidlo pro extrakci.

    > [!IMPORTANT]
    > Třídu lze vytvořit ve stejném projektu, ve kterém jsou testy. Nicméně pokud chcete pravidlo znovu použít, je vhodnější vytvořit samostatný projekt knihovny tříd, do které pravidlo uložíte. Pokud vytvoříte samostatný projekt, je nutné provést volitelné kroky v tomto postupu.

3. (Volitelné) Do projektu knihovny tříd přidejte odkaz na knihovnu dll Microsoft.VisualStudio.QualityTools.WebTestFramework.

4. Vytvořte třídu, která je odvozena od třídy <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule>. Implementujte členy <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.Extract*> a <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.RuleName*>.

5. (Volitelné) Vytvořte nový projekt knihovny tříd.

6. Volitelné V testovacím projektu přidejte odkaz na projekt knihovny tříd, který obsahuje vlastní pravidlo pro extrakci.

7. V projektu testu otevřete test výkonnosti webu v **Editor testu výkonnosti webu**.

8. Chcete-li přidat vlastní pravidlo pro extrakci, klikněte pravým tlačítkem myši na požadavek testu výkonnosti webu a vyberte možnost **Přidat pravidlo extrakce**.

     Zobrazí se dialogové okno **Přidat pravidlo extrakce** . V seznamu **vybrat pravidlo** se zobrazí vaše vlastní ověřovací pravidlo spolu s předdefinovanými ověřovacími pravidly. Vyberte vlastní pravidlo pro extrakci a klikněte na **tlačítko OK**.

9. Spusťte test výkonnosti webu.

## <a name="example"></a>Příklad

Následující kód ukazuje implementaci vlastního pravidla pro extrakci. Toto pravidlo pro extrakci extrahuje hodnotu ze zadaného vstupního pole. Tento příklad použijte jako výchozí bod pro vlastní pravidla pro extrakci.

```csharp
using System;
using System.Collections.Generic;
using Microsoft.VisualStudio.TestTools.WebTesting;
using System.Globalization;

namespace ClassLibrary2
{
    //-------------------------------------------------------------------------
    // This class creates a custom extraction rule named "Custom Extract Input"
    // The user of the rule specifies the name of an input field, and the
    // rule attempts to extract the value of that input field.
    //-------------------------------------------------------------------------
    public class CustomExtractInput : ExtractionRule
    {
        /// Specify a name for use in the user interface.
        /// The user sees this name in the Add Extraction dialog box.
        //---------------------------------------------------------------------
        public override string RuleName
        {
            get { return "Custom Extract Input"; }
        }

        /// Specify a description for use in the user interface.
        /// The user sees this description in the Add Extraction dialog box.
        //---------------------------------------------------------------------
        public override string RuleDescription
        {
            get { return "Extracts the value from a specified input field"; }
        }

        // The name of the desired input field
        private string NameValue;
        public string Name
        {
            get { return NameValue; }
            set { NameValue = value; }
        }

        // The Extract method.  The parameter e contains the web performance test context.
        //---------------------------------------------------------------------
        public override void Extract(object sender, ExtractionEventArgs e)
        {
            if (e.Response.HtmlDocument != null)
            {
                foreach (HtmlTag tag in e.Response.HtmlDocument.GetFilteredHtmlTags(new string[] { "input" }))
                {
                    if (String.Equals(tag.GetAttributeValueAsString("name"), Name, StringComparison.InvariantCultureIgnoreCase))
                    {
                        string formFieldValue = tag.GetAttributeValueAsString("value");
                        if (formFieldValue == null)
                        {
                            formFieldValue = String.Empty;
                        }

                        // add the extracted value to the web performance test context
                        e.WebTest.Context.Add(this.ContextParameterName, formFieldValue);
                        e.Success = true;
                        return;
                    }
                }
            }
            // If the extraction fails, set the error text that the user sees
            e.Success = false;
            e.Message = String.Format(CultureInfo.CurrentCulture, "Not Found: {0}", Name);
        }
    }
}
```

```vb
Imports System
Imports System.Collections.Generic
Imports Microsoft.VisualStudio.TestTools.WebTesting
Imports System.Globalization

Namespace ClassLibrary2

    '-------------------------------------------------------------------------
    ' This class creates a custom extraction rule named "Custom Extract Input"
    ' The user of the rule specifies the name of an input field, and the
    ' rule attempts to extract the value of that input field.
    '-------------------------------------------------------------------------
    Public Class CustomExtractInput
        Inherits ExtractionRule

        ' Specify a name for use in the user interface.
        ' The user sees this name in the Add Extraction dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleName() As String
            Get
                Return "Custom Extract Input"
            End Get
        End Property

        ' Specify a description for use in the user interface.
        ' The user sees this description in the Add Extraction dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleDescription() As String
            Get
                Return "Extracts the value from a specified input field"
            End Get
        End Property

        ' The name of the desired input field
        Private NameValue As String
        Public Property Name() As String
            Get
                Return NameValue
            End Get
            Set(ByVal value As String)
                NameValue = value
            End Set
        End Property

        ' The Extract method.  The parameter e contains the web performance test context.
        '---------------------------------------------------------------------
        Public Overrides Sub Extract(ByVal sender As Object, ByVal e As ExtractionEventArgs)

            If Not e.Response.HtmlDocument Is Nothing Then

                For Each tag As HtmlTag In e.Response.HtmlDocument.GetFilteredHtmlTags(New String() {"input"})

                    If String.Equals(tag.GetAttributeValueAsString("name"), Name, StringComparison.InvariantCultureIgnoreCase) Then

                        Dim formFieldValue As String = tag.GetAttributeValueAsString("value")
                        If formFieldValue Is Nothing Then

                            formFieldValue = String.Empty
                        End If

                        ' add the extracted value to the web performance test context
                        e.WebTest.Context.Add(Me.ContextParameterName, formFieldValue)
                        e.Success = True
                        Return
                    End If
                Next
            End If
            ' If the extraction fails, set the error text that the user sees
            e.Success = False
            e.Message = String.Format(CultureInfo.CurrentCulture, "Not Found: {0}", Name)
        End Sub
    End Class
End Namespace
```

Metoda <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.Extract*> obsahuje základní funkce pravidla pro extrakci. Metoda <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.Extract*> v předchozím příkladu přebírá objekt <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionEventArgs>, jenž poskytuje odpověď generovanou požadavkem, který toto pravidlo pro extrakci pokrývá. Odpověď obsahuje objekt <xref:Microsoft.VisualStudio.TestTools.WebTesting.HtmlDocument>, který obsahuje všechny značky v odpovědi. Vstupní značky jsou z dokumentu <xref:Microsoft.VisualStudio.TestTools.WebTesting.HtmlDocument> odfiltrovány. Každá vstupní značka je prověřena pro atribut s názvem `name`, jehož hodnota se rovná uživatelem zadané hodnotě vlastnosti `Name`. Pokud je nalezena značka s tímto odpovídajícím atributem, je proveden pokus o extrakci hodnoty, která je obsažena v atributu `value`, pokud atribut value existuje. Pokud existuje, budou název a hodnota značky extrahovány a přidány do kontextu testu výkonnosti webu. Pravidlo pro extrakci bude splněno.

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractAttributeValue>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractFormField>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractHttpHeader>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractRegularExpression>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractText>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractHiddenFields>
- [Kódování vlastního ověřovacího pravidla pro test výkonnosti webu](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)