---
title: Povolení funkcí ladění v Visual C++ (-D_DEBUG) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- /D_DEBUG compiler option [C++]
- debugging [C++], enabling debug features
- debugging [MFC], enabling debug features
- assertions, enabling debug features
- D_DEBUG compiler option
- MFC libraries, debug version
- debug builds, MFC
- _DEBUG macro
ms.assetid: 276e2254-7274-435e-ba4d-67fcef4f33bc
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cffa8592c2048c6c6b39eee5c4ca654c41448933
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686707"
---
# <a name="enabling-debug-features-in-visual-c-d_debug"></a>Povolení funkcí ladění v jazyce Visual C++ (/D_DEBUG)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V nástroji [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] jsou funkce ladění, jako jsou kontrolní výrazy, povoleny při kompilování programu s definovaným symbolem **_DEBUG** . **_DEBUG** můžete definovat jedním ze dvou způsobů:  
  
- Zadejte **#define _DEBUG** ve zdrojovém kódu nebo  
  
- Zadejte možnost kompilátoru **/D_DEBUG** . (Pokud vytvoříte projekt v aplikaci Visual Studio pomocí průvodců, **/D_DEBUG** je definována automaticky v konfiguraci ladění.)  
  
  Při definování **_DEBUG** Kompilátor zkompiluje oddíly kódu obklopené **#ifdef _DEBUG** a `#endif` .  
  
  Konfigurace ladění programu knihovny MFC musí být propojena s ladicí verzí knihovny MFC. Soubory hlaviček knihovny MFC určují správnou verzi knihovny MFC, která se má propojit, na základě symbolů, které jste definovali, například **_DEBUG** a **_UNICODE**. Podrobnosti najdete v tématu [verze knihovny MFC](https://msdn.microsoft.com/library/3d7a8ae1-e276-4cf8-ba63-360c2f85ad0e).  
  
## <a name="see-also"></a>Viz také  
 [Ladění nativního kódu](../debugger/debugging-native-code.md)   
 [Nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
