---
title: Řízení viditelnosti ikony či dekorátoru
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1d2082f7e26d3e335ed88bbced0f59d6d6c4780c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546639"
---
# <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Řízení viditelnosti ikony či dekorátoru
*Dekoratér* je ikona nebo řádek textu, který se zobrazí na obrazci v jazyce specifickém pro doménu (DSL). Dekoratér se může zobrazit a zmizí v závislosti na stavu vlastností v modelu. Například na tvaru, který představuje osobu, můžete mít různé ikony, které se zobrazí v závislosti na pohlaví osoby, počtu podřízených objektů atd.

## <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Řízení viditelnosti ikony nebo dekoratér
 Následující postup předpokládá, že jste již definovali tvar a jeho mapování na doménovou třídu. Další informace najdete v tématu [Definování jazyka specifického pro doménu](../modeling/how-to-define-a-domain-specific-language.md).

#### <a name="to-control-the-visibility-of-an-icon-or-text-decorator"></a>Řízení viditelnosti ikony nebo textu dekoratér

1. V diagramu definice DSL přidejte do třídy Shape ikony nebo text dekoratéry, které chcete zobrazit.

   1. Klikněte pravým tlačítkem myši na třídu Shape, přejděte na **Přidat**a pak klikněte na požadovaný typ dekoratér.

   2. Nastavte vlastnost **pozice** dekoratér. Stejné umístění může mít víc než jeden dekoratér. Můžete mít například ikony pro pylové a ženy sdílející stejné pozice.

   3. Nastaví **výchozí vlastnost Icon** ikony dekoratér.

2. Vyberte mapu elementu diagramu, což je šedý spojnice mezi třídou Shape a doménovou třídou v diagramu definice DSL.

3. V okně Podrobnosti DSL na kartě **mapy dekoratér** vyberte dekoratér. Například MaleDecorator.

4. Zaškrtněte pole **Filtr viditelnosti** .

5. Pokud je doménová vlastnost, která má ovládat viditelnost, nastavena na bezprostřední doménovou třídu, ponechte **cestu k vlastnosti filtr** prázdnou.

    V opačném případě klikněte na rozevírací nabídku a přejděte na vztah nebo třídu, kde se nachází vlastnost.

   - Chcete-li se vyhnout zprávě o chybách, neměli byste procházet relaci označenou znakem "*" v navigačním nástroji.

6. **Vlastnost Filter** nastavte na doménovou vlastnost. Například pohlaví.

7. V seznamu **položky viditelnosti** přidejte hodnoty této doménové vlastnosti, pro které by měl být dekoratér viditelný. Například muž.

8. Opakujte postup pro každou ikonu.

9. **Transformujte všechny šablony**, sestavte a spusťte a otevřete testovací diagram.

10. Když změníte hodnotu vlastnosti řízení, dekoratéry by se měla objevit a zmizí.

    Často je žádoucí, aby byla viditelnost řízena složitějším vzorcem než jednoduchou sadou hodnot. Například pokud má být ikona závislá na počtu odkazů konkrétního typu nebo v závislosti na tom, zda je číslo v určitém rozsahu. V takovém případě použijte následující postup.

#### <a name="to-control-the-visibility-of-a-decorator-based-on-a-formula"></a>Řízení viditelnosti dekoratér na základě vzorce

1. Do doménové třídy přidejte vypočítanou vlastnost domény. V okně **vlastnosti** nastavte následující hodnoty:

     **Proprocházetelné =** `False` **– Tato vlastnost skrývá uživatele** .    

     **Druh =** `Calculated` **– to znamená, že budete poskytovat kód, který vypočítá jeho hodnotu** .    

     **Název** například **DecoratorControl**

     **Textový** = `Boolean`

     Další informace najdete v tématu věnovaném [vypočítaným a vlastním vlastnostem úložiště](../modeling/calculated-and-custom-storage-properties.md).

2. Nastaví ovládací prvek nová vlastnost na dekoratérou viditelnost.

    1. Vyberte mapu elementu diagramu, což je šedý spojnici od třídy doména k obrazci. V okně **Podrobnosti DSL** otevřete kartu **DecoratorMap** .

    2. Zaškrtněte pole **Filtr viditelnosti** .

    3. V poli **vlastnost filtru**vyberte vlastnost ovládacího prvku **DecoratorControl**.

    4. V části **položky viditelnosti**zadejte `True` .

3. Na panelu nástrojů **Průzkumník řešení** klikněte na **transformovat všechny šablony** .

4. V nabídce **sestavení** klikněte na **Sestavit řešení** .

5. Dvakrát klikněte na zprávu o chybách, která se zobrazila: "*YourClass* neobsahuje definici pro GetDecoratorControlValue...".

     Textový editor se otevře v Dsl\GeneratedCode\DomainClasses.cs. Nad zvýrazněnou chybou je komentář, který požaduje přidání metody.

6. Poznamenejte si obor názvů, třídu a metodu, které chybí.  Například společnost. FamilyTree. Person. GetDecoratorControlValue ().

7. V samostatném souboru kódu napíšete definici částečné třídy obsahující chybějící metodu. Příklad:

    ```
    namespace Company.FamilyTree
    { partial class Person
      { bool GetDecoratorControlValue()
        {
          return this.Children.Count > 0;
    } } }
    ```

     Další informace o přizpůsobení modelu pomocí programového kódu naleznete v tématu [navigace a aktualizace modelu v kódu programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

8. Znovu sestavte a spusťte řešení.

## <a name="see-also"></a>Viz také

- [Definování obrazců a konektorů](../modeling/defining-shapes-and-connectors.md)
- [Nastavení obrázku pozadí v diagramu](../modeling/setting-a-background-image-on-a-diagram.md)
- [Navigace v modelu a aktualizace modelu v kódu programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Zápis kódu pro úpravu jazyka specifického pro doménu](../modeling/writing-code-to-customise-a-domain-specific-language.md)