---
title: Refaktoring pro extrakci rozhraní (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Extract Interface
- Extract Interface refactoring operation [C#]
ms.assetid: 7d0aa225-3b33-4331-9652-5a67cac6f3d0
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fdcf281e1ace40d1d7cdac0be302810ea173581b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667550"
---
# <a name="extract-interface-refactoring-c"></a>Refaktoring pro extrahování rozhraní (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Extrahovat rozhraní je operace refaktoringu, která poskytuje snadný způsob, jak vytvořit nové rozhraní se členy, které pocházejí z existující třídy, struktury nebo rozhraní.

 Pokud několik klientů používá stejnou podmnožinu členů z třídy, struktury nebo rozhraní nebo pokud více tříd, struktur nebo rozhraní mají podmnožinu členů společné, může být užitečné pro množinu členů v rozhraní. Další informace o použití rozhraní naleznete v tématu [rozhraní](https://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37).

 Extrahování rozhraní generuje rozhraní v novém souboru a umístí kurzor na začátek nového souboru. Můžete určit, kteří členové mají být extrahováni do nového rozhraní, název nového rozhraní a název generovaného souboru pomocí dialogového okna **Rozbalit rozhraní** .

### <a name="to-use-extract-interface"></a>Použití Extrahování rozhraní

1. Vytvořte konzolovou aplikaci s názvem `ExtractInterface` a pak ji nahraďte `Program` následujícím kódem.

    ```csharp
    // Invoke Extract Interface on ProtoA.
    // Note:  the extracted interface will be created in a new file.
    class ProtoA
    {
        public void MethodB(string s) { }
    }
    ```

2. Umístěte kurzor na umístění `MethodB` a klikněte na **Extrahovat rozhraní** v nabídce **Refaktorovat** .

     Zobrazí se dialogové okno **Extrahovat rozhraní** .

     Můžete také zadat klávesovou zkratku CTRL + R, I pro zobrazení dialogového okna **Rozbalit rozhraní** .

     Můžete také kliknout pravým tlačítkem myši na myš, Ukázat na **Refaktorovat**a potom kliknutím na **Extrahovat rozhraní** zobrazit dialogové okno **Extrahovat rozhraní** .

3. Klikněte na **Vybrat vše**.

4. Klikněte na **OK**.

     Zobrazí se nový soubor IProtoA.cs a následující kód:

    ```csharp
    using System;
    namespace TopThreeRefactorings
    {
        interface IProtoA
        {
            void MethodB(string s);
        }
    }
    ```

## <a name="remarks"></a>Poznámky
 Tato funkce je přístupná pouze v případě, že je kurzor umístěn ve třídě, struktuře nebo rozhraní, které obsahuje členy, které byste chtěli extrahovat. Pokud je kurzor na této pozici, vyvolejte operaci refaktoringu extrahovat rozhraní.

 Při vyvolání Extrahování rozhraní ve třídě nebo ve struktuře je seznam základů a rozhraní upraven tak, aby obsahoval nový název rozhraní. Při vyvolání Extrahování rozhraní v rozhraní se seznam základů a rozhraní nezmění.

## <a name="see-also"></a>Viz také
 [Refaktoring (C#)](../csharp-ide/refactoring-csharp.md)