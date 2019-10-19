---
title: V regulárním výrazu (JavaScript) byl očekáván znak ') | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7c10449df9ef3331949695b7423da3eb08b65433
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577542"
---
# <a name="expected--in-regular-expression-javascript"></a>V regulárním výrazu byl očekáván znak ')' (JavaScript)
Pokusili jste se vytvořit zachycení regulárního výrazu, kontrolní výraz nebo skupinu, ale neobsahovaly uzavírací závorky. Kulaté závorky mají v regulárních výrazech několik účelů. Primárně se používají k zachycení dílčích výrazů, k určení kontrolních výrazů nebo ke seskupování vzorů, aby bylo možné položky zacházet jako s jednou jednotkou *, +,? a tak dále.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Přidejte pravé kulaté závorky.  
  
    > [!NOTE]
    > Pokud chcete, aby se shodovala s jednou závorkou, vystavte ji pomocí zpětného lomítka-\\ (-tak, že není interpretována jako speciální znak [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [objektu regulárního výrazu](../../javascript/reference/regular-expression-object-javascript.md)  
 [Syntaxe regulárního výrazu (JavaScript)](https://msdn.microsoft.com/library/1400241x)