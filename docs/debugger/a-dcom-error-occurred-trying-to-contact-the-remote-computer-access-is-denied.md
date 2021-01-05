---
title: Při pokusu o spojení se vzdáleným počítačem došlo k chybě modelu DCOM. Přístup byl zamítnut.
titleSuffix: ''
description: "' Při pokusu o kontaktování vzdáleného počítače došlo k chybě modelu DCOM. Přístup byl odepřen. ' Zobrazit informace o tomto odkazu na chybu vzdáleného ladění sady Visual Studio."
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.remote.dcom_access_denied
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, DCOM error
- remote DCOM access denied error
- DCOM, access errors
ms.assetid: 9d7dfc1b-9fe0-4f54-9c50-9c0e0f8358c5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c430462a224cb4604c09984a5397e540ce752b8a
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729194"
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>Při pokusu o spojení se vzdáleným počítačem došlo k chybě modelu DCOM. Přístup byl zamítnut.
Vzdálené ladění používá model DCOM ke komunikaci mezi místními a vzdálenými počítači v následujících situacích:

- Ladicí program je nastaven na **nativní režim kompatibility** nebo **spravovaný režim kompatibility** je zaškrtnutý na stránce **nástroje > možnosti > ladění** .

- Ladíte spravovaný kód C++ (C++/CLI).

- Pokud je v Visual Studio 2013 zaškrtnuto políčko **Povolit nativní úpravy a pokračování** , na stránce **nástroje > možnosti > ladění**

- Některé scénáře ladění třetích stran

  K této chybě dochází, pokud se proces sady Visual Studio nemůže sám ověřit (nebo poskytnutá pověření byla považována za nedostatečná) k procesu vzdáleného ladicího programu přes model DCOM. Problém může vyřešit nejméně jedno z následujících řešení:

- Vypněte  **režim nativní kompatibility** a **spravovaný režim kompatibility**.

- V Visual Studio 2013 vypněte **možnost Povolit nativní úpravy a pokračovat**.

- Restartujte oba počítače.

- Pokud vzdálené ladění vyžaduje zadání přihlašovacích údajů, ověřte možnost uložit přihlašovací údaje.

## <a name="see-also"></a>Viz také

- [Chyby vzdáleného ladění a řešení potíží](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Vzdálené ladění](../debugger/remote-debugging.md)