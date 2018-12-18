---
title: Kódovaný identifikátor URI obsahuje neplatný znak | Dokumentace Microsoftu
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
- VS.WebClient.Help.SCRIPT5024
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a3f0fdbb-8d4b-41ae-a396-43dfc9483760
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e93d145ea6b0991123c2a7c80f8acf54a83a264
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49832171"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>Kódovaný identifikátor URI obsahuje neplatný znak
Pokusili jste se kódování řetězec jako identifikátor URI (Uniform Resource Identifier), ale obsahuje neplatné znaky. I když většina znaky uvnitř řetězců, které má být převeden na identifikátory URI platný, některé sekvence znaků Unicode jsou neplatné.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Zkontrolujte, jestli řetězec, který má být zakódován obsahuje pouze platné sekvence Unicode. Úplný identifikátor URI se skládá z pořadí komponent a oddělovače. Názvy v lomených závorkách představují součásti a ":", "/", ";" a "?" jsou vyhrazené znaky, které jsou použity jako oddělovače. Obecný formát je následující:  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>Viz také  
 [encodeURI – funkce](../../javascript/reference/encodeuri-function-javascript.md)   
 [encodeURIComponent – funkce](../../javascript/reference/encodeuricomponent-function-javascript.md)