---
title: Visual Studio Tools for Unity programování | Microsoft Docs
description: Podívejte se na příklady programování pomocí rozhraní API Visual Studio Tools for Unity (VSTU). Přizpůsobení souborů projektu vytvořených pomocí VSTU. Sdílení zpětného volání protokolu Unity s VSTU
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
ms.openlocfilehash: 0372cfd110df77867a683b27b17f92cd70ba75aa
ms.sourcegitcommit: 01c1b040b12d9d43e3e8ccadee20d6282154faad
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/14/2020
ms.locfileid: "92039882"
---
# <a name="program-visual-studio-tools-for-unity"></a>Programování Visual Studio Tools for Unity
V této části najdete příklady použití rozhraní Visual Studio Tools for Unity API.

## <a name="examples"></a>Příklady
 Tady je několik příkladů, které ukazují, jak můžete používat rozhraní Visual Studio Tools for Unity API.

### <a name="customize-project-files-created-by-vstu"></a>Přizpůsobení souborů projektu vytvořených pomocí VSTU
 Visual Studio Tools for Unity poskytuje zpětné volání ve stylu Unity během generování souboru projektu. Informace o tom, jak můžete upravit soubor projektu vždy, když je znovu vygenerován, naleznete v tématu [Příklad: generování souboru projektu](../cross-platform/customize-project-files-created-by-vstu.md).

### <a name="share-the-unity-log-callback-with-vstu"></a>Sdílení zpětného volání protokolu Unity s VSTU
 Visual Studio Tools for Unity zaregistruje zpětné volání protokolu s Unity, aby bylo možné streamovat svou konzolu do sady Visual Studio. Pokud vaše skripty v editoru také zaregistrují zpětné volání protokolu v Unity, může s ním narušit zpětné volání VSTU. Další informace o tom, jak můžete sdílet zpětné volání protokolu Unity pomocí VSTU, najdete v tématu [Příklad: zpětné volání protokolu](../cross-platform/share-the-unity-log-callback-with-vstu.md).
