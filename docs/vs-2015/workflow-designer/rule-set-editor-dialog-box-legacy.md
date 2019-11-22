---
title: Dialogové okno editor sad pravidel (starší verze) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleSetDialog.UI
helpviewer_keywords:
- Rule Set Editor dialog box
ms.assetid: 7cfd5df1-1115-4e5c-9b72-121f39419e83
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 83cdd4f549655be524abdd2a4708b316f6747b3e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302756"
---
# <a name="rule-set-editor-dialog-box-legacy"></a>Dialogové okno Editor sad pravidel (starší verze)
Toto téma popisuje, jak používat dialogové okno **editor sad pravidel** ve starších [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Použijte starší [!INCLUDE[wfd2](../includes/wfd2-md.md)] potřeba cílit na platformu [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Dialogové okno **editor sad pravidel** se používá k vytváření a úpravám [sady](https://go.microsoft.com/fwlink?LinkID=65019) sad pravidel, které jsou serializovány do souboru. Rules.

> [!NOTE]
> Chcete-li otevřít soubor. Rules s **editorem XML s kódováním**, je nutné nejprve zavřít přidružené okno návrháře pro pracovní postup nebo aktivitu.

 Informace o tom, jak získat přístup k dialogovému oknu **editor sad pravidel** , naleznete v tématu [How to: Create a sady Rule Set (starší verze)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md).

> [!WARNING]
> Editor pravidel pro starší [!INCLUDE[wfd2](../includes/wfd2-md.md)], který se používá k cílení na [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] nepodporuje cílení na více verzí.

 Následující tabulka popisuje prvky uživatelského rozhraní (UI) v dialogovém okně **Editor sady pravidel** .

|Prvek uživatelského rozhraní (UI)|Popis|
|----------------|-----------------|
|**Přidat pravidlo**|Přidá do sady pravidel novou definici pravidla.|
|**Odstranění**|Odstraní vybrané pravidlo ze sady pravidel.|
|**Řetězení**|Určuje, který typ předávaného řetězení použít se sadou pravidel. K dispozici jsou tyto možnosti:<br /><br /> -   **úplné řetězení**, které určuje, že se mají použít všechny mechanismy pro dopředné řetězení: implicitní, přidávané metody a explicitní pomocí funkce **Update** .<br />-   **sekvenční**, které určuje, že se nemá používat žádný řetěz dopředné řetězení.<br />-   **pouze explicitní aktualizace**, která určuje, že se má provést pouze předávací řetěz při akcích **aktualizace** .<br /><br /> Další informace o dopřední řetězení najdete v tématu [použití aktivity sady](https://go.microsoft.com/fwlink?LinkID=65004).|
|**Název**|Záhlaví sloupce seznamu sad pravidel Kliknutím seřadíte seznam pravidel podle názvu.|
|**Priorita**|Záhlaví sloupce seznamu sad pravidel Kliknutím seřadíte seznam pravidel podle priority.|
|**Nového vyhodnocení**|Záhlaví sloupce seznamu sad pravidel Kliknutím seřadíte seznam pravidel podle typu opětovného vyhodnocení.|
|**Náhled pravidla**|Záhlaví sloupce seznamu sad pravidel Kliknutím seřadíte seznam pravidel ve verzi Preview podmínky a akcí pravidla.|
|**Jméno:**|Zadejte název pravidla.|
|**Upřednostněn**|Zadejte prioritu pravidla. Výchozí priorita je 0.|
|**Nového vyhodnocení**|Určuje typ opětovného vyhodnocení pravidla, které se má použít s pravidlem. K dispozici jsou tyto možnosti:<br /><br /> -   **vždy**, což způsobí, že pravidlo bude v případě potřeby znovu vyhodnoceno.<br />-   **nikdy**, což způsobí, že se pravidlo nikdy nevyhodnotí. V takovém případě se pravidlo spustí jenom jednou.|
|**Aktivně**|Ověřte, že je pravidlo aktivní.|
|**Pomocné**|Zadejte výraz pro podmínku pravidla. Informace o syntaxi výrazu naleznete v části "zadávání výrazů podmínek a akcí" na této stránce.|
|**Pak akce:**|Zadejte výraz pro akce. Informace o syntaxi výrazu naleznete v části "zadávání výrazů podmínek a akcí" na této stránce.|
|**Další akce:**|Zadejte výraz pro akce else. Informace o syntaxi výrazu naleznete v části "zadávání výrazů podmínek a akcí" na této stránce.|
|**OK**|Kliknutím uložíte sadu pravidel do souboru. Rules.|

 Další informace o sadách pravidel najdete v tématu [použití aktivity sady](https://go.microsoft.com/fwlink?LinkID=65004).

## <a name="entering-condition-and-action-expressions"></a>Zadání výrazů podmínky a akce
 Do příslušných textových polí v dialogovém okně **editor sad pravidel** zadáte výrazy pro podmínky a akce then a else jako text. Tuto možnost můžete zadat **.** do editoru pro odkaz na pole, vlastnosti a metody použité v pracovním postupu pomocí typu nabídky technologie IntelliSense. Případně můžete zadat název člena pracovního postupu přímo. Statické metody lze volat na odkazované typy zadáním názvu třídy následovaného názvem metody.

 Do podmínky můžete přidat logické operátory, jako například a, nebo, nikoli. Můžete také přidat predikáty. Predikát je binární operátor a dva operandy. Podporované binární operátory jsou = =, >, \<, > = a < =. Podporované operandy jsou konstantní hodnota, Aritmetická funkce a obor veřejných členů.

 Můžete zadat typ porovnání a můžete porovnat s **hodnotou null** nebo prázdným řetězcem. Můžete vnořit volání členů na proměnnou, která obsahuje komplexní typ, například `this.Address.State == "WA"`.

 Výrazy podporují následující operátory:

- Relační operátory: = =, =,! =

- Operátory porovnání: <, \<=, >, > =

- Aritmetické operátory: +,-, *,/, MOD

- Logické operátory: a, & &, nebo, &#124; &#124;, not,!

- Bitové operátory: &,&#124;

  Priorita operátora výrazu C# sleduje pravidla priority operátora.

  Další informace o podmínkách najdete v tématu [použití podmínek v pracovních postupech](https://msdn.microsoft.com/541211f5-d382-4810-894f-71f00b34fa77).

### <a name="halt-and-update-functions"></a>Zastavení a aktualizace funkcí
 Akce **:** a **Else akce:** výrazy podporují funkci **zastavit** a **aktualizovat** . Chcete **-li použít funkci** zablokovat, zadejte příkaz **zastavit** do **akce:** nebo **Else Action:** textové pole. Akce **zastavení** způsobí, že spuštění sady pravidel se okamžitě zastaví a vrátí se řízení k volajícímu kódu. Použijete funkci **Update** s doposíláním řetězení.

 Příkaz **Update** lze vyjádřit v editoru v jedné ze dvou forem. v následujícím příkladu jsou uvedeny oba formuláře:

```
Update(this.Address.State)
Update("this/Address/State")
```

 Další informace o použití **Update** s dopředné řetězení najdete v tématu [použití aktivity sady](https://go.microsoft.com/fwlink?LinkID=65004).

## <a name="see-also"></a>Viz také
 [Sady](https://go.microsoft.com/fwlink?LinkID=65019) [– dialogové okno vybrat sadu pravidel (starší verze)](../workflow-designer/select-rule-set-dialog-box-legacy.md) [s použitím aktivity sady](https://go.microsoft.com/fwlink?LinkID=65004) [pomocí podmínek v pracovních postupech](https://go.microsoft.com/fwlink?LinkID=65009)