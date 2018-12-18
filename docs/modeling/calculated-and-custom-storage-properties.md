---
title: Vypočtené a vlastní vlastnosti úložiště
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain properties
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: f54589d70bc7cab3959d7f0a7ad2a84d3b028754
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49877189"
---
# <a name="calculated-and-custom-storage-properties"></a>Vypočtené a vlastní vlastnosti úložiště
Všechny vlastnosti domény v jazyka specifického pro doménu (DSL) je možné zobrazit v diagramu a v Průzkumníku jazyk uživatele a je přístupný pomocí kódu programu. Vlastnosti se však liší v tak, že jejich hodnoty jsou uloženy.

## <a name="kinds-of-domain-properties"></a>Typy vlastností domény
 V definici DSL, můžete nastavit **druh** vlastnictví domény, jak je uvedeno v následující tabulce:

|Druh vlastnosti domény|Popis|
|-|-|
|**Standardní** (výchozí)|Doménová vlastnost, která se uloží do *ukládání* a serializovaná do souboru.|
|**Vypočítá**|Vlastnost domény jen pro čtení, není uložen v úložišti, které se počítá z jiných hodnot.<br /><br /> Například `Person.Age` může počítají na základě `Person.BirthDate`.<br /><br /> Je nutné zadat kód, který provede výpočet. Obvykle vypočítat hodnotu z jiné domény vlastnosti. Ale můžete také použít externí prostředky.|
|**Vlastní úložiště**|Doménová vlastnost, která se neuloží, přímo v úložišti, ale může být get a set.<br /><br /> Je nutné zadat metody, které získat a nastavit hodnotu.<br /><br /> Například `Person.FullAddress` by mohly být uloženy v `Person.StreetAddress`, `Person.City`, a `Person.PostalCode`.<br /><br /> Můžete také přístup k externím prostředkům, třeba když chcete získávat a nastavovat hodnoty z databáze.<br /><br /> Váš kód by neměl nastavit hodnoty v úložišti při `Store.InUndoRedoOrRollback` má hodnotu true. Zobrazit [transakce a vlastní nastavení](#setters).|

## <a name="providing-the-code-for-a-calculated-or-custom-storage-property"></a>Poskytuje kód pro vlastnost počítané nebo vlastní úložiště
 Pokud nastavíte typ doménová vlastnost, která chcete počítané nebo vlastní úložiště, je nutné zadat přístupové metody. Při sestavování řešení se zpráva o chybě říct, co je potřeba.

#### <a name="to-define-a-calculated-or-custom-storage-property"></a>Chcete-li definovat počítané nebo vlastní vlastnosti úložiště

1.  V DslDefinition.dsl, vyberte vlastnost domény v diagramu nebo v **Průzkumník DSL**.

2.  V **vlastnosti** okno, nastavte **druh** pole **vypočtené** nebo **vlastní úložiště**.

     Ujistěte se, že jste také nastavili své **typ** na co chcete.

3.  Klikněte na tlačítko **Transformovat všechny šablony** na panelu nástrojů **Průzkumníka řešení**.

4.  Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.

     Zobrazí následující chybová zpráva: "*YourClass* neobsahuje definici pro Get*YourProperty*."

5.  Klikněte dvakrát na chybovou zprávu.

     Dsl\GeneratedCode\DomainClasses.cs nebo DomainRelationships.cs otevře. Nad volání metody zvýrazněný, komentář vás vyzve k zadání implementace u metody Get*YourProperty*().

    > [!NOTE]
    >  Tento soubor je vygenerován z DslDefinition.dsl. Pokud jste tento soubor upravit, vaše změny budou ztraceny při příštím kliknutí na **Transformovat všechny šablony**. Místo toho přidejte požadovanou metodu v samostatném souboru.

6.  Vytvořte nebo otevřete soubor třídy do samostatné složky, například CustomCode\\*YourDomainClass*. cs.

     Ujistěte se, že obor názvů je stejný jako v generovaném kódu.

7.  Napište částečnou implementaci doménové třídy v souboru třídy. Ve třídě, zapsat definice pro chybějící `Get` metodu, která se podobá následujícímu příkladu:

    ```
    namespace Company.FamilyTree
    {  public partial class Person
       {  int GetAgeValue()
          { return System.DateTime.Today.Year - this.BirthYear; }
    }  }
    ```

8.  Pokud nastavíte **druh** k **vlastní úložiště**, budete taky muset zadat `Set` metoda. Příklad:

    ```
    void SetAgeValue(int value)
    { if (!Store.InUndoRedoOrRollback)
        this.BirthYear =
            System.DateTime.Today.Year - value; }
    ```

     Váš kód by neměl nastavit hodnoty v úložišti při `Store.InUndoRedoOrRollback` má hodnotu true. Zobrazit [transakce a vlastní nastavení](#setters).

9. Sestavte a spusťte řešení.

10. Otestujte vlastnost. Ujistěte se, že zkusíte **zpět** a **znovu**.

##  <a name="setters"></a> Transakce a vlastní nastavení
 Metoda Set vlastnosti vlastní úložiště není nutné spustíte transakci, protože je obvykle volána metoda v aktivní transakci.

 Ale metodu Set může také volat Pokud uživatel vyvolá zpět nebo znovu, nebo pokud transakce je vrácena zpět. Když <xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A> má hodnotu true, metodu Set by se měly chovat následovně:

- To by neměla provést změny v úložišti, jako je například přiřazení hodnoty k jiné vlastnosti domény. Správce akcí zpět nastaví jejich hodnoty.

- Ale to by měl aktualizovat všem externím prostředkům, jako jsou databáze nebo obsah souboru nebo objekty mimo úložiště. Tím se zajistí, že jsou uchovávány v synchronism s hodnotami v úložišti.

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

 Další informace o transakcích najdete v tématu [navigace a aktualizace modelu v programovém kódu](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Viz také

- [Navigace v modelu a aktualizace modelu v kódu programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Vlastnosti vlastností domény](../modeling/properties-of-domain-properties.md)
- [Jak se definuje jazyk specifický pro doménu](../modeling/how-to-define-a-domain-specific-language.md)