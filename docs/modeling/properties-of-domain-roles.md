---
title: Vlastnosti rolí domény
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 6b3078fdc54a5efa652d9de737559365cca7f58a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49927083"
---
# <a name="properties-of-domain-roles"></a>Vlastnosti rolí domény
Vlastnosti v následující tabulce jsou spojeny s rolí domény. Informace o rolích domény najdete v tématu [porozumění modelům, třídám a vztahům](../modeling/understanding-models-classes-and-relationships.md). Další informace o tom, jak pomocí těchto vlastností najdete v tématu [přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Vlastnost|Popis|Výchozí|
|-|-|-|
|Typ kolekce|Pokud tato role má násobnost 0.. * nebo 1.. \*, tato vlastnost přizpůsobí obecného typu, který se používá k ukládání kolekci odkazů.|`(none)` - <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601> se používá|
|Vlastní atributy|Atributy, které tady zadáte, se přidají jako atributy do třídy generovaného kódu.|< žádný\>|
|Je-li vlastnost Prohlížitelná|Pokud `True`, a pokud násobnost relací je 0.. 1 nebo 1..1, můžete procházet vlastnosti role uživatele v **vlastnosti** okna. Vlastnost název elementu na druhém konci vztahu odkazu.|`True`|
|Je generátor vlastnost|Pokud `True`, vlastnosti role se vygeneruje pro tuto roli, které můžete použít k procházení vztahů v kódu programu. Pokud nastavíte hodnotu false, mohou procházet relace méně efektivním způsobem pomocí statické metody doménového vztahu.|`True`|
|Modifikátor přístupu metody Getter vlastnosti|Modifikátor přístupu pro metodu getter vygenerované vlastnosti (`public`, `internal`, `private`, `protected`, nebo `protected internal`).|`public`|
|Modifikátor přístupu metody Setter vlastnosti|Modifikátor přístupu pro metodu setter vygenerované vlastnosti (`public`, `internal`, `private`, `protected`, nebo `protected internal`).|`public`|
|Násobnost|Počet elementů modelu, které můžete přehrát opačné role (`0..1`, `1..1`, `0..*`, nebo `1..*`). Pokud je násobnost `0..*` nebo `1..*`, pak představuje vygenerovaná vlastnost kolekci; jinak vygenerovaná vlastnost představuje prvek jednoho modelu.|Závisí na typu relace a zda je zdrojová nebo cílová role vztahu.|
|Název|Název role domény. Tato vlastnost nemůže obsahovat prázdné znaky.|Název doménová třída aktéra role pro tuto roli.|
|Rozšíří kopírování|`DoNotPropagateCopy` -Aktéra role zkopírovaný bude mít žádné kopii tohoto odkazu.<br /><br /> `PropagateCopyToLinkOnly` -Zkopírovaný odkaz směřuje ke stávající Aktér opačné role.<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer` -Zkopírovaný odkaz odkazuje na kopii aktéra opačné role.|`PropagateCopyToLinkAndOppositeRolePlayer` pro zdrojové role přepisovaných objektů.<br /><br /> `DoNotPropagateCopy` pro jiné role.<br /><br /> Další informace najdete v tématu [přizpůsobení chování kopírování](../modeling/customizing-copy-behavior.md)|
|Rozšíří Delete|`True` Chcete-li odstranit prvek, který přehraje tato role při odstraňování související odkaz.|`True` pro cíl vkládání role.<br /><br /> `False` pro jiné role.<br /><br /> Další informace najdete v tématu [přizpůsobení chování odstranění](../modeling/customizing-deletion-behavior.md).|
|Název vlastnosti|Název vlastnosti vygenerované v kódu aktéra role. Tento název nemůže obsahovat prázdné znaky.|Název opačné role, pokud se tato role má nulovou k jednomu jinému nebo násobnost 1: 1; v opačném případě pluralized název opačné role.|
|Aktér role|Doménová třída elementu, který můžete přehrát tuto roli v relaci. Tato vlastnost je pouze pro čtení.|Doménová třída aktéra role pro tuto roli.|
|Poznámky|Neformální poznámky, které jsou spojeny s rolí domény.|< žádný\>|
|Kategorie|Kategorie, ve které se zobrazuje vygenerovaná vlastnost v **vlastnosti** okna ve vygenerovaném návrháři. Pokud je tato vlastnost prázdná, pak vygenerované vlastnosti se zobrazí v části **různé** kategorie|< žádný\>|
|Popis|Popis, který se používá k dokumentaci kódu a používá se v uživatelském rozhraní vygenerovaného návrháře.<br /><br /> Popis se zobrazí v popisu tlačítka technologie IntelliSense pro vygenerovanou vlastnost na třídy aktéra role.|`Description for` *úplný název role*|
|Zobrazovaný název|Název, který se zobrazí ve vygenerovaném návrháři u role domény.|Upravená hodnota vlastnosti Name.|
|Klíčové slovo nápovědy|Nepovinné klíčové slovo, je použít k indexování nápovědy klávesy F1 pro role domény.|\<žádné >|
|Zobrazovaný název vlastnosti|Název, který se zobrazí ve vygenerovaném návrháři u vlastnosti vygenerované role.|Upravená hodnota vlastností názvu vlastnosti.|

> [!NOTE]
> Výchozí hodnota zobrazovaného názvu je založena na hodnotě přidružené vlastnosti vložením mezer před každý znak velká písmena, která předchází znak malé a, který není za nímž následuje jiný velké písmeno.

## <a name="see-also"></a>Viz také

- [Vlastnosti vztahů domény](../modeling/properties-of-domain-relationships.md)