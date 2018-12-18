---
title: Dekódovaný identifikátor URI nemá platné kódování | Dokumentace Microsoftu
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5025
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 029e0790-ffd1-496d-8700-3b3dbac1b6fd
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d37ca55dfd701aaeba2af729511a5ae6a4fa5f4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49841816"
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>Dekódovaný identifikátor URI nemá platné kódování
Pokoušíte se o dekódování nesprávně formátovaný URI (Uniform Resource Identifier). Identifikátory URI mají zvláštní syntaxi; Většina jiných než alfanumerických znaků musí kódováním předtím, než je možné v identifikátoru URI. Můžete použít `encodeURI` a `encodeURIComponent` metody vytvořit identifikátor URI z normální [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] řetězec.  
  
 Úplný identifikátor URI se skládá z pořadí komponent a oddělovače. Obecný formát je následující:  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 Názvy v lomených závorkách představují součásti a ":", "/", ";" a "?" jsou vyhrazené znaky, které jsou použity jako oddělovače.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Ujistěte se, že se pokoušíte dekódování jenom platné identifikátory URI. Nelze dekódovat normální [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] řetězce mohou obsahovat neplatné znaky.  
  
## <a name="see-also"></a>Viz také  
 [decodeURI – funkce](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent – funkce](../../javascript/reference/decodeuricomponent-function-javascript.md)