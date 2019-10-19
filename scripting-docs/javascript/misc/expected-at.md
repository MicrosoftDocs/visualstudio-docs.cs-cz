---
title: Byl očekáván znak @ | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1032
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 82ff8b74-1710-4358-9a26-dc92ab29c53b
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df1c62c00fdfc8b2b28300cbca1052f0fa350b32
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576514"
---
# <a name="expected-"></a>Byl očekáván příkaz ' \@ '
Pokusili jste se vytvořit proměnnou, která se má použít s příkazy podmíněné kompilace pomocí příkazu `@set`, ale nebyl nalezen znak " **@** " před názvem proměnné.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Přidejte znak " **@** " těsně před název proměnné. Příklad:  
  
    ```JavaScript  
    @set @myvar = 1  
    ```  
  
## <a name="see-also"></a>Viz také:  
 [příkaz @set](../../javascript/reference/at-set-statement-javascript.md)    
 @No__t_1 [podmíněné kompilace](../../javascript/advanced/conditional-compilation-javascript.md)  
 [Proměnné podmíněné kompilace](../../javascript/advanced/conditional-compilation-variables-javascript.md)
