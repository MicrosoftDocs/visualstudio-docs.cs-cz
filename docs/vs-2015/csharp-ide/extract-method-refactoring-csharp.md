---
title: Extrahovat metodu refaktoring (C#) | Dokumentace Microsoftu
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
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Extract Method
- Extract Method refactoring operation [C#]
ms.assetid: eeba11df-a815-4bec-9c21-8a831891b783
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: cc05da79676beed5fa698f11843a6b7485280e71
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49228056"
---
# <a name="extract-method-refactoring-c"></a>Refaktoring pro extrahování metody (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Extrahovat metodu** je operace refaktoringu kódu, který poskytuje snadný způsob, jak vytvořit novou metodu z fragmentu kódu do existujícího člena.  
  
 Pomocí **extrahovat metodu**, můžete vytvořit novou metodu extrahováním výběr kódu z uvnitř bloku kódu existujícího člena. Metoda nové, extrahované obsahuje vybraný kód a vybraný kód do existujícího člena je nahrazena volání nové metody. Fragment kódu do své vlastní metody vám umožní rychle a přesně reorganizovat kód pro lepší čitelnost a opakované použití.  
  
 **Extrahovat metodu** má následující výhody:  
  
-   Kdy se klade důraz diskrétní, opakovatelně použitelných metody může vést ke vzniku doporučenými postupy psaní kódu.  
  
-   Může vést ke vzniku svým dokumentování kódu pomocí vhodné organizace.  
  
     Po popisné názvy metod používaných, vysoké úrovně můžete další informace, jako jsou řadu komentáře.  
  
-   Podporuje vytváření citlivější metody pro zjednodušení přepsání.  
  
-   Snižuje dojde k duplikaci kódu.  
  
### <a name="to-use-extract-method"></a>Extrahování metody  
  
1.  Vytvořte konzolovou aplikaci s názvem `ExtractMethod`a potom nahraďte `Program` pomocí následujícího ukázkového kódu.  
  
    ```csharp  
    class A  
    {  
        const double PI = 3.141592;  
  
        double CalculatePaintNeeded(double paintPerUnit, double radius)  
        {  
            // Select any of the following:  
            // 1. The entire next line of code.  
            // 2. The right-hand side of the next line of code.  
            // 3. Just "PI *" of the right-hand side of the next line  
            //    of code (to see the prompt for selection expansion).  
            // 4.  All code within the method body.  
            // ...Then invoke Extract Method.  
  
            double area = PI * radius * radius;  
  
            return area / paintPerUnit;  
        }  
    }  
    ```  
  
2.  Vyberte fragment kódu, které mají být extrahovány:  
  
    ```csharp  
    double area = PI * radius * radius;  
    ```  
  
3.  Na **Refaktorovat** nabídky, klikněte na tlačítko **extrahovat metodu**.  
  
     **Extrahovat metodu** zobrazí se dialogové okno.  
  
     Alternativně můžete také zadat klávesové zkratky CTRL + R, M zobrazíte **extrahovat metodu** dialogové okno.  
  
     Je můžete také kliknout pravým tlačítkem vybrané kódu, přejděte na **Refaktorovat**a potom klikněte na tlačítko **extrahovat metodu** zobrazíte **extrahovat metodu** dialogové okno.  
  
4.  Zadejte název nové metody, jako například `CircleArea`v **nový název metody** pole.  
  
     Ve verzi preview nové podpis metody se zobrazí v části **náhled signatury metody**.  
  
5.  Klikněte na tlačítko **OK**.  
  
## <a name="remarks"></a>Poznámky  
 Při použití **extrahovat metodu** příkazu novou metodu disku do mechaniky následující člen zdroje ve stejné třídě.  
  
## <a name="partial-types"></a>Částečné typy  
 Pokud je třída částečného typu, pak **extrahovat metodu** vytvoří novou metodu hned za člena zdroje. **Extrahovat metodu** Určuje podpis novou metodu vytváření statickou metodu, pokud žádná data instance odkazuje kód do nové metody.  
  
## <a name="generic-type-parameters"></a>Parametry obecného typu  
 Při extrahování metodu, která má parametr obecného typu bez omezení vygenerovaný kód nebude přidávat `ref` Modifikátor pro tento parametr není-li přiřadit hodnotu k ní. Pokud extrahované metody bude podporovat odkazové typy jako argument obecného typu, pak by měl ručně přidáte `ref` modifikátor parametru v podpisu metody.  
  
## <a name="anonymous-methods"></a>Anonymní metody  
 Pokud se pokusíte extrakce části anonymní metody, která obsahuje odkaz na místní proměnnou, která je deklarována nebo odkazované vně anonymní metody, pak Visual Studio se vás upozorní na potenciální sémantickými změnami.  
  
 Pokud anonymní metoda používá hodnotu místní proměnné, v okamžiku, kdy anonymní metody se získá hodnota. Při anonymní metoda je extrahován do jiné metodě, je v tuto chvíli volání do extrahované metody, získat hodnotu místní proměnné.  
  
 Následující příklad ukazuje tento sémantické změny. Pokud tento kód spuštěn, pak **11** vytiskne na konzolu. Pokud používáte **extrahovat metodu** extrahovat oblasti kód, který je označen komentářích ke kódu do své vlastní metody a pak spouštění kódu vytvořeného refaktorované, pak **10** vytiskne na konzolu.  
  
```csharp  
class Program  
{  
    delegate void D();  
    D d;  
    static void Main(string[] args)  
    {  
        Program p = new Program();  
        int i = 10;  
        /*begin extraction*/  
            p.d = delegate { Console.WriteLine(i++); };  
        /*end extraction*/  
        i++;  
        p.d();  
    }  
}  
```  
  
 K této situaci vyřešit, ujistěte se, místní proměnné, které se používají v polích anonymní metody třídy.  
  
## <a name="see-also"></a>Viz také  
 [Refaktoring (C#)](../csharp-ide/refactoring-csharp.md)