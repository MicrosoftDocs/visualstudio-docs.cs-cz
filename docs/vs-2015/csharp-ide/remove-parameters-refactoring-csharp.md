---
title: Refaktoring pro odebrání parametrůC#() | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40c373c3575f007952143e29c8dfc2cfac3d080f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667495"
---
# <a name="remove-parameters-refactoring-c"></a>Refaktoring pro odebrání parametrů (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Remove Parameters` je operace refaktoringu, která poskytuje snadný způsob, jak odebrat parametry z metod, indexerů nebo delegátů. Odebrat parametry změna deklarace; v jakémkoli umístění, kde je člen volán, je parametr odebrán, aby odrážel novou deklaraci.

 Operaci odebrat parametry provedete tak, že nejprve umístíte kurzor na metodu, indexer nebo delegáta. Když je kurzor na pozici, chcete-li vyvolat operaci odebrání `Parameters`, klikněte na nabídku **refaktoring** , stiskněte klávesovou zkratku nebo vyberte příkaz z místní nabídky.

> [!NOTE]
> První parametr v metodě rozšíření nelze odebrat.

### <a name="to-remove-parameters"></a>Odebrání parametrů

1. Vytvořte konzolovou aplikaci s názvem `RemoveParameters` a pak `Program` nahraďte následujícím kódem.

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

2. Umístěte kurzor na metodu `A`, a to buď v deklaraci metody, nebo v volání metody.

3. V nabídce **refaktoring** vyberte možnost **Odebrat parametry** a zobrazí se dialogové okno **Odebrat parametry** .

     Můžete také zadat klávesovou zkratku CTRL + R, V pro zobrazení dialogového okna **Odebrat parametry** .

     Můžete také kliknout pravým tlačítkem myši na kurzor, Ukázat na **Refaktorovat**a kliknout na příkaz **Odebrat** parametry. zobrazí se dialogové okno **Odebrat parametry** .

4. Pomocí pole **Parameters** umístěte kurzor na `int i` a pak klikněte na **Odebrat**.

5. Klikněte na tlačítko **OK**.

6. V **náhledu změn – dialogové okno odebrat parametry** klikněte na **použít**.

## <a name="remarks"></a>Poznámky
 Můžete odebrat parametry z deklarace metody nebo volání metody. Umístěte kurzor do deklarace metody nebo název delegáta a zavolejte odebrat parametry.

> [!CAUTION]
> Příkaz Remove Parameters umožňuje odebrat parametr, na který je odkazováno v těle člena, ale neodebere odkazy na tento parametr v těle metody. To může vést k chybám sestavení v kódu. Můžete však použít dialogové okno **Náhled změn** ke kontrole kódu před provedením operace refaktoringu.

 Pokud je odebraný parametr změněn během volání metody, odebrání parametru odstraní také změnu. Například pokud je volání metody změněno z

```csharp
MyMethod(param1++, param2);
```

 až

```csharp
MyMethod(param2);
```

 operace refaktoringu `param1` nebude zvýšena.

## <a name="see-also"></a>Viz také
 [Refaktoring (C#)](../csharp-ide/refactoring-csharp.md)