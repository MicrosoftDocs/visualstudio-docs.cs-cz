---
title: Sdílení zpětného volání protokolu Unity s VSTU | Dokumentace Microsoftu
ms.custom: ''
ms.date: 07/26/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: aa8a4a229102a6a9439ffb36582cd03e322a086b
ms.sourcegitcommit: 5c049194fa256b876ad303f491af11edd505756c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53027195"
---
# <a name="share-the-unity-log-callback-with-vstu"></a>Sdílení zpětného volání protokolu Unity s VSTU
Visual Studio Tools for Unity zaregistruje zpětné volání protokolu Unity Streamovat konzoly do sady Visual Studio. Pokud editor skriptů také zaregistrovat zpětné volání protokolu Unity, zpětné volání VSTU může narušit zpětného volání. Aby tato možnost, použijte `VisualStudioIntegration.LogCallback` události spolupracovat s VSTU.

## <a name="demonstrates"></a>Demonstruje
 Jak sdílet zpětného volání protokolu Unity, vytvoří Visual Studio Tools for Unity.

## <a name="example"></a>Příklad

```csharp
#if ENABLE_VSTU
using System;

using UnityEngine;
using UnityEditor;

using SyntaxTree.VisualStudio.Unity.Bridge;

[InitializeOnLoad]
public class LogCallbackHook
{
    static LogCallbackHook()
    {
        VisualStudioIntegration.LogCallback += (string condition, string trace, LogType type) =>
        {
            // place code that implements your log callback here
        };
    }
}
#endif
```

## <a name="see-also"></a>Viz také:
 [Příklad: Generování souboru projektu](../cross-platform/customize-project-files-created-by-vstu.md)
