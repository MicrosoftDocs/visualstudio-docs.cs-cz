---
description: Brána firewall pro připojení k Internetu v místním počítači, ze kterého se spouští sada Visual Studio, není nastavená tak, aby povolovala vzdálené ladění.
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bad1dcbfa2dd80ade46bd0e848e3c1f186f3c903
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146962"
---
# <a name="error-firewall-on-local-machine"></a>Chyba: Brána firewall v místním počítači
Brána firewall pro připojení k Internetu v místním počítači, ze kterého se spouští sada Visual Studio, není nastavená tak, aby povolovala vzdálené ladění. Pro spravované nebo nativní vzdálené ladění s výchozím přenosem musí být port TCP 135 otevřený pro přenosy modelu DCOM. Sdílení souborů a tiskáren musí být otevřené a devenv.exe musí být přidány do seznamu výjimek. Otevírání některých portů IPSEC může být také nutné.

 Další informace najdete v tématu [vzdálené ladění](../debugger/remote-debugging.md).
