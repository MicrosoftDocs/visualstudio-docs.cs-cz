---
title: 'Postupy: použití nativních kontrol za běhu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- c.runtime.errorchecks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
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
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4efbb4e151ea47f655f0b28e19d2811d5541e944
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51798752"
---
# <a name="how-to-use-native-run-time-checks"></a>Postupy: Použití nativních kontrol za běhu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V jazyce Visual C++, můžete použít nativní [runtime_checks –](http://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b) zachytit běžné chyby za běhu, jako:  
  
- Poškození ukazatele zásobníku.  
  
- Přetečení místního pole.  
  
- Poškození zásobníku.  
  
- Závislostí na neinicializovaných místních proměnných.  
  
- Ztráta dat na přiřazení k proměnné kratší.  
  
  Pokud používáte **/RTC** s optimalizované (**/O**) výsledky Chyba kompilátoru sestavení. Pokud používáte `runtime_checks` direktivy pragma v optimalizovaných sestavení, direktivy pragma nemá žádný vliv.  
  
  Když ladíte program, který má povolené kontroly za běhu, je výchozí akce pro program a řízení ladicímu programu, když dojde k chybě za běhu. Můžete změnit toto výchozí chování pro všechny kontroly za běhu. Další informace najdete v tématu [Správa výjimek pomocí ladicího programu](../debugger/managing-exceptions-with-the-debugger.md).  
  
  Následující postupy popisují, jak povolit nativní kontroly za běhu v sestavení pro ladění a jak změnit chování nativní kontroly za běhu.  
  
  Další témata v této části obsahují informace:  
  
- [Přizpůsobení Run-Time zkontroluje knihovny Run-Time jazyka C](../debugger/native-run-time-checks-customization.md)  
  
- [Pomocí za běhu bez běhové knihovny jazyka C kontrol](../debugger/using-run-time-checks-without-the-c-run-time-library.md)  
  
### <a name="to-enable-native-run-time-checks-in-a-debug-build"></a>K povolení nativních kontrol za běhu v sestavení pro ladění  
  
-   Použití **/RTC** možnost a propojení s ladicí verzí knihovny run-time jazyka C (/ MDd, například).  
  
### <a name="to-modify-native-run-time-check-behavior"></a>Jestliže chcete upravit chování nativní kontroly za běhu  
  
-   Použití `runtime_checks` direktivy pragma.  
  
## <a name="see-also"></a>Viz také  
 [Ladění v sadě Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [runtime_checks –](http://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b)   
 [Kontrola chyb za běhu](http://msdn.microsoft.com/library/c965dd01-57ad-4a3c-b1d6-5aa04f920501)





