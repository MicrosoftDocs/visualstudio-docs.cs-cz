---
title: Inicializace | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ea9f8a24d342668b3574c3798a32c58c124aca7b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185849"
---
# <a name="init"></a>Init
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Připraví komponentu v aplikaci diagnostiky grafiky na aktivní zachycování a zaznamenávání grafických informací do souboru protokolu grafiky.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void Init(  
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `vsgLogGetter`  
 Odkazovaná entita – například funkce, ukazatel na funkci, výraz lambda nebo objekt funkce, který přijímá jako parametry délku vyrovnávací paměti složené z `wchar_t` a ukazatel na tuto vyrovnávací paměť a vrátí `void` . Při vyvolání určuje volanou entitu název souboru, který se použije k zaznamenání informací o grafice a před vrácením zapíše do zadané vyrovnávací paměti.  
  
## <a name="remarks"></a>Poznámky  
 `Init`Funkce je volána automaticky, pokud `VsgDbg` je instance třídy vytvořena zadáním `bDefaultInit` parametru jeho konstruktoru, `true` v opačném případě `Init` musí být explicitně volána před tím, než bude možné aktivně zachytit a zaznamenat informace o grafice.  
  
 Můžete dokončit a zavřít aktivní soubor protokolu grafiky voláním `UnInit` a pak zachytit a zaznamenat více grafických informací do nového souboru protokolu grafiky voláním metody `Init` . Tuto akci můžete opakovat tolikrát, kolikrát chcete vytvořit několik nezávislých souborů protokolu grafiky pomocí stejné `VsgDbg` instance.  
  
## <a name="see-also"></a>Viz také  
 [UnInit](../debugger/init.md)
