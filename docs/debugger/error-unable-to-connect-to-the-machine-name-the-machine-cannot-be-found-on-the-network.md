---
title: 'Chyba: Nelze se připojit k počítači &lt;název&gt;. Počítač nebyl nalezen v síti. | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.remote.dcom_disabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DCOM, unable to connect error
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3e0654148823d40277bdd9c6b6d8ec5b881fdb80
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31480056"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Chyba: Nelze se připojit k počítači &lt;název&gt;. Počítač nebyl nalezen v síti.
K tomuto chování dochází, pokud platí jedna z následujících podmínek:  
  
-   Připojení ke vzdálenému počítači bylo přerušeno.  
  
-   Váš uživatelský účet na vzdáleném počítači, je zakázán.  
  
-   Vypršela platnost hesla na vzdáleném počítači.  
  
### <a name="to-resolve-this-behavior"></a>Chcete-li toto chování  
  
-   Ujistěte se, že místní počítač a vzdáleného počítače jsou ve stejné síti. K tomu použijte Průzkumník systému Microsoft Windows (nebo Průzkumníka souborů) a zkuste to pro přístup ke vzdálenému počítači.  
  
     – a –  
  
-   Ujistěte se, že je povolena uživatelský účet, který používáte pro připojení ke vzdálenému počítači.  
  
     – a –  
  
-   Ujistěte se, zda je heslo, které používáte pro připojení ke vzdálenému počítači platný a zda nevypršela platnost.  
  
## <a name="see-also"></a>Viz také  
 [Vzdálené ladění](../debugger/remote-debugging.md)   
 [Nastavení ladicího programu a příprava](../debugger/debugger-settings-and-preparation.md)