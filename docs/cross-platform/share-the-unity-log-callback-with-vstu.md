---
title: Sdílení volání protokolu Unity s VSTU | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62815662"
---
# <a name="share-the-unity-log-callback-with-vstu"></a>Sdílení zpětného volání protokolu Unity s VSTU
Visual Studio Tools for Unity zaregistruje zpětné volání protokolu s Unity, aby bylo možné streamovat jeho konzole do sady Visual Studio. Pokud skripty editoru také zaregistrovat zpětné volání protokolu s Unity, zpětné volání VSTU může narušit zpětné volání. Chcete-li této možnosti zabránit, použijte `VisualStudioIntegration.LogCallback` událost ke spolupráci s VSTU.

## <a name="demonstrates"></a>Demonstruje
 Jak sdílet volání protokolu Unity vytvořené Visual Studio Nástroje pro jednotu.

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

## <a name="see-also"></a>Viz také
 [Příklad: Generování souboru projektu](../cross-platform/customize-project-files-created-by-vstu.md)
