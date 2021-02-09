---
title: Povolení funkcí ladění v projektech C++ (-D_DEBUG) | Microsoft Docs
description: V Visual C++ povolíte funkce ladění definováním _DEBUG. Přečtěte si, jak to provést, a Naučte se, jak propojit program knihovny MFC, aby ho bylo možné ladit.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: c0a8941fbda263ce3a2345a135594d2f9eec87e9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871894"
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