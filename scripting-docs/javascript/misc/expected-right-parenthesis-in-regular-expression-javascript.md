---
title: V regulárním výrazu (JavaScript) byl očekáván znak ') | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: af32127476c83100c0340021428e3abc572ef2f7
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815638"
---
# <a name="expected--in-regular-expression-javascript"></a>V regulárním výrazu byl očekáván znak ')' (JavaScript)
Pokusili jste se vytvořit zachycení regulárního výrazu, kontrolní výraz nebo skupinu, ale neobsahovaly uzavírací závorky. Kulaté závorky mají v regulárních výrazech několik účelů. Primárně se používají k zachycení dílčích výrazů, k určení kontrolních výrazů nebo ke seskupování vzorů, aby bylo možné položky zacházet jako s jednou jednotkou *, +,? a tak dále.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Přidejte pravé kulaté závorky.  
  
    > [!NOTE]
    > Pokud chcete, aby se shodovala s jednou závorkou, řídicí znak se zpětným lomítkem \\ (-tak, že není interpretován jako speciální znak pomocí [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  
  
## <a name="see-also"></a>Viz také:  
 [Objekt regulárního výrazu](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntaxe regulárního výrazu (JavaScript)](https://msdn.microsoft.com/library/1400241x)