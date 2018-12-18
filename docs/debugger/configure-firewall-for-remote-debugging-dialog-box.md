---
title: Konfigurace brány Firewall pro vzdálené ladění dialogové okno | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.firewallconfiguration
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Configure Firewall for Remote Debugging dialog box
- remote debugging, configuring firewalls
- firewalls, configuring for remote debugging
ms.assetid: 5dff3393-fdeb-4129-a2f6-31f653107a82
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 982e677639cec6a98ae3aafe3d0ae624df588ccd
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31459646"
---
# <a name="configure-firewall-for-remote-debugging-dialog-box"></a>Dialogové okno Konfigurace brány firewall pro vzdálené ladění
Toto dialogové okno se zobrazí, když brána Windows Firewall blokuje ladicí program příjem informací přes síť. Chcete-li pokračovat, vzdálené ladění, musíte otevřít díru v bráně firewall tak ladicího programu můžete získat informace.  
  
> [!CAUTION]
>  Otevírání díru v bráně Firewall může vystavit zabezpečení hrozeb, které brána Firewall je navržena pro blokování v počítači. Otevírání díru pro vzdálené ladění odblokuje porty 4020 a 4021 ve Visual Studiu 2015. V jiných verzích sady Visual Studio se používají jiné čísla portů. Další informace najdete v tématu [přiřazení portu vzdáleného ladicího programu](../debugger/remote-debugger-port-assignments.md). Kromě toho umožňuje ladicí program otevřít další porty. Další informace najdete v tématu [konfigurace brány Windows Firewall pro vzdálené ladění](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 **Zrušit vzdálené ladění**  
 Zruší požadavek na vzdáleného ladění. Nastavení zabezpečení počítače zůstanou beze změn.  
  
 **Odblokování vzdálené ladění z počítačů v místní sítě (podsítě)**  
 Umožňuje vzdálené ladění počítačů v místní podsíti. Otevře ohrožení zabezpečení počítače na místní podsíti, ale stále blokovat informace pocházející mimo podsíť brány firewall.  
  
 **Odblokování vzdálené ladění z libovolného počítače**  
 Umožňuje vzdálené ladění počítače kdekoli v síti. Toto nastavení je ta nejmíň zabezpečená.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [Vzdálené ladění](../debugger/remote-debugging.md)  
 [Ladění odkazu uživatelského rozhraní](../debugger/debugging-user-interface-reference.md)