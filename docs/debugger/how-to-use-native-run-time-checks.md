---
title: 'Postupy: použití nativních kontrol za běhu | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- c.runtime.errorchecks
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- /RTC compiler option [C++], /O compiler option
- run-time checks, native
- stack, pointer corruption
- stack pointers, corruption
- /O compiler option, /RTC option
- run-time errors, error checks
- O compiler option, /RTC option
- debugger, runtime errors
- variables [debugger], loss of data
- runtime_checks pragma
- variables [debugger], catching dependencies on uninitialized local variables
- run-time errors, debugging
- debugger, native run-time checks
- optimized build option
- RTC compiler option, /O compiler option
- native run-time checks
- run-time checks
- debugging arrays
- stack pointers
- arrays [Visual Studio], debugging
ms.assetid: dc7b2f1e-5ff6-42e0-89b3-dc9dead83ee1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 954cf8436a9f0653685b41920cad84698ae50abb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72732156"
---
# <a name="how-to-use-native-run-time-checks"></a>Postupy: Použití nativních kontrol za běhu
V projektu sady Visual C++ Studio můžete použít nativní [runtime_checks](/cpp/preprocessor/runtime-checks) k zachycení běžných chyb za běhu, jako například:

- Poškození ukazatele zásobníku

- Přetečení místních polí.

- Poškození zásobníku.

- Závislosti na neinicializovaných místních proměnných.

- Ztráta dat u přiřazení do kratší proměnné.

  Použijete-li **/RTC** s optimalizovaným sestavením ( **/o**), dojde k chybě kompilátoru. Použijete-li direktivu pragma `runtime_checks` v optimalizovaném sestavení, direktiva pragma nemá žádný vliv.

  Když ladíte program, který má povolenou kontrolu za běhu, je výchozí akcí pro program zastavení a přerušení ladicího programu v případě, že dojde k chybě za běhu. Toto výchozí chování můžete změnit pro jakoukoli kontrolu za běhu. Další informace naleznete v tématu [Správa výjimek pomocí ladicího programu](../debugger/managing-exceptions-with-the-debugger.md).

  Následující postupy popisují, jak povolit nativní kontroly za běhu v sestavení pro ladění a jak upravit chování při nativním běhu kontroly.

  Další témata v této části poskytují informace o:

- [Přizpůsobení kontrol za běhu pomocí knihovny run-time jazyka C](../debugger/native-run-time-checks-customization.md)

- [Použití kontrol za běhu bez běhové knihovny jazyka C](../debugger/using-run-time-checks-without-the-c-run-time-library.md)

### <a name="to-enable-native-run-time-checks-in-a-debug-build"></a>Povolení nativních kontrol za běhu v sestavení ladění

- Použijte možnost **/RTC** a propojte s ladicí verzí knihovny run-time jazyka C (například/MDD).

### <a name="to-modify-native-run-time-check-behavior"></a>Postup změny nativního chování při kontrole za běhu

- Použijte direktivu pragma `runtime_checks`.

## <a name="see-also"></a>Viz také:
- [Ladění v sadě Visual Studio](../debugger/index.yml)
- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
- [runtime_checks](/cpp/preprocessor/runtime-checks)
- [Kontrola chyb za běhu](/cpp/c-runtime-library/run-time-error-checking)