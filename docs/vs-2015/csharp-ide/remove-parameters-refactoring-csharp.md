---
title: Refaktoring (C#) pro odebrání parametrů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.csharp.refactoring.remove
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], removing
- refactoring [C#], Remove Parameters
- Remove Parameters refactoring [C#]
ms.assetid: f4fc3265-0ef8-4398-a691-c338178697a6
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c9559deda5c5cdc60adc10246196fb66646cfee5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49284385"
---
# <a name="remove-parameters-refactoring-c"></a>Refaktoring pro odebrání parametrů (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Remove Parameters` je operace refaktoringu kódu, která poskytuje snadný způsob, jak odebrat parametry z metod, indexerů nebo delegátů. Odebrat parametry změny deklarace; kteroukoli lokalitou, kdy je člen volán odebere se tak, aby odrážely novou deklaraci parametru.  
  
 Proveďte operaci odebrání parametrů tak, že první umístíte kurzor na metodu, indexer nebo delegáta. Zatímco ukazatel je v umístění, která se má vyvolat odebrat `Parameters` operace, klikněte na tlačítko **Refaktorovat** nabídky, stiskněte klávesovou zkratku, nebo v místní nabídce vyberte příkaz.  
  
> [!NOTE]
>  Nemůžete odebrat první parametr metody rozšíření.  
  
### <a name="to-remove-parameters"></a>Chcete-li odebrat parametry  
  
1.  Vytvořte konzolovou aplikaci s názvem `RemoveParameters`a potom nahraďte `Program` následujícím kódem.  
  
    ```csharp  
    class A  
    {  
        // Invoke on 'A'.  
        public A(string s, int i) { }  
    }  
  
    class B  
    {  
        void C()  
        {  
            // Invoke on 'A'.  
            A a = new A("a", 2);  
        }  
    }  
    ```  
  
2.  Umístěte kurzor na metodu `A`, buď v deklaraci metody nebo volání metody.  
  
3.  Z **Refaktorovat** nabídce vyberte možnost **odebrání parametrů** zobrazíte **odebrání parametrů** dialogové okno.  
  
     Můžete také zadat klávesovou zkratku CTRL + R, V zobrazení **odebrání parametrů** dialogové okno.  
  
     Můžete také kliknout pravým tlačítkem kurzor, přejděte na **Refaktorovat**a potom klikněte na tlačítko **odebrání parametrů** zobrazíte **odebrání parametrů** dialogové okno.  
  
4.  Použití **parametry** pole, umístěte kurzor na `int i`a potom klikněte na tlačítko **odebrat**.  
  
5.  Klikněte na tlačítko **OK**.  
  
6.  V **náhled změn – odebrání parametrů** dialogové okno, klikněte na tlačítko **použít**.  
  
## <a name="remarks"></a>Poznámky  
 Odebrat parametry z deklarace metody nebo volání metody. Umístěte kurzor do pole Název metody prohlášení nebo delegáta a odebrání Parametry vyvolání.  
  
> [!CAUTION]
>  Odeberte parametry umožňuje odebrat parametr, který se odkazuje v těle člena, ale neodebere odkazy na tento parametr v těle metody. Do kódu, což může představovat chyby sestavení. Můžete však použít **náhled změn** dialogové okno zrevidujete váš kód před provedením operace refaktoringu názvů.  
  
 Pokud parametr odebírá se změní při volání metody, pokud chcete odebrání parametru také odebrat úpravy. Například pokud volání metody se změnil z  
  
```csharp  
MyMethod(param1++, param2);  
```  
  
 až  
  
```csharp  
MyMethod(param2);  
```  
  
 operace refaktoringu `param1` nesmí být zvýšena.  
  
## <a name="see-also"></a>Viz také  
 [Refaktoring (C#)](../csharp-ide/refactoring-csharp.md)