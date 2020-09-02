---
title: Refaktoring pro extrahování metod (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Extract Method
- Extract Method refactoring operation [C#]
ms.assetid: eeba11df-a815-4bec-9c21-8a831891b783
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6e6d5e7913a7433fd4b30da490f33dd614c3e2b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667542"
---
# <a name="extract-method-refactoring-c"></a>Refaktoring pro extrahování metody (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Extrahovat metodu** je operace refaktoringu, která poskytuje snadný způsob, jak vytvořit novou metodu z fragmentu kódu v existujícím členu.

 Pomocí **metody Extract**můžete vytvořit novou metodu extrahováním výběru kódu z uvnitř bloku kódu existujícího člena. Nová extrahovaná metoda obsahuje vybraný kód a vybraný kód ve stávajícím členu je nahrazen voláním metody New. Vypnutí fragmentu kódu do své vlastní metody vám umožní rychle a přesně reorganizovat kód pro lepší opakované použití a čitelnost.

 **Metoda extrahování** má následující výhody:

- Doporučuje osvědčené postupy kódování pomocí zdůraznění diskrétních, opakovaně použitelných metod.

- Podporuje kód pro samoobslužné dokumentování prostřednictvím dobré organizace.

     Při použití popisných názvů se metody vysoké úrovně můžou načítat podobně jako u řady komentářů.

- Podporuje vytváření jemnějších metod pro zjednodušení přepsání.

- Snižuje duplicity kódu.

### <a name="to-use-extract-method"></a>Použití metody Extract

1. Vytvořte konzolovou aplikaci s názvem `ExtractMethod` a nahraďte `Program` následující ukázkový kód.

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

2. Vyberte fragment kódu, který chcete extrahovat:

    ```csharp
    double area = PI * radius * radius;
    ```

3. V nabídce **Refaktorovat** klikněte na **Extrahovat metodu**.

     Zobrazí se dialogové okno **Extrahovat metodu** .

     Případně můžete také zadat klávesovou zkratku CTRL + R, M pro zobrazení dialogového okna **Extrahovat metodu** .

     Můžete také kliknout pravým tlačítkem na vybraný kód, Ukázat na **Refaktorovat**a potom kliknout na **Extrahovat metodu** a zobrazit tak dialogové okno **Extrahovat metodu** .

4. Zadejte název nové metody, například `CircleArea` , do pole **název nové metody** .

     Náhled nové signatury metody se zobrazí v části **signatura metody verze Preview**.

5. Klikněte na **OK**.

## <a name="remarks"></a>Poznámky
 Při použití příkazu **Extrahovat metodu** je nová metoda vložena po zdrojovém členovi ve stejné třídě.

## <a name="partial-types"></a>Částečné typy
 Pokud je třída částečný typ, pak **Metoda Extract** vygeneruje novou metodu hned po zdrojovém členu. **Metoda Extract** Určuje podpis nové metody, vytvoří statickou metodu, pokud není na data instance odkazováno pomocí kódu v nové metodě.

## <a name="generic-type-parameters"></a>Parametry obecného typu
 Když extrahujete metodu, která má neomezený parametr obecného typu, vygenerovaný kód nepřidá `ref` Modifikátor k tomuto parametru, pokud není přiřazena hodnota. Pokud extrahovaná metoda bude podporovat typy odkazů jako argument obecného typu, pak byste měli přidat `ref` modifikátor do parametru v signatuře metody ručně.

## <a name="anonymous-methods"></a>Anonymní metody
 Pokud se pokusíte extrahovat část anonymní metody, která obsahuje odkaz na místní proměnnou, která je buď deklarována, nebo odkazována mimo anonymní metodu, pak Visual Studio vás upozorní na potenciální sémantické změny.

 Pokud anonymní metoda používá hodnotu lokální proměnné, je hodnota získána v okamžiku spuštění anonymní metody. Když je anonymní metoda extrahována do jiné metody, hodnota místní proměnné je získána v okamžiku volání extrahované metody.

 Následující příklad znázorňuje tuto sémantickou změnu. Pokud je tento kód spuštěn, bude na konzolu vytištěna **11** . Použijete-li **metodu Extract** k extrakci oblasti kódu, který je označen komentáři kódu, do své vlastní metody a následným spuštěním refaktoringového kódu, bude na konzolu vytištěna **10** .

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

 Chcete-li tuto situaci vyřešit, vytvořte místní proměnné, které jsou použity v polích anonymní metody třídy.

## <a name="see-also"></a>Viz také
 [Refaktoring (C#)](../csharp-ide/refactoring-csharp.md)