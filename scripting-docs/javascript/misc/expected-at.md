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
ms.openlocfilehash: 209a8793c0940511b7ecb2abb32f537a614ebf8b
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85814821"
---
# <a name="expected-"></a>Byl očekáván znak \@ ' '
Pokusili jste se vytvořit proměnnou, která se má použít s příkazy podmíněné kompilace pomocí `@set` příkazu, ale neumístil znaménko " **@** " před název proměnné.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Přidejte znak s znaménkem " **@** " těsně před název proměnné. Příklad:  
  
    ```JavaScript  
    @set @myvar = 1  
    ```  
  
## <a name="see-also"></a>Viz také:  
 [@setVydá](../../javascript/reference/at-set-statement-javascript.md)   
 [Podmíněná kompilace](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Proměnné podmíněné kompilace](../../javascript/advanced/conditional-compilation-variables-javascript.md)
