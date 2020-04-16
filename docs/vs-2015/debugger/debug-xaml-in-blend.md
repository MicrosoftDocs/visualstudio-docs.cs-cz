---
title: Ladění XAML v blendu | Dokumenty společnosti Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 29a37182-2a2c-47e4-a4a9-2d5412738fed
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8e032f9f99087df26c82b4984c2267a35236bf6e
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444606"
---
# <a name="debug-xaml-in-blend"></a>Ladění kódu XAML v programu Blend
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí nástrojů v [!INCLUDE[blend_first](../includes/blend-first-md.md)] aplikaci můžete ladit XAML. Při vytváření projektu se v panelu **Výsledky** zobrazí všechny chyby. Poklepáním na chybu vyhledejte značky související s chybou. Pokud potřebujete více místa pro práci, můžete skrýt panel Výsledky stisknutím **klávesy** F12.  
  
## <a name="syntax-errors"></a>Chyby syntaxe  
 Syntaxe chyby dojít, pokud XAML nebo kód na pozadí soubory nedodržují pravidla formátování jazyka. Popis chyby vám může pomoci pochopit, jak ji opravit. Seznam také určuje název souboru a číslo řádku, kde dojde k chybě. Chyby XAML jsou uvedeny na kartě **Poznámky** v panelu **Výsledky.**  
  
> [!TIP]
> XAML je značkovací jazyk založený na XML a řídí se pravidly syntaxe XML.  
  
 Některé běžné příčiny chyb syntaxe XAML jsou:  
  
- Klíčové slovo bylo chybně napsáno nebo je chybná velká písmena.  
  
- Kolem atributů nebo textových řetězců chybí uvozovky.  
  
- Prvek XAML chybí uzavírací značka.  
  
- Prvek XAML existuje v umístění, kde není povoleno.  
  
  Další informace o běžné syntaxi XAML naleznete v [příručce Basic XAML syntaxe .](https://msdn.microsoft.com/library/windows/apps/hh700351.aspx)  
  
  Můžete také identifikovat a vyřešit jednoduché chyby syntaxe napozadí, [!INCLUDE[blend_subs](../includes/blend-subs-md.md)]chyby kompilace a chyby za běhu v . Chyby na pozadí kódu však může být snazší identifikovat a vyřešit v sadě Visual Studio.  
  
### <a name="debugging-sample-xaml-code"></a>Ladění ukázkového kódu XAML  
 Následující příklad vás provede jednoduchou ladicí relací [!INCLUDE[blend_subs](../includes/blend-subs-md.md)]XAML v .  
  
##### <a name="to-create-a-project"></a>Vytvoření projektu  
  
1. V [!INCLUDE[blend_subs](../includes/blend-subs-md.md)]aplikaci otevřete nabídku **Soubor** a klepněte na tlačítko **Nový projekt**.  
  
    V dialogovém okně **Nový projekt** se na levé straně zobrazí seznam typů projektů. Když klepnete na typ projektu, šablony projektu, které jsou k němu přidruženy, se zobrazí na pravé straně.  
  
2. V seznamu typů projektů klikněte na **XAML (Windows Store)**.  
  
3. V seznamu šablon projektů klikněte na **Prázdná aplikace**.  
  
4. Do **Name** textového pole `DebuggingSample`Název zadejte .  
  
5. V textovém poli **Umístění** ověřte umístění projektu.  
  
6. V seznamu **Jazyk** klepněte na **položku Visual C#** a potom klepnutím na tlačítko **OK** vytvořte projekt.  
  
7. Klikněte pravým tlačítkem myši na návrhovou plochu a potom kliknutím na **Zobrazit zdroj** přepněte do **rozděleného** zobrazení.  
  
8. Kliknutím na odkaz **Kopírovat** v pravém horním rohu kódu zkopírujte následující kód.  
  
   ```  
   <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>  
        <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>  
   </Grid>  
  
   ```  
  
9. Vyhledejte výchozí **mřížku**a vložte kód mezi otevírací a uzavírací značky **Mřížka.** Po dokončení by měl kód vypadat takto:  
  
    ```  
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">  
         <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>  
              <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>  
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">  
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>  
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>  
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>  
         </Grid>  
    </Grid>  
  
    ```  
  
10. Stisknutím kláves CTRL+SHIFT+B sestavte projekt.  
  
    Zobrazí se chybová zpráva s upozorněním, že projekt nelze sestavit, a v dolní části aplikace se zobrazí panel **Výsledky** se seznamem chyb.  
  
    ![Ladění kódu XAML v programu Blend pro Visual Studio](../debugger/media/blend-debugxaml-xaml.png "blend_debugXAML_XAML")  
  
### <a name="resolving-xaml-errors"></a>Řešení chyb XAML  
 Když jsou zjištěny chyby XAML, návrhová plocha zobrazí výstrahu, že projekt obsahuje neplatné značky. Při řešení chyb se aktualizuje seznam chyb v panelu **Výsledky.** Po vyřešení všech chyb je povolena návrhová plocha a aplikace se zobrazí na návrhové ploše.  
  
##### <a name="to-resolve-the-xaml-errors"></a>Řešení chyb XAML  
  
1. Poklepejte na první chybu v seznamu. Popis je "Hodnota < není v atributu platná." Po poklepání na chybu ukazatel najde odpovídající umístění v kódu. Předchozí `<` `Button` je platný a není atribut, jak je navrženo v chybové zprávě. Pokud se podíváte na předchozí řádek kódu, zjistíte, že chybí `Top` uzavírací uvozovky pro atribut. Zadejte uzavírací uvozovky. Všimněte si, že seznam chyb v panelu **Výsledky** se aktualizuje tak, aby odrážel vaše změny.  
  
2. Poklepejte na popis '0' není platný na začátku názvu." `Margin="0,149,0,0"`se zdá být dobře tvarované. Všimněte si však, `Margin` že barevné kódování neodpovídá ostatním instancím `Margin` v kódu. Vzhledem k tomu, že chybí uzavírací uvozovky z předchozího páru název/hodnota (`VerticalAlignment="Top`), `Margin="` je přečtenjako součást hodnoty předchozího atributu a 0 se čte jako začátek páru název/hodnota. Zadejte uzavírací `Top`uvozovky pro . Seznam chyb v panelu **Výsledky** se aktualizuje tak, aby odrážel vaše změny.  
  
3. Poklepejte na zbývající chybu "Uzavírací značka XML 'Button' je neodpovídající." Ukazatel je umístěn na **Grid** uzavírací`</Grid>`značce Grid ( `Grid` ), což naznačuje, že chyba je uvnitř objektu. Všimněte si, že druhý `Button` objekt chybí uzavírací značku. Po přidání uzávěrky `/`se aktualizuje seznam panelu **Výsledky.** Nyní, když byly tyto počáteční chyby vyřešeny, byly identifikovány dvě další chyby.  
  
4. Poklepejte na položku "Člen 'obsah' není rozpoznán nebo není přístupný. In `c` `content` by měl být velkými písmeny. Nahraďte malé písmeno "c" s velkými písmeny "c".  
  
5. Poklepejte na vlastnost Mame neexistuje v `https://schemas.microsoft.com/winfx/2006/xaml` oboru názvů." "M" v "Mame" by mělo být "N". Nahraďte "M" slovem "N". Teď, když xaml lze analyzovat, aplikace se zobrazí na návrhové ploše.  
  
    ![Ladění XAML v prolnutí pro Visual Studio](../debugger/media/blend-debugartboard-xaml.png "blend_debugArtboard_XAML")  
  
    Stisknutím kombinace kláves Ctrl+Shift+B vytvořte projekt a potvrďte, že nedochází k žádným chybám.  
  
## <a name="debugging-in-visual-studio"></a>Ladění v sadě Visual Studio  
 Můžete otevřít [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] projekty v Sadě Visual Studio snadněji ladit kód ve vaší aplikaci. Chcete-li [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] otevřít projekt v sadě Visual Studio, klepněte na něj pravým tlačítkem myši v panelu **Projekty** a potom klepněte na příkaz **Upravit v sadě Visual Studio**. Po dokončení relace ladění v sadě Visual Studio uložte stisknutím kombinace kláves Ctrl+Shift+S všechny [!INCLUDE[blend_subs](../includes/blend-subs-md.md)]změny a přepněte zpět na . Budete vyzváni k opětovnému načtení projektu. Chcete-li pokračovat v [!INCLUDE[blend_subs](../includes/blend-subs-md.md)]práci v souboru , klepněte na tlačítko **Ano na vše.**  
  
 Další informace o ladění aplikace najdete v tématu [Ladění aplikací pro Windows Store ve Visual Studiu](https://msdn.microsoft.com/library/windows/apps/hh441472.aspx).  
  
## <a name="getting-help"></a>Získání nápovědy  
 Pokud potřebujete další pomoc s [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] laděním aplikace, můžete ve [fórech komunity aplikací pro Windows Store](https://social.msdn.microsoft.com/Forums/windowsapps/home?category=windowsapps) vyhledávat příspěvky související s vaším problémem nebo zveřejnit otázku.
