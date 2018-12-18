---
title: Přizpůsobit způsob, jak vytvořit titulky pro ovládací prvky vázané na data v sadě Visual Studio 2015 | Dokumentace Microsoftu
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 38d2e1241c3b16e5bb5cc66531515688d75d52d1
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065384"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Úprava způsobu, kterým Visual Studio vytváří titulky pro ovládací prvky vázané daty
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Při přetažení položky z [okna zdroje dat](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) do Návrháře formulářů Windows, zvláštní pozornost vstupu do play: názvy sloupců v popiscích titulek jsou přeformátována na řetězec čitelnější, pokud dvě nebo více slov jsou nenašel se nedá zřetězit dohromady. Můžete změnit způsob, ve kterém jsou tyto popisky vytvořené, tak, že nastavíte **SmartCaptionExpression**, **SmartCaptionReplacement**, a **SmartCaptionSuffix** hodnoty v **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Data návrháři** klíč registru.

> [!NOTE]
>  Tento klíč registru neexistuje, dokud ho vytvoříte.

 Inteligentní titulky řídí regulárních výrazů do hodnoty **SmartCaptionExpression** hodnotu. Přidávání **návrháře dat** klíč registru přepisuje výchozí regulární výraz, který řídí titulků. Další informace o formátování regulárních výrazů, naleznete v tématu [pomocí regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

 Následující tabulka popisuje hodnoty registru, které řídí titulků.

|Položky registru|Popis|
|-------------------|-----------------|
|**SmartCaptionExpression**|Regulární výraz tak, aby odpovídaly vaše postupy.|
|**SmartCaptionReplacement**|Formát, který se zobrazí všechny skupiny se shodou v **SmartCaptionExpression**.|
|**SmartCaptionSuffix**|Volitelný řetězec pro připojení za účelem titulek.|

 Následující tabulka uvádí vnitřní výchozí nastavení pro tyto hodnoty registru.

|Položky registru|Výchozí hodnota|Vysvětlení|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|(\\\p{Ll}) (\\\p{Lu})&#124;_ +|Odpovídá znak malého písmene, za nímž následuje velkým písmenem nebo podtržítkem.|
|**SmartCaptionReplacement**|$1 $2|$1 představuje žádné znaky se shodou v první závorky výrazu a $2 představuje libovolné znaky shoda v druhé závorky. Nahrazení je první shodu, mezeru a druhý shoda.|
|**SmartCaptionSuffix**|:|Hodnota představuje znak připojenou k vráceného řetězce. Například, pokud je popisek `Company Name`, přípona umožňuje `Company Name:`|

> [!CAUTION]
>  Měli byste být opatrní při teď zrovna nic nedělá v editoru registru. Registr zálohovali začnete upravovat. Pokud Editor registru používán správně, můžete způsobit vážné problémy, které mohou vyžadovat přeinstalaci operačního systému. Microsoft nezaručuje, že lze vyřešit problémy způsobující pomocí Editoru registru nesprávně. Pomocí Editoru registru na vlastní nebezpečí.
>
>  Obsahuje pokyny pro zálohování, úpravy a obnovení registru následujícím článku znalostní báze: [Popis registru Microsoft Windows](http://support.microsoft.com/default.aspx?scid=kb;en-us;256986) (http://support.microsoft.com/default.aspx?scid=kb; en-us; 256986)

### <a name="to-modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Chcete-li změnit inteligentní titulků chování okna zdroje dat

1.  Otevřete okno příkazového řádku kliknutím **Start** a potom **spustit**.

2.  Typ `regedit` v **spustit** dialogové okno a klikněte na tlačítko **OK**.

3.  Rozbalte **HKEY_CURRENT_USER** uzlu.

4.  Rozbalte **softwaru** uzlu.

5.  Rozbalte **Microsoft** uzlu.

6.  Rozbalte **VisualStudio** uzlu.

7.  Klikněte pravým tlačítkem myši **10.0** uzel a vytvořte nový **klíč** s názvem `Data Designers`.

8.  Klikněte pravým tlačítkem myši **návrháře dat** uzel a vytvořte nový **řetězcovou hodnotu** s názvem `SmartCaptionExpression`.

9. Klikněte pravým tlačítkem myši **návrháře dat** uzel a vytvořte nový **řetězcovou hodnotu** s názvem `SmartCaptionReplacement`.

10. Klikněte pravým tlačítkem myši **návrháře dat** uzel a vytvořte nový **řetězcovou hodnotu** s názvem `SmartCaptionSuffix`.

11. Klikněte pravým tlačítkem myši **SmartCaptionExpression** položky a vyberte **změnit**.

12. Zadejte regulární výraz, který chcete, aby **zdroje dat** okna.

13. Klikněte pravým tlačítkem myši **SmartCaptionReplacement** položky a vyberte **změnit**.

14. Zadejte náhradní řetězec ve formátu tak, jak chcete zobrazit tyto vzory se dají v regulárním výrazu odpovídá.

15. Klikněte pravým tlačítkem myši **SmartCaptionSuffix** položky a vyberte **změnit**.

16. Zadejte všechny znaky, které se mají zobrazit na konci titulek.

     Při příštím přetáhněte položky z **zdroje dat** okně titulek popisky jsou vytvořeny pomocí nové hodnoty registru, které jsou k dispozici.

### <a name="to-turn-off-the-smart-captioning-feature"></a>Chcete-li vypnout funkci inteligentního titulků

1.  Otevřete okno příkazového řádku kliknutím **Start** a potom **spustit**.

2.  Typ `regedit` v **spustit** dialogové okno a klikněte na tlačítko **OK**.

3.  Rozbalte **HKEY_CURRENT_USER** uzlu.

4.  Rozbalte **softwaru** uzlu.

5.  Rozbalte **Microsoft** uzlu.

6.  Rozbalte **VisualStudio** uzlu.

7.  Klikněte pravým tlačítkem myši **10.0** uzel a vytvořte nový **klíč** s názvem `Data Designers`.

8.  Klikněte pravým tlačítkem myši **návrháře dat** uzel a vytvořte nový **řetězcovou hodnotu** s názvem `SmartCaptionExpression`.

9. Klikněte pravým tlačítkem myši **návrháře dat** uzel a vytvořte nový **řetězcovou hodnotu** s názvem `SmartCaptionReplacement`.

10. Klikněte pravým tlačítkem myši **návrháře dat** uzel a vytvořte nový **řetězcovou hodnotu** s názvem `SmartCaptionSuffix`.

11. Klikněte pravým tlačítkem myši **SmartCaptionExpression** položky a vyberte **změnit**.

12. Zadejte `(.*)` pro hodnotu. To se bude shodovat celý řetězec.

13. Klikněte pravým tlačítkem myši **SmartCaptionReplacement** položky a vyberte **změnit**.

14. Zadejte `$1` pro hodnotu. To nahradí řetězec odpovídající hodnotu, která je celý řetězec tak, aby zůstane beze změny.

     Při příštím přetáhněte položky z **zdroje dat** popisky titulek okna, jsou vytvořeny s verzí bez úprav titulky.

## <a name="see-also"></a>Viz také
 [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
