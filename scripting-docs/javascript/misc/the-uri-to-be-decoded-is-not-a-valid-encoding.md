---
title: Identifikátor URI, který se má dekódovat, není platné kódování | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5025
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 029e0790-ffd1-496d-8700-3b3dbac1b6fd
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 99df8739137971e32c14f265460ff3f4a9c03816
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572265"
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>Dekódovaný identifikátor URI nemá platné kódování
Pokusili jste se dekódovat nesprávně vytvořený identifikátor URI (Uniform Resource Identifier). Identifikátory URI mají speciální syntaxi; aby bylo možné použít v identifikátoru URI, musí být kódování více než alfanumerických znaků kódováno. Pomocí metod `encodeURI` a `encodeURIComponent` můžete vytvořit identifikátor URI z normálního [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] řetězce.  
  
 Úplný identifikátor URI se skládá z sekvence komponent a oddělovačů. Formulář Obecné je:  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 Názvy v lomených závorkách představují komponenty a ":", "/", ";" a "?" jsou vyhrazené znaky používané jako oddělovače.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Ujistěte se, že se pokoušíte dekódovat pouze platné identifikátory URI. Nelze dekódovat běžné [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] řetězce, protože mohou obsahovat neplatné znaky.  
  
## <a name="see-also"></a>Viz také:  
   [funkce decodeURI –](../../javascript/reference/decodeuri-function-javascript.md)  
 [decodeURIComponent – funkce](../../javascript/reference/decodeuricomponent-function-javascript.md)