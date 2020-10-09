---
title: Byl očekáván znak @ | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 98a35421054e4d2236fe509224ed146063b61a79
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862307"
---
# <a name="expected-"></a>Byl očekáván znak '\@'
Pokusili jste se vytvořit proměnnou, která se má použít s příkazy podmíněné kompilace pomocí `@set` příkazu, ale neumístil znaménko " **@** " před název proměnné.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Přidejte znak s znaménkem " **@** " těsně před název proměnné. Příklad:  
  
    ```JavaScript  
    @set @myvar = 1  
    ```  
  
## <a name="see-also"></a>Viz také  
 [@set Vydá](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/at-set)   
 [Podmíněná kompilace](/previous-versions/windows/internet-explorer/ie-developer/scripting-articles/121hztk3(v=vs.84))   
 [Proměnné podmíněné kompilace](/previous-versions/windows/internet-explorer/ie-developer/scripting-articles/s59bkzce(v=vs.84))