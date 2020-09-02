---
title: Kódovaný identifikátor URI obsahuje neplatný znak | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5024
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a3f0fdbb-8d4b-41ae-a396-43dfc9483760
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6091968dcbdd98240b1705e0fa7dc855dad3bda
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85816069"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>Kódovaný identifikátor URI obsahuje neplatný znak
Pokusili jste se řetězec zakódovat jako identifikátor URI (Uniform Resource Identifier), ale obsahuje neplatné znaky. I když je většina znaků platná uvnitř řetězců, které mají být převedeny na identifikátory URI, některé sekvence znaků Unicode jsou neplatné.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Ujistěte se, že řetězec, který má být kódovaný, obsahuje pouze platné sekvence Unicode. Úplný identifikátor URI se skládá z sekvence komponent a oddělovačů. Názvy v lomených závorkách představují komponenty a ":", "/", ";" a "?" jsou vyhrazené znaky používané jako oddělovače. Formulář Obecné je:  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>Viz také  
 [encodeURI – funkce](../../javascript/reference/encodeuri-function-javascript.md)   
 [encodeURIComponent – funkce](../../javascript/reference/encodeuricomponent-function-javascript.md)