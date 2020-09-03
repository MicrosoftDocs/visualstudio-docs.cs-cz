---
title: Refaktoring přeřazení parametrů (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.reorder
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Reorder Parameters
- Reorder Parameters refactoring [C#]
ms.assetid: 4dabf21a-a9f0-41e9-b11b-55760cf2bd90
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e39564fb108b63859620e2c4a650608cdf1e7e82
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673136"
---
# <a name="reorder-parameters-refactoring-c"></a>Refaktoring přeskupení parametrů (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Reorder Parameters` je operace refaktoringu jazyka Visual C#, která poskytuje snadný způsob, jak změnit pořadí parametrů pro metody, indexery a delegáty. `Reorder Parameters` změní deklaraci a na všech místech, kde je člen volán, parametry jsou přeuspořádány tak, aby odrážely novou objednávku.

 Chcete-li provést `Reorder Parameters` operaci, umístěte kurzor na nebo vedle metody, indexeru nebo delegáta. Pokud je kurzor na pozici, vyvolejte `Reorder Parameters` operaci stisknutím klávesové zkratky nebo kliknutím na příkaz v místní nabídce.

> [!NOTE]
> V metodě rozšíření nelze změnit pořadí prvního parametru.

### <a name="to-reorder-parameters"></a>Změna pořadí parametrů

1. Vytvořte knihovnu tříd s názvem `ReorderParameters` a pak ji nahraďte `Class1` následujícím příkladem kódu.

    ```csharp
    class ProtoClassA
    {
        // Invoke on 'MethodB'.
        public void MethodB(int i, bool b) { }
    }

    class ProtoClassC
    {
        void D()
        {
            ProtoClassA MyClassA = new ProtoClassA();

            // Invoke on 'MethodB'.
            MyClassA.MethodB(0, false);
        }
    }
    ```

2. Umístěte kurzor na `MethodB` , a to buď v deklaraci metody, nebo v volání metody.

3. V nabídce **refaktoring** klikněte na **změnit pořadí parametrů**.

     Zobrazí se dialogové okno **změnit pořadí parametrů** .

4. V dialogovém okně **změnit pořadí parametrů** vyberte `int i` v seznamu **parametry** a pak klikněte na tlačítko dolů.

     Alternativně můžete přetáhnout `int i` za `bool b` seznam **parametrů** .

5. V dialogovém okně **změnit pořadí parametrů** klikněte na tlačítko **OK**.

     Pokud je v dialogovém okně změnit **pořadí parametrů** vybraná možnost **Náhled změn odkazu** , zobrazí se dialogové okno **Náhled změn – parametry změny pořadí** . Poskytuje náhled změn v seznamu parametrů `MethodB` v rámci signatury i volání metody.

    1. Pokud se zobrazí dialogové okno **Náhled změn – změnit pořadí parametrů** , klikněte na **použít**.

         V tomto příkladu je aktualizována deklarace metody a všechny lokality volání metody pro `MethodB` .

## <a name="remarks"></a>Poznámky
 Můžete změnit pořadí parametrů z deklarace metody nebo volání metody. Umístěte kurzor na nebo vedle deklarace metody nebo delegáta, ale ne v těle.

## <a name="see-also"></a>Viz také
 [Refaktoring (C#)](../csharp-ide/refactoring-csharp.md)