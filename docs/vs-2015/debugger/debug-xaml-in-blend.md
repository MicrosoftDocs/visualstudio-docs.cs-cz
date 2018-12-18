---
title: Ladění XAML v programu Blend | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 29a37182-2a2c-47e4-a4a9-2d5412738fed
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8b01fdc6962ea5a564537a083be4e9993533f1e4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51728108"
---
# <a name="debug-xaml-in-blend"></a>Ladění kódu XAML v programu Blend
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete použít nástroje v [!INCLUDE[blend_first](../includes/blend-first-md.md)] pro ladění XAML ve vaší aplikaci. Při vytváření projektu se zobrazí nějaké chyby v **výsledky** panelu. Klikněte dvakrát na chybu najděte značku týkající se chyby. Pokud potřebujete více místa k práci, můžete skrýt **výsledky** panel stisknutím klávesy F12.  
  
## <a name="syntax-errors"></a>Chyby syntaxe  
 Chyby syntaxe dojít, pokud XAML nebo soubory kódu na pozadí nepostupujte podle pravidla formátování jazyka. Popis chyby, pomůže vám pochopit, jak ho opravit. V seznamu také určuje název souboru a číslo řádku, kde dojde k chybě. XAML chyby jsou uvedené na **značek** kartu **výsledky** panelu.  
  
> [!TIP]
>  XAML je jazyk založený na formátu XML kód a řídí se pravidla syntaxe jazyka XML.  
  
 Některé běžné příčiny chyby syntaxe XAML:  
  
- Bylo zadáno chybně klíčového slova nebo je nesprávná velikost písmen.  
  
- Chybí uvozovky kolem atributů nebo textové řetězce.  
  
- XAML elementu chybí ukončovací značku.  
  
- Prvek XAML existuje v umístění, kde není povoleno.  
  
  Další informace o běžných syntaxe XAML, naleznete v tématu [průvodci syntaxí základní XAML](http://go.microsoft.com/fwlink/?LinkId=329942).  
  
  Také můžete zjišťovat a řešit chyby syntaxe jednoduchého kódu, chyby při kompilaci a chyby za běhu v [!INCLUDE[blend_subs](../includes/blend-subs-md.md)]. Použití modelu code-behind chyby může být však usnadňuje identifikaci a řešení v sadě Visual Studio.  
  
### <a name="debugging-sample-xaml-code"></a>Ladění vzorového kódu XAML  
 Následující příklad vás provede jednoduchou XAML ladicí relace v [!INCLUDE[blend_subs](../includes/blend-subs-md.md)].  
  
##### <a name="to-create-a-project"></a>Vytvoření projektu  
  
1. V [!INCLUDE[blend_subs](../includes/blend-subs-md.md)], otevřete **souboru** nabídky a pak klikněte na tlačítko **nový projekt**.  
  
    V **nový projekt** dialogovém okně se zobrazí na levé straně seznamu typů projektů. Po kliknutí na typu projektu, šablony projektů, které jsou s ní spojené se zobrazí na pravé straně.  
  
2. V seznamu typů projektů klepněte **XAML (Windows Store)**.  
  
3. V seznamu šablon projektu klikněte na tlačítko **prázdnou aplikaci**.  
  
4. V **název** textového pole, typ `DebuggingSample`.  
  
5. V **umístění** textové pole, ověřte umístění projektu.  
  
6. V **jazyk** klikněte na možnost **Visual C#** a potom klikněte na tlačítko **OK** pro vytvoření projektu.  
  
7. Klikněte pravým tlačítkem na návrhové ploše a potom klikněte na tlačítko **zobrazit zdroj** přepnout na **rozdělení** zobrazení.  
  
8. Zkopírujte následující kód kliknutím **kopírování** odkaz v pravém horním rohu kódu.  
  
   ```  
   <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>  
        <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>  
   </Grid>  
  
   ```  
  
9. Vyhledejte výchozí **mřížky**a vložte kód mezi otevírací a zavírací **mřížky** značky. Jakmile budete hotovi, váš kód by měl vypadat nějak takto:  
  
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
  
10. Stiskněte kombinaci kláves Ctrl + Shift + B a sestavte projekt.  
  
    Zobrazí se chybová zpráva, upozorní vás, který nemůže být sestaven projekt, a **výsledky** panel s chybami se zobrazí v dolní části aplikace.  
  
    ![Ladění XAML v programu Blend for Visual Studio](../debugger/media/blend-debugxaml-xaml.png "blend_debugXAML_XAML")  
  
### <a name="resolving-xaml-errors"></a>Řešení chyb XAML  
 Při zjištění chyb XAML, návrhovou plochu zobrazí upozornění, že váš projekt obsahuje neplatný kód. Protože případné chyby opravte seznam chyb v **výsledky** panel se aktualizuje. Po vyřešení všech chyb je povolená na návrhovou plochu a aplikace se zobrazí na návrhové ploše.  
  
##### <a name="to-resolve-the-xaml-errors"></a>Chcete-li vyřešit chyby XAML  
  
1. Dvakrát klikněte na první chybu v seznamu. Popis je "hodnotu ' <' není platná v atributu." Když dvakrát kliknete chyby, vyhledá ukazatele příslušné místo v kódu. `<` Předchozí `Button` je platný a ne atributem, jak je navrženo v chybové zprávě. Když se podíváte na předchozím řádku kódu, můžete si všimnout, že uzavírací uvozovky atributu `Top` chybí. Zadejte koncovými uvozovkami. Všimněte si, že seznam chyb v **výsledky** panelu aktualizace tak, aby odrážely změny.  
  
2. Klikněte dvakrát na popis "'0' není platný na začátku názvu." `Margin="0,149,0,0"` Zdá se být správně utvořena. Všimněte si však, že barevné kódování `Margin` se neshoduje s další výskyty `Margin` v kódu. Protože předchozí dvojice název/hodnota chybí uzavírací uvozovky (`VerticalAlignment="Top`), `Margin="` je pro čtení jako část hodnoty předchozí atributu a 0 je pro čtení jako začátek dvojici název/hodnota. Zadejte uzavírací uvozovky u `Top`. V seznamu chyb **výsledky** panelu aktualizace tak, aby odrážely změny.  
  
3. Klikněte dvakrát na zbývající chybu "je neshoda uzavírací značky XML"Tlačítko"." Ukazatel myši nachází v ukončovací **mřížky** značky (`</Grid>`), návrh, který je chyba uvnitř `Grid` objektu. Všimněte si, že druhá `Button` objektu chybí uzavírací značka. Po přidání ukončovací `/`, **výsledky** panel seznam se aktualizuje. Teď, když tyto počáteční chyby byly vyřešeny, dva další chyby byly zjištěny.  
  
4. Dvakrát klikněte na "člena 'content' není rozpoznaný nebo není přístupný." `c` v `content` by měl být velká písmena. Malá "c" nahraďte velká písmena "c".  
  
5. Dvakrát klikněte na "vlastnosti 'Mame' neexistuje v"<http://schemas.microsoft.com/winfx/2006/xaml>"oboru názvů." "M" v "Mame" by měl být "N" Nahraďte "M", "N" Teď, když XAML může být analyzován, aplikace se zobrazí na návrhové ploše.  
  
    ![Ladění XAML v programu Blend for Visual Studio](../debugger/media/blend-debugartboard-xaml.png "blend_debugArtboard_XAML")  
  
    Stiskněte kombinaci kláves Ctrl + Shift + B pro svůj projekt sestavit a potvrďte, že neexistují žádné zbývající chyby.  
  
## <a name="debugging-in-visual-studio"></a>Ladění v sadě Visual Studio  
 Můžete otevřít [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] projekty v sadě Visual Studio, které mají více snadno ladit kód ve vaší aplikaci. Chcete-li otevřít [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] projektu v sadě Visual Studio, klikněte pravým tlačítkem na projekt v **projekty** panelu a potom klikněte na **upravit v sadě Visual Studio**. Po dokončení vaší relace ladění v sadě Visual Studio, stiskněte kombinaci kláves Ctrl + Shift + S uložte všechny provedené změny a pak přejděte zpátky do [!INCLUDE[blend_subs](../includes/blend-subs-md.md)]. Zobrazí se výzva k opětovnému načtení projektu. Klikněte na tlačítko **Ano všem** pokračovat v práci [!INCLUDE[blend_subs](../includes/blend-subs-md.md)].  
  
 Další informace o ladění vaší aplikace najdete v tématu [aplikace Windows Store ladění ve Visual Studiu](http://go.microsoft.com/fwlink/?LinkId=329944).  
  
## <a name="getting-help"></a>Získání nápovědy  
 Pokud potřebujete další pomoc ladění vašeho [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] aplikace, můžete vyhledávat [fóra komunity aplikací pro Windows Store](http://go.microsoft.com/fwlink/?LinkId=280308) příspěvky související problém nebo odeslat dotaz.



