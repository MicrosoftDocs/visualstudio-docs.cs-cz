---
title: Brána firewall v místním počítači | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.firewall.localmachine
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b729c3e7e82a13d86aed16dfb52fda6864aa7f9
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852703"
---
# <a name="error-firewall-on-local-machine"></a>Chyba: Brána firewall v místním počítači
Brána firewall pro připojení k Internetu v místním počítači, ze kterého se spouští sada Visual Studio, není nastavená tak, aby povolovala vzdálené ladění. Pro spravované nebo nativní vzdálené ladění s výchozím přenosem musí být port TCP 135 otevřený pro přenosy modelu DCOM. Sdílení souborů a tiskáren musí být otevřené a devenv.exe musí být přidány do seznamu výjimek. Otevírání některých portů IPSEC může být také nutné.

 Další informace najdete v tématu [vzdálené ladění](../debugger/remote-debugging.md).