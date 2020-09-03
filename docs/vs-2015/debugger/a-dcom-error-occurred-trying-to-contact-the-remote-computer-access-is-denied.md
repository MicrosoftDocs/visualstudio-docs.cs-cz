---
title: Při pokusu o spojení se vzdáleným počítačem došlo k chybě modelu DCOM. Přístup byl zamítnut. | Dokumentace Microsoftu
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.dcom_access_denied
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, DCOM error
- remote DCOM access denied error
- DCOM, access errors
ms.assetid: 9d7dfc1b-9fe0-4f54-9c50-9c0e0f8358c5
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0157b1ade2c38a2c10920b9674d7c9a58ac036b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156534"
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>Při pokusu o spojení se vzdáleným počítačem došlo k chybě modelu DCOM. Přístup byl zamítnut.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vzdálené ladění používá model DCOM ke komunikaci mezi místními a vzdálenými počítači v následujících situacích:  
  
- Ladicí program je nastaven na **nativní režim kompatibility** nebo na stránce **Nástroje/možnosti/ladění** je zaškrtnuté políčko **spravovaný režim** kompatibility.  
  
- Ladíte spravovaný kód C++ (C++/CLI).  
  
- V Visual Studio 2013 platí, že když je **možnost Povolit nativní úpravy a pokračování** zaškrtnutá, na stránce **Nástroje/možnosti/ladění**  
  
- Některé scénáře ladění třetích stran  
  
  K této chybě dochází, pokud se proces sady Visual Studio nemůže sám ověřit (nebo poskytnutá pověření byla považována za nedostatečná) k procesu vzdáleného ladicího programu přes model DCOM. Problém může vyřešit nejméně jedno z následujících řešení:  
  
- Vypněte  **režim nativní kompatibility** a **spravovaný režim kompatibility**.  
  
- V Visual Studio 2013 vypněte **možnost Povolit nativní úpravy a pokračovat**.  
  
- Restartujte oba počítače.  
  
- Pokud vzdálené ladění vyžaduje zadání přihlašovacích údajů, ověřte možnost uložit přihlašovací údaje.  
  
## <a name="see-also"></a>Viz také  
 [Chyby vzdáleného ladění a řešení potíží](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Vzdálené ladění](../debugger/remote-debugging.md)
