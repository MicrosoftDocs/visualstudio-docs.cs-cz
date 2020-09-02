---
title: Povolení funkcí ladění v projektech C++ (-D_DEBUG) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72737959"
---
# <a name="enabling-debug-features-in-c-projects-d_debug"></a>Povolení funkcí ladění v projektech C++ (/D_DEBUG)
V nástroji [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] jsou funkce ladění, jako jsou kontrolní výrazy, povoleny při kompilování programu s definovaným symbolem **_DEBUG** . **_DEBUG** můžete definovat jedním ze dvou způsobů:

- Zadejte **#define _DEBUG** ve zdrojovém kódu nebo

- Zadejte možnost kompilátoru **/D_DEBUG** . (Pokud vytvoříte projekt v aplikaci Visual Studio pomocí průvodců, **/D_DEBUG** je definována automaticky v konfiguraci ladění.)

  Při definování **_DEBUG** Kompilátor zkompiluje oddíly kódu obklopené **#ifdef _DEBUG** a `#endif` .

  Konfigurace ladění programu knihovny MFC musí být propojena s ladicí verzí knihovny MFC. Soubory hlaviček knihovny MFC určují správnou verzi knihovny MFC, která se má propojit, na základě symbolů, které jste definovali, například **_DEBUG** a **_UNICODE**. Podrobnosti najdete v tématu [verze knihovny MFC](/cpp/mfc/mfc-library-versions).

## <a name="see-also"></a>Viz také
- [Ladění nativního kódu](../debugger/debugging-native-code.md)
- [Nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)