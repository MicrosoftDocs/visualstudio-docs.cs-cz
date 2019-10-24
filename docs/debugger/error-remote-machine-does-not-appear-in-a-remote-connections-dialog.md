---
title: 'Chyba: vzdálený počítač se nezobrazuje v dialogovém okně vzdálené připojení | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
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
ms.openlocfilehash: e7d76bf1a889f7c91ced6b85ce16ebeb6e9a1b75
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737516"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>Chyba: vzdálený počítač se nezobrazuje v dialogovém okně vzdálené připojení.
Pokud se vzdálený počítač nezobrazí v dialogovém okně Vzdálená připojení, Projděte si následující běžné příčiny.

 Pokud používáte spravovaný režim kompatibility, podívejte se prosím do dokumentace k sadě Visual Studio 2010: [řešení potíží se vzdáleným laděním – Visual Studio 2010](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/2ys11ead(v=vs.100)).

### <a name="common-causes-for-this-error"></a>Běžné příčiny této chyby

- Vzdálený počítač běží na počítači, který je v jiné podsíti. Pokud to chcete opravit, ručně zadejte název počítače nebo IP adresu v dialogu kvalifikátor.

- Vzdálený ladicí program na vzdáleném počítači neběží. Chcete-li tento problém vyřešit, spusťte vzdálený ladicí program.

- Brána firewall blokuje komunikaci mezi Visual Studio a vzdáleným počítačem. Pokud to chcete opravit, nakonfigurujte bránu firewall tak, aby umožňovala aplikaci Visual Studio a vzdálený ladicí program (Msvsmon) komunikovat.

- Antivirový software blokuje komunikaci mezi Visual Studio a vzdáleným počítačem. Pokud to chcete opravit, nakonfigurujte antivirový software tak, aby umožňoval aplikaci Visual Studio a vzdálený ladicí program (Msvsmon) komunikovat.

## <a name="see-also"></a>Viz také:
- [Vzdálené ladění](../debugger/remote-debugging.md)