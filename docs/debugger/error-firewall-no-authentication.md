---
title: Firewall bez ověřování | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.firewall.noauth
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
ms.openlocfilehash: a8548880df8c69fa59d58bf4c13f7f547ad359bd
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852716"
---
# <a name="error-firewall-no-authentication"></a>Chyba: Bez ověřování brány firewall
Brána firewall pro připojení k Internetu na vzdáleném počítači není nastavená tak, aby povolovala vzdálené ladění. Pro vzdálené ladění pomocí `No Authentication` musí být do seznamu výjimek přidány msvsmon.exe. Otevírání některých portů IPSEC může být také nutné.

> [!NOTE]
> Vzdálený ladicí program dokáže automaticky nakonfigurovat bránu Windows Firewall. Při použití jiné brány firewall než brány Windows Firewall, například brány firewall pro software třetí strany nebo hardwarové brány firewall, je nutné bránu firewall ručně nakonfigurovat tak, aby povolovala vzdálené ladění. Provedete to tak, že povolíte provoz na portech TCP/IP, na kterých msvsmon.exe naslouchá. Ve výchozím nastavení se jedná o port 4018 a 4019, kde 4018 se používá ve všech operačních systémech a 4019 se používá jenom v systému Windows x64, aby bylo možné ladit procesy x86.

 Další informace najdete v tématu [vzdálené ladění](../debugger/remote-debugging.md).