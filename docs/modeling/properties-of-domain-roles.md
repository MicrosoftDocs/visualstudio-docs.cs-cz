---
title: Vlastnosti rolí domény
description: Přečtěte si o vlastnostech přidružených k doméně domény, jako je typ kolekce, vlastní atributy a vlastnost, kterou lze procházet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6dda8e7c5538b0517c181a451072c4f8a9544965
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362337"
---
# <a name="properties-of-domain-roles"></a>Vlastnosti rolí domény
Vlastnosti v následující tabulce jsou spojeny s doménovou rolí. Informace o doménových rolích najdete v tématu [porozumění modelům, třídám a vztahům](../modeling/understanding-models-classes-and-relationships.md). Další informace o tom, jak tyto vlastnosti použít, najdete v tématu [přizpůsobení a rozšíření Domain-Specificho jazyka](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Vlastnost|Popis|Výchozí|
|-|-|-|
|Typ kolekce|Pokud má tato role násobnost 0.. * nebo 1.. \* , tato vlastnost přizpůsobí obecný typ, který se používá k uložení kolekce odkazů.|`(none)` - <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601> se používá|
|Vlastní atributy|Atributy, které zde zadáte, budou přidány jako atributy do generované třídy kódu.|<žádné\>|
|Má procházet vlastnost|Pokud `True` , a pokud je násobnost relace 0.. 1 nebo 1.. 1, vlastnost role může procházet uživatel v okně **vlastnosti** . Vlastnost zobrazuje název elementu na druhém konci odkazu relace.|`True`|
|Je generátorem vlastností|Pokud `True` je pro tuto roli vygenerována vlastnost role, kterou můžete použít k procházení relace v kódu programu. Pokud nastavíte tuto hodnotu false, můžete relaci v méně efektivním způsobu procházet pomocí statických metod doménové relace.|`True`|
|Modifikátor přístupu getter vlastnosti|Modifikátor přístupu pro metodu getter pro generovanou vlastnost ( `public` ,,, `internal` `private` `protected` nebo `protected internal` ).|`public`|
|Modifikátor přístupu metody set vlastnosti|Modifikátor přístupu pro metodu setter pro generovanou vlastnost ( `public` ,,, `internal` `private` `protected` nebo `protected internal` ).|`public`|
|Násobnost|Počet prvků modelu, které mohou hrát opačnou roli ( `0..1` ,, `1..1` `0..*` nebo `1..*` ). Pokud je násobnost `0..*` nebo `1..*` , pak vygenerovaná vlastnost představuje kolekci. v opačném případě vygenerovaná vlastnost představuje jeden prvek modelu.|Závisí na typu vztahu a na tom, zda se jedná o zdrojovou nebo cílovou roli v relaci.|
|Název|Název role domény Tato vlastnost nemůže obsahovat prázdný znak.|Název třídy domény aktéra role pro tuto roli.|
|Šíří kopii|`DoNotPropagateCopy` -Zkopírovaný aktér role nebude mít žádnou kopii tohoto odkazu.<br /><br /> `PropagateCopyToLinkOnly` – Zkopírovaný odkaz odkazuje na existující aktéra opačné role.<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer` – Kopírovaný odkaz odkazuje na kopii aktéra opačné role.|`PropagateCopyToLinkAndOppositeRolePlayer` pro zdrojové role vložení.<br /><br /> `DoNotPropagateCopy` pro jiné role.<br /><br /> Další informace najdete v tématu [přizpůsobení chování kopírování](../modeling/customizing-copy-behavior.md) .|
|Šíří odstranění|`True` Chcete-li odstranit prvek, který tuto roli přehraje při odstranění přidruženého odkazu.|`True` pro cíl role vložení.<br /><br /> `False` pro jiné role.|
|Název vlastnosti|Název vlastnosti generované v kódu aktéra role Tento název nemůže obsahovat prázdný znak.|Název opačné role, pokud má tato role násobnost 0 – jedna nebo jedna ku 1; jinak se jedná o plurální název opačné role.|
|Aktér role|Doménová třída elementu, který může tuto roli v relaci přehrát. Tato vlastnost je jen ke čtení.|Doménová třída aktéra role pro tuto roli|
|Poznámky|Neformální poznámky, které jsou spojeny s doménovou rolí.|<žádné\>|
|Kategorie|Kategorie, pod kterou se vygenerovaná vlastnost zobrazuje v okně **vlastnosti** ve vygenerovaném návrháři. Pokud je tato vlastnost prázdná, zobrazí se v kategorii **různé** kategorie vygenerované vlastnosti.|<žádné\>|
|Popis|Popis, který se používá k dokumentu kódu a který se používá v uživatelském rozhraní vygenerovaného návrháře.<br /><br /> Popis se zobrazí v popisku IntelliSense pro generovanou vlastnost třídy aktéra role.|`Description for`*úplný název role*|
|Zobrazovaný název|Název, který se zobrazí ve vygenerovaném návrháři pro doménovou roli.|Upravená hodnota vlastnosti Name|
|Klíčové slovo Help|Volitelné klíčové slovo, které se používá k indexování Nápověda F1 pro doménovou roli.|\<none>|
|Zobrazovaný název vlastnosti|Název, který se zobrazí ve vygenerovaném návrháři pro vlastnost vygenerované role.|Upravená hodnota vlastnosti názvu vlastnosti.|

> [!NOTE]
> Výchozí hodnota zobrazovaného názvu je založena na přidružené hodnotě vlastnosti vložením mezer před jednotlivá velká písmena, která předchází znakům malých písmen a za kterými nenásleduje další znak velká písmena.

## <a name="see-also"></a>Viz také:

- [Vlastnosti vztahů domény](../modeling/properties-of-domain-relationships.md)