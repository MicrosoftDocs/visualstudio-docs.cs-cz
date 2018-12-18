---
title: Vlastnosti vlastností domény
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain properties
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 431dad2f87fdd5857c91b39152d7f119945c0867
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "50966509"
---
# <a name="properties-of-domain-properties"></a>Vlastnosti vlastností domény
A *doménovou vlastnost* je funkce, které může obsahovat hodnotu prvku modelu. Například `Person` doménová třída může mít vlastnosti `Name` a `BirthDate`. V definici DSL vlastnosti domény patří do domény pole třídy v diagramu a v rámci doménové třídy v Průzkumníku DSL. Další informace najdete v tématu [jak se definuje jazyk specifický pro doménu](../modeling/how-to-define-a-domain-specific-language.md).

> [!NOTE]
>  Slovo "vlastnosti" má dvě použití. A *doménovou vlastnost* je funkce, které definujete na doménovou třídu. Naopak mají mnoho prvků DSL *vlastnosti*, které jsou uvedeny v **vlastnosti** okno v definici DSL. Například každá vlastnost domény má sadu vlastností, které jsou popsány v tomto tématu.

 V době běhu, když uživatel vytvoří instance třídy domény, hodnoty vlastnosti domény můžete zobrazit v okně Vlastnosti a lze zobrazit na tvary.

 Většina vlastností domény jsou implementovány jako běžné vlastnosti CLR. Z programovací pohledu, mají vlastnosti domény bohatší funkcí než normální program vlastnosti:

- Můžete definovat pravidla a události, které monitorují stav vlastnosti. Další informace najdete v tématu [šířící změny a reakce na](../modeling/responding-to-and-propagating-changes.md).

- Transakce zabránit nekonzistentní stavy. Další informace najdete v tématu [navigace a aktualizace modelu v programovém kódu](../modeling/navigating-and-updating-a-model-in-program-code.md).

  Když vyberete doménová vlastnost, která v diagramu nebo v Průzkumníku DSL, zobrazí se následující položky v okně Vlastnosti. Další informace o tom, jak používat tyto položky, naleznete v tématu [přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Vlastnost|Popis|Výchozí hodnota|
|-|-|-|
|**Popis**|Popis, který se používá k dokumentu uživatelského rozhraní (UI) vygenerovaného návrháře.|\<žádné >|
|**Zobrazovaný název**|Název, který se zobrazí ve vygenerovaném návrháři u této vlastnosti domény. Může obsahovat mezery a interpunkční znaménka, například "skladby Title".|\<žádné >|
|**Poskytovatel názvů elementů**|To platí jenom v případě, že jste nastavili `Is Element Name` k `true`. Můžete napsat kód, který poskytuje název pro nový prvek doménové třídy přepisuje výchozí chování.<br /><br /> V souboru kódu v projektu DSL, vytvořte třídu, která je odvozena od <xref:Microsoft.VisualStudio.Modeling.ElementNameProvider>.<br /><br /> Potom v Průzkumník DSL, klikněte pravým tlačítkem na kořenový DSL a klikněte na tlačítko Přidat externí. Zadejte název vaší třídy.<br /><br /> Znovu vyberte tento doménová vlastnost a v rozevíracím seznamu vyberte název třídy.|\<žádné >|
|**Modifikátor přístupu metody getter**|Úroveň přístupu doménové třídy (`public` nebo `internal`). Tato volba určuje obor, ve které program kód může přistupovat k vlastnosti.|`public`|
|**Klíčové slovo nápovědy**|Nepovinné klíčové slovo, je použít k indexování nápovědy klávesy F1 pro tuto doménovou vlastnost.|\<žádné >|
|**Je nelze procházet**|Pokud `True`, doménovou vlastnost se zobrazí uživatelům v okně Vlastnosti, pokud modely tento DSL otevřít.<br /><br /> Pokud `False`, vlastnost domain skryt v uživatelském rozhraní.<br /><br /> Pokud chcete, aby vlastnost domain zobrazena, ale jen pro čtení, nastavte **je jen pro čtení uživatelského rozhraní**.|`True`|
|**Je název elementu**|Pokud `True`, tato vlastnost domény se zobrazí jako název jeho element modelu v Průzkumníku DSL.<br /><br /> Nové prvky modelu, získají jedinečné výchozí hodnotu pro tuto vlastnost. Pokud chcete řídit, jak vygenerovat tyto hodnoty, nastavte **poskytovatel názvů elementů**.|`False`|
|**Je uživatelské rozhraní jen pro čtení**|Pokud `True`, nelze změnit hodnoty vlastnosti domény pomocí uživatelského rozhraní. Je stále možné nastavit programy a se nebude zobrazovat v okně Vlastnosti.<br /><br /> Pokud chcete skrýt doménová vlastnost od uživatele, nastavte **je Prohlížitelná**. Pokud chcete k řízení přístupu podle aplikací, nastavte **modifikátor přístupu metody Setter**.|`False`|
|**Typ**|Druh vlastnosti domény (`Normal`, `Calculated`, nebo `CustomStorage`). Další informace najdete v tématu [vypočtené a vlastní vlastnosti úložiště](../modeling/calculated-and-custom-storage-properties.md).|`Normal`|
|**Jméno**|Název této vlastnosti domény. Musí být platný identifikátor, příklad **SongTitle**.|\<žádné >|
|**Poznámky**|Neformální poznámky, které jsou spojené s touto vlastností domény.|\<žádné >|
|**Modifikátor přístupu metody setter**|Modifikátor přístupu pro metodu setter. Tato volba určuje obor, v programu, který kód můžete nastavit vlastnost.|`public`|
|**Typ**|Typ vlastnosti. Pokud chcete přidat do seznamu dostupných typů, klikněte pravým tlačítkem na kořenový DSL v Průzkumník DSL a klikněte na tlačítko **přidat externí**.|`String`|

## <a name="see-also"></a>Viz také

- [Glosář nástrojů jazyka specifického pro doménu](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)