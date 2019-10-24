---
title: Povolení funkcí ladění v C++ projektech (-D_DEBUG) | Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 19d341cba47e0a3d2259cc57d239c63420095347
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737959"
---
# <a name="enabling-debug-features-in-c-projects-d_debug"></a>Povolení funkcí ladění v C++ projektech (/D_DEBUG)
V [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] jsou při kompilování programu s definovaným symbolem **_DEBUG** povoleny ladění funkcí, jako jsou kontrolní výrazy. **_DEBUG** můžete definovat jedním ze dvou způsobů:

- Zadejte **#define _DEBUG** ve zdrojovém kódu nebo

- Zadejte možnost kompilátoru **/D_DEBUG** . (Při vytváření projektu v aplikaci Visual Studio pomocí průvodců je **/D_DEBUG** definován automaticky v konfiguraci ladění.)

  Když je definována **_DEBUG** , kompilátor zkompiluje oddíly kódu, které jsou obklopeny **#ifdef _DEBUG** a `#endif`.

  Konfigurace ladění programu knihovny MFC musí být propojena s ladicí verzí knihovny MFC. Soubory hlaviček knihovny MFC určují správnou verzi knihovny MFC, která se má propojit, na základě symbolů, které jste definovali, jako je například **_DEBUG** a **_UNICODE**. Podrobnosti najdete v tématu [verze knihovny MFC](/cpp/mfc/mfc-library-versions).

## <a name="see-also"></a>Viz také:
- [Ladění nativního kódu](../debugger/debugging-native-code.md)
- [Nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)