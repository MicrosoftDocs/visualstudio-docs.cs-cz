---
title: Kódovaný identifikátor URI obsahuje neplatný znak | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 72fd550e27e64754fe8c4857e9aa4d25ae5711a6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572244"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>Kódovaný identifikátor URI obsahuje neplatný znak
Pokusili jste se řetězec zakódovat jako identifikátor URI (Uniform Resource Identifier), ale obsahuje neplatné znaky. I když je většina znaků platná uvnitř řetězců, které mají být převedeny na identifikátory URI, některé sekvence znaků Unicode jsou neplatné.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Ujistěte se, že řetězec, který má být kódovaný, obsahuje pouze platné sekvence Unicode. Úplný identifikátor URI se skládá z sekvence komponent a oddělovačů. Názvy v lomených závorkách představují komponenty a ":", "/", ";" a "?" jsou vyhrazené znaky používané jako oddělovače. Formulář Obecné je:  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>Viz také:  
   [funkce encodeURI](../../javascript/reference/encodeuri-function-javascript.md)  
 [encodeURIComponent – funkce](../../javascript/reference/encodeuricomponent-function-javascript.md)