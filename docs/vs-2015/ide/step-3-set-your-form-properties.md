---
title: 'Krok 3: nastavte vlastnosti formuláře | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 634ef037-1525-48c8-ac7f-abf04be69376
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f05e91c13b1a9c52b5afad6942e5847643aa9490
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851552"
---
# <a name="step-3-set-your-form-properties"></a>Krok 3: Nastavte vlastnosti svého formuláře
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dále pomocí okna **vlastnosti** změníte vzhled formuláře.

 ![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo") Verzi videa tohoto tématu najdete v tématu [kurz 1: vytvoření prohlížeče obrázků v Visual Basic-video 1](https://msdn.microsoft.com/vbasic/gg315352.aspx) nebo [kurz 1: vytvoření prohlížeče obrázků ve C# videu 1](https://msdn.microsoft.com/vcsharp/gg278409.aspx). Tato videa používají starší verzi sady Visual Studio, takže existují mírné rozdíly v některých příkazech nabídky a dalších prvcích uživatelského rozhraní. Koncepty a postupy však fungují podobně v aktuální verzi sady Visual Studio.

### <a name="to-set-your-form-properties"></a>Nastavení vlastností formuláře

1. Ujistěte se, že se díváte na Návrhář formulářů. V integrovaném vývojovém prostředí (IDE) sady Visual Studio vyberte kartu **Form1.cs [Design]** (nebo kartu **Form1. vb [design]** v Visual Basic).

2. Zvolte libovolné místo uvnitř formuláře **Form1** a vyberte ho. Podívejte se na okno **vlastnosti** , ve kterém by se teď měly zobrazovat vlastnosti formuláře. Formuláře mají různé vlastnosti. Například můžete nastavit barvu popředí a pozadí, text nadpisu, který se zobrazí v horní části formuláře, velikost formuláře a další vlastnosti.

   > [!NOTE]
   > Pokud se okno **vlastnosti** nezobrazí, ukončete program výběrem čtvercového tlačítka **Zastavit ladění** na panelu nástrojů nebo pouze zavřít okno. Pokud je program zastaven a stále nevidíte okno **vlastnosti** , v řádku nabídek vyberte možnost **zobrazení**, **okno Vlastnosti**.

3. Po výběru formuláře vyhledejte vlastnost **text** v okně **vlastnosti** . V závislosti na tom, jak je seznam seřazený, se možná budete muset posunout dolů. Zvolte **text**, zadejte **Prohlížeč obrázků**a pak zvolte Enter.  Formulář by měl mít nyní v záhlaví text **Viewer** a okno **vlastnosti** by mělo vypadat podobně jako na následujícím obrázku.

    ![Okno Vlastnosti](../ide/media/express-edittextproperty.png "Express_EditTextProperty") okno Vlastnosti

   > [!NOTE]
   > Vlastnosti lze seřadit podle kategorií nebo zobrazení podle abecedy. Mezi těmito dvěma zobrazeními můžete přepínat pomocí tlačítek v okně **vlastnosti** . V tomto kurzu je snazší najít vlastnosti pomocí abecedního zobrazení.

4. Vraťte se na Návrhář formulářů. Vyberte táhlo v pravém dolním rohu formuláře, což je malé bílé čtverce v pravém dolním rohu formuláře a zobrazí se takto.

    ![Přetáhněte popisovač](../ide/media/express-bottomrt-drag.png "Express_BottomRT_Drag") Přetáhněte popisovač

    Přetažením úchytu můžete změnit velikost formuláře, takže je formulář širší a trochu vyšší.

5. Podívejte se na okno **vlastnosti** a Všimněte si, že se změnila vlastnost **Size** . Vlastnost **Size** se změní pokaždé, když změníte velikost formuláře. Zkuste přetáhnout táhlo formuláře, aby se změnila velikost formuláře přibližně 550, 350 (není potřeba přesně), což by mělo pro tento projekt dobře fungovat. Alternativně můžete zadat hodnoty přímo do vlastnosti **Size** a pak zvolit klávesu ENTER.

6. Spusťte program znovu. Nezapomeňte, že ke spuštění programu můžete použít kteroukoli z následujících metod.

   - Klikněte na klávesu **F5** .

   - Na řádku nabídek klikněte na položku **ladit**, **Spustit ladění**.

   - Na panelu nástrojů klikněte na tlačítko **Spustit ladění** , které se zobrazí takto.

      ![Spustit ladění – tlačítko panelu nástrojů](../ide/media/express-icondebug.png "Express_IconDebug") Spustit ladění – tlačítko panelu nástrojů

     Stejně jako předtím, rozhraní IDE sestaví a spustí program a zobrazí se okno.

7. Než budete pokračovat k dalšímu kroku, zastavte program, protože rozhraní IDE vám neumožní změnit program, pokud je spuštěný. Nezapomeňte, že k zastavení programu můžete použít kteroukoli z následujících metod.

   - Na panelu nástrojů klikněte na tlačítko **Zastavit ladění** .

   - Na řádku nabídek klikněte na položku **ladit**, **Zastavit ladění**.

   - Klikněte na tlačítko X v horním rohu okna **Form1** .

### <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Chcete-li přejít na další krok kurzu, viz [Krok 4: rozložení formuláře pomocí ovládacího prvku TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md).

- Pokud se chcete vrátit k předchozímu kroku kurzu, přečtěte si [článek krok 2: spuštění programu](../ide/step-2-run-your-program.md).
