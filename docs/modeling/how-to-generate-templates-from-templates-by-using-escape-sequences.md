---
title: Generování textové šablony z textové šablony
description: Poskytuje informace o tom, jak vygenerovat textovou šablonu z jiné textové šablony pomocí řídicích sekvencí.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, generating templates from templates
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 9347e32a72e7f590f8f513c4b47a4b7aae699f27
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387174"
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>Postupy: Generování šablon ze šablon pomocí řídicích sekvencí
Můžete vytvořit textovou šablonu, která vytvoří jinou textovou šablonu jako její vygenerovaný textový výstup. K tomu je nutné použít řídicí sekvence k vytyčení značek textové šablony. Pokud řídicí sekvence použijete, bude mít vygenerovaná textová šablona předdefinovaný význam. Další informace o použití řídicích sekvencí v textových šablonách najdete v tématu [Použití řídicích sekvencí v textových šablonách](../modeling/using-escape-sequences-in-text-templates.md).

### <a name="to-generate-a-text-template-from-within-a-text-template"></a>Vygenerování textové šablony z textové šablony

- Zpětné lomítko ( ) použijte jako řídicí znak k vytvoření potřebných značek v textové šabloně pro direktivy, příkazy, výrazy a funkce třídy v samostatném souboru \\ textové šablony.

    ```
    \<#@ directive \#>
    \<# statement \#>
    \<#= expression \#>
    \<#+ classfeature \#>
    ```

## <a name="example"></a>Příklad
 Následující příklad používá řídicí znaky k vytvoření textové šablony z textové šablony. Direktiva `output` nastaví cílový typ souboru na typ souboru textové šablony (.tt).

```csharp
\<#@ output extension=".tt" \#>
\<#@ assembly name="System.Xml.dll" \#>
\<#@ import namespace="System.Xml" \#>
\<#
XmlDocument xDoc = new XmlDocument();
//System.Diagnostics.Debugger.Break();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {\#>
           \<#= attr.Name \#>
       \<#}
     }
\#>
```

 Vygenerovaný textový výstup je textová šablona.

```
<#@ output extension=".tt" #>
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>
<#
XmlDocument xDoc = new XmlDocument();
//System.Diagnostics.Debugger.Break();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {#>
           <#= attr.Name #>
       <#}
     }
#>
```
