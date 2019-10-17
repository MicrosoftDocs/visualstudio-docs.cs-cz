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
ms.openlocfilehash: 7f772b74a42b9704f1fd77c731022ddb44774c68
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72430678"
---
# <a name="enabling-debug-features-in-c-projects-d_debug"></a>Povolení funkcí ladění v C++ projektech (/D_DEBUG)
V [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], funkce ladění, jako jsou kontrolní výrazy, jsou povoleny při kompilaci programu s definovaným symbolem **_DEBUG** . **_DEBUG** můžete definovat jedním ze dvou způsobů:

- Zadejte **#define _DEBUG** ve zdrojovém kódu nebo

- Zadejte možnost kompilátoru **/D_DEBUG** . (Při vytváření projektu v aplikaci Visual Studio pomocí průvodců je **/D_DEBUG** definován automaticky v konfiguraci ladění.)

  Když je definována **_DEBUG** , kompilátor zkompiluje oddíly kódu, které jsou obklopeny **#ifdef _DEBUG** a `#endif`.

  Konfigurace ladění programu knihovny MFC musí být propojena s ladicí verzí knihovny MFC. Soubory hlaviček knihovny MFC určují správnou verzi knihovny MFC, která se má propojit, na základě symbolů, které jste definovali, jako je například **_DEBUG** a **_UNICODE**. Podrobnosti najdete v tématu [verze knihovny MFC](/cpp/mfc/mfc-library-versions).

## <a name="see-also"></a>Viz také
- [Ladění nativního kódu](../debugger/debugging-native-code.md)
- [Nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)