---
title: 'Krok 3: Nastavte vlastnosti svého formuláře | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 634ef037-1525-48c8-ac7f-abf04be69376
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 64e197e3f6f34cc46d91c330b4d5f80b3c6ce578
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49848628"
---
# <a name="step-3-set-your-form-properties"></a>Krok 3: Nastavte vlastnosti svého formuláře
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dále použijete **vlastnosti** okno a změně vzhledu formuláře.  
  
 ![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo")video verzi tohoto tématu naleznete v tématu [kurz 1: vytvoření prohlížeče obrázků v jazyce Visual Basic - Video 1](http://go.microsoft.com/fwlink/?LinkId=205209) nebo [kurz 1: vytvoření prohlížeče obrázků v jazyce C# – Video 1](http://go.microsoft.com/fwlink/?LinkId=205199). Tato videa používají starší verzi sady Visual Studio, takže existují mírné rozdíly v některých příkazech nabídek a jiných prvcích uživatelského rozhraní. Nicméně koncepty a postupy fungují podobně jako v aktuální verzi sady Visual Studio.  
  
### <a name="to-set-your-form-properties"></a>Chcete-li nastavit vlastnosti svého formuláře  
  
1. Ujistěte se, že se díváte na návrháře formulářů Windows. V sadě Visual Studio integrované vývojové prostředí (IDE), zvolte **Form1.cs [Design]** kartu (nebo **Form1.vb [Design]** kartu v jazyce Visual Basic).  
  
2. Klikněte kamkoli do formuláře **Form1** ji vyberte. Podívejte se na **vlastnosti** okno, které by nyní měly zobrazovat vlastnosti pro formulář. Formuláře mají různé vlastnosti. Můžete například nastavit popředí a pozadí, text nadpisu, který se zobrazí v horní části formuláře, velikost formuláře a dalších vlastností.  
  
   > [!NOTE]
   >  Pokud **vlastnosti** okno nezobrazí, ukončete program výběrem čtvercového **Zastavit ladění** tlačítko na panelu nástrojů nebo pouze zavřete okno. Pokud program je zastaven a stále nevidíte **vlastnosti** okna na řádku nabídek zvolte **zobrazení**, **okno vlastností**.  
  
3. Po výběru formuláře vyhledejte **Text** vlastnost **vlastnosti** okna. V závislosti na tom, jak je seznam seřazen může být potřeba posuňte se dolů. Zvolte **Text**, typ **prohlížeče obrázků**a stiskněte klávesu ENTER.  Formulář by měl mít nyní text **prohlížeče obrázků** v jeho záhlaví a **vlastnosti** okno by mělo vypadat jako na následujícím obrázku.  
  
    ![Okno vlastností](../ide/media/express-edittextproperty.png "Express_EditTextProperty")  
   Vlastnosti – okno  
  
   > [!NOTE]
   >  Vlastnosti mohou být seřazené podle kategorizovaného nebo abecedního zobrazení. Můžete přepínat mezi těmito dvěma zobrazeními pomocí tlačítek na **vlastnosti** okna. V tomto kurzu je snazší nalézt vlastnosti prostřednictvím abecedního zobrazení.  
  
4. Přejděte zpět do Návrháře formulářů Windows. Zvolte úchyt pro přetažení pravém formuláře, který je bílý čtvereček v pravém dolním formuláře a zobrazí se takto.  
  
    ![Úchyt pro přetažení](../ide/media/express-bottomrt-drag.png "Express_BottomRT_Drag")  
   Úchyt pro přetažení  
  
    Přetažením úchytu změnit velikost formuláře, takže je formulář širší a o něco vyšší.  
  
5. Podívejte se na **vlastnosti** okně a Všimněte si, že **velikost** je změněna vlastnost. **Velikost** vlastnost se změní pokaždé, když změníte velikost formuláře. Zkuste přetáhnout obslužnou rutinu formuláře ke změně jeho velikosti na formulář velikost přibližně 550, 350 (nemusí být přesné), což by mělo fungovat dobře pro tento projekt. Jako alternativu můžete zadat hodnoty přímo ve **velikost** vlastnost a potom stiskněte klávesu ENTER.  
  
6. Spusťte program znovu. Mějte na paměti, můžete použít některý z následujících metod ke spuštění programu.  
  
   - Zvolte **F5** klíč.  
  
   - V panelu nabídky zvolte **ladění**, **spustit ladění**.  
  
   - Na panelu nástrojů **spustit ladění** tlačítko, které se zobrazí takto.  
  
      ![Spuštění ladění tlačítka panelu nástrojů](../ide/media/express-icondebug.png "Express_IconDebug")  
     Spustit ladění tlačítka panelu nástrojů  
  
     Stejně jako dříve rozhraní IDE vytvoří a spustí program a zobrazí se okno.  
  
7. Před přechodem k dalšímu kroku zastavte program, protože rozhraní IDE neumožní změníte program během jejího běhu. Mějte na paměti, můžete použít některý z následujících metod k zastavení programu.  
  
   -   Na panelu nástrojů **Zastavit ladění** tlačítko.  
  
   -   V panelu nabídky zvolte **ladění**, **Zastavit ladění**.  
  
   -   Výběrem tlačítka X v horním rohu **Form1** okna.  
  
### <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat  
  
-   Přechod k dalšímu kroku výukového programu naleznete v tématu [krok 4: rozložení na svůj formulář pomocí ovládacího prvku TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md).  
  
-   Chcete-li vrátit k předchozímu kroku tutoriálu, přečtěte si téma [krok 2: Spusťte svůj Program](../ide/step-2-run-your-program.md).



