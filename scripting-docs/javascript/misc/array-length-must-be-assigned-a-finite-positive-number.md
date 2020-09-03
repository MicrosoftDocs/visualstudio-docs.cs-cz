---
title: Délce pole musí být přiřazeno konečné kladné číslo | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: c51c66a4-a543-4e95-b18d-2cfbcb3d1fdd
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 30e02f4f90300e2c05076553419cda5f8c353ab0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817681"
---
# <a name="array-length-must-be-assigned-a-finite-positive-number"></a>Délce pole musí být přiřazeno konečné kladné číslo.
Při nastavování vlastnosti **Length** existujícího objektu **Array** jste zadali délku pole, která nebyla kladné číslo nebo nula. K této chybě dochází, pokud přiřadíte hodnotu vlastnosti **Length** `Array` objektu, který je záporný nebo není číslo ( `NaN` ). Všimněte si, že [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] automaticky převádí zlomková čísla na celá čísla.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pro vlastnost length přiřaďte kladné celé číslo. Pro velikost pole není k dispozici horní limit, který je jiný než maximální celočíselná hodnota (přibližně 4 000 000 000). Následující příklad ukazuje správný způsob, jak nastavit vlastnost **Length** objektu **Array** .  
  
    ```JavaScript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Používání polí](../../javascript/advanced/using-arrays-javascript.md)