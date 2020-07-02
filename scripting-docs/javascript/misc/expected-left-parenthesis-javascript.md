---
title: Byl očekáván znak ' (' (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1005
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 712315e1-4c68-4f66-84c2-41b83c42d85a
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: adcabbe0b1d7ca7d0298202b5242049b86f8229a
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817096"
---
# <a name="expected--javascript"></a>Byl očekáván znak '(' (JavaScript)
Pokusili jste se uzavřít výraz do sady kulatých závorek, ale nezahrnuli levou závorku. Některé výrazy musí být uzavřeny v rámci sady otevíracích a uzavíracích závorek. Všimněte si použití závorek v následujícím příkladu.  
  
```JavaScript  
for (initialize; test; increment) {  
statement;  
}  
```  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Do výrazu vyhodnocení přidejte levou závorku.