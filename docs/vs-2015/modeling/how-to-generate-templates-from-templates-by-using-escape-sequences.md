---
title: 'Postupy: generování šablon ze šablon pomocí řídicích sekvencí | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, generating templates from templates
ms.assetid: 4126156a-7cea-48b8-925e-7790806cfe6c
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 501b7f040cb841d19c06ccc8fe7615a5b4a5e70d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657349"
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>Postupy: Generování šablon ze šablon pomocí řídicích sekvencí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete vytvořit textovou šablonu, která vytvoří další textovou šablonu jako vygenerovaný textový výstup. K tomu je nutné použít řídící sekvence k vymezení tagů textových šablon. Pokud nepoužíváte řídicí sekvence, vaše vytvořená šablona textu bude mít předem definovaný význam. Další informace o použití řídicích sekvencí v textových šablonách naleznete v tématu [Použití řídicích sekvencí v textových šablonách](../modeling/using-escape-sequences-in-text-templates.md).

### <a name="to-generate-a-text-template-from-within-a-text-template"></a>Vygenerování textové šablony v rámci textové šablony

- Pomocí zpětného lomítka ( \\ ) jako řídicího znaku vytvořte potřebné značky značek v rámci textové šablony pro direktivy, příkazy, výrazy a funkce třídy v samostatném souboru textové šablony.

    ```
    \<#@ directive \#>
    \<# statement \#>
    \<#= expression \#>
    \<#+ classfeature \#>
    ```

## <a name="example"></a>Příklad
 Následující příklad používá řídicí znaky k vytvoření textové šablony z textové šablony. `output`Direktiva nastaví typ cílového souboru na typ souboru textové šablony (. TT).

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

 Generovaný textový výstup je textová šablona.

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
