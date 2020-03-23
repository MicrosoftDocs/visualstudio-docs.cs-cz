---
title: Přizpůsobení souborů projektu vytvořených službou VSTU | Dokumenty společnosti Microsoft
ms.custom: ''
ms.date: 07/26/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 60b8cc1d-cacc-404d-b768-77e81bc354f8
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: ad52e9f97dfbb9a5d0b3d65085c6c2627ccb2232
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62819526"
---
# <a name="customize-project-files-created-by-vstu"></a>Přizpůsobení souborů projektu vytvořených službou VSTU
Visual Studio Tools for Unity poskytuje volání ve stylu Unity během generování souboru projektu. Zaregistrujte `VisualStudioIntegration.ProjectFileGeneration` se s událostí a upravte soubor projektu vždy, když je znovu vygenerován.

## <a name="demonstrates"></a>Demonstruje
 Jak přizpůsobit soubory projektu sady Visual Studio generované visual studio nástroje pro jednotu.

## <a name="example"></a>Příklad

```csharp
#if ENABLE_VSTU
using System;
using System.IO;
using System.Linq;
using System.Text;
using System.Xml.Linq;

using UnityEngine;
using UnityEditor;

using SyntaxTree.VisualStudio.Unity.Bridge;

[InitializeOnLoad]
public class ProjectFileHook
{
    // necessary for XLinq to save the xml project file in utf8
    class Utf8StringWriter : StringWriter
    {
        public override Encoding Encoding
        {
            get { return Encoding.UTF8; }
        }
    }

    static ProjectFileHook()
    {
        ProjectFilesGenerator.ProjectFileGeneration += (string name, string content) =>
        {
            // parse the document and make some changes
            var document = XDocument.Parse(content);
            document.Root.Add(new XComment("FIX ME"));

            // save the changes using the Utf8StringWriter
            var str = new Utf8StringWriter();
            document.Save(str);

            return str.ToString();
        };
    }
}
#endif
```

## <a name="see-also"></a>Viz také
 [Příklad: Zpětné volání protokolu](../cross-platform/share-the-unity-log-callback-with-vstu.md)
