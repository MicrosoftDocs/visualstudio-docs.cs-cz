---
title: 'Postupy: potlačení upozornění použitím položky nabídky | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- warnings, suppressing
- code analysis, suppressing warnings
ms.assetid: 36bd1850-dcde-4ed0-9bc3-0b83df434362
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1c756a5ab6516d78f5370622555898c98658e8b3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49211781"
---
# <a name="how-to-suppress-warnings-by-using-the-menu-item"></a>Postupy: Potlačení upozornění použitím položky nabídky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

POZNÁMKA:]
>  Ve zdroji potlačení nepodporuje webové projekty.  
  
 V okně analýzy kódu můžete použít k potlačení upozornění analýzy kódu. Potlačení upozornění není stejný jako jeho zakázání. Při potlačení varování je zapotřebí, platí pouze pro určité instance třídy porušení zásady. Jiné porušení stejné upozornění se ohlásí stále v okně Seznam chyb.  
  
 Po spuštění analýzy kódu, vy se můžete rozhodnout, že jeden nebo více upozornění analýzy kódu, které jsou zobrazeny v okně analýzy kódu se nevztahují na vaše aplikace. Například můžou určit, že kód je správný, jelikož je. Nebo může být případ, že některé porušení s nízkou prioritou a nebude vyřešen v aktuálním vývojovém cyklu. Bez ohledu na důvod je často užitečné označuje, že varování není použitelné chcete, aby členové týmu vědět, že byl recenzován kód a že bylo zjištěno, že může potlačit upozornění. Ve zdroji potlačení je užitečné, protože to umožňuje umístit potlačení blízko kde vygeneruje upozornění.  
  
 Můžete zvolit, jestli potlačení se zobrazí ve zdrojovém kódu nebo soubor globálního potlačení. Některé potlačení musí být umístěn v souboru globálního potlačení. Pokud tomu tak, **zdroje v** možnost vypnuta.  
  
### <a name="to-suppress-a-warning-by-using-menu-item"></a>K potlačení upozornění použitím položky nabídky  
  
1.  Na **analyzovat** nabídce zvolte **Windows** a klikněte na tlačítko **analýzy kódu**.  
  
2.  V **analýzy kódu** okna, vyberte potlačit upozornění.  
  
3.  Zvolte Akce a potom zvolte **potlačení zpráv**a klikněte na tlačítko buď **zdroje v** nebo **v souboru potlačení projektu**.  
  
     Potlačit konkrétní upozornění a upozornění se zobrazí v okně analýzy kódu jako přeškrtnutá.  
  
> [!NOTE]
>  Potlačení, které nemají cíl joinkind soubor globálního potlačení.



