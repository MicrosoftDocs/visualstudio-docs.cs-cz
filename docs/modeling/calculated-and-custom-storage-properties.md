---
title: Vypočtené a vlastní vlastnosti úložiště
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain properties
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 52915f0bac2bd172daf909541ecfa86396d90a5d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "76115194"
---
# <a name="calculated-and-custom-storage-properties"></a>Vypočtené a vlastní vlastnosti úložiště
Všechny vlastnosti domény v jazyce DSL (Domain Specific Language) lze zobrazit uživateli v diagramu a ve vašem jazykovém Průzkumníku a lze k němu přistupovat prostřednictvím kódu programu. Vlastnosti se ale liší ve způsobu, jakým jsou uložené jejich hodnoty.

## <a name="kinds-of-domain-properties"></a>Typy doménových vlastností
 V definici DSL můžete nastavit **druh** doménové vlastnosti, jak je uvedeno v následující tabulce:

|Druh doménové vlastnosti|Popis|
|-|-|
|**Standardní** (výchozí)|Doménová vlastnost, která je uložena v *úložišti* a serializována do souboru.|
|**Počítaný**|Vlastnost domény jen pro čtení, která není uložena v úložišti, ale je počítána z jiných hodnot.<br /><br /> Například `Person.Age` lze vypočítat z `Person.BirthDate` .<br /><br /> Je nutné zadat kód, který provede výpočet. Obvykle se počítá hodnota z jiných doménových vlastností. Můžete ale také použít externí prostředky.|
|**Vlastní úložiště**|Doménová vlastnost, která se neukládá přímo do úložiště, ale může být Get i set.<br /><br /> Je nutné zadat metody, které získají a nastavují hodnotu.<br /><br /> Například `Person.FullAddress` může být uložen v `Person.StreetAddress` , `Person.City` a `Person.PostalCode` .<br /><br /> Můžete také získat přístup k externím prostředkům, například k získání a nastavení hodnot z databáze.<br /><br /> Váš kód by neměl nastavovat hodnoty v úložišti, pokud `Store.InUndoRedoOrRollback` má hodnotu true. Viz [transakce a vlastní settery](#setters).|

## <a name="providing-the-code-for-a-calculated-or-custom-storage-property"></a>Poskytnutí kódu pro vypočítanou nebo vlastní vlastnost úložiště
 Pokud nastavíte druh doménové vlastnosti na počítané nebo vlastní úložiště, budete muset zadat přístupové metody. Při sestavování řešení vám zpráva o chybě bude informovat o tom, co je potřeba.

#### <a name="to-define-a-calculated-or-custom-storage-property"></a>Definování vypočítané nebo vlastní vlastnosti úložiště

1. V DslDefinition. DSL vyberte vlastnost doména buď v diagramu, nebo v **Průzkumníku DSL**.

2. V okně **vlastnosti** nastavte pole **druh** na **počítané** nebo **vlastní úložiště**.

     Ujistěte se, že jste také nastavili svůj **typ** na to, co chcete.

3. Klikněte na možnost **transformovat všechny šablony** na panelu nástrojů **Průzkumník řešení**.

4. V nabídce **Sestavení** klikněte na **Sestavit řešení**.

     Zobrazí se následující chybová zpráva: "*YourClass* neobsahuje definici pro Get*YourProperty*".

5. Dvakrát klikněte na chybovou zprávu.

     Otevře se Dsl\GeneratedCode\DomainClasses.cs nebo DomainRelationships.cs. Nad zvýrazněným voláním metody komentář vás vyzve k poskytnutí implementace pro Get*YourProperty*().

    > [!NOTE]
    > Tento soubor je vygenerovaný z DslDefinition. DSL. Pokud tento soubor upravíte, změny budou při příštím kliknutí na **transformovat všechny šablony**ztraceny. Místo toho přidejte požadovanou metodu do samostatného souboru.

6. Vytvořte nebo otevřete soubor třídy v samostatné složce, například CustomCode \\ *YourDomainClass*. cs.

     Ujistěte se, že obor názvů je stejný jako ve vygenerovaném kódu.

7. V souboru třídy zapište částečnou implementaci doménové třídy. Ve třídě napište definici pro chybějící `Get` metodu, která se podobá následujícímu příkladu:

    ```
    namespace Company.FamilyTree
    {  public partial class Person
       {  int GetAgeValue()
          { return System.DateTime.Today.Year - this.BirthYear; }
    }  }
    ```

8. Pokud nastavíte **druh** na **vlastní úložiště**, budete také muset zadat `Set` metodu. Příklad:

    ```
    void SetAgeValue(int value)
    { if (!Store.InUndoRedoOrRollback)
        this.BirthYear =
            System.DateTime.Today.Year - value; }
    ```

     Váš kód by neměl nastavovat hodnoty v úložišti, pokud `Store.InUndoRedoOrRollback` má hodnotu true. Viz [transakce a vlastní settery](#setters).

9. Sestavte a spusťte řešení.

10. Otestujte vlastnost. Ujistěte se, že se pokusíte **vrátit zpět** a **znovu provést**akci.

## <a name="transactions-and-custom-setters"></a><a name="setters"></a> Transakce a vlastní Settery
 V metodě set vlastnosti vlastního úložiště není nutné otevřít transakci, protože metoda je obvykle volána uvnitř aktivní transakce.

 Nicméně Metoda set může být volána také v případě, že uživatel vyvolá vrácení akce zpět nebo znovu, nebo pokud transakce je vrácena zpět. Když <xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A> má hodnotu true, vaše metoda Set by se měla chovat takto:

- V tomto úložišti by se neměly dělat změny, jako je například přiřazení hodnot k jiným doménovým vlastnostem. Správce vrácení zpět nastaví své hodnoty.

- Měla by však aktualizovat jakékoli externí prostředky, jako jsou databáze nebo soubory nebo objekty mimo úložiště. Tím zajistíte, že se budou uchovávat v synchronism s hodnotami ve Storu.

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

 Další informace o transakcích naleznete v tématu [navigace a aktualizace modelu v kódu programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Viz také

- [Navigace v modelu a aktualizace modelu v kódu programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Vlastnosti vlastností domény](../modeling/properties-of-domain-properties.md)
- [Jak se definuje jazyk specifický pro doménu](../modeling/how-to-define-a-domain-specific-language.md)
