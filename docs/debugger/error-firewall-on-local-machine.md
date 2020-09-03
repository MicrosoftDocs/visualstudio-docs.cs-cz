---
title: 'Chyba: Brána firewall v místním počítači | Microsoft Docs'
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
ms.openlocfilehash: 115546a0fd3a9aad804391816ce8bac88429d0ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85460749"
---
# <a name="error-firewall-on-local-machine"></a>Chyba: Brána firewall v místním počítači
Brána firewall pro připojení k Internetu v místním počítači, ze kterého se spouští sada Visual Studio, není nastavená tak, aby povolovala vzdálené ladění. Pro spravované nebo nativní vzdálené ladění s výchozím přenosem musí být port TCP 135 otevřený pro přenosy modelu DCOM. Sdílení souborů a tiskáren musí být otevřené a devenv.exe musí být přidány do seznamu výjimek. Otevírání některých portů IPSEC může být také nutné.

 Další informace najdete v tématu [vzdálené ladění](../debugger/remote-debugging.md).