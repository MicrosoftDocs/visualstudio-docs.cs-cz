---
title: Sdílení zpětného volání protokolu Unity s VSTU | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
caps.latest.revision: 5
author: conceptdev
ms.author: crdun
manager: jillfra
ms.openlocfilehash: b58d693980ffc55ccfe613d52e868bccca9908b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145738"
---
# <a name="share-the-unity-log-callback-with-vstu"></a>Sdílení zpětného volání protokolu Unity s VSTU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio Tools for Unity zaregistruje zpětné volání protokolu s Unity, aby bylo možné streamovat svou konzolu do sady Visual Studio. Pokud vaše skripty v editoru také zaregistrují zpětné volání protokolu pomocí Unity, může zpětné volání VSTU kolidovat s vaším zpětným voláním. Chcete-li této možnosti zabránit, použijte `VisualStudioIntegration.LogCallback` událost ke spolupráci s VSTU.  
  
## <a name="demonstrates"></a>Demonstruje  
 Postup sdílení zpětného volání protokolu Unity vytvořeného nástrojem Visual Studio Tools for Unity.  
  
## <a name="example"></a>Příklad  
  
```csharp  
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
```  
  
## <a name="see-also"></a>Viz také  
 [Příklad: Generování souboru projektu](../cross-platform/customize-project-files-created-by-vstu.md)
