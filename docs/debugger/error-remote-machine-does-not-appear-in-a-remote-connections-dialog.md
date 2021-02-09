---
title: Vzdálený počítač se v dialogovém okně vzdálené připojení nezobrazí | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
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
ms.openlocfilehash: be39d733b2e5fe83fa9f7e2241c7de06980bb583
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871362"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>Chyba: Vzdálený počítač se nezobrazuje v dialogovém okně Vzdálená připojení
Pokud se vzdálený počítač nezobrazí v dialogovém okně Vzdálená připojení, Projděte si následující běžné příčiny.

 Pokud používáte spravovaný režim kompatibility, podívejte se prosím do dokumentace k sadě Visual Studio 2010: [řešení potíží se vzdáleným laděním – Visual Studio 2010](/previous-versions/visualstudio/visual-studio-2010/2ys11ead(v=vs.100)).

### <a name="common-causes-for-this-error"></a>Běžné příčiny této chyby

- Vzdálený počítač běží na počítači, který je v jiné podsíti. Pokud to chcete opravit, ručně zadejte název počítače nebo IP adresu v dialogu kvalifikátor.

- Vzdálený ladicí program na vzdáleném počítači neběží. Chcete-li tento problém vyřešit, spusťte vzdálený ladicí program.

- Brána firewall blokuje komunikaci mezi Visual Studio a vzdáleným počítačem. Pokud to chcete opravit, nakonfigurujte bránu firewall tak, aby umožňovala aplikaci Visual Studio a vzdálený ladicí program (Msvsmon) komunikovat.

- Antivirový software blokuje komunikaci mezi Visual Studio a vzdáleným počítačem. Pokud to chcete opravit, nakonfigurujte antivirový software tak, aby umožňoval aplikaci Visual Studio a vzdálený ladicí program (Msvsmon) komunikovat.

## <a name="see-also"></a>Viz také
- [Vzdálené ladění](../debugger/remote-debugging.md)