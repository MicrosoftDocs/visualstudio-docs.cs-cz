---
title: Zapouzdřit pole refaktoring (C#) | Dokumentace Microsoftu
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
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- CSharp
helpviewer_keywords:
- Encapsulate Field refactoring operation [C#]
- refactoring [C#], Encapsulate Field
ms.assetid: bf714a04-ab1e-49ce-99ce-dda1ebb1a17f
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 35d7e03e30aa5301ee65f15a8591fbccd1de3fcd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49223539"
---
# <a name="encapsulate-field-refactoring-c"></a>Refaktoring pro zapouzdření polí (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Zapouzdřit pole** operace refaktoringu umožňuje rychlé vytvoření vlastnosti z existujícího pole a bezproblémově aktualizace kódu s odkazy na novou vlastnost.  
  
 Když [pole](http://msdn.microsoft.com/library/3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7) je [veřejné](http://msdn.microsoft.com/library/0ae45d16-a551-4b74-9845-57208de1328e), jiné objekty nemají přímý přístup do tohoto pole a jeho nebyla rozpoznána v objektu, který vlastní toto pole můžete upravit. S použitím [vlastnosti](http://msdn.microsoft.com/library/e295a8a2-b357-4ee7-a12e-385a44146fa8) zapouzdřit pole, můžete zakázat přímý přístup k polím.  
  
 Chcete-li vytvořit novou vlastnost **zapouzdřit pole** operace změní modifikátor přístupu pro pole, které chcete k zapouzdření [privátní](http://msdn.microsoft.com/library/654c0bb8-e6ac-4086-bf96-7474fa6aa1c8)a poté vygeneruje [získat](http://msdn.microsoft.com/library/a52de048-fbe0-41b0-82ec-8e4ac04d3a71)a [nastavit](http://msdn.microsoft.com/library/30d7e4e5-cc2e-4635-a597-14a724879619) přístupové objekty pro toto pole. V některých případech se pouze `get` vygenerovali přístupový objekt, například když je deklarováno pole jen pro čtení.  
  
 Aktualizuje refaktoringu modul kódu s odkazy na nové vlastnosti v oblasti určené v **aktualizace odkazy** část **zapouzdřit pole** dialogové okno.  
  
### <a name="to-create-a-property-from-a-field"></a>Pro vytvoření vlastnosti z pole  
  
1.  Vytvořte konzolovou aplikaci s názvem `EncapsulateFieldExample`a potom nahraďte `Program` pomocí následujícího ukázkového kódu.  
  
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
  
2.  V [Editor kódu](../ide/writing-code-in-the-code-and-text-editor.md), umístěte kurzor na slovo v deklaraci na název pole, které chcete k zapouzdření. V následujícím příkladu, umístěte kurzor na slovo `width`:  
  
    ```csharp  
    public int width, height;  
    ```  
  
3.  Na **Refaktorovat** nabídky, klikněte na tlačítko **zapouzdřit pole**.  
  
     **Zapouzdřit pole** zobrazí se dialogové okno.  
  
     Můžete také zadat klávesové zkratky CTRL + R, E zobrazíte **zapouzdřit pole** dialogové okno.  
  
     Můžete také kliknout pravým tlačítkem kurzor, přejděte na **Refaktorovat**a potom klikněte na tlačítko **zapouzdřit pole** zobrazíte **zapouzdřit pole** dialogové okno.  
  
4.  Zadejte nastavení.  
  
5.  Stisknutím klávesy ENTER nebo kliknutím **OK** tlačítko.  
  
6.  Pokud jste vybrali **náhled změn odkazu** možnost, pak bude **náhled změn odkazu** otevře se okno. Klikněte na tlačítko **použít** tlačítko.  
  
     Následující `get` a `set` ve zdrojovém souboru se zobrazí kód přístupového kódu:  
  
    ```csharp  
    public int Width  
    {  
        get { return width; }  
        set { width = value; }  
    }  
    ```  
  
     Kód v `Main` metoda je rovněž aktualizováno pro nový `Width` název vlastnosti.  
  
    ```csharp  
    Square mySquare = new Square();  
    mySquare.Width = 110;  
    mySquare.height = 150;  
    // Output values for width and height.  
    Console.WriteLine("width = {0}", mySquare.Width);  
    ```  
  
## <a name="remarks"></a>Poznámky  
 **Zapouzdřit pole** operaci je možné, pouze když se kurzor na stejném řádku jako deklarace pole.  
  
 Pro deklarace, které deklarují více polí **zapouzdřit pole** používá čárku jako hranice mezi poli a zahájí refaktoring na pole, které je nejblíže kurzoru a na stejném řádku jako kurzor. Můžete také zadat pole, které chcete zapouzdřit tak, že vyberete název pole v deklaraci.  
  
 Kód, který je generován operaci refaktoringu je modelovaná funkci fragmenty kódu transakci zapouzdřit pole. Fragmenty kódu lze měnit. Další informace najdete v tématu [fragmenty kódu](../ide/code-snippets.md).  
  
## <a name="see-also"></a>Viz také  
 [Refaktoring (C#)](../csharp-ide/refactoring-csharp.md)   
 [Fragmenty kódu v jazyce Visual C#](../ide/visual-csharp-code-snippets.md)