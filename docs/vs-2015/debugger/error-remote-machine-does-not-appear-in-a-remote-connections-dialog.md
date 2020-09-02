---
title: 'Chyba: vzdálený počítač se nezobrazuje v dialogovém okně vzdálené připojení | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 5fd98a5b-2cf3-4438-8b0f-6f1a742a62ce
caps.latest.revision: 5
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a97211c1fa86123a2a7a65f2ff86b0cecac957dc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697317"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>Chyba: Vzdálený počítač se nezobrazuje v dialogovém okně Vzdálená připojení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud se vzdálený počítač nezobrazí v dialogovém okně Vzdálená připojení, Projděte si následující běžné příčiny.  
  
 Pokud používáte spravovaný režim kompatibility, podívejte se prosím do dokumentace k sadě Visual Studio 2010: [řešení potíží se vzdáleným laděním – Visual Studio 2010](https://msdn.microsoft.com/library/2ys11ead\(v=vs.100\).aspx) .  
  
### <a name="common-causes-for-this-error"></a>Běžné příčiny této chyby  
  
- Vzdálený počítač běží na počítači, který je v jiné podsíti. Pokud to chcete opravit, ručně zadejte název počítače nebo IP adresu v dialogu kvalifikátor.  
  
- Vzdálený ladicí program na vzdáleném počítači neběží. Chcete-li tento problém vyřešit, spusťte vzdálený ladicí program.  
  
- Brána firewall blokuje komunikaci mezi Visual Studio a vzdáleným počítačem. Pokud to chcete opravit, nakonfigurujte bránu firewall tak, aby umožňovala aplikaci Visual Studio a vzdálený ladicí program (Msvsmon) komunikovat.  
  
- Antivirový software blokuje komunikaci mezi Visual Studio a vzdáleným počítačem. Pokud to chcete opravit, nakonfigurujte antivirový software tak, aby umožňoval aplikaci Visual Studio a vzdálený ladicí program (Msvsmon) komunikovat.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení nástrojů Remote Tools na zařízení](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
