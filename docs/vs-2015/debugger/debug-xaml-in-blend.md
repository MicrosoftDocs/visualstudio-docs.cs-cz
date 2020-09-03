---
title: Ladění XAML v Blendu | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "81444606"
---
# <a name="debug-xaml-in-blend"></a>Ladění kódu XAML v programu Blend
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí nástrojů v nástroji můžete [!INCLUDE[blend_first](../includes/blend-first-md.md)] LADIT XAML ve vaší aplikaci. Při sestavování projektu jsou všechny chyby zobrazeny na panelu **výsledků** . Dvojím kliknutím na chybu vyhledejte značku týkající se chyby. Pokud potřebujete více místa pro práci, můžete panel **výsledků** skrýt stisknutím klávesy F12.  
  
## <a name="syntax-errors"></a>Chyby syntaxe  
 Pokud soubory XAML nebo kódu na pozadí nedodržují pravidla formátování jazyka, dojde k chybám syntaxe. Popis chyby vám může pomoct pochopit, jak je opravit. V seznamu se také určuje název souboru a číslo řádku, ve kterém k chybě dochází. Chyby XAML jsou uvedeny na kartě **značky** na panelu **výsledků** .  
  
> [!TIP]
> XAML je jazyk značek založený na jazyce XML a následující pravidla syntaxe XML.  
  
 Některé běžné příčiny chyb syntaxe XAML:  
  
- Klíčové slovo bylo špatně napsáno nebo je nesprávné zadání velkých a malých písmen.  
  
- Okolo atributů nebo textových řetězců chybí uvozovky.  
  
- V elementu XAML chybí uzavírací značka.  
  
- Prvek XAML existuje v umístění, kde není povolen.  
  
  Další informace o běžných syntaxech jazyka XAML naleznete v tématu [základní průvodce syntaxí jazyka XAML](https://msdn.microsoft.com/library/windows/apps/hh700351.aspx).  
  
  Můžete také identifikovat a vyřešit jednoduché chyby syntaxe kódu na pozadí, chyby kompilace a běhové chyby v [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] . Chyby kódu na pozadí ale můžou být snáze identifikovatelné a řešitelné v aplikaci Visual Studio.  
  
### <a name="debugging-sample-xaml-code"></a>Ladění ukázkového kódu XAML  
 Následující příklad vás provede jednoduchou ladicí relací XAML v [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] .  
  
##### <a name="to-create-a-project"></a>Vytvoření projektu  
  
1. V aplikaci [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] otevřete nabídku **soubor** a poté klikněte na možnost **Nový projekt**.  
  
    V dialogovém okně **Nový projekt** se zobrazí seznam typů projektu na levé straně. Když kliknete na typ projektu, šablony projektu, které jsou k němu přidruženy, se zobrazí na pravé straně.  
  
2. V seznamu typů projektů klikněte na **XAML (Windows Store)**.  
  
3. V seznamu šablon projektů klikněte na **prázdná aplikace**.  
  
4. Do textového pole **název** zadejte `DebuggingSample` .  
  
5. V textovém poli **umístění** ověřte umístění projektu.  
  
6. V seznamu **jazyk** klikněte na možnost **Visual C#** a potom kliknutím na tlačítko **OK** vytvořte projekt.  
  
7. Klikněte pravým tlačítkem myši na návrhovou plochu a potom kliknutím na tlačítko **Zobrazit zdroj** přepněte na **rozdělené** zobrazení.  
  
8. Zkopírujte následující kód kliknutím na odkaz **Kopírovat** v pravém horním rohu kódu.  
  
   ```  
   <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>  
        <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>  
   </Grid>  
  
   ```  
  
9. Vyhledejte výchozí **mřížku**a vložte kód mezi otevírací a uzavírací značkou **mřížky** . Až budete hotovi, váš kód by měl vypadat takto:  
  
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
  
    Zobrazí se chybová zpráva s upozorněním, že projekt nelze sestavit, a na panelu **výsledků** se zobrazí chyby v dolní části aplikace.  
  
    ![Ladění kódu XAML v programu Blend pro Visual Studio](../debugger/media/blend-debugxaml-xaml.png "blend_debugXAML_XAML")  
  
### <a name="resolving-xaml-errors"></a>Řešení chyb XAML  
 Když jsou zjištěny chyby XAML, návrhová plocha zobrazí výstrahu, že projekt obsahuje neplatné označení. Při řešení chyb se seznam chyb na panelu **výsledky** aktualizuje. Po vyřešení všech chyb je návrhová plocha zapnutá a vaše aplikace se zobrazí na návrhové ploše.  
  
##### <a name="to-resolve-the-xaml-errors"></a>Řešení chyb XAML  
  
1. Dvakrát klikněte na první chybu v seznamu. Popis je "hodnota" < "není platná v atributu". " Když dvakrát kliknete na chybu, ukazatel najde odpovídající umístění v kódu. `<`Předchozí `Button` je platný a nikoli atribut, který je navržen v chybové zprávě. Pokud se podíváte na předchozí řádek kódu, všimnete si, že uzavírací uvozovky pro atribut `Top` chybí. Zadejte uzavírací uvozovky. Všimněte si, že seznam chyb na panelu **výsledky** se aktualizuje tak, aby odrážel vaše změny.  
  
2. Dvakrát klikněte na popis "0" není platný na začátku názvu. " `Margin="0,149,0,0"` Zdá se, že je správně vytvořený. Všimněte si však, že barevné kódování neodpovídá `Margin` ostatním instancím `Margin` v kódu. Vzhledem k tomu, že uzavírací uvozovky chybí v předchozí dvojici název/hodnota ( `VerticalAlignment="Top` ), `Margin="` jsou čteny jako součást hodnoty předcházejícího atributu a hodnota 0 je čtena jako začátek dvojice název/hodnota. Zadejte uzavírací uvozovky pro `Top` . Seznam chyb na panelu **výsledky** se aktualizuje tak, aby odrážel vaše změny.  
  
3. Dvakrát klikněte na zbývající chybu a "tlačítko uzavírací značky XML" se neshoduje. " Ukazatel je umístěn na pravé značce **mřížky** ( `</Grid>` ), což naznačuje, že chyba je uvnitř `Grid` objektu. Všimněte si, že v druhém `Button` objektu chybí uzavírací značka. Po přidání se `/` seznam panelů **výsledků** aktualizuje. Nyní, když byly vyřešeny tyto počáteční chyby, byly zjištěny dvě další chyby.  
  
4. Dvakrát klikněte na "obsah" není rozpoznán nebo není přístupný. " `c`V části `content` by měla být velká písmena. Nahraďte malý případ "c" velkým písmenem "c".  
  
5. Dvakrát klikněte na vlastnost mame neexistuje v `https://schemas.microsoft.com/winfx/2006/xaml` oboru názvů. "M" v "mame" musí být "N". Nahradí "M" za "N". Teď, když je možné XAML analyzovat, se aplikace zobrazí na návrhové ploše.  
  
    ![Ladění XAML v Blend pro Visual Studio](../debugger/media/blend-debugartboard-xaml.png "blend_debugArtboard_XAML")  
  
    Stisknutím kombinace kláves CTRL + SHIFT + B Sestavte projekt a potvrďte, že nejsou žádné zbývající chyby.  
  
## <a name="debugging-in-visual-studio"></a>Ladění v sadě Visual Studio  
 Můžete otevřít [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] projekty v aplikaci Visual Studio pro snazší ladění kódu v aplikaci. Chcete-li otevřít [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] projekt v aplikaci Visual Studio, klikněte pravým tlačítkem myši na projekt na panelu **projekty** a poté klikněte na možnost **Upravit v aplikaci Visual Studio**. Po dokončení ladění relace v aplikaci Visual Studio stiskněte kombinaci kláves CTRL + SHIFT + S a uložte všechny provedené změny a poté přepněte zpět na [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] . Zobrazí se výzva k opětovnému načtení projektu. Pokud chcete pokračovat v práci, klikněte na **Ano** [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] .  
  
 Další informace o ladění aplikace naleznete v tématu [ladění aplikací pro Windows Store v aplikaci Visual Studio](https://msdn.microsoft.com/library/windows/apps/hh441472.aspx).  
  
## <a name="getting-help"></a>Získání nápovědy  
 Pokud potřebujete další nápovědu k ladění vaší [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] aplikace, můžete ve [fórech komunity aplikací pro Windows Store](https://social.msdn.microsoft.com/Forums/windowsapps/home?category=windowsapps) vyhledat příspěvky související s vaším problémem nebo odeslat otázku.
