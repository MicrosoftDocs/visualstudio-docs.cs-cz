---
title: Vlastnosti vlastností domény
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain properties
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: debf263fa18d2a6af8e95ee959002686540e2c06
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658207"
---
# <a name="properties-of-domain-properties"></a>Vlastnosti vlastností domény
*Doménová vlastnost* je funkcí prvku modelu, který může obsahovat hodnotu. Například `Person` doménová třída může mít vlastnosti `Name` a `BirthDate`. V definici DSL jsou vlastnosti domény uvedené v poli doménová třída v diagramu a v části doménová třída v Průzkumníku DSL. Další informace najdete v tématu [Definování jazyka specifického pro doménu](../modeling/how-to-define-a-domain-specific-language.md).

> [!NOTE]
> Slovo "Property" obsahuje dva způsoby použití. *Doménová vlastnost* je funkce, kterou definujete pro doménovou třídu. Naproti tomu mnoho prvků DSL má *vlastnosti*, které jsou uvedeny v okně **vlastnosti** definice DSL. Například každá doménová vlastnost má sadu vlastností, které jsou popsány v tomto tématu.

 V době spuštění může uživatel při vytváření instancí doménové třídy zobrazit v okno Vlastnosti hodnoty vlastností domény a lze je zobrazit v obrazcích.

 Většina doménových vlastností je implementována jako běžné vlastnosti CLR. Nicméně z programovacího hlediska mají doménové vlastnosti širší funkčnost než běžné vlastnosti programu:

- Můžete definovat pravidla a události, které sledují stav vlastnosti. Další informace najdete v tématu [reagování na změny a šíření změn](../modeling/responding-to-and-propagating-changes.md).

- Transakce zabraňují nekonzistentním stavům. Další informace naleznete v tématu [navigace a aktualizace modelu v kódu programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

  Když vyberete doménovou vlastnost v diagramu nebo v Průzkumníku DSL, uvidíte v okno Vlastnosti následující položky. Další informace o tom, jak tyto položky použít, najdete v tématu [přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Vlastnost|Popis|Výchozí hodnota|
|-|-|-|
|**Popis**|Popis, který se používá k dokumentaci uživatelského rozhraní (UI) vygenerovaného návrháře.|\<none >|
|**Zobrazované jméno**|Název, který se zobrazí ve vygenerovaném návrháři pro tuto doménovou vlastnost. Může obsahovat mezery a interpunkční znaménka, například "název skladby".|\<none >|
|**Poskytovatel názvu elementu**|To platí jenom v případě, že jste nastavili `Is Element Name` na `true`. Můžete napsat kód, který poskytuje název nového prvku doménové třídy a přepisuje výchozí chování.<br /><br /> V souboru kódu v projektu DSL vytvořte třídu, která je odvozena z <xref:Microsoft.VisualStudio.Modeling.ElementNameProvider>.<br /><br /> Pak v Průzkumníku DSL klikněte pravým tlačítkem na kořen DSL a pak klikněte na Přidat externí typ. Zadejte název vaší třídy.<br /><br /> Znovu vyberte tuto vlastnost domény a v rozevíracím seznamu vyberte název třídy.|\<none >|
|**Modifikátor přístupu getter**|Úroveň přístupu doménové třídy (`public` nebo `internal`). Tento ovládací prvek určuje obor, ve kterém má kód programu přístup k vlastnosti.|`public`|
|**Klíčové slovo Help**|Volitelné klíčové slovo, které se používá k indexování Nápověda F1 pro tuto doménovou vlastnost.|\<none >|
|**Je Procházet**|Pokud je `True`, zobrazí se uživateli v okně Vlastnosti doménová vlastnost, když jsou modely této DSL otevřené.<br /><br /> Pokud je `False`, doménová vlastnost je v uživatelském rozhraní skrytá.<br /><br /> Pokud chcete vlastnost domain nastavit jako viditelnou, ale jen pro čtení, nastaví **se jako uživatelské rozhraní jen pro čtení**.|`True`|
|**Je název elementu**|Pokud `True`, tato doménová vlastnost se zobrazí jako název svého prvku modelu v Průzkumníku DSL.<br /><br /> Nové prvky modelu získají jedinečnou výchozí hodnotu pro tuto vlastnost. Pokud chcete určit, jak se tyto hodnoty generují, nastavte **poskytovatele názvu elementu**.|`False`|
|**Je pouze pro čtení uživatelského rozhraní**|Pokud `True`, hodnota vlastnosti doména se nedá změnit pomocí uživatelského rozhraní. Pořád ho můžou nastavit programy a zobrazí se v okno Vlastnosti.<br /><br /> Chcete-li skrýt vlastnost domény od uživatele, lze nastavit nastavení **Procházet**. Pokud chcete řídit přístup pomocí programů, nastavte **modifikátor přístupu setter**.|`False`|
|**Plnění**|Druh doménové vlastnosti (`Normal`, `Calculated` nebo `CustomStorage`). Další informace najdete v tématu věnovaném [vypočítaným a vlastním vlastnostem úložiště](../modeling/calculated-and-custom-storage-properties.md).|`Normal`|
|**Jméno**|Název této doménové vlastnosti. Musí to být platný identifikátor, například **SongTitle**.|\<none >|
|**Poznámky**|Neformální poznámky, které jsou spojeny s touto doménovou vlastností.|\<none >|
|**Modifikátor přístupu metody setter**|Modifikátor přístupu pro metodu setter. Tento ovládací prvek určuje rozsah, ve kterém může kód programu nastavit vlastnost.|`public`|
|**Textový**|Typ vlastnosti. Pokud chcete přidat seznam dostupných typů, klikněte pravým tlačítkem na kořen DSL v Průzkumníku DSL a pak klikněte na **Přidat externí typ**.|`String`|

## <a name="see-also"></a>Viz také

- [Glosář Nástroje DSL](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)