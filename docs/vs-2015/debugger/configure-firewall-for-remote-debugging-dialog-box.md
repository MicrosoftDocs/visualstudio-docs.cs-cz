---
title: Dialogové okno Konfigurace brány firewall pro vzdálené ladění | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.firewallconfiguration
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- Configure Firewall for Remote Debugging dialog box
- remote debugging, configuring firewalls
- firewalls, configuring for remote debugging
ms.assetid: 5dff3393-fdeb-4129-a2f6-31f653107a82
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 26e2b1300feb8d2a15e63089ee9bddde5f2d1ef4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702288"
---
# <a name="configure-firewall-for-remote-debugging-dialog-box"></a>Dialogové okno Konfigurace brány firewall pro vzdálené ladění
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto dialogové okno se zobrazí, když brána Windows Firewall zablokuje ladicí program, aby přijímal informace prostřednictvím sítě. Chcete-li pokračovat ve vzdáleném ladění, je nutné otevřít díru v bráně firewall, aby ladicí program mohl získat informace.  
  
> [!CAUTION]
> Otevření otvoru v bráně firewall může váš počítač vystavit bezpečnostním hrozbám, které je brána firewall navržená k blokování. Otevření díry pro vzdálené ladění odblokuje porty 4020 a 4021 v aplikaci Visual Studio 2015. V jiných verzích sady Visual Studio se používají další čísla portů. Další informace najdete v tématu [Přiřazení portů vzdáleného ladicího programu](../debugger/remote-debugger-port-assignments.md). Kromě toho umožňuje ladicímu programu otevřít další porty. Další informace najdete v tématu [Konfigurace brány Windows Firewall pro vzdálené ladění](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 **Zrušit vzdálené ladění**  
 Zruší pokus o vzdálené ladění. Nastavení zabezpečení vašeho počítače zůstane beze změny.  
  
 **Odblokovat vzdálené ladění z počítačů v místní síti (podsíti)**  
 Umožňuje vzdálené ladění počítačů v místní podsíti. To může v počítačích v místní podsíti otevřít ohrožení zabezpečení, ale brána firewall nadále zablokuje informace přicházející mimo podsíť.  
  
 **Odblokovat vzdálené ladění z libovolného počítače**  
 Umožňuje vzdálené ladění počítačů kdekoli v síti. Toto nastavení je nejnižší zabezpečení.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [Nastavení nástrojů Remote Tools na zařízení](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)   
 [Ladění odkazu uživatelského rozhraní](../debugger/debugging-user-interface-reference.md)
