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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d5f3e57bbac1d2c293c5a9f910beca5484db06cc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871590"
---
# <a name="error-firewall-on-local-machine"></a>Chyba: Brána firewall v místním počítači
Brána firewall pro připojení k Internetu v místním počítači, ze kterého se spouští sada Visual Studio, není nastavená tak, aby povolovala vzdálené ladění. Pro spravované nebo nativní vzdálené ladění s výchozím přenosem musí být port TCP 135 otevřený pro přenosy modelu DCOM. Sdílení souborů a tiskáren musí být otevřené a devenv.exe musí být přidány do seznamu výjimek. Otevírání některých portů IPSEC může být také nutné.

 Další informace najdete v tématu [vzdálené ladění](../debugger/remote-debugging.md).