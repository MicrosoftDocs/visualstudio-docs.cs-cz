---
title: Řízení viditelnosti ikony nebo Dekorátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2697fd5d-b936-4b6b-b87b-be64825dc7a4
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 4befc49fab1d1b53d70f1b79ee1a2bbe96be11f1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49913407"
---
# <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Řízení viditelnosti ikony či dekorátoru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A *dekoratér* je ikona nebo řádek textu, který se zobrazí na tvar z jazyka specifického pro doménu (DSL). Můžete provést dekoratéru zobrazují a zmizí v závislosti na stavu vlastnosti v modelu. Například pro obrazec představující osoby, může mít jiné ikony, které se zobrazí v závislosti na osoby pohlaví, počet podřízených a tak dále.  
  
## <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Řízení viditelnosti ikony nebo dekorátoru  
 Následující postup předpokládá, že jsou již definovány obrazec a jejich mapování na doménovou třídu. Další informace najdete v tématu [jak se definuje jazyk specifický pro doménu](../modeling/how-to-define-a-domain-specific-language.md).  
  
#### <a name="to-control-the-visibility-of-an-icon-or-text-decorator"></a>Řízení viditelnosti ikony nebo text dekoratér  
  
1. V definici DSL diagramu přidejte do třídy tvar ikony nebo dekoratéry textu, které se mají zobrazit.  
  
   1.  Klikněte pravým tlačítkem na třídu tvar, přejděte na **přidat**a potom klikněte na požadovaný typ dekoratér.  
  
   2.  Nastavte dekoratér **pozice** vlastnost. Více než jeden dekoratér může mít na stejné pozici. Například můžete mít ikony pro muže a ženy, sdílení na stejné pozici.  
  
   3.  Nastavte **výchozí ikona** vlastnost dekoratér ikony.  
  
2. Vyberte mapa elementu diagramu, který je Šedá čára mezi obrazec třídy a třídy domény na diagramem definice DSL.  
  
3. V okně podrobností DSL v **mapování Dekoratéru** kartu, vyberte dekoratér. Například MaleDecorator.  
  
4. Zkontrolujte, **filtr viditelnosti** pole.  
  
5. Pokud je doménová vlastnost, která by měla řídit viditelnost na okamžité doménová třída, ponechejte **cesta k vlastnosti filtru** prázdné.  
  
    V opačném případě klikněte na rozevírací nabídku a přejděte do relace nebo třídy, kde se nachází vlastnost.  
  
   -   Aby se zabránilo zprávu o chybách, by neměla procházet relace označené "*" v nástroji pro navigaci.  
  
6. Nastavte **vlastnost filtru** k doménové vlastnosti. Třeba pohlaví.  
  
7. V **záznamy viditelnosti** seznamu, přidejte hodnoty této vlastnosti domény, pro který by měl být dekoratér viditelný. Například muže.  
  
8. Opakujte kroky pro jednotlivé ikony.  
  
9. **Transformovat všechny šablony**, sestavení a spuštění a otevřete diagram testu.  
  
10. Když změníte řídicí hodnotu vlastnosti, by měl dekoratéry se zobrazí a zmizí.  
  
    Často budete chtít viditelnost kontrolován vzorec složitější než jednoduché sady hodnot. Například v ikony závisí na počtu odkazů určitého typu, nebo k němu závisí na tom, zda je číslo v určitém rozsahu. V takovém případě použijte následující postup.  
  
#### <a name="to-control-the-visibility-of-a-decorator-based-on-a-formula"></a>Řízení viditelnosti dekorátoru podle vzorce  
  
1.  Přidáte počítané doménová vlastnost, která do doménové třídy. V **vlastnosti** okno, nastavte následující hodnoty:  
  
     **IsBrowsable =**`False`**-skryje vlastnost od uživatele**  
  
     **Typ =**`Calculated`**– to znamená, že zadáte kód, který vypočítá její hodnotu**  
  
     **Název** například **DecoratorControl**  
  
     **Typ** = `Boolean`  
  
     Další informace najdete v tématu [vypočtené a vlastní vlastnosti úložiště](../modeling/calculated-and-custom-storage-properties.md).  
  
2.  Vytvořit novou vlastnost řízení viditelnosti dekorátoru.  
  
    1.  Vyberte mapa elementu diagramu, který je Šedá čára z doménové třídy na obrazec. V **podrobnosti DSL** otevřené okno **DecoratorMap** kartu.  
  
    2.  Zkontrolujte, **filtr viditelnosti** pole.  
  
    3.  V **vlastnost filtru**, vyberte vlastnosti ovládacího prvku **DecoratorControl**.  
  
    4.  V části **záznamy viditelnosti**, zadejte `True`.  
  
3.  Klikněte na tlačítko **Transformovat všechny šablony** v panelu nástrojů Průzkumníka řešení.  
  
4.  Klikněte na tlačítko **sestavit řešení** na **sestavení** nabídky.  
  
5.  Dvakrát klikněte na panel zprávy o chybách, které se má zobrazovalo: "*YourClass* neobsahuje definici pro GetDecoratorControlValue...".  
  
     Do textového editoru se otevře na Dsl\GeneratedCode\DomainClasses.cs. Nad zvýrazněnou chybu je komentář, který budete vyzváni k přidání metody.  
  
6.  Poznámka: obor názvů, třídy a metody, které nebyly nalezeny.  Například Company.FamilyTree.Person.GetDecoratorControlValue().  
  
7.  V samostatném souboru kódu zápis, který obsahuje metodu chybí definice částečné třídy. Příklad:  
  
    ```  
    namespace Company.FamilyTree  
    { partial class Person  
      { bool GetDecoratorControlValue()  
        {  
          return this.Children.Count > 0;  
    } } }  
    ```  
  
     Další informace o přizpůsobení modelu pomocí kódu programu najdete v tématu [navigace a aktualizace modelu v programovém kódu](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
8.  Znovu sestavte a spusťte řešení.  
  
## <a name="see-also"></a>Viz také  
 [Definování obrazců a konektorů](../modeling/defining-shapes-and-connectors.md)   
 [Nastavení obrázku pozadí v diagramu](../modeling/setting-a-background-image-on-a-diagram.md)   
 [Procházení a aktualizace modelu v programovém kódu](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Zápis kódu pro úpravu jazyka specifického pro doménu](../modeling/writing-code-to-customise-a-domain-specific-language.md)



