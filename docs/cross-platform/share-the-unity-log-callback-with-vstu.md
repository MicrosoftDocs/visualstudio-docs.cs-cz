---
title: Sdílení zpětného volání protokolu Unity s VSTU | Microsoft Docs
ms.custom: ''
ms.date: 07/26/2018
ms.technology: vs-unity-tools
ms.topic: how-to
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: dc54c51f078e5b800a9cc9f2de687db7b1fa0387
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815041"
---
# <a name="share-the-unity-log-callback-with-vstu"></a>Sdílení zpětného volání protokolu Unity s VSTU
Visual Studio Tools for Unity zaregistruje zpětné volání protokolu s Unity, aby bylo možné streamovat svou konzolu do sady Visual Studio. Pokud vaše skripty v editoru také zaregistrují zpětné volání protokolu pomocí Unity, může zpětné volání VSTU kolidovat s vaším zpětným voláním. Chcete-li této možnosti zabránit, použijte `VisualStudioIntegration.LogCallback` událost ke spolupráci s VSTU.

## <a name="demonstrates"></a>Demonstruje
 Postup sdílení zpětného volání protokolu Unity vytvořeného nástrojem Visual Studio Tools for Unity.

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
 [Příklad: generování souboru projektu](../cross-platform/customize-project-files-created-by-vstu.md)
