---
title: Refaktoring pro zapouzdření poleC#() | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- CSharp
helpviewer_keywords:
- Encapsulate Field refactoring operation [C#]
- refactoring [C#], Encapsulate Field
ms.assetid: bf714a04-ab1e-49ce-99ce-dda1ebb1a17f
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b4f5ddbe7eab925b06584f00b04bed3c74e9811
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667575"
---
# <a name="encapsulate-field-refactoring-c"></a>Refaktoring pro zapouzdření polí (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Operace refaktoringu **zapouzdřit pole** umožňuje rychle vytvořit vlastnost z existujícího pole a pak plynule aktualizovat kód s odkazy na novou vlastnost.

 Když je [pole](https://msdn.microsoft.com/library/3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7) [veřejné](https://msdn.microsoft.com/library/0ae45d16-a551-4b74-9845-57208de1328e), ostatní objekty mají přímý přístup k tomuto poli a mohou jej upravit, Nerozpoznáno objektem, který je vlastníkem daného pole. Když použijete [vlastnosti](https://msdn.microsoft.com/library/e295a8a2-b357-4ee7-a12e-385a44146fa8) k zapouzdření tohoto pole, můžete zakázat přímý přístup k polím.

 Chcete-li vytvořit novou vlastnost, operace **zapouzdření pole** změní modifikátor přístupu pro pole, které chcete zapouzdřit do [privátního](https://msdn.microsoft.com/library/654c0bb8-e6ac-4086-bf96-7474fa6aa1c8), a poté vygeneruje přístupové objekty [Get](https://msdn.microsoft.com/library/a52de048-fbe0-41b0-82ec-8e4ac04d3a71) a [set](https://msdn.microsoft.com/library/30d7e4e5-cc2e-4635-a597-14a724879619) pro toto pole. V některých případech je vygenerován pouze přistupující objekt `get`, například při deklaraci pole jen pro čtení.

 Modul refaktoringu aktualizuje váš kód o odkazy na novou vlastnost v oblastech, které jsou uvedeny v části **aktualizace odkazů** dialogového okna **zapouzdření pole** .

### <a name="to-create-a-property-from-a-field"></a>Vytvoření vlastnosti z pole

1. Vytvořte konzolovou aplikaci s názvem `EncapsulateFieldExample` a poté nahraďte `Program` následujícím příkladem kódu.

    ```csharp
    class Square
    {
        // Select the word 'width' and then use Encapsulate Field.
        public int width, height;
    }
    class MainClass
    {
        public static void Main()
        {
            Square mySquare = new Square();
            mySquare.width = 110;
            mySquare.height = 150;
            // Output values for width and height.
            Console.WriteLine("width = {0}", mySquare.width);
            Console.WriteLine("height = {0}", mySquare.height);
        }
    }
    ```

2. V [editoru kódu](../ide/writing-code-in-the-code-and-text-editor.md)umístěte kurzor do deklarace na název pole, které chcete zapouzdřit. V následujícím příkladu umístěte kurzor na slovo `width`:

    ```csharp
    public int width, height;
    ```

3. V nabídce **Refaktorovat** klikněte na položku **zapouzdření pole**.

     Zobrazí se dialogové okno **zapouzdření pole** .

     Můžete také zadat klávesovou zkratku CTRL + R, E pro zobrazení dialogového okna **zapouzdření pole** .

     Můžete také kliknout pravým tlačítkem myši na kurzor, Ukázat na **Refaktorovat**a potom kliknout na tlačítko **zapouzdření pole** . zobrazí se dialogové okno **zapouzdření pole** .

4. Zadejte nastavení.

5. Stiskněte klávesu ENTER nebo klikněte na tlačítko **OK** .

6. Pokud jste vybrali možnost **Náhled změn odkazu** , otevře se okno **Náhled změn odkazů** . Klikněte na tlačítko **použít** .

     Ve zdrojovém souboru se zobrazí následující `get` a přístupový kód `set`:

    ```csharp
    public int Width
    {
        get { return width; }
        set { width = value; }
    }
    ```

     Kód v metodě `Main` je aktualizován také na nový název vlastnosti `Width`.

    ```csharp
    Square mySquare = new Square();
    mySquare.Width = 110;
    mySquare.height = 150;
    // Output values for width and height.
    Console.WriteLine("width = {0}", mySquare.Width);
    ```

## <a name="remarks"></a>Poznámky
 Operace **zapouzdření pole** je možná pouze v případě, že je kurzor umístěn na stejném řádku jako deklarace pole.

 U deklarací, které deklarují více polí, **pole zapouzdření** používá čárku jako hranici mezi poli a inicializuje Refaktoring pro pole, které je nejblíže kurzorem a na stejném řádku jako kurzor. Můžete také určit, které pole chcete zapouzdřit, a to tak, že vyberete název tohoto pole v deklaraci.

 Kód, který je generován touto operací refaktoringu, je modelován funkcí fragmentů kódu polí zapouzdření. Fragmenty kódu lze upravovat. Další informace naleznete v tématu [fragmenty kódu](../ide/code-snippets.md).

## <a name="see-also"></a>Viz také
 [Refaktoring (C#)](../csharp-ide/refactoring-csharp.md) [vizuální C# fragmenty kódu](../ide/visual-csharp-code-snippets.md)