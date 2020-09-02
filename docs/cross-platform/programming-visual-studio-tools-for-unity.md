---
title: Visual Studio Tools for Unity programování | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: a5758cb0-e73b-45f5-8cae-c0eb40491026
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 0811445e2dcf985aef7b6449ff3fb86c5ac9a1c8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62818212"
---
# <a name="program-visual-studio-tools-for-unity"></a>Programování Visual Studio Tools for Unity
V této části najdete příklady použití rozhraní Visual Studio Tools for Unity API.

## <a name="examples"></a>Příklady
 Tady je několik příkladů, které ukazují, jak můžete používat rozhraní Visual Studio Tools for Unity API.

### <a name="customize-project-files-created-by-vstu"></a>Přizpůsobení souborů projektu vytvořených pomocí VSTU
 Visual Studio Tools for Unity poskytuje zpětné volání ve stylu Unity během generování souboru projektu. Informace o tom, jak můžete upravit soubor projektu vždy, když je znovu vygenerován, naleznete v tématu [Příklad: generování souboru projektu](../cross-platform/customize-project-files-created-by-vstu.md).

### <a name="share-the-unity-log-callback-with-vstu"></a>Sdílení zpětného volání protokolu Unity s VSTU
 Visual Studio Tools for Unity zaregistruje zpětné volání protokolu s Unity, aby bylo možné streamovat svou konzolu do sady Visual Studio. Pokud vaše skripty v editoru také zaregistrují zpětné volání protokolu v Unity, může s ním narušit zpětné volání VSTU. Další informace o tom, jak můžete sdílet zpětné volání protokolu Unity pomocí VSTU, najdete v tématu [Příklad: zpětné volání protokolu](../cross-platform/share-the-unity-log-callback-with-vstu.md).
