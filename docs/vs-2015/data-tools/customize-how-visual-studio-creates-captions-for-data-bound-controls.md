---
title: Přizpůsobit způsob, jak vytvořit titulky pro ovládací prvky vázané na data v sadě Visual Studio 2015 | Dokumentace Microsoftu
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c0e54f68ab7e34f1cfb6abb228f552cc3792a8b7
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77476922"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Úprava způsobu, kterým Visual Studio vytváří titulky pro ovládací prvky vázané daty
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Když přetáhnete položky z [okna zdroje dat](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) do Návrhář formulářů, bude se zvláštní aspekt považovat za přehrání. názvy sloupců v popiscích titulků se přeformátují na čitelnější řetězec, když se zjistí dvě nebo více slov, která se mají zřetězit dohromady. Můžete přizpůsobit způsob, jakým jsou tyto popisky vytvořeny, nastavením hodnot **SmartCaptionExpression**, **SmartCaptionReplacement**a **SmartCaptionSuffix** v klíči registru nástroje **HKEY_CURRENT_USER \software\microsoft\visualstudio\10.0\Data Designer** .

> [!NOTE]
> Tento klíč registru neexistuje, dokud ho vytvoříte.

 Inteligentní titulky jsou ovládány pomocí regulárního výrazu zadaného do hodnoty hodnoty **SmartCaptionExpression** . Přidání klíče registru **Návrháře dat** přepíše výchozí regulární výraz, který řídí popisky titulků. Další informace o regulárních výrazech naleznete v tématu [použití regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

 Následující tabulka popisuje hodnoty registru, které řídí titulků.

|Položky registru|Popis|
|-------------------|-----------------|
|**SmartCaptionExpression**|Regulární výraz tak, aby odpovídaly vaše postupy.|
|**SmartCaptionReplacement**|Formát pro zobrazení všech skupin odpovídajících v **SmartCaptionExpression**.|
|**SmartCaptionSuffix**|Volitelný řetězec pro připojení za účelem titulek.|

 Následující tabulka uvádí vnitřní výchozí nastavení pro tyto hodnoty registru.

|Položky registru|Výchozí hodnota|Vysvětlení|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|(\\\p{Ll}) (\\\p{Lu}) &#124;_+|Odpovídá znak malého písmene, za nímž následuje velkým písmenem nebo podtržítkem.|
|**SmartCaptionReplacement**|$1 $2|$1 představuje žádné znaky se shodou v první závorky výrazu a $2 představuje libovolné znaky shoda v druhé závorky. Nahrazení je první shodu, mezeru a druhý shoda.|
|**SmartCaptionSuffix**|:|Hodnota představuje znak připojenou k vráceného řetězce. Například pokud je titulek `Company Name`, přípona ho umožňuje `Company Name:`|

> [!CAUTION]
> Měli byste být opatrní při teď zrovna nic nedělá v editoru registru. Registr zálohovali začnete upravovat. Pokud Editor registru používán správně, můžete způsobit vážné problémy, které mohou vyžadovat přeinstalaci operačního systému. Microsoft nezaručuje, že lze vyřešit problémy způsobující pomocí Editoru registru nesprávně. Pomocí Editoru registru na vlastní nebezpečí.

### <a name="to-modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Chcete-li změnit inteligentní titulků chování okna zdroje dat

1. Otevřete příkazové okno kliknutím na **Start** a pak na **Spustit**.

2. Do dialogového okna **Spustit** zadejte `regedit` a klikněte na **OK**.

3. Rozbalte uzel **HKEY_CURRENT_USER** .

4. Rozbalte uzel **software** .

5. Rozbalte uzel **Microsoft** .

6. Rozbalte uzel **VisualStudio** .

7. Pravým tlačítkem myši klikněte na uzel **10,0** a vytvořte nový **klíč** s názvem `Data Designers`.

8. Klikněte pravým tlačítkem myši na uzel **Návrháři dat** a vytvořte novou **řetězcovou hodnotu** s názvem `SmartCaptionExpression`.

9. Klikněte pravým tlačítkem myši na uzel **Návrháři dat** a vytvořte novou **řetězcovou hodnotu** s názvem `SmartCaptionReplacement`.

10. Klikněte pravým tlačítkem myši na uzel **Návrháři dat** a vytvořte novou **řetězcovou hodnotu** s názvem `SmartCaptionSuffix`.

11. Klikněte pravým tlačítkem na položku **SmartCaptionExpression** a vyberte **Upravit**.

12. Zadejte regulární výraz, který má okno **zdroje dat** použít.

13. Klikněte pravým tlačítkem na položku **SmartCaptionReplacement** a vyberte **Upravit**.

14. Zadejte náhradní řetězec ve formátu tak, jak chcete zobrazit tyto vzory se dají v regulárním výrazu odpovídá.

15. Klikněte pravým tlačítkem na položku **SmartCaptionSuffix** a vyberte **Upravit**.

16. Zadejte všechny znaky, které se mají zobrazit na konci titulek.

     Při příštím přetahování položek z okna **zdroje dat** se popisky titulků vytvoří pomocí nových hodnot registru.

### <a name="to-turn-off-the-smart-captioning-feature"></a>Chcete-li vypnout funkci inteligentního titulků

1. Otevřete příkazové okno kliknutím na **Start** a pak na **Spustit**.

2. Do dialogového okna **Spustit** zadejte `regedit` a klikněte na **OK**.

3. Rozbalte uzel **HKEY_CURRENT_USER** .

4. Rozbalte uzel **software** .

5. Rozbalte uzel **Microsoft** .

6. Rozbalte uzel **VisualStudio** .

7. Pravým tlačítkem myši klikněte na uzel **10,0** a vytvořte nový **klíč** s názvem `Data Designers`.

8. Klikněte pravým tlačítkem myši na uzel **Návrháři dat** a vytvořte novou **řetězcovou hodnotu** s názvem `SmartCaptionExpression`.

9. Klikněte pravým tlačítkem myši na uzel **Návrháři dat** a vytvořte novou **řetězcovou hodnotu** s názvem `SmartCaptionReplacement`.

10. Klikněte pravým tlačítkem myši na uzel **Návrháři dat** a vytvořte novou **řetězcovou hodnotu** s názvem `SmartCaptionSuffix`.

11. Klikněte pravým tlačítkem na položku **SmartCaptionExpression** a vyberte **Upravit**.

12. Jako hodnotu zadejte `(.*)`. To se bude shodovat celý řetězec.

13. Klikněte pravým tlačítkem na položku **SmartCaptionReplacement** a vyberte **Upravit**.

14. Jako hodnotu zadejte `$1`. To nahradí řetězec odpovídající hodnotu, která je celý řetězec tak, aby zůstane beze změny.

     Při příštím přetahování položek z okna **zdroje dat** jsou popisky titulků vytvořeny s nezměněnými titulky.

## <a name="see-also"></a>Viz také
 [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
