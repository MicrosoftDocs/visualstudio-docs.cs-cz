---
title: Přizpůsobení popisků pro ovládací prvky vázané na data
ms.date: 11/03/2017
ms.topic: conceptual
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: f7780cfb3b266de6f477e74d1b352cf6b24aab42
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76113657"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Úprava způsobu, kterým Visual Studio vytváří titulky pro ovládací prvky vázané daty

Při přetahování položek z [okna zdroje dat](add-new-data-sources.md#data-sources-window) do návrháře se dorazí na zvláštní pozornost: názvy sloupců v popiscích titulků se přeformátují na čitelnější řetězec, když se zjistí dvě nebo více slov, která se mají zřetězit dohromady.

::: moniker range="vs-2017"

Způsob, jakým se tyto popisky vytvářejí, můžete přizpůsobit nastavením hodnot **SmartCaptionExpression**, **SmartCaptionReplacement**a **SmartCaptionSuffix** v klíči registru **HKEY_CURRENT_USER \software\microsoft\visualstudio\15.0\Data Designs** .

::: moniker-end

::: moniker range=">=vs-2019"

Způsob, jakým se tyto popisky vytvářejí, můžete přizpůsobit nastavením hodnot **SmartCaptionExpression**, **SmartCaptionReplacement**a **SmartCaptionSuffix** v klíči registru **HKEY_CURRENT_USER \software\microsoft\visualstudio\16.0\Data Designs** .

::: moniker-end

> [!NOTE]
> Tento klíč registru neexistuje, dokud ho vytvoříte.

Inteligentní titulky řídí regulárních výrazů do hodnoty **SmartCaptionExpression** hodnotu. Přidávání **návrháře dat** klíč registru přepisuje výchozí regulární výraz, který řídí titulků. Další informace o regulárních výrazech naleznete v tématu [použití regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

Následující tabulka popisuje hodnoty registru, které řídí titulků.

|Položky registru|Popis|
|-------------------|-----------------|
|**SmartCaptionExpression**|Regulární výraz, který použijete pro shodu se vzorem.|
|**SmartCaptionReplacement**|Formát, který se zobrazí všechny skupiny se shodou v **SmartCaptionExpression**.|
|**SmartCaptionSuffix**|Volitelný řetězec pro připojení za účelem titulek.|

Následující tabulka uvádí vnitřní výchozí nastavení pro tyto hodnoty registru.

|Položky registru|Výchozí hodnota|Vysvětlení|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|**(\\\p{Ll})(\\\p{Lu})&#124;_+**|Odpovídá znak malého písmene, za nímž následuje velkým písmenem nebo podtržítkem.|
|**SmartCaptionReplacement**|**$1 $2**|**$1** představuje všechny znaky, které odpovídají v první závorce výrazu, a **$2** představuje všechny znaky, které odpovídají v druhých závorkách. Nahrazení je první shodu, mezeru a druhý shoda.|
|**SmartCaptionSuffix**|**:**|Hodnota představuje znak připojenou k vráceného řetězce. Například, pokud je popisek `Company Name`, přípona umožňuje `Company Name:`|

> [!CAUTION]
> Při cokoli v editoru registru Buďte velmi opatrní. Registr zálohovali začnete upravovat. Pokud Editor registru používán správně, můžete způsobit vážné problémy, které mohou vyžadovat přeinstalaci operačního systému. Microsoft nezaručuje, že lze vyřešit problémy způsobující pomocí Editoru registru nesprávně. Pomocí Editoru registru na vlastní nebezpečí.
>
> Informace o zálohování, úpravách a obnovování registru najdete v tématu [informace o registru Windows pro pokročilé uživatele](https://support.microsoft.com/help/256986/windows-registry-information-for-advanced-users).

## <a name="modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Úprava chování inteligentního titulkování v okně zdroje dat

1. Otevřete okno příkazového řádku kliknutím **Start** a potom **spustit**.

2. Typ `regedit` v **spustit** dialogové okno a klikněte na tlačítko **OK**.

3. Rozbalte **HKEY_CURRENT_USER** > **software** > uzlu **Microsoft** > **VisualStudio** .

::: moniker range="vs-2017"

4. Pravým tlačítkem myši klikněte na uzel **15,0** a vytvořte nový **klíč** s názvem `Data Designers`.

::: moniker-end

::: moniker range=">=vs-2019"

4. Pravým tlačítkem myši klikněte na uzel **16,0** a vytvořte nový **klíč** s názvem `Data Designers`.

::: moniker-end

5. Klikněte pravým tlačítkem myši na uzel **Návrháři dat** a vytvořte tři nové řetězcové hodnoty:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. Klikněte pravým tlačítkem na hodnotu **SmartCaptionExpression** a vyberte **Upravit**.

7. Zadejte regulární výraz, který chcete, aby **zdroje dat** okna.

8. Klikněte pravým tlačítkem na hodnotu **SmartCaptionReplacement** a vyberte **Upravit**.

9. Zadejte náhradní řetězec ve formátu tak, jak chcete zobrazit tyto vzory se dají v regulárním výrazu odpovídá.

10. Klikněte pravým tlačítkem na hodnotu **SmartCaptionSuffix** a vyberte **Upravit**.

11. Zadejte všechny znaky, které se mají zobrazit na konci titulek.

    Při příštím přetáhněte položky z **zdroje dat** okně titulek popisky jsou vytvořeny pomocí nové hodnoty registru, které jsou k dispozici.

## <a name="turn-off-the-smart-captioning-feature"></a>Vypnutí funkce inteligentního titulkování

1. Otevřete okno příkazového řádku kliknutím **Start** a potom **spustit**.

2. Typ `regedit` v **spustit** dialogové okno a klikněte na tlačítko **OK**.

3. Rozbalte **HKEY_CURRENT_USER** > **software** > uzlu **Microsoft** > **VisualStudio** .

::: moniker range="vs-2017"

4. Pravým tlačítkem myši klikněte na uzel **15,0** a vytvořte nový **klíč** s názvem `Data Designers`.

::: moniker-end

::: moniker range=">=vs-2019"

4. Pravým tlačítkem myši klikněte na uzel **16,0** a vytvořte nový **klíč** s názvem `Data Designers`.

::: moniker-end

5. Klikněte pravým tlačítkem myši na uzel **Návrháři dat** a vytvořte tři nové řetězcové hodnoty:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. Klikněte pravým tlačítkem myši **SmartCaptionExpression** položky a vyberte **změnit**.

7. Zadejte `(.*)` pro hodnotu. To se bude shodovat celý řetězec.

8. Klikněte pravým tlačítkem myši **SmartCaptionReplacement** položky a vyberte **změnit**.

9. Zadejte `$1` pro hodnotu. To nahradí řetězec odpovídající hodnotu, která je celý řetězec tak, aby zůstane beze změny.

    Při příštím přetáhněte položky z **zdroje dat** popisky titulek okna, jsou vytvořeny s verzí bez úprav titulky.

## <a name="see-also"></a>Viz také:

- [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
