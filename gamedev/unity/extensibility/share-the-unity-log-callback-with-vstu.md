---
title: Sdílení zpětného volání protokolu Unity s VSTU | Microsoft Docs
description: Sdílejte své zpětné volání protokolu Unity s rozhraním, které je zaregistrované ve službě Visual Studio Tools for Unity (VSTU), a zasílat ho do služby Visual Studio.
ms.custom: ''
ms.date: 07/26/2018
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: how-to
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: a1f4e7be068a152fc76c95160bdc7930f61e1f74
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2020
ms.locfileid: "94341663"
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

## <a name="see-also"></a>Viz také
 [Příklad: generování souboru projektu](./customize-project-files-created-by-vstu.md)
