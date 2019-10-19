---
title: Očekávala se hexadecimální číslice | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 67a86df7-49f9-43cb-99c6-99b1a427827a
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6672046e0f7bf5e39c334dc0ba30f22eaff6e9a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573383"
---
# <a name="expected-hexadecimal-digit"></a>Byla očekávána šestnáctková číslice.
Vytvořili jste nesprávnou řídicí sekvenci Unicode. Řídicí sekvence Unicode začínají na \u, následované přesně čtyřmi šestnáctkovými číslicemi (ne více a méně). Šestnáctkové číslice Unicode můžou obsahovat jenom čísla 0-9, Velká písmena A – F a malá písmena a-f. Následující příklad ukazuje správně vytvořenou řídicí sekvenci Unicode.  
  
```JavaScript  
z = "\u1A5F";  
```  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Ujistěte se, že vaše hexadecimální číslice Unicode začínají na \u, obsahuje jenom čísla 0-9, Velká písmena A-F, malá písmena a-f; a jsou seskupeny do čtyř číslic.  
  
    > [!NOTE]
    > Pokud chcete použít textový literál \u v řetězci, použijte dvě zpětná lomítka – (\\ \u) – jedno pro řídicí sekvence prvního zpětného lomítka.  
  
## <a name="see-also"></a>Viz také:  
 [Datové typy](../../javascript/data-types-javascript.md)