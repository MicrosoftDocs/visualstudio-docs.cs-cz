---
title: Ladění XAML v Blendu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 29a37182-2a2c-47e4-a4a9-2d5412738fed
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.technology: vs-ide-debug
ms.workload:
- uwp
ms.openlocfilehash: 9ac692c756aaa29b2b13f20eecd039154a28d80b
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/22/2020
ms.locfileid: "77558189"
---
# <a name="debug-xaml-in-blend"></a>Ladění kódu XAML v programu Blend

Pomocí nástrojů v Blend pro Visual Studio můžete ladit XAML ve vaší aplikaci. Při sestavování projektu jsou všechny chyby zobrazeny na panelu **výsledků** . Dvojím kliknutím na chybu vyhledejte značku týkající se chyby. Pokud potřebujete více místa pro práci, můžete panel **výsledků** skrýt stisknutím klávesy **F12**.

## <a name="syntax-errors"></a>Chyby syntaxe

Pokud soubory XAML nebo kódu na pozadí nedodržují pravidla formátování jazyka, dojde k chybám syntaxe. Popis chyby vám může pomoct pochopit, jak je opravit. V seznamu se také určuje název souboru a číslo řádku, ve kterém k chybě dochází. Chyby XAML jsou uvedeny na kartě **značky** na panelu **výsledků** .

> [!TIP]
> XAML je jazyk značek založený na jazyce XML a následující pravidla syntaxe XML.

Některé běžné příčiny chyb syntaxe XAML:

- Klíčové slovo bylo špatně napsáno nebo je nesprávné zadání velkých a malých písmen.

- Okolo atributů nebo textových řetězců chybí uvozovky.

- V elementu XAML chybí uzavírací značka.

- Prvek XAML existuje v umístění, kde není povolen.

Další informace o běžných syntaxech jazyka XAML naleznete v tématu [základní průvodce syntaxí jazyka XAML](/windows/uwp/xaml-platform/xaml-syntax-guide).

Můžete také identifikovat a vyřešit jednoduché chyby syntaxe kódu na pozadí, chyby kompilace a běhové chyby v Blendu. Chyby kódu na pozadí ale můžou být snáze identifikovatelné a řešitelné v aplikaci Visual Studio.

### <a name="debugging-sample-xaml-code"></a>Ladění ukázkového kódu XAML

Následující příklad vás provede jednoduchou ladicí relací XAML v Blendu.

#### <a name="to-create-a-project"></a>Vytvoření projektu

1. V Blendu otevřete nabídku **soubor** a pak klikněte na **Nový projekt**.

    V dialogovém okně **Nový projekt** se zobrazí seznam typů projektu na levé straně. Když kliknete na typ projektu, šablony projektu, které jsou k němu přidruženy, se zobrazí na pravé straně.

2. V seznamu typů projektů klikněte na možnost **univerzální pro Windows**.

3. V seznamu šablon projektů klikněte na **prázdná aplikace (univerzální pro Windows)** .

4. Do textového pole **název** zadejte `DebuggingSample`.

5. V textovém poli **umístění** ověřte umístění projektu.

6. V seznamu **jazyk** klikněte na možnost **vizuál C#** a potom kliknutím na tlačítko **OK** vytvořte projekt.

7. Klikněte pravým tlačítkem myši na návrhovou plochu a potom kliknutím na tlačítko **Zobrazit zdroj** přepněte na **rozdělené** zobrazení.

8. Zkopírujte následující kód kliknutím na odkaz **Kopírovat** v pravém horním rohu kódu.

   ```xml
   <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>
        <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>
   </Grid>
   ```

9. Vyhledejte výchozí **mřížku**a vložte kód mezi otevírací a uzavírací značkou **mřížky** . Až budete hotovi, váš kód by měl vypadat takto:

    ```xml
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

10. Stisknutím **kombinace kláves Ctrl**+**SHIFT**+**B** Sestavte projekt.

    Zobrazí se chybová zpráva s upozorněním, že projekt nelze sestavit, a na panelu **výsledků** se zobrazí chyby v dolní části aplikace.

    ![Ladění kódu XAML v programu Blend pro Visual Studio](../debugger/media/blend_debugxaml_xaml.png "blend_debugXAML_XAML")

### <a name="resolve-xaml-errors"></a>Vyřešit chyby XAML

Když jsou zjištěny chyby XAML, návrhová plocha zobrazí výstrahu, že projekt obsahuje neplatné označení. Při řešení chyb se seznam chyb na panelu **výsledky** aktualizuje. Po vyřešení všech chyb je návrhová plocha zapnutá a vaše aplikace se zobrazí na návrhové ploše.

#### <a name="to-resolve-the-xaml-errors"></a>Řešení chyb XAML

1. Dvakrát klikněte na první chybu v seznamu. Popis je "hodnota" < "není platná v atributu". " Když dvakrát kliknete na chybu, ukazatel najde odpovídající umístění v kódu. `<` předchozí `Button` je platný, a nikoli atribut navrhovaný v chybové zprávě. Pokud se podíváte na předchozí řádek kódu, všimnete si, že uzavírací uvozovky pro atribut `Top` chybět. Zadejte uzavírací uvozovky. Všimněte si, že seznam chyb na panelu **výsledky** se aktualizuje tak, aby odrážel vaše změny.

2. Dvakrát klikněte na popis "0" není platný na začátku názvu. " Zdá se, že `Margin="0,149,0,0"` správně vytvořená. Všimněte si však, že barevné kódování `Margin` neodpovídá ostatním instancím `Margin` v kódu. Vzhledem k tomu, že uzavírací uvozovky chybí v předchozí dvojici název/hodnota (`VerticalAlignment="Top`), `Margin="` je čtena jako součást hodnoty předcházejícího atributu a hodnota 0 je čtena jako začátek dvojice název/hodnota. Zadejte uzavírací uvozovky pro `Top`. Seznam chyb na panelu **výsledky** se aktualizuje tak, aby odrážel vaše změny.

3. Dvakrát klikněte na zbývající chybu a "tlačítko uzavírací značky XML" se neshoduje. " Ukazatel je umístěn na pravé značce **mřížky** (`</Grid>`), což naznačuje, že chyba je uvnitř objektu `Grid`. Všimněte si, že v druhém objektu `Button` chybí uzavírací značka. Po přidání uzavírací `/`se seznam panelu **výsledků** aktualizuje. Nyní, když byly vyřešeny tyto počáteční chyby, byly zjištěny dvě další chyby.

4. Dvakrát klikněte na "obsah" není rozpoznán nebo není přístupný. " `c` v `content` by měla být velká písmena. Nahraďte malý případ "c" velkým písmenem "c".

5. Dvakrát klikněte na vlastnost mame neexistuje v oboru názvů `http://schemas.microsoft.com/winfx/2006/xaml`. "M" v "mame" musí být "N". Nahradí "M" za "N". Teď, když je možné XAML analyzovat, se aplikace zobrazí na návrhové ploše.

    ![Ladění XAML v Blend pro Visual Studio](../debugger/media/blend_debugartboard_xaml.png "blend_debugArtboard_XAML")

    Stisknutím **kombinace kláves Ctrl**+**SHIFT**+**B** Sestavte projekt a potvrďte, že nejsou žádné zbývající chyby.

## <a name="debug-in-visual-studio"></a>Ladění v sadě Visual Studio

Projekty Blendu v aplikaci Visual Studio můžete otevřít pro snazší ladění kódu v aplikaci. Chcete-li otevřít projekt Blend v aplikaci Visual Studio, klikněte pravým tlačítkem myši na projekt na panelu **projekty** a potom klikněte na možnost **Upravit v aplikaci Visual Studio**. Po dokončení ladění relace v aplikaci Visual Studio stiskněte kombinaci kláves CTRL + SHIFT + S a uložte všechny změny a pak přepněte zpět do Blendu. Zobrazí se výzva k opětovnému načtení projektu. Pokud chcete pokračovat v práci v Blendu, klikněte na **Ano** .

Další informace o ladění aplikace naleznete v tématu [ladění aplikací pro UWP v aplikaci Visual Studio](../debugger/debugging-windows-store-and-windows-universal-apps.md).

## <a name="get-help"></a>Podpora

Pokud potřebujete další nápovědu k ladění aplikace Blendu, můžete ve [fórech komunity aplikací pro UWP](https://social.msdn.microsoft.com/Forums/windowsapps/home?category=windowsapps) vyhledat příspěvky související s vaším problémem nebo odeslat otázku.
