---
title: 'Chyba: bez ověřování brány firewall | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.firewall.noauth
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: dda1acb8-bed7-4bc8-9991-9cdc49c2ac1e
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: db13165c584399952dc491cf714ac84ee4de7598
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697430"
---
# <a name="error-firewall-no-authentication"></a>Chyba: Bez ověřování brány firewall
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Brána firewall pro připojení k Internetu na vzdáleném počítači není nastavená tak, aby povolovala vzdálené ladění. Pro vzdálené ladění pomocí `No Authentication` musí být do seznamu výjimek přidány msvsmon.exe. Otevírání některých portů IPSEC může být také nutné.  
  
> [!NOTE]
> Vzdálený ladicí program dokáže automaticky nakonfigurovat bránu Windows Firewall. Při použití jiné brány firewall než brány Windows Firewall, například brány firewall pro software třetí strany nebo hardwarové brány firewall, je nutné bránu firewall ručně nakonfigurovat tak, aby povolovala vzdálené ladění. Provedete to tak, že povolíte provoz na portech TCP/IP, na kterých msvsmon.exe naslouchá. Ve výchozím nastavení se jedná o port 4018 a 4019, kde 4018 se používá ve všech operačních systémech a 4019 se používá jenom v systému Windows x64, aby bylo možné ladit procesy x86.  
  
 Další informace najdete v tématu [nastavení nástrojů Remote Tools na zařízení](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).
