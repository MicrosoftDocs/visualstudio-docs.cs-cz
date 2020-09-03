---
title: Určení, kdy a kde Poznámka používá | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Group_
- _At_
- _When_
- _At_buffer_
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 1eb32aa7d87da75ebf37b27aa1d425adb85f8c9b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77278450"
---
# <a name="specifying-when-and-where-an-annotation-applies"></a>Určení, kdy a kde se má poznámka použít
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud je Poznámka podmíněná, může vyžadovat další poznámky k určení tohoto analyzátoru.  Například pokud má funkce proměnnou, která může být buď synchronní, nebo asynchronní, funkce se chová takto: v synchronním případě je vždy úspěšné, ale v asynchronním případě hlásí chybu, pokud nemůže být okamžitě úspěšná. Pokud je funkce volána synchronně, kontrola hodnoty výsledku neposkytne analyzátoru kódu žádnou hodnotu, protože by nebyla vrácena.  Nicméně pokud je funkce volána asynchronně a výsledek funkce není kontrolován, může dojít k závažné chybě. Tento příklad znázorňuje situaci, ve které byste mohli použít `_When_` anotaci popsanou dále v tomto článku – Chcete-li povolit kontrolu.  
  
## <a name="structural-annotations"></a>Strukturální poznámky  
 Chcete-li určit, kdy a kde se poznámky vztahují, použijte následující strukturální poznámky.  
  
|Poznámka|Popis|  
|----------------|-----------------|  
|`_At_(expr, anno-list)`|`expr` je výraz, který vrací lvalue. Poznámky v `anno-list` jsou aplikovány na objekt, který je pojmenován `expr` . Pro každou anotaci `anno-list` v `expr` je interpretována v předběžné podmínce, pokud je Poznámka interpretována v předběžné podmínce, a v případě, že je Poznámka interpretována v podmínkách post.|  
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr` je výraz, který vrací lvalue. Poznámky v `anno-list` jsou aplikovány na objekt, který je pojmenován `expr` . Pro každou anotaci `anno-list` v `expr` je interpretována v předběžném stavu, pokud je Poznámka interpretována v předběžné podmínce, a v případě, že je Poznámka interpretována v podmínkách post.<br /><br /> `iter` je název proměnné, která je vymezena na anotaci (včetně `anno-list` ). `iter` má implicitní typ `long` . Identicky pojmenované proměnné v jakémkoli ohraničujícím oboru jsou ze hodnocení skryté.<br /><br /> `elem-count` je výraz, který je vyhodnocen jako celé číslo.|  
|`_Group_(anno-list)`|Poznámky v `anno-list` jsou všechny považované za všechny kvalifikátory, které se vztahují k poznámce skupiny, která se používá u každé poznámky.|  
|`_When_(expr, anno-list)`|`expr` je výraz, který lze převést na `bool` . Pokud je hodnota nenulová ( `true` ), poznámky, které jsou určeny v, `anno-list` jsou považovány za použitelné.<br /><br /> Ve výchozím nastavení je pro každou anotaci v `anno-list` , `expr` interpretován jako použití vstupních hodnot, pokud je Poznámka podmínkou, a jako výstupních hodnot, pokud je Poznámka podmínkou. Chcete-li přepsat výchozí hodnotu, můžete použít `_Old_` vnitřní při vyhodnocení podmínky post, aby označovala, že by měly být použity vstupní hodnoty. **Poznámka:**  Různé poznámky mohou být povoleny jako důsledek použití, je- `_When_` li zahrnuta proměnlivá hodnota (například `*pLength` ), protože vyhodnocený výsledek v předběžné `expr` podmínce se může lišit od vyhodnoceného výsledku v podmínkách post.|  
  
## <a name="see-also"></a>Viz také  
 [Použití poznámek SAL k omezení vad kódu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Porozumění SAL](../code-quality/understanding-sal.md)   
 [Zadávání poznámek k parametrům funkcí a návratovým hodnotám](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Zadávání poznámek k chování funkcí](../code-quality/annotating-function-behavior.md)   
 [Přidávání poznámek ke strukturám a třídám](../code-quality/annotating-structs-and-classes.md)   
 [Zadávání poznámek k chování při zamykání](../code-quality/annotating-locking-behavior.md)   
 [Vnitřní funkce](../code-quality/intrinsic-functions.md)   
 [Doporučené postupy a příklady](../code-quality/best-practices-and-examples-sal.md)
