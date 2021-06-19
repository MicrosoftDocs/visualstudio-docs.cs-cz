---
title: Vypočtené a vlastní vlastnosti úložiště
description: Zjistěte, jak se v diagramu a v Průzkumníku jazyka zobrazují všechny vlastnosti domény v jazyce specifickém pro doménu (DSL).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain properties
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f98dca6759b9e4a77e71139b6d9ec9b394d99b04
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385419"
---
# <a name="calculated-and-custom-storage-properties"></a>Vypočtené a vlastní vlastnosti úložiště
Všechny vlastnosti domény v jazyce specifickém pro doménu (DSL) je možné zobrazit uživateli v diagramu a v průzkumníku jazyka a jsou přístupné prostřednictvím programového kódu. Vlastnosti se ale liší způsobem, jakým jsou jejich hodnoty uložené.

## <a name="kinds-of-domain-properties"></a>Typy vlastností domény
 V definici DSL můžete nastavit **Druh** vlastnosti domény, jak je uvedeno v následující tabulce:

|Druh vlastnosti domény|Description|
|-|-|
|**Standard** (výchozí)|Vlastnost domény, která je uložena v *obchodě a* serializován do souboru.|
|**Počítaný**|Vlastnost domény jen pro čtení, která není uložená v obchodě, ale počítá se z jiných hodnot.<br /><br /> Můžete například `Person.Age` vypočítat z `Person.BirthDate` .<br /><br /> Musíte zadat kód, který provádí výpočet. Obvykle vypočítáte hodnotu z jiných vlastností domény. Můžete ale také použít externí prostředky.|
|**Vlastní úložiště**|Vlastnost domény, která není uložena přímo v obchodě, ale může být nastavena i get.<br /><br /> Musíte zadat metody, které zadat a nastavit hodnotu.<br /><br /> Například může `Person.FullAddress` být uložen v , a `Person.StreetAddress` `Person.City` `Person.PostalCode` .<br /><br /> Můžete také přistupovat k externím prostředkům, například k získání a nastavení hodnot z databáze.<br /><br /> Pokud je hodnota true, váš kód by neměl v `Store.InUndoRedoOrRollback` obchodě nastavovat hodnoty. Viz [Transakce a vlastní sestavy.](#setters)|

## <a name="providing-the-code-for-a-calculated-or-custom-storage-property"></a>Poskytnutí kódu pro počítané nebo vlastní vlastnosti úložiště
 Pokud nastavíte vlastnost Druh domény na Počítané nebo Vlastní úložiště, musíte zadat metody přístupu. Když sestavíte řešení, zobrazí se v sestavě chyb informace o tom, co je potřeba.

#### <a name="to-define-a-calculated-or-custom-storage-property"></a>Definování počítané nebo vlastní vlastnosti úložiště

1. V souboru DslDefinition.dsl vyberte vlastnost domény v diagramu nebo v **Průzkumníku DSL.**

2. V okně **Vlastnosti** nastavte pole **Druh** na Calculated (Počítané) nebo Custom **Storage (Vlastní úložiště).** 

     Ujistěte se, že jste také **nastavili jeho Typ** na to, co chcete.

3. Klikněte **na Transformovat všechny** šablony na panelu nástrojů **Průzkumník řešení**.

4. V nabídce **Sestavení** klikněte na **Sestavit řešení**.

     Zobrazí se následující chybová zpráva:*Vaše třída* neobsahuje definici pro Get *YourProperty.*

5. Dvakrát klikněte na chybovou zprávu.

     Otevře se Dsl\GeneratedCode\DomainClasses.cs nebo DomainRelationships.cs. Nad zvýrazněnou voláním metody vás komentář vyzve k zadání implementace pro Get *YourProperty*().

    > [!NOTE]
    > Tento soubor se vygeneruje z dslDefinition.dsl. Pokud tento soubor upravíte, při příštím kliknutí na Transformovat **všechny** šablony se změny ztratí. Místo toho přidejte požadovanou metodu do samostatného souboru.

6. Vytvořte nebo otevřete soubor třídy v samostatné složce, například CustomCode \\ *YourDomainClass*.cs.

     Ujistěte se, že je obor názvů stejný jako ve vygenerované kódu.

7. V souboru třídy zapište částečnou implementaci třídy domény. Ve třídě napište definici chybějící metody, která `Get` se podobá následujícímu příkladu:

    ```
    namespace Company.FamilyTree
    {  public partial class Person
       {  int GetAgeValue()
          { return System.DateTime.Today.Year - this.BirthYear; }
    }  }
    ```

8. Pokud kind **(Druh)** **nastavíte na Custom Storage**(Vlastní úložiště), budete muset zadat také `Set` metodu . Příklad:

    ```
    void SetAgeValue(int value)
    { if (!Store.InUndoRedoOrRollback)
        this.BirthYear =
            System.DateTime.Today.Year - value; }
    ```

     Pokud je hodnota true, váš kód by neměl v `Store.InUndoRedoOrRollback` obchodě nastavovat hodnoty. Viz [Transakce a vlastní sestavy.](#setters)

9. Sestavte a spusťte řešení.

10. Otestujte vlastnost . Ujistěte se, že jste **zkusili vrátit zpět** **a znovu provést příkaz**.

## <a name="transactions-and-custom-setters"></a><a name="setters"></a> Transakce a vlastní sestavy
 V metodě Set vlastnosti Vlastní úložiště není nutné otevřít transakci, protože metoda je obvykle volána uvnitř aktivní transakce.

 Metoda Set však může být volána také v případě, že uživatel vyvolá Zpět nebo Znovu, nebo pokud transakce je vrácena zpět. Pokud <xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A> má hodnotu true, metoda Set by se měla chovat takto:

- Neměla by provádět změny v obchodě, například přiřazovat hodnoty jiným vlastnostem domény. Správce vrácení zpět nastaví své hodnoty.

- Měla by však aktualizovat všechny externí prostředky, například obsah databáze nebo souboru, nebo objekty mimo úložiště. Tím se ujistěte, že jsou udržovány v synchronizaci s hodnotami v obchodě.

  Příklad:

```
void SetAgeValue(int value)
{
  // If we are in Undo, no changes to Store objects:
  if (!this.Store.InUndoRedoOrRollback)
  {
    this.BirthYear = System.DateTime.Today.Year - value;
  }
  // But always update external objects:
  System.IO.File.WriteAllText(AgeFile, value);
}
```

 Další informace o transakcích najdete v tématu [Navigace a aktualizace modelu v kódu programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Viz také

- [Navigace v modelu a aktualizace modelu v kódu programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Vlastnosti vlastností domény](../modeling/properties-of-domain-properties.md)
- [Jak se definuje jazyk specifický pro doménu](../modeling/how-to-define-a-domain-specific-language.md)
