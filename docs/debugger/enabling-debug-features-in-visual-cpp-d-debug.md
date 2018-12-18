---
title: Povolení funkcí ladění v jazyce Visual C++ (-D_DEBUG) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 772467caf74a381fc2ef5cc74e8e31bf2ff0503c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949614"
---
# <a name="enabling-debug-features-in-visual-c-ddebug"></a>Povolení funkcí ladění v jazyce Visual C++ (/D_DEBUG)
V [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], funkce ladění, jako je kontrolní výrazy jsou povolené při kompilaci programu symbol **_DEBUG** definované. Můžete definovat **_DEBUG** v jednom ze dvou způsobů:  
  
- Zadejte **#define _DEBUG** ve zdrojovém kódu, nebo  
  
- Zadejte **/D_DEBUG** – možnost kompilátoru. (Pokud vytváříte projekt v sadě Visual Studio pomocí průvodců **/D_DEBUG** je automaticky definovaný v konfiguraci ladění.)  
  
  Když **_DEBUG** je definován, kompilátor zkompiluje částech kód obklopený **#ifdef _DEBUG** a `#endif`.  
  
  Konfigurace ladění pro aplikace MFC je třeba propojit s ladicí verzí knihovny MFC. Soubory hlaviček knihovny MFC určit správnou verzi knihovny MFC pro propojení s založený na symboly, které jste definovali, jako například **_DEBUG** a **_UNICODE**. Podrobnosti najdete v tématu [MFC – knihovní verze](/cpp/mfc/mfc-library-versions).  
  
## <a name="see-also"></a>Viz také  
 [Ladění nativního kódu](../debugger/debugging-native-code.md)   
 [Nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)